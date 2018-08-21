---
layout: post
title: "Vue.js devtoolsが表示されない時のチェックポイント"
description: "Vue.js開発に役立つChrome拡張の「Vue.js devtools」が表示されない時のチェックポイント"
categories: [Trouble shooting]
tags:
  - Vue.js
---

![Vue.js devtools](/postimg/2018/08/20-a.png)


## チェック① <br> Vue.js devtools がインストールされているか

灯台下暗し。他人のPCだったり、最近PCを切り替えたりしていませんか。または、妖精さんの仕業で __オフ__ になっていたりしませんか。Chrome本体のアップデートでセキュリティが強化されて安全のため自動的に停止されているなんて可能性はありそうです。

- [chrome://extensions/](chrome://extensions/)
- [Vue.js devtools - Chrome ウェブストア](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)

![Vue.js devtools management](/postimg/2018/08/20-e.png)


## チェック② <br> Chrome Devtoolsを開くタイミング

対象のページを開いてから「ん？これどうなってるんだろう…」という流れだと Chrome Devtools を後で開くとうまく表示されないことがあります。
ネットワークの通信状況を閲覧するときのように、Chrome Devtools を開いた状態にしてからページを読み込んでみましょう。


## チェック③ <br> 開発モードになっているか

Vue.jsの実行コードがプロダクションモード（本番モード）になっていると、DevtoolsはVueアプリの構造を検出できません。

![Vue.js devtools available or not](/postimg/2018/08/20-b.png)


## チェック④ <br> キャッシュされていないか

キャッシュされたコードが読み込まれている可能性があります。
Networkタブにある Disable cache を有効にして再読込してみましょう。

![Vue.js devtools disable cache](/postimg/2018/08/20-c.png)


## チェック⑤ <br> Vue.jsライブラリ本体と実行コードを分けていないか

シングルページアプリケーション（SPA）であれば webpack 等で１ファイルにバンドルするのが通常ですが、状況によってはVue.jsライブラリ本体と実行コードを分けている場合があると思います。

このとき、必死に実行コード側を開発モード (mode=development) にしても、ライブラリ本体が本番モード (mode=production) になっていては開発ツールは有効になりません。


## チェック⑥ <br> 他のページやアプリなら動作するのか

Vue.jsのオンラインドキュメントでは、開発モードもしくは内部構造の閲覧が許可された状態で公開されています。
このページで動作確認をしてみて、原因が開発中のアプリなのか拡張機能なのか切り分けてみましょう。

- [はじめに — Vue.js](https://jp.vuejs.org/v2/guide/)


## チェック⑦ <br> それでもダメなとき

「以前は使えていたのに、急に使えなくなった！！」という時は、拡張機能自体を疑ってみます。
まずは拡張機能が最近更新されたかどうか、それがインストール中のものとバージョンが一致しているかどうかを確認します。バグなどがあれば GitHub の Issue で同じように困っている人がすでに報告していないかを見てみましょう。

![Vue.js devtools chrome webstore](/postimg/2018/08/20-d.png)

![Vue.js devtools management](/postimg/2018/08/20-e.png)

![Vue.js devtools github issues](/postimg/2018/08/20-f.png)

- [Issues · vuejs/vue-devtools](https://github.com/vuejs/vue-devtools/issues)

---

開発がんばってネ😇
