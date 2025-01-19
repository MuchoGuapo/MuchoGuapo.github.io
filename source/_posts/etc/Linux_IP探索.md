---
title: 'ネットワーク上の機器のIPを探し出す'
date: 2020-05-26 17:30:00
tags:
- ネットワーク
- 機器探索
categories:
- 'etc Linuxプログラミング実践'
- 'c) Linuxの使えるコマンド'
excerpt: 'コマンドfpingでネットワーク上の機器のIPを探し出しました。'
cover_image : images/fping.jpg
pid: command_fping
---

## fping - ネットワーク上の使用IP探索
![linux](https://burturki.sirv.com/diy/linux.png?w=300)

ネットワーク上で各機器が使用しているIPを探索するには、fpingコマンドを使います。

## 実行結果

```bash
fping -g 192.168.1.0/24 -a -q
```

```result
192.168.1.1
192.168.1.54
192.168.1.197
192.168.1.228
```
