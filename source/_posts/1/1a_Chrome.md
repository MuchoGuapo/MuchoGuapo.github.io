---
title: '1a) Chromeのインストール'
date: 2020-05-16 17:30:00
tags:
- ブラウザ
- Chrome
categories:
- '1 LinuxとNodejsでプログラミング'
- 'a) Linuxでの環境作成'
excerpt: 'プログラミングエディタAtomを、Linux Debian10にインストールしました。インストールに必要な手順を解説するとともに、Chromeインストール後のapt updateの警告の回避方法について調べました。'
cover_image : chrome.png
pid: browser_chrome
---

## ブラウザ - Google Chrome
### はじめに
![Chrome](https://burturki.sirv.com/diy/chrome.png?w=300)

Chromeは、Googleが開発したWebブラウザです。

> [Chrome公式ページ（日本語）](https://www.google.com/intl/ja_jp/chrome/)

Windows, Mac, Linuxのプラットフォーム上で使用でき、すべてのデバイスで、同一の操作感と個人情報の同期を取ることができます。
セキュリティも十分確保され、また使用用途によってプラグインツールを使うことができるなど使い勝手の良いブラウザとなっています。

> [Google Linux Software Repositories](https://www.google.com/linuxrepositories/)

ChromeをコマンドラインでLinux Debian10にインストールしました。
> [参考ページ](https://linuxize.com/post/how-to-install-google-chrome-web-browser-on-debian-10/)

### Chromeのインストール
LinuxでのChromeのインストールは、次の手順で行います。

```
1. ソフトウエア配布元から認証キーを取得
2. リポジトリ更新
3. リポジトリ情報によりソフトウエアをインストール
```

`
debインストール : wget, apt install
aptインストール : wget, apt-key, sh, apt-get update, apt-get install
`

## インストールに必要なコマンド

apt、apt-key、sh、wget

## インストール手順

インストールは、su権限により、下記の手順を実行します。

1. wgetのインストール
2. インストールパッケージのダウンロード
3. Chromeのインストール

## インストール方法（インストールパッケージによる）

### 1. wgetのインストール（ファイルダウンロード用コマンド）

```bash
# Using Debian, as root
sudo apt-get install wget
```

### 2. インストールパッケージをダウンロード

```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

### 3. Chromeのインストール

```bash
# Using Debian, as root
sudo apt install ./google-chrome-stable_current_amd64.deb
```

## インストール方法（認証キーによる）

1. wgetのインストール
2. 認証キーを取得
3. 認証キーをリポジトリに追加
4. apt-transport-httpsのインストール
5. リポジトリを更新
6. Chromeのインストール

### 1. wgetのインストール

（上記参照）

### 2. Googleの認証キーを取得

```bash
# Using Debian, as root
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```

### 3. 認証キーをローカルOSのリポジトリに追加

```bash
# Using Debian, as root
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
```

### 4. OSのリポジトリを更新

```bash
# Using Debian, as root
sudo apt-get update
```

### 5. Chromeをインストール

```bash
# Using Debian, as root
sudo apt-get install google-chrome-stable
```

## Chromeインストール後に発生する警告メッセージを回避する

Chromeインストール後にapt updateコマンドを実行すると、以下のような警告メッセージが発生するようになりました。

```
W: Target Packages (main/binary-amd64/Packages) is configured 
multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:
...
```

対応方法を調べたところ、次のページを見つけました。

> https://askubuntu.com/questions/766354/how-to-fix-update-problem-on-ubuntu-16-04

Eliah KaganさんとAveryFreemanさんによれば、/etc/apt/sources.list.d/google.list内の以下を行をコメントアウトするように書かれていました。

```bash
cd /etc/apt/sources.list.d

# Using Debian, as root
nano google.list
```

google.listで下記のラインをコメントアウトします。

```nano: google.list
# deb http://dl.google.com/linux/chrome/deb/ stable main
```

コメントアウト後にapt updateを再度実行すると、上記の警告メッセージが出ないようになりました。

## まとめ

ブラウザChromeは、Windows, Mac, Linuxのいずれのプラットフォームでも使用でき、モバイルChromeともリンクできるとても便利なブラウザです。

Debian10にデフォルトでインストールされているブラウザFirefoxとともに、使用用途によって使い分けることができます。
