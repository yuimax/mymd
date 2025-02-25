# ����
markd.js �� Markdown ���@�ɓƎ��̊g����ǉ����A�摜�T�C�Y���w��\�ɂł��܂����B

# �� (Google Gemini)
�͂��AMarkdown�̕��@�ɓƎ��̊g����ǉ����ĉ摜�T�C�Y���w�肷�邱�Ƃ͉\�ł��Bmarked.js�𗘗p����ꍇ�A�ȉ��̕��@�Ŏ����ł��܂��B

**1. marked.js�̊g���@�\�����p����**

marked.js�ɂ́Alexer��renderer���J�X�^�}�C�Y���邱�Ƃ�Markdown�̉�́E�ϊ��������g������@�\������܂��B����𗘗p���āA�摜�T�C�Y���w�肷�邽�߂̓Ǝ��̕��@���`���܂��B

**2. �Ǝ��̕��@���`����**

�Ⴆ�΁A�ȉ��̂悤�ȕ��@�ŉ摜�T�C�Y���w�肷��Ƃ��܂��B

```markdown
![��փe�L�X�g](�摜��URL){width=300 height=200}
```

���̕��@�ł́A`{}`�̒���`width`��`height`�̒l���w�肷�邱�ƂŁA�摜�̕��ƍ�����ݒ�ł��܂��B

**3. marked.js��lexer���J�X�^�}�C�Y����**

lexer���J�X�^�}�C�Y���āA��L�̕��@����͂ł���悤�ɂ��܂��B��̓I�ɂ́A`rules.inline`�ɐV�������[����ǉ����A`inline.image`�̏������I�[�o�[���C�h���܂��B

```javascript
const marked = require('marked');

const myRenderer = new marked.Renderer();

myRenderer.image = function(href, title, text) {
  const sizeMatch = href.match(/\{width=(\d+) height=(\d+)\}/);
  let width = '';
  let height = '';
  if (sizeMatch) {
    width = sizeMatch[1];
    height = sizeMatch[2];
    href = href.replace(/\{width=\d+ height=\d+\}/, '');
  }
  return `<img src="${href}" alt="${text}" width="${width}" height="${height}">`;
};

marked.setOptions({
  renderer: myRenderer
});

const markdownText = '![�L�̉摜](https://www.example.com/cat.jpg){width=300 height=200}';
const htmlText = marked(markdownText);

console.log(htmlText);
```

**4. marked.js��renderer���J�X�^�}�C�Y����**

renderer���J�X�^�}�C�Y���āA��͂��ꂽ����HTML��`<img>`�^�O�ɔ��f�����܂��B��L�̗�ł́A`renderer.image`���I�[�o�[���C�h���āA`width`��`height`�̒l��`<img>`�^�O�̑����ɒǉ����Ă��܂��B

**5. marked.js�����s����**

��L�̃R�[�h�����s���邱�ƂŁAMarkdown�e�L�X�g��HTML�ɕϊ�����܂��B�ϊ����ꂽHTML�ɂ́A�w�肵���摜�T�C�Y�����f���ꂽ`<img>`�^�O���܂܂�܂��B

**���ӓ_**

*   lexer��renderer�̃J�X�^�}�C�Y�́Amarked.js�̃o�[�W�����ɂ���ĈقȂ�ꍇ������܂��B
*   �Ǝ��̕��@���`����ۂ́A������Markdown���@�ƏՓ˂��Ȃ��悤�ɒ��ӂ���K�v������܂��B

��L�̕��@���Q�l�ɁAmarked.js���J�X�^�}�C�Y���āAMarkdown���@�ɓƎ��̊g����ǉ����Ă݂Ă��������B


