---
layout: post
title: "Vue.js - 非同期コンポーネントとvue-router組合せサンプル"
description: "Vue.jsでRecursive Componentsエラー"
categories: [How to]
tags:
  - JavaScript
---

## やりたかったこと

Markdown で書いた記事をたくさん用意しておいて、
それを記事表示用の1つのコンポーネントを使って表示したい。
どの記事の内容を表示するかは vue-router の `:id` で振り分ける。
そうすることで記事の追加・削除に自動的に対応できるため。

- [非同期コンポーネント — Vue\.js](https://jp.vuejs.org/v2/guide/components.html#非同期コンポーネント)

公式に案内されている「非同期コンポーネント」という機能を使って実現できないだろうか。


### 問題点

どの記事なのか、にあたる `$route.params.id` が、
記事ファイル名の解決を行う際に参照できない。
このブロックには vue-router 関連のオブジェクトが引き渡されないから？


## 実現例

vue-cli を使った、単一ファイルコンポーネントの方式で例を示す。

Router の記述は普通。

```js
// :
Vue.use(Router);

export default new Router({
  routes: [
    // :
    {
      path: '/article/:id',
      name: 'Article',
      component: Article,
    },
  ],
});
```

苦肉の策として URL (`window.location.href`) から直接引っ張り出したものを使うことができた。

```jade
<template lang="pug">
.container
  h2 {{ $route.params.id }}
  async-article
</template>

<script>
export default {
  components: {
    'async-article': () => {
      // console.log($route);
      // => ReferenceError: $route is not defined
      const filename = window.location.href.match(/[^/]+$/)[0];
      return import(`../articles/${filename}.md`);
    },
  },
};
</script>

<style scoped>
</style>
```

なんとか動いた。Vue超便利。

おわり。
