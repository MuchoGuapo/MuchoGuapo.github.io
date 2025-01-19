---
title: 'bashでよく使用するコマンドを登録'
date: 2020-06-10 17:30:00
tags:
- bash
- コマンド
- エイリアス
categories:
- 'etc Linuxプログラミング実践'
- 'c) Linuxの使えるコマンド'
excerpt: 'bash上でよく使用するコマンドをエイリアスで短縮登録します。'
cover_image : alias.jpg
pid: alias_for_bash
---

## bash - コンソール画面
![linux](https://burturki.sirv.com/diy/linux.png?w=300)
bashは、Linux上でコマンド実行ができるコンソールと呼ばれるツールです。
alias.jpg

## alias - 短縮コマンド設定
毎回同じコマンドを打ち込む場合、コマンド登録しておくと便利です。
設定したエイリアスは、シェルスクリプトの起動時に読み込まれます。

### 使っているシェルの種類の調べ方
```bash
ps -p $$
```

Debian10のシェルはbashです。bashのコマンド登録は、設定ファイル'.bashrc'上で行います。
bashで頻繁に同じコマンドを打ち込む場合には、あらかじめ短縮コマンドとしてエイリアス設定しておくと、作業が軽減されます。

## 使用方法

### 設定

bashのエイリアス設定は、設定ファイル'.bashrc'の最終行に、aliasとして追加登録します。

```設定例
alias apin = 'apt install'
```

### '.bashrc'はどこにあるか？

ホームディレクトリに存在します。'.'付きの隠しファイルです。

### エイリアスの追加方法

'.bashrc'の最終行に、エイリアスを追加します。

```
nano: '.bashrc'
alias cdg='cd ~/git/blog'
```

### 反映
エイリアスを反映させるためには、シェルを再起動します。シェルコンソールを一旦閉じて、再度立ち上げると、新しく作ったエイリアスが使えるようになります。

## シンボリックリンク
Linuxでよく使うツールはあらかじめシンボリックリンクを登録しておくと、グローバルに使用できます。bashで/usr/local以外のシンボリックリンクを登録する方法について調べてみました。

### bashのシンボリックリンクを設定する
Debianにおける.bashrcの役割とシンボリックリンクのPATHの通し方

> [](https://www.mk-mode.com/blog/2014/07/20/linux-bash-setting-files-debian/)

> [](https://qiita.com/thermes/items/926b478ff6e3758ecfea)

> [](https://techracho.bpsinc.jp/hachi8833/2019_06_06/66396)

shファイルの実行 - Linux

> [](https://linuxfan.info/post-1486)

/usr/localにシンボリックリンク、パスを通す

> [Linux入門 ~「パスを通す」とは~](https://qiita.com/Naggi-Goishi/items/2c49ea50602ea80bf015)

## まとめ
頻繁につかうコマンドは.bashrcにまとめて登録しておくと、コマンド打ち込み時の作業負荷が大幅に軽減できます。