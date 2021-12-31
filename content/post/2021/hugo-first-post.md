---
title: "このサイトを作ったきっかけ" # Title of the blog post.
date: 2021-11-27T23:40:53+09:00 # Date of post creation.
description: "最初の投稿です。" # Description used for search engine.
featured: false # Sets if post is a featured post, making appear on the home page side bar.
draft: false # Sets whether to render this page. Draft of true will not be rendered.
toc: false # Controls if a table of contents should be generated for first-level links automatically.
# menu: main
# featureImage: "/images/path/file.jpg" # Sets featured image on blog post.
# thumbnail: "/images/path/thumbnail.png" # Sets thumbnail image appearing inside card on homepage.
# shareImage: "/images/path/share.png" # Designate a separate image for social media sharing.
# codeMaxLines: 10 # Override global value for how many lines within a code block before auto-collapsing.
# codeLineNumbers: false # Override global value for showing of line numbers within code block.
# figurePositionShow: true # Override global value for showing the figure label.
showReadTime: false
categories:
  - Test
tags:
  - Test
# comment: false # Disable comment if false.
---

## サイト作成のきっかけ

きっかけはshimpei.tkドメインが余っていたことから始まる。

shimpei.tkは個人用途で使おうと思って結構前に取得したドメイン。以前はメールアドレスに使っていたけどやはりプッシュ配信ができないのが不便でGmailに移行してしまってメール用としても今は使っていない。

しかしドメインを遊ばせておくのももったいないと思って、何かできるかなと考えたところ、海外とか離れたところにいる友達に近況を知らせるサイトを作ったらいいのでは？と。まぁ僕の近況を知りたい人がどれだけいるかははなはだ疑問だけど。

だったらSNSでよくない？となるんだけど、どうも僕はSNSに投稿するのが合わないというか、投稿したときの「私がこんな投稿したよ、見てみて！いいねちょうだい！」みたいな雰囲気がどうも苦手。

InstagramにしろTwitterにしろLINEのタイムラインにしろ、投稿するとそれがフォローしてくれている人の画面に出るわけで、他の人に見られるのかーと思うと投稿が遠のいてしまう。

友達に見られるのが嫌なら自分の日記帳にでも書いてれば？となるかもしれないけど、ここがミソで、別に見てほしくないわけではないんだよなぁ。やっぱりせっかく書くなら他の人にも見てもらいたいという思いもあるわけで・・・

見てほしいけど、大げさに知らせたくないというこの微妙な気持ち・・・

そこでブログなら、こっちからお知らせするわけではないので、通知で煩わすことはないので安心。僕ごときの投稿で「○○さんがストーリーズを公開しました」なんて通知をフォロワーみんなに送って時間や集中力を奪いたくないわけで。

つまり**プッシュ型**ではなく**プル型**で発信したいというのが望み

その点ブログならひっそり公開しておいて、見たい人が見たいときに見てくれるという感じでまさにプル型なので、この塩梅がちょうどよい。

しかもいいね！もないし既読機能ももちろんないから誰が見てどんな反応があるかも気にしなくていいというのも楽。見てくれた友達からDMが来るかもしれないけどそれは別に構わないしむしろうれしい。こっちから返信や反応を押し付けているわけではない自発的なものなので。

ちょっと話題がそれるけど、最近思うのはいいね！とかってなんか義務になってしまいがちってこと。見たよ！代わりにとりあえずいいねしとくみたいな・・・。だから自分の投稿にいいねはむしろいらないんだけど、SNSだと機能をOFFにすることもできず・・・ということでそういうのも含めて自分で設定できるブログがやっぱ合ってるのかなーって。

## サイトの技術選定

と、まぁここからは技術的なお話。ブログのような形式でサイトを作るとしてすぐに思いつくのは言わずと知れたWordpress。でもWordpressには飽きたというか、目新しくないのでパス。やっぱここは新しい技術を使ってみようと思い、ヘッドレスCMSとか、静的サイトジェネレーターあたりのキーワードで探してみると、どうやら[Hugo](https://gohugo.io/)という静的サイトジェネレーターが使いやすそうで情報も比較的多かったので決定。

Golangで書かれてるらしいけど、Linux用のバイナリを落としてきてWSL2の/usr/local/binに放り込むだけでhugoコマンドが使えるようになる。

たくさんある中で選んだテーマは[Hugo Clarity](https://github.com/chipzoller/hugo-clarity)。なんかデザインが良かったので。多言語対応で機能も一通りそろっている。

記事はMarkdownで書けるのでVS Codeでガシガシ書いてhugoコマンドで書き出して、サーバーへアップロードするだけ。ビルドしてVPSにrsyncするスクリプトを書いて自動デプロイもどきをしている。

## まとめ

ということで完全に個人的な趣味のブログなので見たい方はぜひ見ていただけたら嬉しいです。