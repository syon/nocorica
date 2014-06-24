---
layout: post
title: "stoneを使ってプロキシ認証を自動化する"
---
<img src="http://blog.nocorica.jp/wp-content/uploads/2013/11/proxy-auth-dialog.png" alt="proxy-auth-dialog" width="439" height="296" class="alignnone size-full wp-image-337" /><!--more-->

<h3>はじめに</h3>
検索してここに辿り着いたあなたは、さぞかしお怒りのことでしょう。
でももう安心してください。それは実現できます。
だけど注意してください。あくまで自己責任でお願いします。


<h3>stoneの入手</h3>
<a href="http://www.gcd.org/sengoku/stone/Welcome.ja.html">Simple Repeater `stone'</a>
stone version 2.3e for WindowsXP をダウンロード
※Windows7でも使えています
ここでは、解凍したフォルダを C:\stone23xp に置いたものとして説明します。


<h3>認証情報のBase64エンコード</h3>
<a href="http://homepage3.nifty.com/georgei/hmetzger/base64.html">JavaScript による Base64 エンコーダ/デコーダ</a>
username:password の形式でBase64エンコードします。
例） tanaka:secret123　→　dGFuYWthOnNlY3JldDEyMw==


<h3>設定ファイル stone.cfg の作成</h3>
以下の例に従って設定内容を1行で記述し C:\stone23xp\stone.cfg として保存します。
中央の8080でstoneのポート番号を指定しています。
<pre class="lang:default decode:true " >
proxy.example.co.jp:8080/proxy 8080 "Proxy-Authorization: Basic dGFuYWthOnNlY3JldDEyMw=="
</pre> 


<h3>サービス化と起動</h3>
<pre class="lang:default decode:true " >
cd C:\stone23xp
stone -M install repeater -C C:\stone23xp\stone.cfg
net start repeater
services.msc
</pre> 
Stone repeater >プロパティ > スタートアップの種類(E): 自動


<h3>使い方</h3>
インターネットオプション > 接続タブ > LANの設定 > LANにプロキシサーバを使用するにチェック。
アドレス(E): localhost　ポート(T): 8080
※パスワードを変更したら、Base64エンコードをやり直して stone.cfg を修正しサービスを再起動します。


<h3>サービス削除</h3>
<pre class="lang:default decode:true " >
stone -M remove repeater
</pre>
上記でうまくいかないときは
<pre class="lang:default decode:true " >
sc.exe delete repeater
</pre>
→ OS再起動
