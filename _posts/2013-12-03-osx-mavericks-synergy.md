---
layout: post
title: "OSX Mavericks で Synergy を動かす手順"
imagefeature: 
featured: true
description: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [Trouble shooting]
tags:
  - Mac
  - Software
---
<strong>2014.02.18 修正版がリリースされました。</strong>
<ul><li><a href="http://synergy-foss.org/blog/synergy-1-4-16-released/">Synergy Blog - Synergy 1.4.16 released</a></li></ul>
<blockquote>Bug #3642 – Failed to start server on Mac OS X 10.9 Mavericks, assistive devices problem</blockquote>

ダウンロード: <a href="http://synergy-foss.org/download/?list">http://synergy-foss.org/download/?list</a>

以下、旧版向けに手順を残しておきます。

<hr style="margin:4em 0;">

<img src="/postimg/2013/12/pref.png" alt="pref" width="668" height="200" class="alignnone size-full wp-image-349" />
システム環境設定を開き、「セキュリティとプライバシー」を選択します。

<div style="height:30px;"></div>

<img src="/postimg/2013/12/security.png" alt="security" width="668" height="522" class="alignnone size-full wp-image-350" />
プライバシータブの左にあるリストからアクセシビリティを選択。
ターミナルがあればチェック。もしなければ、アプリケーションフォルダにあるユーティリティに入っているターミナルアイコンをドラッグ＆ドロップします。

<div style="height:30px;"></div>

ターミナルで次のコマンドを実行します。
<blockquote>
$ /Applications/Synergy.app/Contents/MacOS/Synergy & exit
</blockquote>

via: <a href="http://synergy-foss.org/blog/mac-os-x-10-9-mavericks-support/" target="_blank">Synergy Blog - Mac OS X 10.9 Mavericks support</a>
