---
layout: post
title: "Docker＋Ubuntuで日本語入力できないのを解決した"
description: "Docker＋Ubuntuで日本語入力できないのを解決した"
categories: [Trouble shooting]
tags:
  - Docker
  - Ruby
---

![japanese input on shell on ubuntu on docker](/postimg/2017/01/08-a.png)


## Context

IRKit という赤外線リモコン信号を制御するものがあるのですが、
これを Ruby から操作する Gem を使って赤外線信号を登録するときに日本語名称を割り当てるんですね。
それがそのまま内部に保存している JSON のキーになっているので、
コマンドで呼び出す時も日本語で指定する必要があるわけです。

で、今回この処理を Docker の中に閉じ込めようとしたところ動作せずにつまづきました。
原因は「Docker＋Ubuntuで日本語入力できないこと」に行き着いたため、調査し解決に至りました。

#### 参考記事

- [Docker1\.11 / Ubuntu14\.04 でコンテナの bash から日本語入力できない時 \- Qiita](http://qiita.com/narupo/items/ebee3018fb302365c053)
- [docker の ubuntu イメージで日本語が入力できない件 \- しゅんログ](http://shunlog.hateblo.jp/entry/2016/04/13/114059)
- [IRKit GUIをDockerに対応してメニューバーから使えるようにしました \- syonx](http://syonx.hatenablog.com/entry/2017/01/08/223522)


## 解決方法

下記の Dockerfile に示すとおり設定すれば OK です。
参考記事に記載のやり方よりも、`ENV`を使用したこちらの方がよいと思います。

### Dockerfile（抜粋）

```
RUN apt-get install -y language-pack-ja-base language-pack-ja
ENV LANG=ja_JP.UTF-8
```
