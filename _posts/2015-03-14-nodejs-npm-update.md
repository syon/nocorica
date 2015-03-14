---
layout: post
title: "Node.js と npm のアップデート"
imagefeature:
featured: true
description: "Its ON, baby"
headline: "Let's Fire up the Engines"
categories: [How to]
tags:
  - Node.js
---

![](/postimg/2015/03/nodejs.png)

## node
- [linux - How can I update Node.js and NPM to the next versions? - Stack Overflow](http://stackoverflow.com/questions/6237295/how-can-i-update-node-js-and-npm-to-the-next-versions)

```bash
$ node -v
$ sudo npm cache clean -f
$ sudo npm install -g n
$ sudo n stable
$ node -v
```

## npm

```bash
$ npm install -g npm
```

`ERR!`とか言われて`npm: command not found`となったら

```bash
$ curl -L https://npmjs.org/install.sh | sudo sh
```

※ 途中で`Password:`と聞かれる

![](/postimg/2015/03/14-shell.png)
