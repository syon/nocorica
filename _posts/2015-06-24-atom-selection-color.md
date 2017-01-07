---
layout: post
title: "Atomで選択範囲の背景色を見やすく変更する"
description: "Atomで選択範囲の背景色を見やすく変更する"
imagefeature:
featured: true
message: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [How to]
tags:
  - Atom
---

### できあがりイメージ
![](/postimg/2015/06/24-1.png)

### デフォルト状態はこんな感じ

![](/postimg/2015/06/24-2.png)

ちょっと見にくいですね。


## 手順

### スタイルシートを開く ( ~/.atom/styles.less )

![](/postimg/2015/06/24-3.png)

これに以下を追記します。

```sass
atom-text-editor::shadow {
  .gutter .cursor-line {
    background-color: fade(cyan, 14%);
  }
  .highlights {
    .selection .region {
      background: fade(cyan, 30%);
    }
    .find-result .region {
      border: 1px solid fade(cyan, 80%);
    }
  }
}
```

保存するとその瞬間に以下の画像のように反映されます。

![](/postimg/2015/06/24-1.png)

変更されるのは３箇所です。

- 選択中の行番号
- テキストの選択範囲
- 検索にヒットした箇所

テキストの選択範囲については、気持ち濃いめ(30%)にしています。これは検索と`command + D`（次の一致も選択）をよく使うので、そのときにわかりやすくする意図があります。お好みに応じて調整してみてください。


### ちなみに

`cyan`の箇所を`yellow`にするとこんな感じです。

![](/postimg/2015/06/24-4.png)
