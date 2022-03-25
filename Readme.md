
# <img alt="Logo" src="docs/logo.png" width="350">

PHP / JavaScript 製のテレビのリモート視聴ソフト（いわゆるロケフリ）です。  
YouTube やニコニコ動画などの動画配信サービスの UI を意識した、モバイルフレンドリーなレスポンシブ Web UI が特徴です。  
放送中の番組の視聴・録画番組の検索/再生・複数同時視聴などの基本機能に加え、Twitter と連携してキャプチャ付きでツイートする機能やニコニコ実況のコメントを表示 / 投稿する機能、字幕を表示する機能なども実装しています。

## [ダウンロードはこちら](https://github.com/tsukumijima/TVRemotePlus/releases)
## 概要
![Screenshot](docs/screenshot1.png)
<span style="font-size: 80%; float: right;">＊画像はイメージです</span>

  - [概要](#概要)
    - [開発動機](#開発動機)
  - [機能](#機能)
  - [セットアップ](#セットアップ)
    - [別途必要なソフト](#別途必要なソフト)
    - [インストール & セットアップ](#インストール--セットアップ)
    - [トラブルシューティング](#トラブルシューティング)
  - [使い方](#使い方)
    - [キーボードショートカット](#キーボードショートカット)
  - [PWA について](#pwa-について)
    - [PWA のインストール手順](#pwa-のインストール手順)
  - [Chromecast (Google Cast) 機能について](#chromecast-google-cast-機能について)
    - [注意](#注意)
    - [Chromecast (Google Cast) 機能の使い方](#chromecast-google-cast-機能の使い方)
  - [Twitter API 開発者アカウントの取得について](#Twitter-API-開発者アカウントの取得について)
  - [リバースプロキシで外出先からアクセスする（上級者向け）](#リバースプロキシで外出先からアクセスする上級者向け)
  - [注意事項・既知の問題](#注意事項既知の問題)
  - [利用ソフトウェア](#利用ソフトウェア)
  - [利用ライブラリ](#利用ライブラリ)
  - [動作環境](#動作環境)
  - [動作確認](#動作確認)
  - [寄付について](#寄付について)
  - [不具合報告・フィードバック](#不具合報告フィードバック)
  - [その他・謝辞](#その他謝辞)
  - [Release Notes](#release-notes)
  - [License](#license)

スマホ・PC 両方での利用に最適化されたテレビ視聴ソフトを求めて開発しました。  
一応、コンセプトは「動画配信サイト風の直感的で使いやすいレスポンシブ Web UI」です（実現できているかは微妙ですが…）。

機能的には TVRemoteViewer_VB と似ている部分がありますが、下記のように TVRemoteViewer_VB にはない機能、逆にこの TVRemotePlus にはない機能もあります。  
また、TVRemotePlus は複数のオープンソースソフトウェア（組み込み済み）を利用して動作します。単体では動作しません。  
このほか、**いわゆる TS 抜き環境が事前に導入されている必要があります。** 

基本的にド素人が作った出来の悪い<s>ｸｿｺｰﾄﾞ</s>自己満ソフトのおすそ分けです。できる範囲で不具合は修正しますが、必ず動く保証はありません。  
また、動けばいいや程度で強引に実装してしまっている箇所があるため、いろいろ不具合があるかもしれません。

ドキュメントは最新の情報に更新できていない場合があります。あらかじめご了承ください。

> **TVRemotePlus は現在メンテナンスモードです。**  
> これ以上の機能追加は行われないほか、アップデートがあったとしても、最低限の変更と不具合修正のみとなります。完全な開発終了ではありませんが、それに近い状態です。
> 
> 背景には、開発開始当初のつたない技術力で無計画に実装を進めていってしまった結果、作者自身ですら手に負えないほどのスパゲティコードになってしまったという事情があります…。  
> TVRemotePlus に既知の問題がいくつもあることは重々承知していますが、比較的簡単に修正できるものに関しては、v2.6.1 の時点ですでに修正を完了しています。  
> 現在残っている不具合は、現行のコードでは修正が困難な問題か、まだ把握できていないバグかのいずれかです。

> 現在は [KonomiTV](https://github.com/tsukumijima/KonomiTV) の開発を進めています。  
> TVRemotePlus で実装していた機能を引き継ぎつつ、まったく新しいテレビ視聴・録画視聴のユーザー体験を作り上げ、追求したいという想いから開発しています。  
> まだ TVRemotePlus のすべての機能を代替できるほどにはなっていませんが、よろしければお試しください。

### 開発動機
「ふとんでゴロゴロしながらスマホで YouTube みたいにテレビとか録画とか見たい」  
「外出先でもスマホでニュース眺めたい（ワンセグは画質悪いしアンテナとかめんどくさい）」  
「ニコ生みたいにニコニコ実況のコメントを流したいしコメントもしたい」  
「Twitter 実況するの割と手順が煩雑になりがちだし見ながら Twitter で実況したい」  
「折角 Twitter 実況するならテレビの画面もキャプチャしてツイートしたい」  
「録画見るときにもコメント流したいし YouTube みたいに簡単に見たい（ファイルを漁りたくない）」  
「字幕流して放送画面と一緒にキャプチャしてリプライ用画像を量産したい」  

などなど…（動機が不順すぎる）

## 機能
![Screenshot](docs/screenshot2.png)

ざっくりにするつもりがかなり雑多になってしまった…  

太字のところが大まかな機能（このソフトでできること）です。  

載せきれていない機能もあるので、詳しく知りたい場合は [リリースノート](https://github.com/tsukumijima/TVRemotePlus/blob/master/docs/Release_Notes.md) の方も参照してください。

 - **放送中のテレビが見れます**
   - BS・CS も見れます
   - YouTube Live とかニコ生を見るような感覚で視聴できます
   - **ピクチャーインピクチャーにも対応しています**
     - 対応しているブラウザは現状最新の PC 版 Edge・Chrome・Safari 、iOS / iPadOS 版 Safari のみです
     - 画面の端においたミニプレイヤーでテレビを見ながら他の作業をする、といった事ができます
     - Android 版 Chrome ではブラウザが非対応のため使えませんが、その代わり全画面にしてからホームボタンを押すとピクチャーインピクチャーに切り替わるようになっています
   - **プレイヤーをフルスクリーンにする事ができます**
     - 端末フルスクリーンとブラウザフルスクリーンがあり、後者はプレイヤーがブラウザの描画画面いっぱいに広がります
     - 画面全体をフルスクリーンにすることもできます（ iOS Safari を除く）
     - Android の場合、端末フルスクリーンにすると画面が自動で横向きになります
       - iOS は Screen Orientation API に対応していないため非対応です
     - iOS では Safari の仕様でフルスクリーンにするとブラウザデフォルトのプレイヤーが使用されます
       - そのため、コメントを表示させたい場合はブラウザフルスクリーンを使うようにしてください
       - iPadOS では Fullscreen API がサポートされているため、フルスクリーンにしても通常のプレイヤーで再生できるようになっています
     - スマホなどのスペックの低い端末では、端末フルスクリーンにするとコメント描画が非常に重くなることがあります
       - 多くの場合、ブラウザフルスクリーンにすることで改善します
       - 動作が極端に重い場合、Android の設定から［ユーザー補助サービス］が ON になっているアプリを全て OFF にしてみると軽くなるようです
   - **生放送の場合は、プレイヤーの ● Live ボタンを押すと同期できます**
     - 仕組み上どうしても遅延してしまうのですが、このボタンを押せば遅延を最小限にする事ができます
   - **再生中の番組のスクショを保存できます（ PC のみ）**
     - プレイヤーのスクリーンショットボタンをクリックするとダウンロードできます
     - これとは別に、再生中の番組をスクショして Twitter にツイートできる機能もあります（後述）
       - Twitter にツイートした画像を保存できる機能もあります
   - **エンコードには ffmpeg・QSVEncC・NVEncC・VCEEncC が利用可能です**
     - 全て同梱済みのため、改めてダウンロードする必要はありません
     - QSVEncC・NVEncC・VCEEncC を選択すると高速にエンコードできますが（＝放送波との遅延が少なくなる）、それぞれ対応した GPU が必要になります
   - **デフォルトで使う BonDriver を設定できます（設定しておけば毎回 BonDriver を選ぶ必要がありません）**
     - デフォルトの BonDriver は地デジ用・BS/CS 用でそれぞれ設定できます
     - ストリーム開始時にはデフォルト以外の BonDriver も選択できます
       - 選択できる BonDriver は地デジなら地デジ用 BonDriver（_T*.dll）、BS/CS なら BS/CS 用 BonDriver（_S*.dll）と無印 BonDriver（それ以外） になります
   - 現在の視聴人数を表示できます
     - 視聴人数は端末ごとにカウントされます
   - 長時間再生していると突然エンコードが止まってしまう事があるため、20秒経ってもストリームが更新されていない場合は自動でストリームを再起動します
   - ストリーム開始に失敗した（30秒経ってもストリームが更新されない）場合は、自動でストリームを終了し配信休止中の状態に戻ります
     - 何度試してもストリーム開始に失敗するときに無限ループにならないようにするためです
   - 動画プレイヤーには [DPlayer](https://github.com/MoePlayer/DPlayer) という JavaScript 製プレイヤーを TVRemotePlus 向けにかなり改良を加えた上でお借りしています
     - フォークは [tsukumijima/DPlayer](https://github.com/tsukumijima/DPlayer) にあります
  - **複数のストリームを同時に配信できます**
    - **ライブ配信を同時配信して2つのチャンネルを行き来したり、時間のかかる録画ファイルのエンコードをライブ配信を見ている間に行わせておく、といったことができます**
    - 今視聴しているストリームを終了するにはサイドメニューの［このストリームを終了］ボタンを、  
      今視聴しているストリームも含め全てのストリームを終了したい場合は［全てのストリームを終了］ボタンをそれぞれクリック or タップしてください
    - ストリーム番号の指定がない場合、ライブ配信の場合は現在視聴しているストリームで、ファイル再生の場合は空いているストリームでそれぞれストリームを開始します
    - デフォルトは Stream 1・2・3・4 の4ストリームが用意されていて、4ストリームを全て使い切っているときのみ Stream 5 以降が順次利用可能になります
    - それぞれのストリームをクリック or タップすると、そのストリームの視聴画面に遷移します
    - 赤いストリーム終了ボタンをクリック or タップすると、そのストリームのみストリーム終了することができます
    - ストリームが Offline になった場合は、自動でストリーム一覧から消去されます
 - **録画した番組も見れます**
   - TS ファイル・MP4 ファイル・MKV ファイルの再生に対応しています
   - YouTube のような感覚で録画番組を再生できます
   - **録画番組の名前順・日付順のソートができます**
     - 録画が新しい順・録画が古い順・名前昇順・名前降順で並び替えができます
   - **再生履歴を表示できます**
     - 再生履歴の保存件数は設定から変更できます（デフォルトは10件です）
   - **番組のタイトルでキーワード検索することもできます**
     - 検索結果も 録画が新しい順・録画が古い順・名前昇順・名前降順で並び替えできます
   - **MP4・MKV ファイルはプログレッシブダウンロード機能が使えます**
     - エンコードせずに生の MP4・MKV ファイルをそのまま再生する事ができる機能です
     - 最初から最後まで再生できる・再エンコードしないのでそのままの画質で再生できる・再生が安定している などのメリットがあります
     - 一方、ブラウザが対応していない H.265 などのコーデックでエンコードされている場合は映像が再生できない場合があります
     - MKV ファイルは PC / Android の Chrome でしか再生できません
   - 初回インストール時のみ、リスト更新に時間がかかることがあります
     - これはサムネイルや番組情報をバックグラウンドで取得しているためです
     - リスト更新処理はバックグラウンドで動くため、タブを閉じても問題ありません
     - 初回インストール時点での録画ファイルの量が多いほど、リスト更新に時間がかかります
     - 初回のリスト更新が終われば、リストをリセットしない限り、今後リスト更新に時間がかかることはありません
       - 長くても10秒程度で終わるはずですが、長い間ファイル再生ページを開かなかった場合は処理するファイルも増えるため少し時間がかかることもあります
   - ファイルリストの内容がおかしくなった場合は、右上のメニューから［リストをリセット］をクリック・タップすると、リストをリセットできます
     - 番組情報は再度取得し直しますが、サムネイルはリセットされません
 - **最近流行りのダークモードにできます**
   - 個人設定から［ダークモード］をオンにするとダークモードに変わります
   - 割とカッコよくて良いと思います（私はいつもダークモードで使っています）
   - 初回読み込み時には端末のテーマに合わせてダークモードか通常モードか選択されます
 - **局ロゴを表示できます**
   - 局ロゴを表示する場合は EDCB_Material_WebUI で局ロゴが表示できる状態にしておいてください
     - EDCB_Material_WebUI の局ロゴ API を利用しています
   - 局ロゴを表示するかどうかは［個人設定］→［番組表に局ロゴを表示］から変更できます
 - **ナビゲーションメニューを垂直に表示できます**
    - 横長のビューポートでもっとプレイヤーを大きくしたいのに上のヘッダーが邪魔で横の余白だけ余ってるって事があるかと思いますが、そういう時に使うとプレイヤーをより大きく表示できます
    - お使いの PC やタブレットの画面レイアウトに応じて適宜設定してみてください
 - **災害時などに表示されるＬ字画面をクロップして隠せます**
   - ︙サブメニュー → [Ｌ字画面のクロップ] から設定できます
   - 台風などの災害時でＬ字画面がうざったい場合などに使えそうです
 - **ニコニコ実況のコメントが流せます**
   - 2020/12/16 からのニコ生に移行した新しいニコニコ実況にも v2.4.0 以降から対応しています
     - [ニコニコ実況 過去ログ API](https://jikkyo.tsukumijima.net/) を利用し、今までの過去ログも録画番組と一緒に楽しめます
   - プレイヤーの設定からオフにもできます
   - 色コメや上・下固定にも対応しています
     - 改造元の動画プレイヤーの兼ね合いで、文字サイズは今のところ再現できていません
   - コメントの透明度も調整できます
   - ニコニコ実況にコメントを投稿することもできます
     - ただし、コメントを投稿する場合は環境設定からニコニコにログインするメールアドレス・パスワードを設定しておく必要があります
     - ファイル再生時はコメントを投稿できません
 - **Twitter 実況が簡単にできます**
   - Twitter 実況機能を使う場合は、予め Twitter API の開発者アカウントを作成しておく必要があります（[詳しくはこちら](docs/Twitter_Develop.md)）
   - **動画プレイヤーの下にあるフォームから番組を見ながら Twitter 実況できます**
     - ハッシュタグ欄に実況する番組のハッシュタグタグを書いておけば、ツイート後にいちいちハッシュタグを再入力する手間を省けます
   - **放送中の番組をキャプチャ（スクショ）して画像付きで Twitter に投稿できます**
     - ニコニコ実況のコメントを合成した画像をツイートすることもできます
     - 字幕（後述）をオンにしているときは字幕も一緒に合成されます
     - キャプチャは最大4枚まで添付してツイートできます
     - キャプチャ画像リストの画像を右クリック or 長押しすると画像を拡大表示できます
   - Twitter に投稿したキャプチャ画像はデフォルトでは `C:\(TVRemotePlusをインストールしたフォルダ)\data\upload` に保存されます
     - 設定から画像の保存場所を変えることもできます
     - 投稿後に画像を削除するよう設定することもできます
   - ハッシュタグ を 1 分以内に Twitter API 経由で連投するとほぼ確実に Twitter 側からシャドウバンされるため、1 分以内にハッシュタグ付きツイートを連投した場合にハッシュタグを除去してシャドウバンを防止する機能もついています（詳細は後述のトラブルシューティングの項を参照）
     - 必要ない場合は設定からオフにできますが、確実にシャドウバンされやすくなります
 - **字幕を表示できます**
   - [aribb24.js](https://github.com/monyone/aribb24.js) を利用し字幕を表示できます
      - aribb24.js は、b24.js を参考に字幕を Canvas を用いてできるだけ正確に描画できるライブラリです
        - TVTest の TVCaptionMod2 と同様かそれ以上の再現度を誇ります
      - 自力ではとても実装できないような完成度で、要望に対応していただいたりも含め本当にありがたいです
      - v2.6.0 以降では、iOS / iPadOS 端末でも字幕が表示できるようになりました！
   - 字幕はストリーム開始時に字幕をオンにした場合にのみ表示できます
     - デフォルトはライブ配信・ファイル再生ともに字幕オンになっています
   - 別途プレイヤー側で字幕のオン・オフを設定できます
 - **ネイティブアプリのように使うことができます（ PWA 機能・[後述](#pwa-について)）**
   - PWA は、Web アプリをあたかもネイティブアプリのように使えるようにすることができる新しい仕組みのことです
   - インストールするとアプリアイコンから TVRemotePlus を起動できるようになるほか、ブラウザのアドレスバーが表示されないためより見やすくなります
   - PWA 機能を利用する場合は、予め各端末に自己署名証明書をインストールし、HTTPS で TVRemotePlus にアクセスできる状態にする必要があります（後述）
 - **Google Cast デバイスにキャストする事ができます（暫定実装・[後述](#chromecast-google-cast-機能について)）**
   - Google Cast に対応しているデバイスであればキャストできるので、Chromecast 以外にも Google Home（音声のみ）や Google Nest Hub・AndroidTV などにもキャストできます（Chromecast・Google Home 以外は未検証）
   - 現状コメントや字幕は表示できませんが、PC で録画した番組をテレビの大画面で見ることができます
   - 手元のスマホにはコメントや字幕が流れるので、スマホを時々見ながらテレビで録画番組を見るのもありかもしれません
 - **Basic 認証も（一応）できます**
   - おまけ機能で作者も使っていないので、一部の機能が動かない可能性があります
   - セキュリティ的な面では弱い認証形式です、気になる方は適宜他の対策を取ってください
   - デフォルトでは Basic 認証機能はオフになっています、利用する場合は環境設定からオンにしてください
   - デフォルトのユーザー名は user 、パスワードは password になっていますが、Basic 認証機能を使う場合は必ず変えるようにしてください
 - **リバースプロキシを使い外部から視聴できるようにする事もできます（上級者向け・詳しくは [こちら](docs/Reverse_Proxy.md) ）**
   - 上級者向けですが、Apache や nginx などの Web サーバーに用意されているリバースプロキシ機能を使えば、外部から https://example.com/tvrp/ のような URL で TVRemotePlus にアクセス出来るようにすることもできます
   - 基本的にセキュリティの面から Tailscale などの VPN を経由してアクセスする事をおすすめしますが、この方法であれば速度低下や手間がかかるといった VPN のデメリットがなくなります
     - その代わり、設定を誤ると PC がセキュリティ的に無防備になる可能性もあります、十分細心の注意を払って設定してください
   - また、Web サーバーやネットワークの基本的な知識がない方にはおすすめできません
   - この他、Basic 認証をオンにするなど、各自でセキュリティ対策を行ってください
   - セキュリティ向上のため、Basic 認証なしで利用する場合は［リバースプロキシからのアクセス時に環境設定を非表示にする］の設定をオンにしておくことをおすすめします
      - 設定ページに不正なリクエストが送信された場合、PHP の各種関数や Windows コマンドにアクセスできてしまう可能性があります
      - 脆弱な部分は修正したつもりですが、リバースプロキシからのアクセス時は環境設定を保存できないようにすることで、リスクを大幅に減らすことができます
   - リバースプロキシ自体のセットアップ方法は割愛します

## セットアップ
![Screenshot](docs/screenshot3.png)

アーカイブは 64bit 版のみです。（ BonDriver は 32bit・64bit 両方対応しています）  
技術的には 32bit 版のアーカイブも可能ですが、こちら側でアーカイブを作成するのが面倒なためです。

### 別途必要なソフト
 - **TVTest**
   - BonDriver の TVTest 用チャンネル設定ファイル（.ch2）が TSTask で必要なためです。
     - 32bit・64bit は問いませんが、古いバージョンの TVTest だとチャンネル設定ファイルのフォーマットが異なっているなどで動かないことがあるかもしれません。
     - TVTest 0.10.0 のチャンネル設定ファイルにて動作確認をしています。
     - .ch2 ファイルさえ用意できれば大丈夫です。
   - また、BonDriver も TVTest と同じものを利用できます。
   - （ないとは思いますが）チャンネルスキャンをしていない場合は、必ずしておいてください。
   - 動作確認済みのアーカイブは [こちら](https://github.com/tsukumijima/DTV-Built#%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89) よりどうぞ。
 - **EDCB + EDCB Material WebUI**
   - 番組表の取得に利用します（なくても動作しますが、番組情報が取得できません）。
   - EDCB に加え、[EDCB Material WebUI](https://github.com/tsukumijima/EDCB_Material_WebUI) を導入しておいてください。素の EDCB だけでは動きません。
   - この他、設定ページまたはインストーラーで EDCB Matrial WebUI が動作している URL を設定する必要があります。
   - TVRock 等を利用している場合は、別途 TVRemoteViewer 2.93m（再うｐ）版を導入し、その URL を設定することで番組表が取得出来るようになります（対応していただき感謝です）。 
   - 動作確認済みのビルド済みアーカイブ（ EDCB Material WebUI 同梱済み）は [こちら](https://github.com/tsukumijima/DTV-Built#%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89) よりどうぞ。

### インストール & セットアップ

1. **Release から最新の TVRemotePlus をダウンロード・解凍する**
2. **解凍したフォルダの中の install.bat を実行し、インストーラー通りに進める**
   - CUI ベースですが、比較的簡単にインストールできると思います
   - 後述しますが、半角スペースの入ったパス、日本語（マルチバイト文字）の入ったパスにインストールするのは不具合の原因になるため、できるだけ避けてください
   - C:\Program Files や C:\Users 以下へのインストールも推奨しません（個人的には `C:\DTV\TVRemotePlus` とかがおすすめ）
     - 特に C:\Program Files 以下は半角スペースが入っている上に権限が特殊なためまずまともに動きません
3. **下の [Twitter API 開発者アカウントの取得について](#Twitter-API-開発者アカウントの取得について) の項目を参考にし、Twitter API 開発者アカウントを取得し、アプリケーションを作成する（任意）**
   - その後、設定ページの［Twitter 投稿］から、作成したアプリケーションの Consumer Key などを入力してください
   - 既に Twitter API アカウントを持っている方、ツイート投稿機能を利用しない方は適宜ステップを飛ばしてください
4. **`C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask\BonDriver` フォルダに、いつも TVTest などで使用している BonDriver と .ch2 ファイル（チャンネル設定ファイル）を入れる**
   - BonDriver は 32bit・64bit 両方対応しています、インストーラーでどちらかを指定してください
   - **B-CAS カードを PLEX 製チューナー付属の内蔵カードリーダーで利用している場合は、TVTest 等で使っている WinSCard.dll・WinSCard.ini を `C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask` フォルダに入れてください**
     - ストリームの起動に失敗する or 再開 → 中断を繰り返す 場合はまずは WinSCard.dll・WinSCard.ini が配置されているかを確認してみてください
     - SoftCas を利用している場合も同様の手順で可能だと思います
   - **実際に使用される TSTask は `C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask\TSTask-tvrp.exe` です。**
     - 32bit・64bit フォルダはインストール時に選択された 32bit・64bit に合わせてどちらか片方の TSTask を `C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask` 以下に -tvrp のサフィックスをつけて展開するためのもので、実際には使用されません。
     - BonDriver の 32bit・64bit を変更する場合に TSTask を差し替えられるよう、念のため残しているものです。
     - エンコーダー類も同様ですが、-tvrp のサフィックスは `taskkill /IM` を実行するとき、他で利用している TSTask.exe を強制終了してしまう事態を避けるために付与しています。 
   - TSTask の設定は予め TVRemotePlus 向けにカスタムされています。TSTask-tvrp.ini を削除した場合、正常に動作しない可能性があります。
5. **デスクトップに追加されたショートカットをダブルクリックし、Web サーバーを起動する**
   - TVRemotePlus-Launcher がタスクトレイに表示された状態で立ち上がり、バックグラウンドで Web サーバー (Apache) を起動します
     - 起動（タスクトレイへの表示）に時間がかかる場合がありますが、しばらく待ちましょう
       - もう一度ダブルクリックして「同じサーバー (Apache) を複数起動することはできません」というエラーが出たら起動自体はできています
     - 起動したら タスクトレイのアイコンを右クリック →［サーバー (Apache) の設定］から、Web サーバー (Apache) の設定内容や起動ログを確認できます
6. **ブラウザの URL 欄に http://( TVRemotePlus の動いている PC のローカル IP アドレス):8000/ と入力し、TVRemotePlus の Web アプリへアクセスすると、使えるようになっています**
7. **画面左上の ≡ サイドメニュー → 設定 → 環境設定 から、適宜必要な箇所を設定する**
   - 今は何も設定しなくても一応動くようにはなっていますが、できるだけ目を通しておいてください
   - 番組表を表示する場合は、EDCB Material WebUI のある URL（通常は http://(EDCBをインストールしたPC):5510/ ）を［EDCB Material WebUI (EMWUI) のある URL］に設定してください
     - 事前にインストーラーで設定している場合はこの手順は不要です
   - config.php（設定ファイル）を **UTF-8・LFが読み込めるテキストエディタ（メモ帳はできるだけ避けてください）** で開き、直で編集することも可能です
     - 変更出来たら、**文字コード UTF-8・改行コード LF** で変更を保存します（ Shift-JIS など UTF-8 以外の文字コードで保存した場合、動作しなくなります）
8. **局ロゴを表示させる（任意）**
   - 局ロゴの表示には EDCB Material WebUI の機能を使っているので、EDCB Material WebUI で局ロゴが表示できる状態なら TVRemotePlus でも局ロゴが表示できるようになります
   - EDCB Material WebUI で局ロゴを表示させる方法に関しては [こちら](https://github.com/tsukumijima/EDCB_Material_WebUI#%E5%B1%80%E3%83%AD%E3%82%B4) を参照ください
   - 私のビルド済みアーカイブであれば EDCB Material WebUI 関東のテレビ局と BS・CS のほぼ全ての局ロゴを内蔵しているので、何もしなくても局ロゴを表示できるはずです
   - また、EDCB と同じフォルダに TVTest を置いていて、TVTest フォルダ以下に LogoData.ini と Logo フォルダがあればそれも自動で利用されます
9.  **後は適当に使ってください…**
   - アップデートがある時は ≡ サイドメニューのバージョン情報のアイコンが赤くなります
     - できるだけ最新の TVRemotePlus を使うことをお勧めします
     - config.php（設定ファイル）は新機能が追加された場合などに変更される事があるため、アップデートモードでインストールすると正しく動作しない場合があります
     - その場合は一旦 config.php を新しいものに置きかえ、設定をやり直してください
   - エラーが出てうまく動かない場合があるかもしれませんが、ほとんどの場合、設定ミスによるものです
   - PC 起動時に一緒に TVRemotePlus を起動させたい場合は、適宜デスクトップに作成されたショートカットをスタートアップフォルダにコピーし、スタートアップに登録してください
     - スタートアップフォルダはエクスプローラーの上のパス入力欄から `%AppData%\Microsoft\Windows\Start Menu\Programs\Startup` と入力すると開けます
11. **アンインストールしたいときは、インストールしたフォルダごと削除してください**
   - レジストリや AppData 以下は汚していません
     - データ等は全てインストールしたフォルダ以下に保存されています
   - デスクトップのショートカットは適宜削除してください

### トラブルシューティング

よくある不具合報告をまとめています。  
うまく動かないときは、一度トラブルシューティングを全部読んでみることをおすすめします。  
解決しない場合は [Release Notes](docs/Release_Notes.md) も読んでみてください。

 - **インストールフォルダへのパスに日本語（全角文字）が含まれていると、正常に動きません。**
   - Webサーバー（Apache）や PHP が日本語フォルダに対応していないためです。
   - もしかすると動くかもしれませんが、基本的にお勧めしません…
   - **また、半角スペースのあるフォルダ（例：`C:\Digital TV\TVRemotePlus` ）も避けてください。**
    - いつだかのアップデートでエラーにならないように一応修正しましたが、避けたほうが無難だと思います。
   - 例えば、`C:\テレビ\TVRemotePlus` だとか `C:\freesoft\ＴＶＲＰ` はエラーになると思います。
   - `C:\DTV\TVRemotePlus` のように、インストールフォルダへのパスが全て半角英数字・半角スペースなしで完結するようにしてください。
   - **C:\Program Files や C:\Users 以下へのインストールも推奨しません**（個人的には `C:\DTV\TVRemotePlus` とかがおすすめ）。
 - install.bat 実行時に **「コンピューターに VCRUNTIME140.dll がないため、プログラムを開始できません。」というエラーが表示される場合は、[こちら](https://www.microsoft.com/ja-jp/download/details.aspx?id=53587)より Visual C++ 2015 再頒布可能パッケージ をダウンロード・インストールしてください。**
   - vc_redist.x64.exe のみダウンロードし、ダウンロードが終わったら vc_redist.x64.exe を実行してランタイムをインストールしてください。
 - **起動する際に下のようなファイアウォール云々が出た場合、許可しておいてください。**
   - ![Screenshot](docs/firewall.png)
   - プライベートネットワークのみの許可で構いません（ VPN 等を利用して外部からアクセスする場合は変わってくるかもしれません）。
 - **「チャンネル設定ファイルが見つからないため、ストリームを開始できません。」と表示される場合、TVRemotePlus 側でチャンネル設定ファイルが認識できていません。**
   - チャンネル設定ファイル（.ch2）のファイル名は地デジの場合 BonDriver_(機種名)_T(0-9).ch2、BS・CSの場合は BonDriver_(機種名)_S(0-9).ch2 である必要があります。
   - 例えば BonDriver_FSUSB2N.ch2 のように地デジのみのチューナーで _T や _S が付いていない場合は TVRemotePlus 側で地デジ用か BS・CS 用かを認識できないため、
     ファイル名を BonDriver_FSUSB2N_T.ch2、または BonDriver_FSUSB2N_T0.ch2 のように変更してください。
 - **何度やってもストリームの開始に失敗する場合、TSTask 側で正常に放送波を受信できていない可能性があります。**
   - 正常に放送波を受信できない場合、エンコーダーの起動に失敗してストリームが開始されません。
   - 考えられる要因：
     1. BonDriver を正常にオープンできていないため、受信自体ができていない
        - 後述の PX-S1UD・PX-Q1UD はこのケースにあたります。
        - あとは BonDriver の 32bit と 64bit を間違えているとか… 
     2. BonDriver はオープンできているが、何らかの原因で 0Mbps になってしまう (0Mbps病)
        - IT35.dll などの BDASpecial プラグインを入れ忘れていたときにも起こるみたいです。
     3. 受信自体はできているが、チャンネル設定ファイル (.ch2) が正しくないため、TVRemotePlus から指定されたチャンネルを選択できない
        - TVTest から持ってきた .ch2 ファイル自体がおかしいか、コピペしたとかで文字エンコードがおかしくなっている可能性があります。
        - .ch2 ファイルは Shift-JIS・CR+LF か UTF-16LE・CR+LF・BOM 付き のどちらかだったはず…
     4. 受信とチャンネル選択もできているが、スクランブルが正しく解除できていない
        - B-CAS（カードリーダー）を読み込む仕組みは TVTest と同じなので、本来は TVTest でスクランブルを解除できていれば TSTask でもスクランブルを解除できるはずです。
        - TVTest でスクランブルを解除できているのに TSTask だとできていない場合は、
          1. PLEX 系チューナーの内蔵カードリーダーを使っているが、TVTest に入れている WinSCard.dll/.ini を `C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask` フォルダに入れていない
          2. TVTest で .scard などの特殊な読み取り方式を使っている
          3. SoftCas を使っている場合で、設定が不正か winscard.dll/.ini (内蔵カードリーダーのものとは別物) を `C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask` フォルダに入れていない  
          といった場合が考えられます。
        - TSTask はカードリーダーを認識してかつ中身が B-CAS カードだった場合、何も指定しなくても自動的にそのカードリーダを選択し、スクランブルを解除してストリームを配信します。
     5. 正常に受信できているが、TSTask の UDP 送信ポートが他のソフトとバッティングしているためエンコーダー側でストリームを受信できない
        - 詳しくは下記の「TVRemotePlus は通常、ポート 8000・8100・8201～8210 あたりを使用します」を参考にしてください。
   - `C:\(TVRemotePlusをインストールしたフォルダ)\log` に書き出されているログを確認してみてください。
   - TSTaskCentre (TSTaskCentre-tvrp.exe)（TSTask と同じフォルダにある）を起動して、TSTask 単体で受信できているかを確認してください。
     - TSTask 側で正常に受信できていない場合は TVRemotePlus 側からは為すすべがありません…
   - 後述のように、BonDriverProxyEx や Spinel から受信し、それを TSTask で受信させた方がうまくいく場合もあります。
   - また、まれですがエンコーダー側に問題がある場合もあります（おもにハードウェアエンコーダー（ QSVEncC・NVEncC・VCEEncC ））。
     - NVEncC の場合は GPU のドライバを更新すると直ったりすることがあるようです。
     - 録画番組の場合、ドロップなどで不正なパケットがあると途中でエンコードが止まってしまうことがあります。
       - ffmpeg でエンコードするとだいたいうまく行きます。
 - **PX-S1UD・PX-Q1UD といった PLEX 製の USB スティック型チューナーをお使いの場合、TSTask 側の問題でストリーム開始に失敗することがあります。**
   - その場合、BonDriverProxyEx (BonDriver_Proxy) を間に挟むことで TSTask 側でも BonDriver を開けるようになります。
   - PX-S1UD・PX-Q1UD で使う BonDriver (BonDriver_BDAT) の実装は BonDriver の中でも特殊で、TSTask 側がうまく BonDriver を開けないのが原因です。
     - OpenTuner() 辺りが問題らしい…？
   - PX-BCUD で動くかどうかはわかりませんが、もしうまく動かないようであれば同様に BonDriverProxyEx を挟むと改善するはずです。
   - PX-S1UD・PX-Q1UD でも BonDriver_BDA が使えるという話も見ました。もし可能であればそちらの方がいいかもしれません。
 - **ストリームが正常に終了できない（チャンネルが変更できない）場合は、環境設定 → ［ストリーム終了時に TSTask を強制終了する］をオンにしてみてください。**
   - この設定をオンにすると TSTask を taskkill /F で強制終了します。
   - 通常の BonDriver を使うと TSTask が taskkill だけでは終了できないことがある問題の対策用の設定です。
   - また、BonDriverProxyEx (BonDriver_Proxy) や Spinel (BonDriver_Spinel) を使うと改善した、という報告もあります。
 - **TVRemotePlus は通常、ポート 8000・8100・8201～8210 あたりを使用します。**
   - ポート 8000 … HTTP アクセス用
   - ポート 8100 … HTTPS アクセス用
   - ポート 8201～8210 あたり … TSTask での UDP 送信に利用
   - インストール時にポートを変更している場合はこの限りではありません。
   - ffmpeg・QSVEncC・NVEncC・VCEEncC といったエンコードソフトが落ちてしまう場合は、ポートがバッティングしている可能性があります。
     - HTTP・HTTPS アクセス用ポートは初回インストール時に変更可能です（ HTTPS アクセス用ポートは HTTP アクセス用ポート + 100 になります）。
     - TSTask での UDP 送信用ポートは 設定ページ にて変更可能です。
 - ストリーム開始フォームの チャンネル もしくは 使用BonDriver の項目が空の場合は、**`C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask\BonDriver` フォルダに使用する BonDriver や .ch2ファイル が入っているかを確認してください。**
   - それでも読み込めていない場合、.ch2ファイルがこちらの想定しているものと違っている可能性があります（不具合報告していただけると助かります）。
   - `C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask` フォルダに BonDriver や .ch2ファイル を置いた場合、認識されません。必ず `C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask\BonDriver` フォルダに入れてください。
 - **ブラウザでアクセスしようとすると「 CONNECTION REFUSED 」と出てアクセスできない場合は、Web サーバー（Apache）が起動しているかどうか確認してください。**
   - Apache が異常終了した場合ダイヤログが表示されるほか、タスクトレイのアイコンを右クリック →［サーバー (Apache) の設定］から Apache のエラーログを確認できます。
   - 起動しているのにアクセスできない場合は、URL 欄に打ち込んだ TVRemotePlus の動いている PC のローカル IP アドレスが正しいかどうか、確認してください。
   - また、お使いのセキュリティソフトのファイアウォールにて、適宜 Web サーバー（Apache）とポート 8000・8100 へのアクセスを許可しておいてください。
 - **HTTPS 用 URL でアクセスしようとすると Bad Request と出てアクセスできない場合は、URL が本当に https:// になっているかどうか確認してください。**
   - Bad Request は、主に HTTPS（ https:// ）用の URL に HTTP（ http:// ）でアクセスしようとした際に起こるエラーです。
   - HTTP 用の URL に HTTPS でアクセスしようとすると、「192.168.x.xx から無効な応答が送信されました。」というエラーが発生します。
  - **GitHub がサーバーダウンしている場合、TVRemotePlus の読み込みが極端に遅くなることがあります。**
    - デフォルトではページを開くたびに GitHub に TVRemotePlus のアップデートがないか問い合わせているのですが、
      GitHub が落ちていてレスポンスすら返ってこない状態の場合、GitHub のレスポンスを待ってしまうため接続がタイムアウトになるまで処理が続いてしまいます。
    - GitHub が落ちている場合は、一時的に 環境設定 → ［TVRemotePlus のアップデートを確認する］をオフにしてみてください。
  - **古い Android 端末では、コメント描画が重くなる場合があります。**
    - コメント描画中にキャプチャする場合、キャプチャ画像の取得に時間がかかることがあります。
    - 最新の端末でも、（スペックにもよりますが）コメントが多く流れているとキャプチャに少し時間がかかります。
    - 動作が極端に重い場合、**Android の設定から［ユーザー補助サービス］が ON になっているアプリを全て OFF にしてみると軽くなります。**
  - **ブラウザによっては、MP4 や MKV のプログレッシブダウンロードでの再生ができない場合があります。**
    - 全てのブラウザで再生できるのは MP4 + H.264 の組み合わせのみです。
    - MP4 + H.265 は Safari と 旧 Edge しか対応していない他、MKV は元々再生できるのが不思議なくらいで、Chrome 以外では再生できません。
    - 画質設定で Original 以外を選択し、TS と同じようにエンコードしながら再生するよう設定すれば、どのブラウザでも再生できます。
    - 詳しくは https://twitter.com/TVRemotePlus/status/1242890072937992193 をご覧ください。
  - **Twitter 連携機能を使いハッシュタグ付きツイートを送信した際にハッシュタグが外れる事がありますが、不具合ではありません。**
    - 環境設定の「ハッシュタグ付きツイートを連投したと判断しハッシュタグを外すまでの秒数」が設定されている場合にこのような現象が発生します。デフォルトは 60（秒）です。
    - Twitter にはシャドウバンという自分のアカウントの全ツイートが一定期間一切 Twitter 検索に引っかからなくなる措置があり、**ハッシュタグ、特にトレンドに入っているタグをつけたツイートを 60 秒以内に連投する状態が一定期間続くと、過去の経験上ほぼ確実にシャドウバンされてしまいます。**
      - 以前 3 ヶ月近くかけて調べましたが、60 秒という値がシャドウバンされるかどうかの分水嶺になっているようです。
        - 30 秒だとシャドウバンされてしまいますが、少なくとも私のアカウントでは 60 秒にするとシャドウバンされる事が減りました。
        - ただし、トレンド 1 位になっているようなツイート数が特に多いハッシュタグのついたツイートを連投すると、ハッシュタグ付きツイートの間隔を 60 秒空けていたとしても問答無用でシャドウバンされがちです。こればかりは Twitter 実況する以上どうしようもない…
    - これに対する苦肉の策として、デフォルトで 60 秒以内に連投した場合にハッシュタグを外し、通常ツイートとして送信することでシャドウバンを極力回避するような設定になっています。
      - 鬱陶しい場合は 0 秒に設定すればオフになりますが、確実にシャドウバンされやすくなるため注意してください。

## 使い方
![Screenshot](docs/screenshot4.png)

 - TVRemotePlus を起動する際は、デスクトップにある TVRemotePlus-Launcher のアイコンをダブルクリックし、利用中は TVRemotePlus-Launcher がタスクトレイに表示されている状態にしておいてください。
 - ブラウザの URL 欄に http://( TVRemotePlus の動いている PC のローカル IP アドレス):8000/ と入力し、TVRemotePlus の Web アプリへアクセスします。
   - HTTPS 用の URL は https://( TVRemotePlus の動いている PC のローカル IP アドレス):8100/ です。
   - 毎回打つのは面倒なため、ショートカットに登録しておくことをおすすめします。
 - 再生ページの下のチャンネル一覧から見たいチャンネルを選び、［ストリーム開始］をクリック・タップします。
 - ファイル再生の場合、サイドメニュー →［ファイル再生］から、見たいチャンネルを選び、［再生する］をクリック・タップします。
 - 左上のボタンを押すと、サイドメニューが開きます。
 - 右上のボタンを押すと、サブメニューが開きます。サブチャンネルの表示/非表示の切り替え、キーボードショートカットの表示、キャスト開始や録画ファイルリストの手動更新などに利用します。
   - うまく更新されない場合は、サブメニュー →［リストを更新］をクリック・タップし、録画ファイルリストに反映させてください。
   - リストの更新には時間がかかる事があります（録画ファイル数が多いと数分かかる事があるかもしれません）
   - ［リストを更新］をクリック・タップした後は、タブを閉じてもそのままバックグラウンドで処理が継続されます。
   - また、サブメニュー →［リストをリセット］をクリック・タップすると、録画ファイルリストをリセットします。うまく番組情報が取得できなかった際などに使ってください。
 - 隠し機能ですが、コマンドラインからストリームを開始する事もできます（ライブ配信のみ）
   - コマンドプロンプトから  
     `C:\(TVRemotePlusをインストールしたフォルダ)\stream.bat ONAir (ストリーム番号) (チャンネル番号)`  
     と実行すると、指定したストリームでライブ配信を開始できます。
     - チャンネル番号は 5(テレビ朝日), 141(BS日テレ) のように指定します。
     - コマンド例：`C:\DTV\TVRemotePlus\stream.bat ONAir 1 141`
     - `C:\(TVRemotePlusをインストールしたフォルダ)\stream.bat ONAir (ストリーム番号) (チャンネル番号) (動画の画質) (エンコード) (字幕データ) (使用 BonDriver)`  
       のように、詳細に指定することもできます。
       - コマンド例：`C:\DTV\TVRemotePlus\stream.bat ONAir 1 5 1080p QSVEncC false BonDriver_Proxy_T.dll`
       - 動画の画質・エンコード・字幕データ・使用 BonDriver の各項目に default と指定すると、デフォルトに指定されている値を使用します。
   - `C:\(TVRemotePlusをインストールしたフォルダ)\stream.bat Offline (ストリーム番号)`  
     と実行すると、指定したストリームを終了できます。
   - この機能を利用し、タスクスケジューラなどに登録しておくと、指定した時間に自動で指定したチャンネルのストリームを起動 / 終了できるようになります。
   - ほとんどメンテナンスしていないので、正常に動作しない可能性が高いです。
 - TVRemotePlus を終了する際は、タスクトレイのアイコンを右クリック →［サーバー (Apache) を終了］をクリックしてください。

### キーボードショートカット
  
  右上の︙メニュー →［ショートカット一覧］もしくは ? キーを押すと、キーボードショートカットの一覧を表示できます。

 - スペースキー … 再生 / 一時停止
 - → キー … 5秒早送りする
 - Ctrl (or Cmd) + → キー … 15秒早送りする
 - Shift + → キー … 30秒早送りする
 - Alt (or Option) + → キー … 60秒早送りする
 - ← キー … 5秒巻き戻しする
 - Ctrl (or Cmd) + ← キー … 15秒巻き戻しする
 - Shift + ← キー … 30秒巻き戻しする
 - Alt (or Option) + ← キー … 60秒巻き戻しする
 - S キー … 字幕の表示/非表示を切り替える
 - D キー … コメントの表示/非表示を切り替える
 - ↑ キー (プレイヤーにフォーカスした状態) … 音量を 10% 上げる 
 - ↓ キー (プレイヤーにフォーカスした状態) … 音量を 10% 下げる
 - F キー … フルスクリーンのオン/オフを切り替える
 - W キー … ブラウザフルスクリーンのオン/オフを切り替える
 - E キー … 画面全体のフルスクリーンのオン/オフを切り替える
 - P キー … ピクチャーインピクチャーのオン/オフを切り替える（ブラウザが対応している場合のみ）
 - L キー … ストリームを同期する（ライブ配信時のみ）
 - C キー … コメント入力フォームを表示・フォーカスする
 - ? キー … キーボードショートカットの一覧を表示する
 - Tab キー … 通常時：ツイート入力フォームにフォーカスする/フォーカスを外す・キャプチャ画像リスト表示時：プレイヤーにフォーカスする / フォーカスを外す
    - ツイート入力フォームにフォーカスしているときは上記の英字キー（ F・W・E・P・S・C キー）のキーボードショートカットが効きません
    - 英字キーのキーボードショートカットを使う場合、一旦 Tab キーを押してツイート入力フォームへのフォーカスを解除してください
    - キーが重複するため、キャプチャ画像リストのキーボードショートカットはプレイヤーにフォーカスされていない状態でのみ利用できます
 - Alt (or Option) + Q キー … キャプチャ画像リストを表示する
 - Alt (or Option) + 1 キー … ストリームをキャプチャする
   - Shift キーを押しながら上記のショートカットを実行すると、字幕を表示しているときでも字幕を入れずにキャプチャできます
 - Alt (or Option) + 2 キー … ストリームをコメント付きでキャプチャする
   - Shift キーを押しながら上記のショートカットを実行すると、字幕を表示しているときでも字幕を入れずにキャプチャできます
 - Alt (or Option) + 3 キー … ハッシュタグ以外のツイート・画像のリセット
 - Ctrl (or Cmd) + V キー (ツイート入力フォームにフォーカスした状態) … クリップボード内の画像を取り込む

## PWA について
![Screenshot](docs/screenshot5.png)

PWA (Progressive Web Apps) とは、

 - **アプリアイコンをデスクトップやホーム画面に追加してそのショートカットから起動出来る**
 - **ブラウザバーを気にせず大きな画面で使える（上の画像を参照）**
 - **起動時に数秒スプラッシュ画面が表示される（ iOS・Android のみ）**
 
など、**Web アプリをローカルアプリのように利用できる新しい仕組みのことです。**  
有名なサイトでは Twitter（新 UI 版）が対応しています。  
TVRemotePlus は、PWA に対応しています（ただし Service Worker の機能は使っていないため、高速化されるわけではありません）。  

しかし、PWA を利用するためには、HTTPS 通信が必須です。そのため、インストール時に予め HTTPS 通信用の自己署名証明書（いわゆるオレオレ証明書）を作成・有効にしてあります。  
自己署名証明書を信頼させ、お使いの端末で PWA を利用するためには、あらかじめ端末に自己署名証明書をインストールしておく必要があります。  
証明書のインストール後、TVRemotePlus と HTTPS でアクセス出来るようになれば、PWA 機能が利用出来るようになります。  
また、PWA は Windows・macOS・Android は Chrome 、iOS では Safari が対応しています。

### PWA のインストール手順
 1. PWA を利用したい端末で TVRemotePlus の設定ページを開き、証明書 (TVRemotePlus.crt) をダウンロードします。
 2. その後、ダウンロードした証明書を開き、端末にインストールします（この時、表示が「CA 証明書」になっているかどうかを確認してください）。
   - 「この種類のファイルはコンピュータに損害を与える可能性が～」と警告が出ることがありますが、無視して「保存」をクリックします。
   - Windows の場合、ダウンロードした TVRemotePlus.crt をクリックし、自己署名証明書を［証明書を全て次のストアに配置する］→［信頼されたルート証明機関］に設定してからインポートします。
   - macOS の場合、インストール後はまだ信頼されていないため、キーチェーンアクセス内のインストールした証明書（ × マークがついている）をクリックします。
     - その後、［信頼］タブを開き、［この証明書を使用するとき］を［常に信頼］に変更してください。
     - × マークが消えて + マークになっていれば OK です。
   - iPhone・iPad の場合、Safari 以外のブラウザでは証明書（プロファイル扱いになる）をダウンロードできません。
 3. インストール後、Chrome または Safari が立ち上がっている場合は一旦終了してから（スマホ・タブレットの場合はタスクを切る）ブラウザをもう一度起動します。
 4. **https://( TVRemotePlus の動いている PC のローカル IP アドレス):8100/** にアクセスし、アドレスバーに鍵マークが正常についていれば、自己署名証明書の導入は完了です。
    - この時に必ず https:// を付けてアクセスしてください。https:// を付けないと http:// と判定されてしまいエラーが出ます。
 5. ブラウザのメニュー等から **［ホーム画面に追加］または［TVRemotePlus をインストール］すると、ネイティブアプリのように利用できるようになっています。**
 6. Android の場合、何故かスプラッシュ画面のアイコンが小さい場合がありますが、原因は不明です（ Chrome の自動推定のせいらしいですが…）。
 7. iPhone・iPad の場合、Safari であれば自己署名証明書をインストールしなくても、http://( TVRemotePlus の動いている PC のローカル IP アドレス):8000/ にアクセスして共有ボタンから［ホーム画面に追加］をタップする事でインストールできます。
    - ただし、自己署名証明書をインストールしない場合、Service Worker に依存する機能は使えないらしいです。現状 Service Worker の機能は使っていないため問題はありません。

## Chromecast (Google Cast) 機能について

Chromecast (Google Cast) 機能は、Chromecast・AndroidTV・Google Home・Google Nest Hub など、 **Google Cast に対応した端末に「キャスト」する事ができる機能です。**（暫定実装）  
この機能を使うと、Chromecast を接続しているテレビや AndroidTV などで TVRemotePlus で配信しているストリームを大画面で視聴することができます。  
ライブ配信はテレビ側で見れるのであまり必要性はないかもしれませんが、**録画した番組（ファイル再生）もキャストすることができます。**  
TS 抜きチューナーで録画した番組を普通のテレビで気軽に見る事ができるので、TS抜き環境とは別にテレビを持っているのであれば割と便利だと思います。
私もほぼファイル再生にしか使っていませんが、東京の実家にチューナーを置いて地方で見てる、という方とかにはライブ配信のキャストも使えるかもしれません。

### 注意
  - **やろうと思えば実装できるとは思いますが、現状コメントや字幕の再生には対応していません…**
    - 手元のスマホにはコメントや字幕が流れるので、スマホのコメントや字幕を見ながらテレビで録画を見るのもありかもしれません
    - Chromecast 周りは本当に不親切な Google の英語ドキュメントくらいしか情報がないので実装するやる気が…
  - **Chrome ネイティブのキャスト機能を使う場合、上の PWA のセットアップ手順を参考に、HTTPS でアクセスするようにしてください。**
    - **HTTP でアクセスした場合、Chrome ネイティブのキャスト機能が使えないため、サーバー側からキャストを開始します**
    - Chrome ネイティブのキャスト端末選択画面ではない場合はその辺りも疑ってみてください
  - Windows10 1809 以前では、サーバー側からキャストする場合に Google Cast デバイスがスキャンできない不具合があるようです（詳細は後述）
    - Windows 標準の mDNS を無効化して Bonjour をインストールするか、Windows10 1903 以降に更新してください
    - Windows10 1903 では標準で mDNSが機能するため、Bonjour を入れる必要はないかもしれません
  - 使い方とか見てれば分かると思いますが、正直かなり動くか微妙なので、暫定実装としています
    - あまり使っていないので、いろいろ不具合を抱えていると思われます

### Chromecast (Google Cast) 機能の使い方
1. テレビの前にスマホ（もしくは PC ）を持っていき、TVRemotePlus を開きます。
2. 再生したいチャンネル・録画番組のストリームを開始し、Chromecast 等で再生したいチャンネル/番組が再生できる状態にします。
3. 右上のサブメニューを開き、「キャストを開始」をクリックします。
4. **PC / Android の Chrome であれば Chrome ネイティブのキャスト機能（以下「ブラウザキャスト」）、対応していないブラウザではサーバー側から（無理やり）キャスト（以下「サーバーキャスト」）するような実装になっています。**
  - このため、ブラウザキャストであればサーバーと異なるネットワークのテレビにキャストすることもできますが、サーバーキャストではサーバーと同じネットワークにあるテレビにしかキャストできません
  - 極論ですが、リモート視聴先から自宅のテレビにキャストすることも仕組み上は可能です
5. PC / Android の Chrome の場合、**同じ Wi-Fi ネットワーク上にある Google Cast 対応デバイスが表示されるので、それをタップするとキャストを開始します。**
   - Google Home などのスピーカーしかついていないデバイスの場合、音声のみ再生されます
   - 同じ Wi-Fi ローカルネットワーク上に Google Cast デバイスが見つからなかった場合は表示されません
   - PC の Chrome からキャストする場合、Chrome 側の不具合か、Google Cast デバイスが見つからないことがあります
     - ブラウザを再起動するとなぜか直ったりします
   - **仕様上、VPN 経由でキャストすることはできません**
     - Chromecast などのデバイスは当然ながら VPN 接続には対応していないため、キャストを指示されてもストリームにアクセスできないためです
6. その他のブラウザ（サーバーキャスト）の場合、初回キャストの場合は同じサイドメニュー → \[キャストを開始\] → \[デバイスをスキャン\] をタップし、**予め Wi-Fi 上の Google Cast 対応デバイスをスキャンしておく必要があります**
   - サーバーキャストを使う場合、**予め Bonjour という mDNS に対応するためのソフトを別途インストールしておく必要があるようです**
     - iTunes の中に入っています
     - Google Cast 対応デバイスをスキャンするのに利用します
   - Google Home などのスピーカーしかついていないデバイスへの再生には対応していません（うまく再生できなかったので表示しないようにしています）
   - また、TVRemotePlus のサーバー上でスキャンするため、当然ながらキャストできるのはサーバー PC のあるローカルネットワーク上の Google Cast 対応デバイスに限られます
   - スキャンする際は **TVRemotePlus（Apache）を管理者権限で実行させてください**（ Bonjour サービスを再起動させた直後にスキャンしないとうまく行かないらしい）
   - 正直、**スキャン機能は動くかどうか非常に微妙です**
   - **機能は Chrome ネイティブの方が上位互換なので、できるだけ HTTPS でアクセスした上で Chrome にて再生させる事をおすすめします**
     - 非対応ブラウザ向けに以前作った無理やりな実装を残しているだけでほぼメンテナンスしていないので、不具合がいろいろあると思います
   - Bonjour をインストールしたのにスキャンできなかったりする場合もありますが、前述した不具合でない場合は正直お手上げです…
7. サーバーキャストの場合、**スキャンが正常に完了すると Google Cast デバイスが表示されているので、それをタップするとキャストを開始します。**
   - キャストを開始すると、再生させていた動画がブラックアウトし、「（キャストしているデバイス名）で再生しています」と表示されます
8. **プレイヤー上で再生・停止・シーク・音量調整（ PC のみ）させると、キャストしているデバイスで再生しているストリームも同期して反映されます。**
   - 微妙に動作がズレますがご愛嬌…
   - ブラウザキャストの方が綺麗に同期されています サーバーキャストの方は同期できていません
   - 操作方法自体は YouTube をキャストする時とさほど変わらないと思います
9.  キャストを終了する場合、**もう一度右上のサブメニューを開き、［キャストを終了］をタップすると、キャストを終了できます**。
   - ブラウザキャストの場合はキャストしているデバイスが表示されるので、適宜終了させてください
   - キャストを終了すると動画が元に戻り、ミュートも解除されて再び音声が流れます
   - 念のためリロードしておくと良いかもしれません

## Twitter API 開発者アカウントの取得について
長くなるため別ページにまとめています。  
[Twitter_Develop.md](docs/Twitter_Develop.md)

## リバースプロキシで外出先からアクセスする（上級者向け）
長くなるため別ページにまとめています。  
[Reverse_Proxy.md](docs/Reverse_Proxy.md)

 
## 注意事項・既知の問題
 - 端末のスペックにもよりますが、基本的に動作が重めです（コメント表示時は特に…）
   - コメントが多くなると固まることもあります…
   - コメントが多すぎて重い場合、プレイヤーの設定でコメント表示をオフにすると軽くなります
 - スペックやその時々の状況によっても変わりますが、仕様上ストリーム開始（チャンネル切り替え）に 5 ～ 20 秒程度かかります
 - 配信準備中…からストリームにうまく移らない・ストリームが止まったときは、時計表示をクリック or タップするとリロードされます
 - TSTask はクライアントプログラムを起動させないオプションで起動させています
   - 立ち上がってるか心配な場合、タスクマネージャーで調べるか別途 TSTaskCentre を起動させるといいと思います
   - 環境設定 → ［TSTask の起動時に TSTaskCentre も起動する］をオンにすると TSTaskCentre も一緒に起動します
   - デフォルトでは ffmpeg・QSVEncC・NVEncC・VCEEncC はバックグラウンドで実行されます（ログは `C:\(TVRemotePlusをインストールしたフォルダ)\log` に出力される）が、
     環境設定 → ［エンコーダーのログをファイルに書き出す］をオフにした上で［エンコーダーのウインドウを表示する］をオンにすると、独立ウインドウにて起動します
 - ニコニコ実況にコメントを投稿する場合、数秒～数十秒遅延している事を念頭に入れた上でコメントしてください
 - 同梱している動作に必要なソフトウェアは全て TVRemotePlus 向けに設定やフォルダ構成を最適化したものになります

## 利用ソフトウェア
動作に必要なソフトウェアをお借りしています。   
全て配布アーカイブの中に組み込んでいますが、BonDriver 周りは各自で用意し、別途 `C:\(TVRemotePlusをインストールしたフォルダ)\bin\TSTask\BonDriver` に入れてください。  
また、QSVEncC を利用する場合は Intel QSV に対応した GPU が、NVEncC を利用する場合は NVIDIA GPU が、VCEEncC を利用する場合は AMD の Radeon GPU が必要です。

- Apache (2.4.46・Web サーバー)
- PHP (7.4.4・実行環境)
- TSTask (0.2.0(patch)・テレビ放送の受信 → UDP 送信)
- TSTaskCentreEx (1.2.0・TSTask へのコマンド送信)
- arib-subtitle-timedmetadater (4.0.9・ARIB 字幕を ID3 メタデータに変換)
- rplsinfo (1.5.2・TS ファイル内の番組情報の取得に利用)
- ffmpeg (4.4・UDP 受信 → エンコード)
- ffprobe (4.4・録画ファイルの動画情報の取得に利用)
- QSVEncC (6.10・UDP 受信 → ハードウェアエンコード)
- NVEncC (5.46・UDP 受信 → ハードウェアエンコード)
- VCEEncC (6.17・UDP 受信 → ハードウェアエンコード)

## 利用ライブラリ

- **CSS ライブラリ**
  - Font Awesome (アイコンフォント)
  - Material Icons (アイコンフォント)
  - Google Fonts (Web フォント)
- **JavaScript ライブラリ**
  - jQuery (フレームワーク)
  - DPlayer (フォーク・JavaScript 製の動画プレイヤー)
  - hls.js (HLS 形式の動画を再生するライブラリ)
  - aribb24.js (ARIB 字幕をブラウザで表示・再生できるライブラリ)
  - CSS Browser Selector (ブラウザや OS ごとにクラスを付与してくれるライブラリ)
  - js-cookie (Cookie の読み取り・書き込みができるライブラリ)
  - moment.js (日付操作ライブラリ)
  - PWACompat (PWA 対応を楽にしてくれるライブラリ)
  - Swiper (スライダーライブラリ)
  - Toastr (トースト通知ライブラリ)
  - Velocity.js (アニメーションライブラリ)
- **PHP ライブラリ**
  - TwitterOAuth (Twitter API ライブラリ)
  - CastV2inPHP (PHP からキャストできるライブラリ)

## 動作環境
  - サーバー：**Windows 10 64bit**
    - 64bit 環境がほとんどのため、同梱しているソフトは全て 64bit 版で組み込んでいます
      - 32bit 環境でも動作させる事自体は可能ですが、同梱しているソフトを全て 32bit 版に差し替える必要があります
  - クライアント：**最新の Chrome・Firefox・Safari など**
    - **Chrome 系のブラウザを強く推奨します**
      - Firefox でも動きますが、あまり検証できていないためもしかすると不具合があるかもしれません
      - Chromium Edge・Brave・Opera・Vivaldi はいずれも Chrome 系のブラウザです
        - いずれのブラウザも Chrome と同じ Blink ブラウザエンジンを採用しています
    - **IE11・Edge Legacy・macOS 版 Safari はサポートしていません**
      - このうち Edge Legacy と macOS 版 Safari では一応動きますが、ブラウザ側の問題で一部の機能が動作しません
    - **キャプチャ機能は Firefox 向け Android・macOS 向け Safari では動作しません**
      - ブラウザ側のバグによるエラーでキャプチャに失敗します
    - **iOS・iPadOS 端末は、ブラウザ側の問題で一部の機能が動作しません**
      - 自動再生されないなどの問題で、Safari 側の仕様やバグに起因するものです
      - iOS・iPadOS 向けのブラウザ（ Chrome・Firefox も含む）は全て Safari のブラウザエンジンである Webkit (WKWebView) を使うことが義務付けられているため、iOS・iPadOS 端末を使う以上は回避できません

## 動作確認
  - サーバー：Windows 10 Pro 64bit (Desktop) + PLEX PX-Q3PE4・Earthsoft PT3
    - スペック：
      - CPU：Core i7-2600K
      - GPU：Intel Graphics 3000・NVIDIA Geforce GTX 1660Ti
      - RAM：8GB
    - PX-Q3PE4 の兄弟機種である PX-W3PE4・PX-W3U4・PX-Q3U4 でも同様に使えると思います
      - 基本的に TSTask が対応しているチューナーなら使えるはずです
    - PT3 でも動作を確認しました
      - チューナーのオープンが速いため、視聴までにかかる時間は PLEX 系チューナーよりも短縮されます
    - 首都圏での利用を前提に開発しています
      - （確かめようがないのですが）チャンネル周りなど、地方では一部動作しない箇所があるかもしれません
    - スカパープレミアム (SPHD) には今のところ対応していません
      - [SPHD に対応させたフォーク](https://github.com/yt4687/TVRemotePlus) があるので、それを使ってみてください
  - クライアント：
    - Windows・macOS
      - Chrome
      - (Firefox)
    - Android
      - Chrome
    - iOS
      - Safari

## 寄付について
寄付したいという方が何人かいらっしゃったので、アマギフだけ受けつけています。  
出来の悪いソフトなので寄付して頂かなくても大丈夫です（特典もなにもないです）が、もし寄付して頂けるのであれば [Twitter の DM（クリックすると DM が開きます）](https://twitter.com/messages/compose?recipient_id=1194724304585248769) か tvremoteplusあっとgmail.com まで送っていただけるととても助かります。

## 不具合報告・フィードバック
不具合報告やフィードバックは [Twitter](https://twitter.com/TVRemotePlus) か [5ch のロケフリスレ](https://mevius.5ch.net/test/read.cgi/avi/1592685644/) にて受け付けています。  
また、使い方がよくわからない場合なども質問いただいて構いません。

5ch の方でも構いませんが、どうしても埋もれてしまったりすることがあるほか、個別の事柄に対応しきれないこともあります。  
特に不具合報告の場合は Twitter で質問いただく方が確実だと思います。こちらとしてもやりやすいです。

## その他・謝辞
詳しくない方でもできるだけ簡単にセットアップできるようにしたつもりですが、  
ソフトの性質上、どうしても一部難しい箇所や環境によってうまく動かない箇所があるかもしれません。

また、このソフトを利用して起こったいかなる不利益も、私（開発者）は一切の責任を負いかねます。あくまで自己責任にて利用してください。  
改変・再配布等はお好きにどうぞ（フォークの内容を取り込む事があるかもしれません）。  

TVTest (NicoJK)・TVRemoteViewer_VB・EDCB Material WebUI・EPGStation など、数多くの先駆者様・ソフトウェア・サイト、  
また様々なネット上の文献を参考にし、ここまで作り上げる事ができました。  
jikkyo_channels.json は TVRemoteViewer_VB にて使われていた ch_sid.txt をチャンネル名を現在の情報に修正し JSON 形式に変換した上で使わせて頂いています。  
TVRemotePlus の字幕表示機能は aribb24.js を DPlayer に組み込んで使わせて頂いています。  
また、QSVEncC・NVEncC・VCEEncC の作者の rigaya 様にはエンコード時の字幕対応等で多大な協力を頂きました。  
この場で厚く御礼申し上げます。本当にありがとうございました！

## Release Notes
[Release_Notes.md](docs/Release_Notes.md)

## License
[MIT License](License.txt)