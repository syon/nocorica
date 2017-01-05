---
layout: post
title: "rbenv による Ruby のインストール失敗と解決"
description: "rbenv による Ruby のインストール失敗と解決"
imagefeature:
featured: true
message: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [Trouble shooting]
tags:
  - Ruby
---

![rbenv failed](/postimg/2017/06/01.png)

```bash
$ rbenv install 2.3.3
Downloading ruby-2.3.3.tar.bz2...
-> https://cache.ruby-lang.org/pub/ruby/2.3/ruby-2.3.3.tar.bz2
Installing ruby-2.3.3...

BUILD FAILED (OS X 10.12.2 using ruby-build 20160913)

Inspect or clean up the working tree at /var/folders/80/pmy3nw1d0x91qxkdc8h4n6wm0000gn/T/ruby-build.20170106021536.40179
Results logged to /var/folders/80/pmy3nw1d0x91qxkdc8h4n6wm0000gn/T/ruby-build.20170106021536.40179.log

Last 10 log lines:
checking host system type... x86_64-apple-darwin16.3.0
checking target system type... x86_64-apple-darwin16.3.0
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... configure: error: in `/var/folders/80/pmy3nw1d0x91qxkdc8h4n6wm0000gn/T/ruby-build.20170106021536.40179/ruby-2.3.3':
configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details
make: *** No targets specified and no makefile found.  Stop.
```

## 調査

- [Xcode Command Line Tools · macOS Sierra · Install](http://railsapps.github.io/xcode-command-line-tools.html)

```bash
$ xcode-select -p
/Applications/Xcode.app/Contents/Developer

$ gcc
clang: error: no input files

$ xcode-select --install
xcode-select: error: command line tools are already installed, use "Software Update" to install updates
```
