---
layout: post
title: "Windowsの環境変数Pathを改行して表示するRubyワンライナー"
imagefeature: 
featured: true
description: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: Engineering
tags:
  - Ruby
  - Windows
---
<blockquote><code>echo %path% | ruby -F; -ane 'puts $F'</code></blockquote>

<h4>解説</h4>
<ol>
	<li>echo %path%で出力される内容を、rubyコマンドの引数として渡し、-nオプションによって行ごとに処理をループしている。</li>
	<li>echo %path%の結果は;区切りの1行文字列のため、ループは1回となる。</li>
	<li>Kernel.#gets により組込変数$_に格納されループが開始する。</li>
	<li>次に、-aオプションによってループの先頭で自動的に$F = $_.splitが実行される。</li>
	<li>splitの区切り文字は空白文字(\s)のようだが、オプション-F;で;を区切り文字に指定している。</li>
	<li>最後に結果の格納された$Fをputsで出力している。</li>
</ol>

c.f. <a href="http://d.hatena.ne.jp/maeharin/20130113/ruby_oneliner">Rubyワンライナー入門 - maeharinの日記</a>
