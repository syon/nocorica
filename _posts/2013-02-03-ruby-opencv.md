---
layout: post
title: "Ruby & OpenCVで画像処理"
---
<img src="http://blog.nocorica.jp/wp-content/uploads/2013/02/cv1-e1359880824316.png" alt="" width="650" height="391" class="alignnone size-full wp-image-93" /><!--more-->
<h4>導入</h4>
<ul>
<li><a href="http://ser1zw.hatenablog.com/entry/2013/01/29/235320">ruby-opencvをようやくRubyGems.orgに登録しました - ser1zw's blog</a></li>
<li><a href="http://tools4hack.santalab.me/howto-mountainlion-install-homebrew.html">[Mac] Mountain Lionへパッケージ管理「Homebrew」をインストールする手順のメモ | Tools 4 Hack</a></li>
</ul>

<h4>画像を表示する</h4>
<ul>
<li><a href="https://github.com/ruby-opencv/ruby-opencv">ruby-opencv/ruby-opencv · GitHub</a></li>
</ul>
<pre class="lang:ruby decode:true " title="sample.rb" >
require 'opencv'
include OpenCV

if ARGV.size == 0
  puts "Usage: ruby #{__FILE__} ImageToLoadAndDisplay"
  exit
end

image = nil
begin
  image = CvMat.load(ARGV[0], CV_LOAD_IMAGE_COLOR) # Read the file.
rescue
  puts 'Could not open or find the image.'
  exit
end

window = GUI::Window.new('Display window') # Create a window for display.
window.show(image) # Show our image inside it.
GUI::wait_key # Wait for a keystroke in the window.
</pre>

<p>
$ ruby sample.rb Lenna.jpeg ってやると画像が表示される。
画像のウィンドウで何かキーを押すと処理終了。
<br/>
</p>

<h4>テンプレートマッチング</h4>
<li><ul>
<a href="http://qiita.com/items/9f277d7fc0479c9f4ca4">ruby-opencv を使ってテンプレートマッチングしてみた #Ruby #OpenCV - Qiita</a>
</li></ul>

<pre class="lang:ruby decode:true " title="matching.rb" >
#!/usr/bin/env ruby

require 'opencv'
include OpenCV

image = OpenCV::IplImage.load("Lenna.jpeg")
template = OpenCV::IplImage.load("template.jpg")

result = image.match_template(template)
min_score, max_score, min_point, max_point = result.min_max_loc

from = min_point
to = OpenCV::CvPoint.new(from.x + template.width, from.y + template.height)
image.rectangle!(from, to, :color =&gt; OpenCV::CvColor::Black, :thickness =&gt; 1)

window = OpenCV::GUI::Window.new("canvas")
window.show image

GUI::wait_key

image.save_image("output.png")
</pre> 

<p>
template.jpgにマッチする範囲の境界線を黒で描く。
画像のウィンドウで何かキーを押すと"output.png"を出力して処理終了。
</p>
