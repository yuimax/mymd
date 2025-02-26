# 質問
MkDocsで、
MarkdownをHTMLに変換する際に、
img要素があればファイルから画像サイズを取得し、
そのimg要素のwidth,height属性に反映させたいです。  
これをMkDocsのプラグインとして実現する方法を教えてください。 

# 回答 (ChatGPT)
MkDocsのプラグインを作成して、MarkdownをHTMLに変換する際に`img`要素を解析し、ローカルの画像ファイルのサイズを取得して`width`と`height`属性を追加する方法を説明します。

## 1. 必要なライブラリをインストール
画像のサイズを取得するために`Pillow`を使用します。インストールされていない場合は、以下のコマンドでインストールしてください。

```sh
pip install pillow
```

## 2. MkDocsのカスタムプラグインを作成
MkDocsでは、カスタムプラグインを作成してMarkdownのHTML変換処理をフックできます。以下のような`image_size_plugin.py`を作成します。

```python
import os
import re
from markdown.postprocessors import Postprocessor
from markdown.extensions import Extension
from PIL import Image
from mkdocs.plugins import BasePlugin

class ImageSizePostprocessor(Postprocessor):
    def __init__(self, md, docs_dir):
        super().__init__(md)
        self.docs_dir = docs_dir  # ドキュメントのルートディレクトリ

    def run(self, text):
        img_pattern = re.compile(r'<img\s+([^>]*?src="([^"]+)"[^>]*?)>', re.IGNORECASE)
        
        def replace_img_tag(match):
            img_tag = match.group(0)
            attrs = match.group(1)
            src = match.group(2)

            # 画像のフルパスを取得
            img_path = os.path.join(self.docs_dir, src)
            if os.path.exists(img_path):
                try:
                    with Image.open(img_path) as img:
                        width, height = img.size
                    # width, heightを追加
                    if 'width=' not in attrs and 'height=' not in attrs:
                        new_attrs = f'{attrs} width="{width}" height="{height}"'
                        return f'<img {new_attrs}>'
                except Exception as e:
                    print(f"Failed to open image {src}: {e}")
            return img_tag

        return img_pattern.sub(replace_img_tag, text)


class ImageSizeExtension(Extension):
    def __init__(self, docs_dir):
        self.docs_dir = docs_dir
        super().__init__()

    def extendMarkdown(self, md):
        md.postprocessors.register(ImageSizePostprocessor(md, self.docs_dir), 'image_size', 0)


class ImageSizePlugin(BasePlugin):
    def on_post_page(self, output, page, config):
        extension = ImageSizeExtension(config['docs_dir'])
        page.markdown.md.registerExtension(extension)
        return page.markdown.convert(output)
```

## 3. `mkdocs.yml`にプラグインを登録
`mkdocs.yml` に以下を追加します。

```yaml
plugins:
  - search
  - image-size
```

## 4. プラグインを認識させる
プラグインを`mkdocs`で使えるようにするため、`setup.py`を作成してパッケージ化します。

```python
from setuptools import setup, find_packages

setup(
    name="mkdocs-image-size",
    version="0.1",
    packages=find_packages(),
    install_requires=["mkdocs", "Pillow"],
    entry_points={
        "mkdocs.plugins": [
            "image-size = image_size_plugin:ImageSizePlugin",
        ]
    },
)
```

以下のコマンドでインストールします。

```sh
pip install -e .
```

## 5. 動作確認
`mkdocs serve` を実行し、`img`タグに`width`と`height`が追加されているか確認してください。

---

このプラグインは、`docs`ディレクトリ内の画像に対して`width`と`height`を自動で追加する仕組みになっています。