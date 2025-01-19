---
title: 'プログラミングエディタ Atom'
date: 2020-05-16 17:30:00
tags:
- プログラミングエディタ
- Atom
categories:
- '1 LinuxとNodejsでプログラミング'
- 'a) ツールをインストールする'
excerpt: 'プログラミングエディタAtomを、Linux Debian10にインストールしました。インストールに必要な手順を解説するとともに、Chrome・npmをインストールすると起動不具合の回避方法についても調べてみました。'
cover_image : images/atom.png
pid: editor_atom
---

## プログラミングエディタ - Atom
![atom](https://burturki.sirv.com/diy/atom.png?w=300)

Atomは、Windows, Mac, Linuxのプラットフォーム上で使用できるプログラミングエディタで、GitHubにより開発されました。

> [Atom公式ページ（英語）](https://atom.io/)

日本語パッケージをクリック一つでインストールできるなど、便利なパッケージがたくさんあり、用途に応じて様々なカスタマイズが可能です。インストール手順について、公式ページのリンクをご紹介します。

> [Atom公式ページ（英語）](https://flight-manual.atom.io/getting-started/sections/installing-atom/)

コマンドラインからインストールしました。


### エディタ - Atom Editor, Visual Studio Code, Typora

**Atom Editor**

`
aptインストール : wget, apt-key, sh, apt-get update, apt-get install
`

## インストールに必要なコマンド

wget、apt-key、sh、apt-get update、apt-get install

## インストール手順

インストール手順はsu権限で、次のように実行します。

1. wgetのインストール
2. 認証キーの取得
3. 認証キーをリポジトリに追加
4. リポジトリを更新
5. Atomのインストール

## インストール方法

### 1. wgetコマンドのインストール

wgetコマンドをDebian10で使用するためには、次のコマンドでインストールします。

```bash
# Using Debian, as root
sudo apt-get install wget
```

### 2. Atomの認証キーをリモートから取得

```bash
# Using Debian, as root
wget -qO - https://packagecloud.io/AtomEditor/atom/gpgkey | sudo apt-key add -
```

### 3. 認証キーをOSのリポジトリに追加

```bash:command
# Using Debian, as root
sudo sh -c 'echo "deb [arch=amd64] https://packagecloud.io/AtomEditor/atom/any/ any main" > /etc/apt/sources.list.d/atom.list'
```

### 3. OSのリポジトリを更新

```bash:command
# Using Debian, as root
sudo apt-get update
```

### 4. Atomをインストール

```bash:command
# Using Debian, as root
sudo apt-get install atom
```

## Chromeやnpmをインストールすると、Atomが起動しなくなる

Atomのインストール後、その他のソフト・ツールをインストールしたところ、Atom自体が起動しなくなりました。対応方法を調べたところ、次のページを見つけました。

> https://github.com/electron/electron/issues/17972

vladimiryさんのコメント（commented on 28 Apr 2019）によれば、「atomのchrome-sandboxのパーミッションを変更すると不具合が改善する」とありました。

具体的には、「Chrome環境下でAtomを実行するためには、chrome-sandboxの所有権限を"root/4755"に変更する必要がある」と書かれています。

そこで下記手順を試したところ、Atomが無事起動するようになりました。

```bash:command
# Using Debian, as root
cd /user/share/atom
chown root chrome-sandbox
chmod 4755 chrome-sandbox
```

一連のQAを読んでみたところ、Chromeインストール後にAtomが立ち上がらなくなる原因は、「Atomのデフォルト設定はセキュリティ-プライバシーにChronium-sandboxを使っているが、Chromeのインストール時、Chronium-sandboxからChrome-sandboxに切り替わらないために脆弱性対策からAtomが起動しない」とありました。

Chrome, npmインストール後に、このような現象が起きるらしいとも記載がありました。

## まとめ

プログラミングエディタAtomは、Windows, Mac, Linuxのいずれのプラットフォームでも使用できるとても便利なエディタです。

特にペイン分割という操作がとても便利です。画面を複数枚のペインに上下左右に分割でき、異なるソースを並べて同時編集することができます。
