---
layout: post
title: "RubyでMacのスクリーンショット画像を解析"
imagefeature: 
featured: true
description: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: Engineering
tags:
  - Ruby
---
<!--more-->
<h3>"screencapture"コマンドからのアプローチ</h3>
<ul>
	<li><a href="http://tech.hisasann.com/ruby/81/">Macのスクリーンショットを動画にするRubyコード | ひささん日記</a></li>
	<li><a href="http://d.hatena.ne.jp/zariganitosh/20121124/one_liner_screenshot">ワンライナーでそのまま使えるスクリーンショットが撮れる！ - ザリガニが見ていた...。</a></li>
	<li><a href="http://d.hatena.ne.jp/nishiohirokazu/20120731/1343745529">Macのスクリーンショットで1日の作業を記録して動画で振り返り - 西尾泰和のはてなダイアリー</a></li>
</ul>
 
<h4>"screencapture"コマンド</h4>
<pre class="lang:default highlight:0 decode:true " title="screencapture" >
usage: screencapture [-icMPmwsWxSCUtoa] [files]
  -c         force screen capture to go to the clipboard
  -C         capture the cursor as well as the screen. only in non-interactive modes
  -d         display errors to the user graphically
  -i         capture screen interactively, by selection or window
               control key - causes screen shot to go to clipboard
               space key   - toggle between mouse selection and
                             window selection modes
               escape key  - cancels interactive screen shot
  -m         only capture the main monitor, undefined if -i is set
  -M         screen capture output will go to a new Mail message
  -o         in window capture mode, do not capture the shadow of the window
  -P         screen capture output will open in Preview
  -s         only allow mouse selection mode
  -S         in window capture mode, capture the screen not the window
  -t&lt;format&gt; image format to create, default is png (other options include pdf, jpg, tiff and other formats)
  -T&lt;seconds&gt; Take the picture after a delay of &lt;seconds&gt;, default is 5
  -w         only allow window selection mode
  -W         start interaction in window selection mode
  -x         do not play sounds
  -a         do not include windows attached to selected windows
  -r         do not add dpi meta data to image
  -l&lt;windowid&gt; capture this windowsid
  -R&lt;x,y,w,h&gt; capture screen rect
  files   where to save the screen capture, 1 file per screen
</pre> 
<p>
"-R&lt;x,y,w,h&gt;"の書き方がわからない。。
</p>

<h3>CGWindow APIからのアプローチ</h3>
<ul>
	<li><a href="http://redartisan.com/2008/1/12/rubycocoa-screen-capture">Desktop Screen Capture via Ruby Cocoa! - Red Artisan</a></li>
	<li><a href="https://developer.apple.com/library/mac/#documentation/Carbon/reference/CGWindow_Reference/Reference/Functions.html">Quartz Window Services Reference: Functions #CGWindowListCreateImage</a></li>
</ul>
