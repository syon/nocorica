---
layout: post
title: "Windows Ruby 1.9.3 で opencv-0.0.7.gem の install 失敗"
imagefeature: 
featured: true
description: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [Trouble shooting]
tags:
  - Ruby
  - Windows
---
未解決。もう！なんなん！(`ε´）
<!--more-->
<h4>gem install opencv</h4>
<pre class="lang:default highlight:0 decode:true " title="cmd.exe" >C:\&gt;gem install opencv
Fetching: opencv-0.0.7.gem (100%)
Building native extensions.  This could take a while...
ERROR:  Error installing opencv:
        ERROR: Failed to build gem native extension.

    C:/Ruby193/bin/ruby.exe extconf.rb
&gt;&gt; check require libraries...
checking for main() in -lcxcore... no
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
        --with-opt-dir
        --without-opt-dir
        --with-opt-include
        --without-opt-include=${opt-dir}/include
        --with-opt-lib
        --without-opt-lib=${opt-dir}/lib
        --with-make-prog
        --without-make-prog
        --srcdir=.
        --curdir
        --ruby=C:/Ruby193/bin/ruby
        --with-opencv-dir
        --without-opencv-dir
        --with-opencv-include
        --without-opencv-include=${opencv-dir}/include
        --with-opencv-lib
        --without-opencv-lib=${opencv-dir}/lib
        --with-ffcall-dir
        --without-ffcall-dir
        --with-ffcall-include
        --without-ffcall-include=${ffcall-dir}/include
        --with-ffcall-lib
        --without-ffcall-lib=${ffcall-dir}/lib
        --with-cxcorelib
        --without-cxcorelib
extconf.rb:32:in `block in &lt;main&gt;': libcxcore not found. (RuntimeError)
        from extconf.rb:31:in `each'
        from extconf.rb:31:in `&lt;main&gt;'


Gem files will remain installed in C:/Ruby193/lib/ruby/gems/1.9.1/gems/opencv-0.0.7 for inspection.
Results logged to C:/Ruby193/lib/ruby/gems/1.9.1/gems/opencv-0.0.7/ext/gem_make.out
</pre> 

 
<h4>gem_make.out</h4>
<pre class="lang:default highlight:0 decode:true " title="gem_make.out" >C:/Ruby193/bin/ruby.exe extconf.rb
&gt;&gt; check require libraries...
checking for main() in -lcxcore... no
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
  --with-opt-dir
  --without-opt-dir
  --with-opt-include
  --without-opt-include=${opt-dir}/include
  --with-opt-lib
  --without-opt-lib=${opt-dir}/lib
  --with-make-prog
  --without-make-prog
  --srcdir=.
  --curdir
  --ruby=C:/Ruby193/bin/ruby
  --with-opencv-dir
  --without-opencv-dir
  --with-opencv-include
  --without-opencv-include=${opencv-dir}/include
  --with-opencv-lib
  --without-opencv-lib=${opencv-dir}/lib
  --with-ffcall-dir
  --without-ffcall-dir
  --with-ffcall-include
  --without-ffcall-include=${ffcall-dir}/include
  --with-ffcall-lib
  --without-ffcall-lib=${ffcall-dir}/lib
  --with-cxcorelib
  --without-cxcorelib
extconf.rb:32:in `block in &lt;main&gt;': libcxcore not found. (RuntimeError)
  from extconf.rb:31:in `each'
  from extconf.rb:31:in `&lt;main&gt;'
</pre> 
