---
title: 'brewを理解する'
date: 2020-05-16 17:30:00
tags:
- Linux
- Debian
- パッケージ管理
- 'package manager'
- brew
categories:
- '1 LinuxとNodejsでプログラミング'
- 'b) パッケージ管理を学ぶ'
excerpt: 'Linuxのパッケージ管理brewを説明します。インストール方法、リポジトリの管理、コマンド実行時の警告・エラー回避方法について調べました。'
cover_image : images/apt.jpg
pid: package_manager_brew
---

## brew - パッケージ管理
![nodejs](https://burturki.sirv.com/diy/nodejs.png?w=300)

Mac OS用ソフトウエアのパッケージ管理として、Homebrewは発展してきました。

> [Homebrew公式ページ](https://brew.sh/)

Unixと親和性の高いLinuxでもLinuxbrewとして発展しました。

> [Debian10にLinuxbrewをインストールする](https://www.tacoskingdom.com/blog/52)

Go言語の静的サイトジェネレーターHugoをインストールする場合には、brewコマンドが必要となります。

> [Hugo公式ページ インストール手順](https://gohugo.io/getting-started/installing/)

## インストールに必要なコマンド

build-essential, curl, file, git
gcc, GNU C


## <a id="anchor3">インストール手順</a>

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

```
test -d ~/.linuxbrew && eval $(~/.linuxbrew/bin/brew shellenv)
test -d /home/linuxbrew/.linuxbrew && eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)
test -r ~/.bash_profile && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile
echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.profile
```

```
brew install hello
```

プロファイル設定

```
eval $(/home/hamkaz/.linuxbrew/bin/brew shellenv)

exportの２行を追記する

```
sudo nano ~/.bashrc

export PATH="/home/linuxbrew/.linuxbrew/bin:$PATH"
export PATH="/home/linuxbrew/.linuxbrew/share/man:$PATH"
```

バージョン確認

```
hamkaz@debian1-de-kaz:~$ brew --version
```
