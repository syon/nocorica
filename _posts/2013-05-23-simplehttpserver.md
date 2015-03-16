---
layout: post
title: "ローカルでのWebサイト作成に役立つPythonのWebサーバ SimpleHTTPServer / http.server"
description: "ローカルでのWebサイト作成に役立つPythonのWebサーバ SimpleHTTPServer / http.server"
imagefeature:
featured: true
message: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: Engineering
tags:
  - Server
---
<h4>Python 2</h4>
<blockquote><code>$ python -m SimpleHTTPServer 8000</code></blockquote>

<h4>Python 3</h4>
<blockquote><code>$ python -m http.server 8000</code></blockquote>



起動時のディレクトリがDocumentRoot
control + Z で終了

<h4>ポート転送</h4>
<ul><li>
<a href="http://blog.webcreativepark.net/2013/08/06-121744.html" target="_blank">ローカルのWebサイトを確認する方法 - to-R</a>
</li></ul>
<blockquote><code>sudo ipfw add 100 fwd 127.0.0.1,8000 tcp from any to me 80</code></blockquote>

もとに戻すには $ sudo ipfw list で通し番号を確認して $ sudo ipfw delete *****
