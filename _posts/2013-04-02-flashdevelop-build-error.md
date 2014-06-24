---
layout: post
title: "FlashDevelopでビルドエラー >> Vectors are not supported in FP9."
---

<blockquote>
private var _allowDomainParameters:Vector.&lt;Array&gt;;
^
Error: Type was not found or was not a compile-time constant: Array.
</blockquote>


Vectors are not supported in FlashPlayer 9.

(Menu) Project > Properties... > Outputタブ
もっと上のバージョンを選択する。
