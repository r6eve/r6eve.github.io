---
title: 日本語タイトル
---

**Hello world**, this is my first Jekyll blog post.

I hope you like it!

あのイーハトーヴォのすきとおった風、夏でも底に冷たさをもつ青いそら、うつくしい森で飾られたモリーオ市、郊外のぎらぎらひかる草の波。

またそのなかでいっしょになったたくさんのひとたち、ファゼーロとロザーロ、羊飼のミーロや、顔の赤いこどもたち、地主のテーモ、山猫博士のボーガント・デストゥパーゴなど、いまこの暗い巨きな石の建物のなかで考えていると、みんなむかし風のなつかしい青い幻燈のように思われます。では、わたくしはいつかの小さなみだしをつけながら、しずかにあの年のイーハトーヴォの五月から十月までを書きつけましょう

- foo
- bar
  - qux

https://r6eve.github.io

[foobar](https://r6eve.github.io)

Source code are highlighted:

```perl
#!/usr/bin/perl

sub print_hello {
    print "Hello, Jekyll!\n";
}

print_hello;
```

foobar

```bash
cd ${pkgname}
makepkg -s
pacman -U ${pkgname}-${pkgver}-${pkgrel}-${arch}.pkg.tar.zst
```

```ocaml
module List = struct
  include List

  let is_empty = function
    | [] -> true
    | _ -> false

  let last l =
    let rec doit = function
      | [] -> failwith "last"
      | [a] -> a
      | _ :: l -> doit l
    in
    doit l
end
```

| foo | baz | qux |
| --- | --- | --- |
| a   | b   | c   |
| x   | y   | z   |

| ![ocaml](/img/ocaml.png "キャプションテスト") |
| --------------------------------------------- |
| 図1 : OCamlドキュメントの惨状                 |

foo bar qux
