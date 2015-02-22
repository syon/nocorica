---
layout: post
title: "メモ: GitHub Pages & Jekyll"
imagefeature: 
featured: true
description: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: Engineering
tags:
  - Software
  - Jekyll
---

<ul>
  <li><a href="https://help.github.com/categories/20/articles" target="_blank">GitHub Help</a></li>
  <li><a href="https://help.github.com/articles/creating-pages-with-the-automatic-generator" target="_blank">Creating Pages with the automatic generator · GitHub Help</a></li>
</ul>

<blockquote>
<ol>
  <li>https://github.com/new</li>
  <li>Repository name: [username].github.io</li>
  <li>GitHub Pages - Automatic Page Generatorボタン</li>
</ol>
</blockquote>

<ul>
  <li><a href="http://web.sfc.keio.ac.jp/~t10078si/wpx/?p=862" target="_blank">jekyll+github pagesでブログを作る « fragments</a></li>
  <li><a href="http://blog.makitasako.com/entry/2013-04-13-makingmyblog.html" target="_blank">blog.makitasako.com - ブログをGitHubに移行しました。</a></li>
  <li><a href="http://blog.eiel.info/blog/2013/02/17/github-pages/" target="_blank">Github Pages について整理しておきます - そんなこと覚えてない</a></li>
  <li><a href="http://melborne.github.io/2012/05/13/first-step-of-jekyll/" target="_blank">30分のチュートリアルでJekyllを理解する</a></li>
  <li><a href="http://krakenbeal.blogspot.jp/2012/05/ruby-jekyll-jekyll-bootstrap.html" target="_blank">ruby と jekyll と jekyll-bootstrap で静的サイトを作る - KRAKENBEAL RECORDS</a></li>
  <li><a href="http://melborne.github.io/2013/05/20/now-the-time-to-start-jekyll/" target="_blank">Jekyllいつやるの？ジキやルの？今でしょ！</a></li>
</ul>

### サーバの開始

```bash
$ jekyll serve
```

起動時に下記のようなエラーが出たら記述のとおりに対処。
control+Z で終了が原因。control+C を使う。

```bash
WARN  TCPServer Error: Address already in use - bind(2)
error: Address already in use - bind(2). Use --trace to view backtrace

$ lsof -wni tcp:4000

COMMAND  PID USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
ruby    2997 Syon    7u  IPv4 0x8d68181a447e1d8f      0t0  TCP *:terabase (LISTEN)

$ kill -9 2997
$ jekyll serve
```

<ul>
  <li><a href="http://stackoverflow.com/questions/10261477/tcpserver-error-address-already-in-use-bind2">ruby - TCPServer Error: Address already in use - bind(2) - Stack Overflow</a></li>
</ul>
