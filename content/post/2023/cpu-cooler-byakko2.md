---
title: "CPUクーラーを白虎2へ交換" # Title of the blog post.
date: 2023-03-08T20:26:55+09:00 # Date of post creation.
description: "Article description." # Description used for search engine.
featured: false # Sets if post is a featured post, making appear on the home page side bar.
draft: false # Sets whether to render this page. Draft of true will not be rendered.
toc: false # Controls if a table of contents should be generated for first-level links automatically.
# menu: main
# featureImage: "/images/path/file.jpg" # Sets featured image on blog post.
# thumbnail: "/images/path/thumbnail.png" # Sets thumbnail image appearing inside card on homepage.
# shareImage: "/images/path/share.png" # Designate a separate image for social media sharing.
codeMaxLines: 10 # Override global value for how many lines within a code block before auto-collapsing.
codeLineNumbers: false # Override global value for showing of line numbers within code block.
figurePositionShow: true # Override global value for showing the figure label.
showReadTime: false
categories:
  - PC
tags:
  - 自作PC
# comment: false # Disable comment if false.
---

キッチンPCとして家族が主に使っているパソコン、以前電原稿交換したという記事を書いたが(
[PCの電源交換]({{< ref "post/2022/kitchen-pc-replace-power.md" >}})を参照)、今度はCPUファンが止まってしまい「CPU Fan Error」というエラーが出て起動しなくなってしまった。

パソコンが壊れた時に直すのは私の役目になっている。まぁ他に直せる人がいないから仕方ないのだけど。

サイドパネルを開けてファンとヒートシンクを見ると埃が結構溜まっている。それが原因かと思いきれいに掃除してみるもやはりファンは回らず。

ケースファンを端子に挿してみると回るので、端子に電流は流れている。となると、CPUファンの故障だろうか。まぁファンは可動部品だから寿命が来たのだろう。

というわけでCPUクーラーをメルカリで探してみると、Core i5 2400と純正CPUクーラーの未使用品セットが2000円で出品されていた。

純正CPUクーラーだけでもアマゾンだと2000円弱するのでCPU付きなのはお得だ。もちろん今のよりグレードが低かったら無駄になるが、今使ってるCPUはCeleron G530というエントリーグレードなので、この際CPUも交換してしまえば処理速度向上も見込める。

さすがにどれだけ回っていたかわからないCPUファンは避けたいのでちょうど未使用品があってよかった。

さらにどうせならストレージもHDDからSSDに変えてみようということで、256GBのSSDも2300円ぐらいでアマゾンで購入。それにしても一昔前と比べるとSSDも安くなったものだ。10年以上前は128GBのSSDを1万以上出して買った記憶がある。

[![::img-medium](/images/post/byakko2-001.jpg)](/images/post/byakko2-001.jpg)  


さて、CPUとSSDを変えたらどれくらい早くなるかな～とワクワクしながら発送通知を待っていたものの、一向に出品者から連絡がない。
購入から一日経過して何の音沙汰もないため、こちらからメッセージを送ってみるも何の返信もない。さらに一日経過したので、発送予定を聞いてみるもやはり返事がない。もうアマゾンで買ったSSDは届いているというのに・・・

パーツが届かないと当然パソコンが使えず、テレビも見れない。私はテレビは見ないけど、親はちょっと寂しそう。二日経っても何も連絡がないので、このままだと進展なしと判断し、直接店舗へ行って買ってくることに。近くのハードオフに白虎2というCPUクーラーが1600円であったので、それを買ってきた。

中古なのかと思っていたが、箱を開けてみると使った形跡がなく、新古品だった。ファンの消耗はなさそうでよかった。グリスも付属していたので別に買ってくる必要もなくて助かった。

[![::img-medium](/images/post/byakko2-002.jpg)](/images/post/byakko2-002.jpg)  
[![::img-medium](/images/post/byakko2-003.jpg)](/images/post/byakko2-003.jpg)  
[![::img-medium](/images/post/byakko2-004.jpg)](/images/post/byakko2-004.jpg)  

早速取り付けてみる。プッシュピンが固くてなかなかはまらず結構苦労したが、なんとかマザーボードに固定できた。もちろん動作も問題なし。

CPUファンの問題は解消したので今度はストレージ。
HDDで起動することを確認し、その後ハードディスクをSSDに換装する。

クローンできるソフト「Macrium Reflect」の無料体験版を使ってハードディスクをSSDに複製する。30日しか使えないがHDDをSSDにクローンする作業なんて何回もやらないので問題なし。クローン自体は1時間ぐらいかかって完了。

さっそく複製し終えたSSDで起動してみるが、黒い画面のままWindowsが立ち上がらない。

起動しない理由をネットで色々調べて、対応法をいろいろ試してみる。bootrecでマスターブートレコードの修復とかやってみるも効果なし。結局windowsのインストールディスクからスタートアップ修復を行ったらSSDから起動するようになった。

やはりSSDは早い。Windowsの起動もだいぶ短縮された。アプリも体感できるレベルで早くなっている。CPUはCeleronのままでここまで違いが出るとはSSD恐るべし。HDDのままCeleronからCore i5に変えるより、CPUはCeleronのままHDDをSSDに変えた方が変化を体感できる。

メルカリで買ったCPUとCPUクーラーは、購入から3日目になってようやく出品者から連絡が来て週末に発送しますとのこと。購入したのが日曜日だったのでなんと6日後！もう別のを買ってしまったし、商品説明では1～2日で発送になっていたのだからと堂々とキャンセル申請することに。メルカリで初めてのキャンセル申請。さて出品者は同意してくれるだろうか。