---
layout: post
title: "stoneを使ってプロキシ認証を自動化する"
description: "stoneを使ってプロキシ認証を自動化する"
imagefeature:
featured: true
message: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [How to]
tags:
  - Server
  - Windowss
---

![proxy auth dialog](/postimg/2013/11/proxy-auth-dialog.png)

### はじめに

検索してここに辿り着いたあなたは、さぞかしお怒りのことでしょう。  
でももう安心してください。それは実現できます。  
だけど注意してください。あくまで自己責任でお願いします。


### stoneの入手

- [Simple Repeater `stone'](://www.gcd.org/sengoku/stone/Welcome.ja.html)  

stone version 2.3e for WindowsXP をダウンロード  
※Windows7でも使えています  
ここでは、解凍したフォルダを C:\stone23xp に置いたものとして説明します。


### 認証情報のBase64エンコード

- [JavaScript による Base64 エンコーダ/デコーダ](://homepage3.nifty.com/georgei/hmetzger/base64.html)  

`username:password` の形式でBase64エンコードします。  
例） `tanaka:secret123`　→　`dGFuYWthOnNlY3JldDEyMw==`


### 設定ファイル stone.cfg の作成

以下の例に従って設定内容を1行で記述し `C:\stone23xp\stone.cfg` として保存します。  
中央の8080でstoneのポート番号を指定しています。

```
proxy.example.co.jp:8080/proxy 8080 "Proxy-Authorization: Basic dGFuYWthOnNlY3JldDEyMw=="
```


### サービス化と起動

```
cd C:\stone23xp
stone -M install repeater -C C:\stone23xp\stone.cfg
net start repeater
services.msc
```

Stone repeater `>` プロパティ `>` スタートアップの種類(E): 自動


### 使い方
インターネットオプション `>` 接続タブ `>` LANの設定 `>` LANにプロキシサーバを使用するにチェック。
アドレス(E): `localhost`　ポート(T): `8080`  
※パスワードを変更したら、Base64エンコードをやり直して stone.cfg を修正しサービスを再起動します。


### サービス削除

```
stone -M remove repeater
```

上記でうまくいかないときは

```
sc.exe delete repeater
```

→ OS再起動
