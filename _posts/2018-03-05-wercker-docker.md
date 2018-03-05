---
layout: post
title: "WerckerでDockerイメージを使う時の注意"
description: "WerckerでDockerイメージを使う時の注意"
categories: [How to]
tags:
  - Docker
---

Wercker のビルドやデプロイにて Docker のイメージを使うことが可能です。
しかし、おもむろにイメージを指定して実行したところ以下のようなエラーに遭遇しました。

![](/postimg/2018/03/05-a.png)

```bash
⟩ wercker dev
--> No Docker host specified, checking: /var/run/docker.sock
--> Executing pipeline
--> Running step: setup environment
Pulling from squidfunk/mkdocs-material: latest
Digest: sha256:ca2f069a55d05a57658eb531db39cbfa4af3302a6b5b07b8886a8bc847970f0b
Status: Image is up to date for squidfunk/mkdocs-material:latest
--> Copying source to container
ERROR --> Step failed: setup environment 4.23s
Guest command failed with exit code -1: mkdir -p "/pipeline/output"
ERROR Guest command failed with exit code -1: mkdir -p "/pipeline/output"
WARNING Box container has already stopped.
FATAL Exiting.
```

イメージ利用の制約事項として Dockerfile 内で `ENTRYPOINT`
を定義してはならない、という前提があると推測されます。

```dockerfile
# [抜粋] https://github.com/squidfunk/mkdocs-material/blob/master/Dockerfile
ENTRYPOINT ["mkdocs"]
CMD ["serve", "--dev-addr=0.0.0.0:8000"]
```

それは `wercker.yml` の `steps` を書くときのことを思い起こせば気づくのですが、
以下の例のように `mkdocs build` といったコマンドたちをシェルで実行する必要があるからですね。

```bash
# [抜粋] wercker.yml
build:
  steps:
    - script:
      code: |
        mkdocs build
```

ではどうすれば良いかというと、この Docker イメージをラップするイメージを作り、
そちらを Wercker から呼ぶことで回避できました。

- [syon/mkdocs\-material \- Docker Hub](https://hub.docker.com/r/syon/mkdocs-material/)
  - [Dockerfile](https://github.com/syon/wiki/blob/master/Dockerfile)

なにか他にスマートなやり方があればいいのですが、わかりませんでした。
なのでひとまずはこれで。
