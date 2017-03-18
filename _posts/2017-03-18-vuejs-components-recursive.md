---
layout: post
title: "Vue.js - Unknown custom element (vue-cli Single File Components)"
description: "Vue.jsでRecursive Componentsエラー"
categories: [Trouble shooting]
tags:
  - JavaScript
---

![Unknown custom element](/postimg/2017/03/18-a.png)

### Problem

Vue.js を試してみようと、`vue-cli` を使って Single File Components 方式で始めてみました。

- [vuejs/vue\-cli: Simple CLI for scaffolding Vue\.js projects](https://github.com/vuejs/vue-cli)
- [Single File Components — Vue\.js](https://vuejs.org/v2/guide/single-file-components.html)

ところが、コンポーネントを入れ子にしたタイミングでエラー発生。

> Unknown custom element: \<Hello\> - did you register the component correctly? For recursive components, make sure to provide the "name" option.

### Solution 1

通常の方法であれば、下記のようなコードによってコンポーネントを登録すれば解決します。

```js
import SomeCompo from './SomeCompo.vue'
import AnotherCompo from './AnotherCompo.vue'

Vue.component(SomeCompo.name, SomeCompo);
Vue.component(AnotherCompo.name, AnotherCompo);
```

ですが、これをこれから作るコンポーネントすべてに対していちいち行わなくてはならないのでしょうか。まだ始めたばかりなのでその流儀はわかりませんが、自分なりの解決法を考えました。

#### 再帰的にコンポーネントを登録する

はじめは以下のようなやりかたで、ルートコンポーネントを渡して再帰的に登録するやりかたを考えました。各`.vue`ファイルのスクリプトで`components: []`に依存コンポーネントを定義して自動で解決してもらいます。ですが、__このやり方はよくないです__。

![Register Components Recursively Function](/postimg/2017/03/18-c.png)

```js
function registerComponentsRecursively(compo) {
  if (compo.components) {
    compo.components.forEach(function(c){
      Vue.component(c.name, c)
      registerComponentsRecursively(c)
    })
  }
}

registerComponentsRecursively(App)
```

### Solution 2

まずこちらは公式から引用した Single File Components のサンプルです。`components:`の箇所を改めてよく見てみると、 __配列ではなくオブジェクト__ になっているじゃありませんか。

<img src="/postimg/2017/03/18-b.png" style="max-height:700px;">

```js
  components: {
    OtherComponent
  }
```

結局のところ、これをキチンとやればOKなのでした。おわり。
