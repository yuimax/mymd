# tkinter.Text
- 複数行のテキストを表示したり編集できるクラス

## サンプル
![02-textbox.pyのスクリーンショット](img/02-text-01.png)

```python
import tkinter

root = tkinter.Tk()
root.title('複数行のテキストを表示')
root.geometry('300x200+100+20')
root.minsize(250, 150)
root.config(bg='#c0c0c0', padx=6, pady=6)

textbox = tkinter.Text(root, font=('BIZ UDPゴシック', 15), padx=6, spacing1=10)
textbox.pack(side='top', expand=True, fill='both')
textbox.insert('end', 'Hello World!\n')
textbox.insert('end', 'やあ、みんないがすか！\n')
textbox.focus()

root.mainloop()
```

- コンストラクタ Text() の第１引数で親ウィンドウを指定
- コンストラクタ、または config() の font 引数でフォントを指定
- insert() でテキストを追加
- テキストはキーボードで編集できる

## コンストラクタ
- 第1引数で親ウィンドウを指定する
    - 例： <span class="code">textbox = tkinter.Text(root)</span>
- 第2引数以降で、config() の項目も設定できる
    - 例：  <span class="code">textbox = tkinter.Text(root, padx=6, spacing1=4)</span>

## おもなメソッド
- 詳細なメソッド一覧についてはこちら： **[TkDocs / Text](https://tkdocs.com/pyref/text.html)**

### config(項目名1=設定値1, ...)
- Text クラスには次のような設定項目がある（他の項目もあるが省略）

<table class="etc">
<tr style="background:#f0f0f0;"><th>項目名<th>意味<th>デフォルト値
<tr><td>foreground<td>文字色： 省略形の <b>fg</b> でもよい<td>"SystemWindowText"
<tr><td>background<td>背景色： 省略形の <b>bg</b> でもよい<td>"SystemWindow"
<tr><td>selectforeground<td>選択エリアの文字色<td>"SystemHighlightText"
<tr><td>selectbackground<td>選択エリアの背景色<td>"SystemHighlight"
<tr><td>padx<td>左右のパディング（pixel単位）<td>1
<tr><td>pady<td>上下のパディング（pixel単位）<td>1
<tr><td>spacing1<td>行の上の空白（pixel単位）<td>0
<tr><td>spacing2<td>文字間の空白（pixel単位）（※1）<td>0
<tr><td>spacing3<td>行の下の空白（pixel単位）<td>0
<tr><td>font<td>("フォント名", サイズ, "スタイル")<td>不明
<tr><td>state<td>"normal"： テキスト変更許可<br>"disabled"： テキスト変更禁止<td>"normal"
<tr><td>wrap<td>"char"： 自動改行は文字区切り<br>"word"： 自動改行は単語区切り<br>"none"： 自動改行なし<td>"char"
</table>

- （※1）spacing2 は環境により使えないかも？
	- 我が家の Windows 環境では spacing2 は無視された
- font のフォント名は、OS にインストールされたものが使える
	- 例： "Arial"、"Courier", "BIZ UDPゴシック"、"游ゴシック"、…
	- 無効なフォント名を指定すると、"TkDefaultFont" が使われるらしい
- font のサイズは、整数（ポイント単位）で指定する
	- サイズ 0 を指定するとデフォルトサイズになる
	- デフォルトは 13.5 ポイント相当に見えるが詳細は不明
- font のスタイルは "bold"、"italic"、"underline"、"overstrike" が利用可能
	- 複数のスタイルを並べて指定することもできる
	- 例： <span class="code">font=("游ゴシック", 15, "bold", "italic")</span>

### cget(項目名)
- config() の項目名を文字列で渡すと、その現在の値を返す
- 参考： すべての項目名を表示する方法
	- 引数なしの config() で辞書を取得し、その keys() を調べる
	- 例： <span class="code">for name in textbox.config().keys(): print(name)</span>

### insert(位置, 文字列)
- 指定した位置に任意の文字列を追加する
	- 文字列内に、改行コード（<span class="code">\n</span>）を含めてもよい
- 位置は次の形式で指定する

<table class="etc">
<tr><td>"行位置.文字位置"<td>整数で行位置と文字位置を指定する
<tr><td>"1.0"<td>テキスト全体の先頭は、上の記法で "1.0" になる
<tr><td>"行位置.end"<td>行末の改行位置は "end" で指定できる
<tr><td>"end"<td>テキスト全体の末尾
<tr><td>"end-1c"<td>テキスト全体の末尾の直前の文字
<tr><td>"insert"<td>現在のカーソル位置
<tr><td>"sel.first"<td>選択領域の先頭
<tr><td>"sel.last"<td>選択領域の末尾
</table>

### delete(位置1, 位置2)
- 位置1から位置2の直前までを削除する（位置2を含まない）
	- 例： 1行目を空行にする： <span class="code">textbox.delete("1.0", "1.end")</span>
	- 例： 1行目をすべて削除： <span class="code">textbox.delete("1.0", "2.0")</span>

### see(位置)
- 指定した位置までスクロールする
- 位置の指定方法は、上記 insert() メソッドと同じ
	- 例：全テキストの先頭を表示する： <span class="code">textbox.see("1.0")</span>
	- 例：全テキストの末尾を表示する： <span class="code">textbox.see("end")</span>

### count(位置1, 位置2, カウント対象)
- 位置1から位置2までの範囲でカウント対象を数える（位置2を含む）

<table class="etc">
<tr style="background:#f0f0f0;"><th>カウント対象<th>意味
<tr><td>"chars"<td>文字数
<tr><td>"lines"<td>行数
</table>

- 全体の末尾に見えない終端文字（EOF）があるものとして数える
- "chars" は、通常の文字の他に改行コードも1文字、EOF も1文字として数える
- "lines" は、EOF も1行として数える
- EOF を含めたくない場合は、範囲を "end-1c" までとする
	- 例： EOF を含まない全行数： <span class="code">textbox.count("1.0", "end-1c", "lines")</span>

### focus()
- フォーカスを得る
	- フォーカスを得ると現在のカーソル位置に文字カーソルが表示される

### update()
- 画面を更新する（待機中の描画処理をすべて実行する）

