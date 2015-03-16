---
layout: post
title: "Atomでパッケージをインストールする方法とメニューの日本語化"
description: "Atomでパッケージをインストールする方法とメニューの日本語化"
imagefeature:
featured: true
message: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [How to]
tags:
  - Atom
  - Editor
---

## 設定画面を開く

![](/postimg/2015/03/15-1.png)

メニューから `Preferences...` を選択します。ショートカット `command + ,` でも行けます。


## パッケージを検索する

![](/postimg/2015/03/15-2.png)

左のメニューから ＋ Install を選んで検索画面に行きます。
お探しのパッケージを見つけてインストールボタンを押して完了です。  
変更が反映されない場合があるので __Atomを再起動__ しておきましょう。

パッケージのインストール方法は以上ですが、実際の流れがわかるよう、例としてメニューの日本語化をやってみます。


## 日本語化パッケージをインストールする

![](/postimg/2015/03/15-3.png)

「__Localization__」というパッケージを検索してインストールします。

### 再起動

![](/postimg/2015/03/15-4.png)

Atomを再起動します。

### 設定を Japanese に変更

![](/postimg/2015/03/15-5.png)

メニューの Packages に Localization が追加されているので、そこから Japanese を選択します。すると、自動的に Atom が再起動されてメニューが日本語化されているのが確認できます。

![](/postimg/2015/03/15-6.png)

### うまくいかないときは？

![](/postimg/2015/03/15-7.png)

Japanese を選択しても、Atomが再起動されず無反応な場合があります。そのような場合には Localization の設定画面で Current Language に Japanese と手打ちして再起動したところうまく反映されました。

### 警告が出る (2015.03.15)

![](/postimg/2015/03/15-8.png)

Atomのウィンドウの右下に警告アイコンが表示されました。これについては、すでに GitHub に同じ内容の報告が上がっているので待っていれば対応されるかと思います。  
状況が変わりましたらまた更新します。

- [Issues · pandarison/Atom-Localization](https://github.com/pandarison/Atom-Localization/issues)
