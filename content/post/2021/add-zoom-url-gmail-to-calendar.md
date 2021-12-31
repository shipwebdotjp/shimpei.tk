---
title: "Gmailに来たZoomの招待リンクをGoogle Calendarに登録" # Title of the blog post.
date: 2021-12-21T20:35:04+09:00 # Date of post creation.
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
  - ライフハック
# comment: false # Disable comment if false.
---

## 概要
### 目的
Zoomミーティングに参加するときにわざわざGmailを開いてリンクをクリックするのが面倒なので、
Zoomのアプリを開いて、ミーティングタブに表示されるミーティング予定の「参加」ボタンクリック一発で参加したい。  


## 必要な準備
### ZoomとGoogleカレンダーの連携
1. zoom.usにログインして、プロフィールの編集から「カレンダーと連絡先の統合」でGoogleカレンダーと連携しておく
1. 招待メールを受け取ったら、招待メールの中に記されているZoomリンクを場所欄にコピペした予定をカレンダーに登録
1. これでZoomアプリのミーティングタブに、Googleカレンダーに登録されている予定が表示され「参加」ボタンからワンクリックでZoomに参加できるようになる。
1. 「場所」欄にZoomの招待リンクを入れて予定を登録するのがポイント。

## スクリプト
さらにものぐさな私は、招待メールが来たら、リンクを自動ででGoogleカレンダーに登録できないか考えた。  
それでGoogle Apps Scriptを使い、Gmailを定期的にチェックし、Zoomリンクが含まれたメールが来ていたらその件名と日付、URLで予定作成しGoogleカレンダーに登録するスクリプトを作成した。

```
//新着メールチェック
function mailCheck(){
  const SEARCH_TERM = 'is:unread zoom.us/j/';
  const threads = GmailApp.search(SEARCH_TERM, 0, 30);
  const messages = GmailApp.getMessagesForThreads(threads);
  const regexpUrl = RegExp('https:\/\/[^.]+\.zoom\.us\/j\/.*', 'gi');
  const label = GmailApp.getUserLabelByName("Zoom");

  for(var i=0; i < messages.length;i++){
    thread = messages[i];
    for(var j=0; j < thread.length; j++){
      message = thread[j];
      if(message.isUnread() && !message.isStarred()){
        const plainBody = message.getPlainBody();
        let title = message.getSubject();
        const resultTitle = plainBody.match(/トピック:\s(.*)/i);
        if (resultTitle != null) {
          title = resultTitle[1];
        }
        title = title.replace(/[0-9]{1,2}\/[0-9]{1,2}\(.\)[0-9]{1,2}:[0-9]{1,2}～/,"");
        console.log(title);
        
        const resultUrl = plainBody.match(regexpUrl);
        if (resultUrl == null) {
          continue;
        }
        const zoomUrl = resultUrl[0];
        console.log("URL:"+ zoomUrl);

        const resultTime = plainBody.match(/([0-9]{4})年([0-9]{1,2})月([0-9]{1,2})日\s([0-9]{1,2}):([0-9]{1,2})\s*(PM|AM)?/i);
        if (resultTime == null) {
          continue;
        }else{
          const year = parseInt(resultTime[1]);
          const month = parseInt(resultTime[2]);
          const dayOfMonth = parseInt(resultTime[3]);
          const startTimeHour = resultTime[6] == "PM" ? parseInt(resultTime[4]) + 12 : parseInt(resultTime[4]);
          const startTimeMin = parseInt(resultTime[5]);
          const startTime = new Date(year, month - 1, dayOfMonth, startTimeHour, startTimeMin, 0);
          const endTime = new Date(year, month - 1, dayOfMonth, startTimeHour + 1, startTimeMin, 0);
          createEvent(title, zoomUrl, startTime, endTime);
          message.star();
          message.getThread().addLabel(label);
          console.log("start: "+startTime.toString());
        }
      }
    }
    
  }
}

function createEvent(title, location, startTime, endTime) {
  const calendar = CalendarApp.getDefaultCalendar();
  const option = {
    location: location,
  }
  calendar.createEvent(title, startTime, endTime, option);
}
```

### 使用方法
1. Googleドライブで新しいGoogle Apps Scriptを作成し、上のコードをコピペ
2. プロジェクトに名前を付けて保存
3. スクリプトのタイムゾーンを変更
    1. 「プロジェクトの設定」で「「appsscript.json」マニフェスト ファイルをエディタで表示する」にチェックを入れる
    2. エディタで「appsscript.json」を開き「timeZone」の"America/New_York"を"Asia/Tokyo"に変更
4. 実行する。承認が必要というダイアログが出るので権限を確認→詳細→○○に移動→許可
5. もう一度実行
6. トリガーを追加して定期的に実行するように設定する
7. GmailでZoomという名前のラベルを作成しておく（処理済みはこのラベルが付く）

## 感想
Gmailを開いてリンクをクリックするのも、参加ボタンをクリックするのも同じのような気もするけど、こんな利点があると思った。
- 埋もれた招待メールを探さなくてもいい
- Zoomミーティングに参加する前にカメラや音声チェックをする習慣があるので、かならずZoomアプリは先に開いているのでスムーズに入室できる。

それではよいZoomライフを。