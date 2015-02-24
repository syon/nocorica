---
layout: post
title: "チェックボックスをすべて選択するJavaScriptとブックマークレット"
imagefeature: 
featured: true
description: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: Engineering
tags:
  - JavaScript
  - jQuery
---
<style>
form[name="monthlist"] {
  background: #f8f8f8;
  padding: 10px 20px;
  box-shadow: 0 0 3px #bbb;
}
form[name="monthlist"]>li {
  list-style: none;
}
</style>
<h4>表示</h4>
<form name="monthlist">
  <li><input type="checkbox" name="january">   January</li>
  <li><input type="checkbox" name="february">  February</li>
  <li><input type="checkbox" name="march">     March</li>
  <li><input type="checkbox" name="april">     April</li>
  <li><input type="checkbox" name="may">       May</li>
  <li><input type="checkbox" name="june">      June</li>
  <li><input type="checkbox" name="july">      July</li>
  <li><input type="checkbox" name="august">    August</li>
  <li><input type="checkbox" name="september"> September</li>
  <li><input type="checkbox" name="october">   October</li>
  <li><input type="checkbox" name="november">  November</li>
  <li><input type="checkbox" name="december">  December</li>
</form>
<h4>HTMLソース</h4>
<pre class="lang:default decode:true " >&lt;form name="monthlist"&gt;
  &lt;li&gt;&lt;input type="checkbox" name="january"&gt;   January
  &lt;li&gt;&lt;input type="checkbox" name="february"&gt;  February
  &lt;li&gt;&lt;input type="checkbox" name="march"&gt;     March
  &lt;li&gt;&lt;input type="checkbox" name="april"&gt;     April
  &lt;li&gt;&lt;input type="checkbox" name="may"&gt;       May
  &lt;li&gt;&lt;input type="checkbox" name="june"&gt;      June
  &lt;li&gt;&lt;input type="checkbox" name="july"&gt;      July
  &lt;li&gt;&lt;input type="checkbox" name="august"&gt;    August
  &lt;li&gt;&lt;input type="checkbox" name="september"&gt; September
  &lt;li&gt;&lt;input type="checkbox" name="october"&gt;   October
  &lt;li&gt;&lt;input type="checkbox" name="november"&gt;  November
  &lt;li&gt;&lt;input type="checkbox" name="december"&gt;  December
&lt;/form&gt;</pre> 
 
<h4>ページに存在するすべてのチェックボックスをONにする（jQueryなし）</h4>
<pre class="lang:default decode:true " >var elems=document.getElementsByTagName('input');
for(i=0;i&lt;elems.length;i++){if(elems[i].type=='checkbox'){elems[i].checked=true;}}
</pre>
<style>
#checkall {
  display: inline-block;
  background-image: linear-gradient(to bottom,#fefefe,#f4f4f4);
  border: 1px solid #ccc;
  text-shadow: 0 1px 0 #fff;
  text-decoration: underline;
  border-radius: 3px;
  padding: 3px 10px;
}
</style>
上記のブックマークレット：<a id="checkall" href="javascript:(function(){var%20elems=document.getElementsByTagName('input');for(i=0;i%3Celems.length;i++){if(elems[i].type=='checkbox'){elems[i].checked=true;}}})();">すべて選択</a>

<h4>jQueryを使ってページに存在するすべてのチェックボックスをONにする</h4>
<pre class="lang:default decode:true " >$(':checkbox').attr("checked", true);</pre> 
