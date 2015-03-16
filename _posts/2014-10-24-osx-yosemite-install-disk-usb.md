---
layout: post
title: "OSX Yosemite USBインストールディスク作成手順"
description: "OSX Yosemite USBインストールディスク作成手順"
imagefeature:
featured: true
message: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [How to]
tags:
  - Mac
---

## App Store からダウンロード

![](/postimg/2014/10/24-05.png)

ここでボタンを押しても勝手にインストールが始まったりはしないのでご安心を。  
「OS X Yosemite インストール」というアプリがインストールされるだけです。

なお、Yosemite 上の App Store でもダウンロードができるようです。  
ここでの例は Mavericks を使用していますが、Yosemite を入れてからもインストールディスクは作れるのではないかと思います。

![](/postimg/2014/10/24-04.png)

↑こいつは閉じます。


## USBメモリを用意

Yosemite は 5 GB ちょっとです。 __8 GB あれば十分__ です。  
クリーンインストールに専用化するのであれば 8 GB をおすすめします。

[![](/postimg/2014/10/24-00.jpg)](http://amzn.to/10rrRhx)

[【Amazon.co.jp限定】Transcend SuperSpeed USB 3.0&Hi-Speed USB 2.0 USBメモリ 700シリーズ 32GB (無期限保証) TS32GJF700E (FFP)](http://amzn.to/10rrRhx)

[![](/postimg/2014/10/24-toshiba8gb.jpg)](http://amzn.to/ZPWzA0)

[【8GB】 東芝/TOSHIBA USBフラッシュメモリ(TransMemory) USB2.0 Windows7/Mac対応 UHYBS-008GH](http://amzn.to/ZPWzA0)


## ディスクユーティリティを開く

![](/postimg/2014/10/24-09.png)


## ディスクのフォーマット

左のエリアで USB ディスクのトップ階層（画像だと 31.59 GB JetFlash〜のところ）を選択してから、タブ「消去」を選択。

- フォーマット：`Mac OS 拡張（ジャーナリング）`
- 名前：`Yosemite` ※次に実行するコマンドで使用します

![](/postimg/2014/10/24-11.png)


## USBメモリのインストールディスク化

ターミナルを開いて以下のコマンドを実行。

```bash
sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume /Volumes/Yosemite --applicationpath /Applications/Install\ OS\ X\ Yosemite.app --nointeraction
```

![](/postimg/2014/10/24-17.png)


## 動作確認

`option`キーを押しながらMacを起動。
下図のようにUSB起動ディスクが認識されれば成功。

![](/postimg/2014/10/24-disk.jpg)
