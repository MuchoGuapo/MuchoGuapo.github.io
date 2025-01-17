---
title: '1d) Hexoのインストール'
date: 2020-05-13 17:30:00
tags:
- Hexo初心者
- インストール
categories:
- '1 LinuxとNodejsでプログラミング'
- 'b) Node.jsとHexoのインストール'
excerpt: 'Hexoインストールと動作確認を行う。'
cover_image : hexo.png
pid: hexo-setup-installing
---

## Hexoのインストール
Hexoのインストール方法をまとめました
![hexo](https://burturki.sirv.com/diy/hexo.png?w=300)

## 前提条件
Linux Debian/Ubuntu系、デスクトップPCへインストールする。
※注　RaspbianOSなどについてはインストール上の制限があり、別途記述する。

## インストール手順

* 1. Node.js
* 2. npm
* 3. git
* 4. hexo-cli

### インストールに必要なコマンド

ソフト管理 apt
パッケージ管理 node
バージョン管理 npm
ソースコード管理 git
Hexoクライアント hexo-cli

コマンドがインストールされているかチェックする方法は、下記の通り。

```
node -v
npm -v
git version
hexo-cli -v
```

バージョン確認できないものはインストールされていないので、インストールを行う。

### 1. Node.jsインストール

```bash
# Debian 10, as root
apt install nodejs 
```

### 2. npmインストール

```bash
# Debian 10, as root
apt install npm
```

### 3. gitインストール

```bash
# Debian 10, as root
apt install git
```

### 4. hexo-cliインストール

```bash
# Debian 10, as root
npm install -g hexo-cli
```

## 立ち上げ

Hexoのシンボリックリンクは/usr/local/binにあり、PC上のどのディレクトリからもbashで実行できる。

### バージョン確認

```bash
hexo version
```

### Hexoの初期処理

hexo init <dir>コマンドで初期化し、配下の<dir>に移動

```bash
hexo init <Directory>
```

npm installが合わせて実行される。追加プラグインはpackage.jsonに追記する。

### Hexoサーバーの立ち上げ

```bash
cd <Directory>
hexo server
```

### ブラウザで確認

ブラウザーで確認

```
http://localhost:4000
```

## まとめ
見た目のデザインは、デフォルトテーマlandscapeとなっている。
他のデザインに変更する場合、ディレクトリthemes配下に好みのテーマを**git clone**する。
