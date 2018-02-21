---
layout: post
title: "JavaのSetリストを突き合わせて積集合を得る方法"
description: "JavaのSetリストを突き合わせて積集合を得る方法を、サンプルコードを使って解説します。"
categories: [How to]
tags:
  - Java
---

## 積集合（論理積）を導くには

`Set#retainAll`を使います。

- [Set \(Java Platform SE 7 \)](https://docs.oracle.com/javase/jp/7/api/java/util/Set.html#retainAll(java.util.Collection))

> __`boolean retainAll(Collection<?> c)`__
>
> セット内の要素のうち、指定されたコレクション内にある要素だけを保持します (オプションの操作)。
> つまり、セットから、指定されたコレクション内にない要素をすべて削除します。
> 指定されたコレクションもセットである場合、このオペレーションは、その値が 2 つのセットの共通部分になるように
> このセットを効率的に変更します。
>
> __戻り値:__ 呼び出しの結果としてこのセットが変更された場合は true


## サンプルコード

コードをコピーして、以下のサイトでオンラインで試すことができます。

- [Online Java Compiler](https://www.tutorialspoint.com/compile_java_online.php)

```java
import java.util.*;

public class HelloWorld {

    public static void main(String []args) {

        Set<String> pref = new HashSet<String>();
        pref.add("東京");
        pref.add("神奈川");
        pref.add("大阪");
        pref.add("愛知");
        pref.add("北海道");
        System.out.println("[都道府県] " + String.join(", ", pref));

        Set<String> city = new HashSet<String>();
        city.add("東京");
        city.add("横浜");
        city.add("大阪");
        city.add("名古屋");
        city.add("札幌");
        System.out.println("[主要都市] " + String.join(", ", city));

        // retainAllは元のセットを変更するので注意。この例では別セットを生成
        Set<String> seki = new HashSet<String>(pref);
        seki.retainAll(city);
        System.out.println("[積集合] " + String.join(", ", seki));
    }
}
```

```bash
$ java -Xmx128M -Xms16M HelloWorld
[都道府県] 神奈川, 愛知, 北海道, 東京, 大阪
[主要都市] 名古屋, 札幌, 東京, 大阪, 横浜
[積集合] 東京, 大阪
```
