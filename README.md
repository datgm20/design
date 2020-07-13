# 基礎実習(ゲームデザイン実習) デジタルアーツ東京2020年度生
- [シラバス](https://1drv.ms/x/s!Anf4PowESFUjg_tm4AUjwjQr72mPJg?e=bcG9Lr)

# 参考資料
- [伊藤 周, Kitposition ～きっとポジション～. ユニティちゃんが教える！初心者向けUnity講座](https://www.udemy.com/course/unity-chan-tutorial-01/)
  - Unity2019.3.x(最新版)
- [質問](https://meet.google.com/dyf-fsns-kou)
- [キー入力スコア報告](https://docs.google.com/spreadsheets/d/10VcsR850aqWKN-C6tEuSExmgqET3EMH81KonU-yz7aI/)
  - 授業ページの左上の丸い矢印(再読み込み)をクリック
  - キー入力スコア報告を右クリックして、新しいタブで開く
  - 自分の行に、記録した最高スコアを入力
- [ひろはす ゲームクリエイター養成所. デザインの基本である配色を解説します](https://www.youtube.com/watch?v=Knpj-iEhfy4)
- [Adobe Color. 色の作成ツールWebページ](https://color.adobe.com/ja/create/color-wheel)

# 6回目
## 話題
- [Anna Mészáros. デザイナーではない人がデザインする上で大切な4つの基本原則](https://gigazine.net/news/20190518-fundamental-design-principles/)

## 文字のデザイン
- [スライド](https://am1.jp/dat/design/design5-font.pdf)

## フリーフォントの探し方とUnityでの活用方法
- [coliss. 2020年用、日本語のフリーフォント420種類のまとめ -商用サイトだけでなく紙や同人誌などの利用も明記](https://coliss.com/articles/freebies/japanese-free-fonts.html)
  - タイトル用と本文用の2つのフォントを見つけて、リンクをメモ帳などにとっておく
- [TextMeshPro向け　ASCIIコード＋JIS第1水準の文字](http://am1tanaka.hatenablog.com/entry/2019/10/14/183408)
- [手順](https://docs.google.com/document/d/1V8witriNqNILYd5tdnEE9pnvZokuHfTY3oJEBDtgAo0/)


## UnityのUI(uGUI)
- 新しいシーンを作って、*Scenes*フォルダーに`UI`という名前で保存
- [UnityのUI基礎](https://docs.google.com/document/d/1oUDdWBGk2XUjAyt7RLHL2a1shBwrZp-ghrOb4wzGddk/)

## PhotoshopでUIを作る
kyubuns氏作の[Baum2](https://github.com/kyubuns/Baum2)の紹介。書き出しに失敗したり、Unityへのインポートが動かなかったりして、今のところ読み込みに成功していないので、動画で機能を紹介。

- [CG METHOD. psdデータからuGUIにコンバートする方法](https://www.cg-method.com/entry/psd-to-ugui/)

## Photoshopで作った画像をレイヤー分割
- [テラシュールブログ. Photoshopで作った画像をレイヤー単位で分割、配置/描画順をそのままにSprite Renderで配置してくれる 「2D PSD Importer」](http://tsubakit1.hateblo.jp/entry/2018/12/18/200751#PSD-Importer)
  - [2d-animation-v2-samples](https://github.com/Unity-Technologies/2d-animation-v2-samples)

## 参考
- [Adobe. モバイルアプリおよびゲームエンジン用アニメーションの書き出し](https://helpx.adobe.com/jp/animate/using/create-sprite-sheet.html)
- [PHOTOSHOPVIP. 現役デザイナーが教える！完璧な書体を決める10個の黄金ルールまとめ](http://photoshopvip.net/105840?utm_content=bufferf79a8&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)
- [個人開発のUI設計術](https://crieit.net/posts/UI)


## まとめ演習
- [提出用URL](https://docs.google.com/spreadsheets/d/1Ky6bU27vJy_jl4-Yu3UiaHj-ZuHUPcQHXOVgjsRn-Mc/)
- 先週の画面サンプルにUIを追加
- 抽象化したキャラクターを作成する

### キーワード
- 抽象化
- 記号
  - アイコン
    - 対象の形を抽象化した記号
  - インデックス
    - 対象を連想させる記号
  - シンボル
    - ！や？など、共通認識がある記号
- モノグラム
- 点、線、面
- 幾何学形態の利用
  - 図形間の距離、大きさ
  - 図形の形状、配置
  - 黄金比、白銀比
- 図と地、ゲシュタルト心理学、プレグナンツの法則
- 錯視

### 提出
- 完成したら、GitHub Desktopでコミットして、Publishすれば提出完了



# 5回目
## 演習準備
- GitHub Desktopを起動
- File > Optionsで、必要ならSign outしてから、自分のアカウントでSign in
- 先週のu0701をコミットしてPublish
- [こちら](https://docs.google.com/spreadsheets/d/10VcsR850aqWKN-C6tEuSExmgqET3EMH81KonU-yz7aI/edit?usp=sharing)にリポジトリーのURLを貼り付け
- Unity Hubを起動して、前回のプロジェクト`u0701`を開く

### シーンの新規作成
- FileメニューからNew Sceneを選択
- [Ctrl]+[S]キーで保存して、Scenesフォルダーに`Colors`という名前で保存
- *Main Camera*をクリックして選択
- *Clear Flags*を*Solid Color*にする
- *Background*の右の四角をクリック
- 黒っぽくする
- xをクリックして、カラーウィンドウを閉じる

### カラーパレット用のQuadを作成
- *Hierarchy*ウィンドウの*Create*から、*3D Object* > *Quad*を選択
- *Project*ウィンドウの*Create*をから、*Material*を作成して、Enterキーを押す
- 作成した*New Material*をドラッグして、*Quad*にドロップ
- *New Material*をクリックして選択したら、*Shader*のコンボボックスをクリックして、*Unlit* > *Color*を選択
- 必要に応じて、*Inspector*ウィンドウの*Transform*欄の*Scale*の*X*と*Y*を調整して丁度良い大きさにする

以上で、色を直接設定できる正方形が作れる。

## 内容
- [色とUIのデザイン](https://am1.jp/dat/design/design4-color.pdf)
  - [図](https://am1.jp/dat/design/design4-color-fig.pdf)

## 演習1:色見本の作成
### カラーパレットを作成
- QuadとMaterialを作成して、作成したマテリアルをQuadにアタッチしておく
- RGBで色を作る
- HSVで色を作る(60ごと6分割)
- QuadとMaterialを複数作成して、それぞれ色を設定
- Main Cameraの背景色とQuadの組み合わせを色々と試してみよう

ここまでできたら、一度保存をして、GitHubにコミット、プッシュしておく([手順](https://github.com/dat19/gp1/blob/master/github-unity.md#%E5%A4%89%E6%9B%B4%E3%81%97%E3%81%9F%E3%82%82%E3%81%AE%E3%82%92%E5%8F%8D%E6%98%A0%E3%81%95%E3%81%9B%E3%82%8B%E6%89%8B%E9%A0%86))。


# 4回目

## 内容
- [PC保有アンケート](https://forms.gle/u4fcc8GzKpDAeaPv9)

## 形のデザイン
- [形のデザイン](https://am1.jp/dat/design/design3-shape.pdf)の導入
- 形だけで面白いものは作れる
- 参考： [FOTORIA. 三分割法で写真の構図をバッチリ決定！イラストで撮影方法を解決](https://fotoria.net/ja/blog/bc/photo-shoot-techniques/sc/composition/ar/rule-of-thirds/)

## 参考作品
- [VOODOO](https://play.google.com/store/apps/developer?id=VOODOO)
  - https://play.google.com/store/apps/details?id=com.neonplay.casualrollersplat2
  - https://play.google.com/store/apps/details?id=com.h8games.helixjump
  - https://play.google.com/store/apps/details?id=io.voodoo.paper2
  - https://play.google.com/store/apps/details?id=com.bigframes.color_road
- その他
  - https://play.google.com/store/apps/details?id=com.crazylabs.tricky.traps.game
  - https://play.google.com/store/apps/details?id=com.azurgames.stackball
  - https://play.google.com/store/apps/details?id=com.gamestart.fill
  - https://play.google.com/store/apps/details?id=com.colorup.game

## 演習：基本図形を使ってカジュアルゲームの画面イメージを作ってみよう
- [演習手順](https://docs.google.com/document/d/1xV3s3uG9jT0wCEfQEid83Pc5nBC7pLg8HZg0V8UyJI4/)

### 利用するツール
- Photoshop
- Unity

### 抽象化：円や四角、三角形といった図形を組み合わせてキャラクターを作ってみよう
- 抽象化するキャラクターを選ぶ(ピカチュウでもアイアンマンでもなんでもよい)
- 図形ツールを使って、そのキャラクターを徹底的に抽象化した形を描く(図形、色設定など自由に使ってよい)
- ポイント：元のキャラクターを連想できる限界まで形を抽象化する
- Photoshopの画像を画面に見立てて、丁度よいサイズにキャラクターの大きさを設定する

### 敵や障害物、地面などを作る
- 上記のキャラクターが映えるようなその他の素材を描く
- これも基本図形で構成してみよう


# 3回目
## 先週のミニゲームの企画書の提出(まだやってない人)
- 作成したスライドの右上の 共有 をクリック
- リンクを取得の下にある「リンクを知っている全員に変更」をクリック
- リンクをコピー をクリック
- 完了 をクリック
- [ドキュメントの共有URLの提出先](https://docs.google.com/spreadsheets/d/10VcsR850aqWKN-C6tEuSExmgqET3EMH81KonU-yz7aI/edit?usp=sharing) を開く
- 自分の名前の右の欄に、右クリックして貼り付け

## 内容
- [基本的なゲームデザイン論](https://docs.google.com/document/d/1kAfX8-_TyGLNSCaSC4t5R4VafvQYte-Zx-p-pQlB-Tg/)

### 演習A:ブレストをやってみよう
- 列でグループを作る
- 案をまとめるGoogleドキュメントを作成する
  - 真ん中の人が、Googleドライブを開いて、Googleドキュメントを新規に作成
  - タイトルを「03ブレスト」にする
  - 右上の共有をクリックして、ユーザーやグループのところに、メンバー全員にGmailアドレスを入力してもらったら 送信(教員も入れる)
  - メンバーは自分のGmailを開くと、招待メールが届くので、httpsから始まるリンクをクリック
  - ドキュメントの上の方に、自分の名前を入力
- ブレスト
  - 最前列の人から、何か思いついたことを箇条書きで入力する
  - 一人が入力を終えたら、隣の人がそこに書かれたことの案を発展させたことを追加で書き足したり、全然違う何か思いついたことを書き足す
  - 以上を時間内で繰り返す
  - 盛り上がってきたら、順番関係なく書き込んでもよい
- 案の集約
  - ブレストの下に「チーム企画概要」という見出しを作って、企画概要に関する項目を書いていく
  - 企画概要の各項目を、ブレストで盛り上がった内容を元に埋めていく
  - このフェーズでは出た案を全て使おうとは思わず、一番強いものから3つ程度で組み立ててみる

教員へもドキュメントは共有済みなので、提出のための特別な操作は不要。





# 2回目
- ゲームデザイン概論(1)
  - [アンケート ゲームに必要なものとは？](https://docs.google.com/forms/d/e/1FAIpQLScM31NloHp6Htd3xH2VX8zl4CNuGLt_2NH6whMiapisjZam4A/viewform?usp=sf_link)
  - ゲームの定義 [Capm Network. ゲーム理論](http://capm-network.com/?tag=%E3%82%B2%E3%83%BC%E3%83%A0%E7%90%86%E8%AB%96)
  - [ゲームの定義や要素からミニゲームを考える](https://docs.google.com/presentation/d/1_psbxg6vPk21C3nAcytyVJm8QTYr-G7AV1qAtjcRclg/)
  - [参考：Unity1週間ゲームジャム　クリエイターズLT](https://www.youtube.com/watch?v=-qWwYVWgczA&feature=emb_logo)
    - [tnkさん. 「斬新さ」から考えるゲーム開発](https://youtu.be/-qWwYVWgczA?t=3002)
    - [EIKIさん. ゴリラが人類を強制的にSTAY HOMEさせるゲーム](https://youtu.be/-qWwYVWgczA?t=6719)
- 演習：ミニゲームを考えてみよう
  - Googleスライドの使い方
    - gmail を開いて、右上のGoogleアプリをクリックして、Google Driveを選択
    - 左上のスライド名の部分をクリックして、「ミニゲームを考える：氏名」に変更(例：ミニゲームを考える：田中　雄)
    - レイアウトボタンをクリックして、タイトルと本文を選択
    - 手書きのものは、スマホで撮影して、学校で作成したgmailに送信
  - サムネイルを描く
  - 操作方法：unityroomを参考に、キーやマウスなど、どうやって動かすのかを書く
    - 選択肢に対応するもの
  - ルール
    - 何をするのか
    - 何をしたらいけないのか
  - 簡単な世界観など(あれば)    
  - **プレイヤーは、何を制限されるのか？　を考えるとまとめやすい**
- 参考： https://docs.google.com/drawings/d/1mGXGcm8mcXUBmP3rqVQheMDZLl3jd86qapLr7NChwjU/
- 参考： [nekogeek. カジュアルゲームの最新ゲームを50本遊んで、企画の方向を考えよう](https://nekogeek.jp/play-casual-games-a-lot/)
  - [ArtStation](https://www.artstation.com/)
- 画像取り込み
  - CamScan  [Android](https://play.google.com/store/apps/details?id=com.intsig.camscanner&hl=ja) / [iOS](https://apps.apple.com/jp/app/camscanner-%E3%82%B9%E3%82%AD%E3%83%A3%E3%83%B3%E3%82%A2%E3%83%97%E3%83%AA-pdf-%E5%A4%89%E6%8F%9B-ocr/id388627783)

# 1回目
## 内容
- [ガイダンス](https://docs.google.com/presentation/d/1-N9I50H3w64zj32ngfojcXPu7f83zeDYag3eZjlF2dA/)
  - 参考： [制作において心がけて欲しいこと](https://github.com/dat19/design/blob/master/01-note.md)
  - [卒業後の見通しを考えよう](a01卒業後の見通しを考えよう.md)
- [質問の準備　動画](https://www.youtube.com/watch?v=nE6FesKgPio&list=PLdRD_lOLS4j3FvkAqc5ddKHEH25GYMH3f)で画面共有の練習
- [環境の構築](https://docs.google.com/document/d/1iKEY2fyk483ayLxnpG648OfvVIOeDsQ-f3QJbabE0EA/)
  - Gmailアドレスの取得。**学校の活動専用**のアカウントを作成する
    - Gmailは、携帯番号の設定が必要です。２段階認証で必要なだけで、営業電話がかかってきたり、番号が他に漏れることはありません
    - Gmail / GitHub
  - Windowsの基本操作
  - 作業用フォルダーの作成
  - Googleドキュメントでノートをとる
- [キー入力練習](https://www.e-typing.ne.jp/)
  - [結果をここに報告](https://docs.google.com/spreadsheets/d/10VcsR850aqWKN-C6tEuSExmgqET3EMH81KonU-yz7aI/)

