---
layout: post
title: "FlashDevelopでビルドエラー >> Vectors are not supported in FP9."
description: "FlashDevelopでビルドエラー >> Vectors are not supported in FP9."
imagefeature:
featured: true
message: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [Trouble shooting]
tags:
  - Flash
---

<blockquote>
private var _allowDomainParameters:Vector.&lt;Array&gt;;
^
Error: Type was not found or was not a compile-time constant: Array.
</blockquote>


Vectors are not supported in FlashPlayer 9.

(Menu) Project > Properties... > Outputタブ
もっと上のバージョンを選択する。
