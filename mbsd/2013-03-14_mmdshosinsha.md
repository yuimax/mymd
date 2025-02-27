## 記事情報
- 著者
	- <a href="https://www.nicovideo.jp/user/31648716" target="_user">切な顔P</a>
- サルベージ記事へのリンク
	- 2013-03-14: <a href="https://mmdblomagasaru.blogspot.com/2025/01/mmd_30.html" target="_page">MMD初心者覚書まとめ</a>
	- 2013-05-05: <a href="https://mmdblomagasaru.blogspot.com/2025/01/blog-post_30.html" target="_page">動画作成レポ的な何か</a>
	- 2013-07-16: <a href="https://mmdblomagasaru.blogspot.com/2025/01/blog-post_85.html" target="_page">こうしたらちょっと見栄えが変わるんじゃないかとかそんなんまとめ</a>
	- 2013-07-25: <a href="https://mmdblomagasaru.blogspot.com/2025/01/blog-post_31.html" target="_page">女の子モーションを男性モデルに入れる時に便利かなとかそんなモーフ</a>

## 読んでみた
- ブロマガ本体とリンク先の著者ブログに各種の解説があります
- 初心者は全部読んでおくことをオススメ
<!-- -->
- **MMD小ネタとか基本とか超初級編**
	- キーフレームの打ち方
	- 補間曲線の使い方
	- Aviスクリーン（動画内スクリーン）について
	- MMEの割り当てタブについて
	- MMDの保存(**pmm**ファイル)と、MMEの保存(**emm**ファイル)
	- MMEでモデル別に設定を保存(**emd**ファイル)
	- モーションの修正いろいろ
	- エフェクトが使えない場合
- **ステージとエフェクトについて（超初級編）**
	- ステージを探すには： VPVP wiki、BowlRoll、ニコニコ静画
	- まず何より先に Readme を
	- ステージの各種不具合への対処法
	- アクセサリの影の ON／OFF
	- ステージの移動とかサイズの変更とか
- **ステージとエフェクトについて（初級編)**
	- MMEの導入法： ぐぐって
	- エフェクトを入れると変な四角： 「MMD 連凧」でぐぐって
	- 物体に白い縁取り、窓の外が見えない： 透過素材の順番
	- ステージと影： 地面影とセルフシャドウの使い分け
	- どうしてもだめなら ExcellentShadow2 の出番
	- 床の鏡面反射： WorkingFloor だいすき
	- ステージの質感を上げる
	- Luminous 系で遊ぶ
- **モーション修正 多段化活用編**
	- フレーム位置角度修正： 選択範囲を一気に修正する基本操作
	- キーフレームを打ちなおす： 特定のキーを修正する基本操作
	- 足の修正： 足は難しいのでハイキックを例に実践
	- 多段化して腕の修正： 多段化のススメ
- **動画作成レポ的な何か。**
	- カメラ自作のコツいろいろ
		- 移動方向や回転方向を連続させない
		- 音に合わせたカット割を
		- 三分割法は役に立つ
		- お借りしたモーションの見せ場を生かす
		- 視野角にも気をくばる
	- モデルさんを途中で入れ替える
		- モデルごとに動画を出力し AviUtl で合成
		- モデル非表示を駆使し動画内で切り替える
	- AviUtlでやっていること
		- 単色で色調補正
		- グラデーションで色調補正
		- 色調補正はMMD側でo_Tonemapを使うのもよし
- **こうしたらちょっと見栄えが変わる**
	- ステージと影
		- アクセサリの影をON／OFFしてみる
		- 地面影を消すと良い場合
		- エフェクト ExcellentShadow2 などの利用
		- エフェクト不要の物体はMMEの設定で影を消す
	- 反射する床 WorikingFloor
		- カメラ角度やTr値を工夫すると見栄えがよい
		- 丸とか三角とかの床を配布
	- 視野角の話
		- 極端な視野角だとモデルがブサイクになるよ
		- 著者の流儀は視野角27度
		- あえて視野角を変えて効果を出す例
	- 物理演算
		- 複数のモデルが重なると剛体が干渉するよ
	- シェーダー
		- データPの AdultShader はいいぞ
		- ちょっと設定をいじるだけでイメージが変わる
	- モーション
		- 腕の角度が違うとけっこう目立つので修正しよう
		- 多段化ボーンはおすすめだよ
	- 透過材質
		- 描画順に気を付けるべき
- **女の子モーションを男性モデルに入れる**
	- 内股のモーションを男性っぽくする方法の考察
	- 足と足IKをボーンモーフでガニ股にするとそれらしくなる
	- PMXエディタで上記モーフを作る方法

<!-- -->
