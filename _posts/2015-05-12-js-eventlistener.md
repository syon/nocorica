---
layout: post
title: "JavaScript - addEventListener / removeEventListener サンプル"
description: "JavaScript - addEventListener / removeEventListener サンプル"
imagefeature:
featured: true
message: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [How to]
tags:
  - JavaScript
---

## cf.

#### [EventTarget.addEventListener - Web API インターフェイス | MDN](https://developer.mozilla.org/ja/docs/Web/API/EventTarget/addEventListener)

> 複数の同一の EventListener が、同じ EventTarget に同じ引数で登録された場合、重複するインスタンスは反映されません。EventListener が 2 度呼び出されることはなく、重複するインスタンスは反映されないので、removeEventListener で手動で削除する必要はありません。


## Code sample

```js
// 関数を定義
function processEvent() {
  console.log("clicked!");
}

// イベントを割り当てる要素を取得
var el = document.getElementById("Example");

// クリックイベントリスナーを追加
el.addEventListener("click", processEvent, false);

// クリック
el.click();
//=> clicked!

// クリックイベントリスナーを追加
el.addEventListener("click", processEvent, false);

// クリック
el.click();
//=> clicked!

// クリックイベントリスナーを除去
el.removeEventListener("click", processEvent, false);

// クリック
el.click();
//=>
```


## Code sample (NG)

```js
// イベントを割り当てる要素を取得
var el = document.getElementById("Example");

// クリックイベントリスナーを追加
el.addEventListener("click", function(){console.log("clicked.");}, false);

// クリック
el.click();
//=> clicked.

// クリックイベントリスナーを追加
el.addEventListener("click", function(){console.log("clicked.");}, false);

// クリック
el.click();
//=> clicked.
//=> clicked.

// クリックイベントリスナーを除去
el.removeEventListener("click", function(){console.log("clicked.");}, false);

// クリック
el.click();
//=> clicked.
//=> clicked.
```

