---
layout: post
title: "Vue.js - Unknown custom element (vue-cli 単一ファイルコンポーネント)"
description: "Vue.jsでRecursive Componentsエラー"
categories: [Trouble shooting]
tags:
  - JavaScript
  - Vue.js
---

![Unknown custom element](/postimg/2017/03/18-a.png)

## Problem

Vue.js を試してみようと、`vue-cli` を使って Single File Components 方式で始めてみました。

- [vuejs/vue\-cli: Simple CLI for scaffolding Vue\.js projects](https://github.com/vuejs/vue-cli)
- [Single File Components — Vue\.js](https://vuejs.org/v2/guide/single-file-components.html)

ところが、コンポーネントを入れ子にしたタイミングでエラー発生。

> Unknown custom element: \<Hello\> - did you register the component correctly? For recursive components, make sure to provide the "name" option.

> 未知のカスタム要素: \<Hello\> ― 正しくコンポーネントを登録しましたか？
再帰的なコンポーネントの利用においては "name" オプションが提供されていることを確認してください。

もしあなたが再帰的なコンポーネントのような難しいことをしようとしていないならば、
エラーの原因は些細な記述ミスである可能性が高いです。


## 従来方式のおさらい

コンポーネントを *.js ファイルに記述する従来の方式であれば、下記のようにしてコンポーネントを登録します。

```js
Vue.component(SomeCompo.name, SomeCompo);
Vue.component(AnotherCompo.name, AnotherCompo);
```

- [コンポーネントの登録 — Vue\.js](https://jp.vuejs.org/v2/guide/components-registration.html)


## 単一ファイルコンポーネント方式でのコンポーネント登録方法

[単一ファイルコンポーネント](https://jp.vuejs.org/v2/guide/single-file-components.html)
とは `SomeComponent.vue` のように *.vue 拡張子のファイルで表現したコンポーネントを指します。

こちらは公式から引用した Single File Components のサンプルです。`components:`の箇所を改めてよく見てみると、<mark>__配列ではなくオブジェクト__</mark> になっているじゃありませんか。

<img src="/postimg/2017/03/18-b.png" style="max-height:700px;">

```js
  components: {
    OtherComponent
  }
```

従来のJavaScriptを知っている方なら、これはシンタックスエラーと勘違いするかもしれません。ですが、ES2015 からショートハンドで上記のように書けるようになりました。
言い換えると、以下の通り書いたときと同じ意味になります。

```js
  components: {
    OtherComponent: OtherComponent
  }
```

つまり "OtherComponent" という名前のコンポーネントとして `OtherComponent` を登録しています。
[パスカルケース (PascalCase)で登録](https://jp.vuejs.org/v2/guide/components-registration.html)
したコンポーネント `OtherComponent` は、ケバブケース (kebab-case) `other-component` でテンプレート内に記述して利用します。
なので `<other-component>...</other-component>` とマークアップすることでコンポーネントを配置できます。

上の画像 Hello.vue のテンプレート内を見てみると `other-component` と書いてあり、呼び出していることがわかります。
さらにテンプレートは Jade (現Pug) で簡潔に書ける例を提示しているため `<x>` `</x>` の形式を簡略化しています。

- [pugjs/pug](https://github.com/pugjs/pug#syntax)

---

さて、問題は解決できたでしょうか。

お困りの際はこちらからどうぞ。暇してたらサポートします。

<a href="https://twitter.com/intent/tweet?screen_name=syonxv&ref_src=twsrc%5Etfw" class="twitter-mention-button" data-show-count="false">Tweet to @syonxv</a><script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
