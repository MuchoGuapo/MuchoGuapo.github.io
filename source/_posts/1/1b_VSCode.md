---
title: '1b) Visual Studio Codeのインストール'
date: 2020-07-18 22:30:00
tags:
- プログラミング
- エディタ
- 'VisualStudioCode'
categories:
- '1 LinuxとNodejsでプログラミング'
- 'a) Linuxでの環境作成'
excerpt: 'プログラミングエディタVisual Studio Codeを、Linux Debian10にインストールしました。インストール手順について調べるとともに、使用感についてAtomと比較してみました。'
cover_image : vsc.png
pid: editor_visual-studio-code
---

## プログラミングエディタ - Visual Studio Code
VisualStudio Codeは、Microsoftにより開発されたプログラミングエディタです。
![VSCode](https://burturki.sirv.com/diy/vsc.png?w=300)

Windows, Mac, Linuxといったプラットフォームで使用できます。
> [参考ページ：Visual Studio Code](https://azure.microsoft.com/ja-jp/products/visual-studio-code/)

Linuxでよく使われているプログラミングエディタにはAtomがあります。最近のプログラミング記事で、AtomからVisual Studio Codeへの移行をよく目にするようになり、Visual Studio Codeのインストール方法を調べてみました。

> [参考ページ：Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux)

Debian/Ubuntu上では、開発に便利なChrome、Node.js、VisualStudioCodeなどのインストールは、1. ソフトウエア配布元から認証キーを取得、2. リポジトリ更新後、リポジトリ情報に従いソフトウエアをインストール、という手順で行います。

解説によればインストール方法には、snap、debパッケージ、apt installの３種類が紹介されていました。

今回は、認証キーを取得してapt installする方法でインストールして、Visual Studio Codeのプログラミングエディタとしての使い勝手と操作感をAtomと比較しました。

**Visual Studio Code**

`
aptインストール : curl, install, sh, apt-get update, apt-get install, apt-transport-https
`

## インストールに必要なコマンド

curl、gpg、install、sh、apt-get install、apt-transport-https

## インストール手順

インストールは次の手順で行います。su権限が必要になります。

* (1) Microsoftの認証キーを取得

* (2) 認証キーをリポジトリに追加

* (3) Visual Studio Codeの認証キーを取得

* (4) apt-transport-httpsのインストール（httpsに対応したaptコマンド）

* (5) リポジトリを更新

* (6) Visual Studio Codeのインストール

## インストール方法

### 1. Microsoftの認証キーをリモートから取得

```bash
# Using Debian, as root
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
```

### 2. 認証キーをOSのリポジトリに追加

```bash
# Using Debian, as root
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
```

### 3. Visual Studio Codeの認証キーをリモートから取得

```bash
# Using Debian, as root
sudo sh -c 'echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
```

### 4. httpsに対応したaptのインストール

```bash
# Using Debian, as root
sudo apt-get install apt-transport-https
```

### 5. OSのリポジトリを更新

```bash
# Using Debian, as root
sudo apt-get update
```

### 6. Visual Studio Codeのインストール

```bash
# Using Debian, as root
sudo apt-get install code
```

## 起動方法

コマンドラインからは、`code`で実行します。
GUIからは、`メニュー > アクセサリ`から`Visual Studio Code`をクリックして起動します。

## Tips

### 日本語化

> [Visual Studio Codeを日本語化する方法](https://qiita.com/HiroCh/items/481adfa969dbe689f566)

### 長い１行の折り返し

https://www.atmarkit.co.jp/ait/articles/1807/27/news035.html

## まとめ

プログラミングエディタVisual Studio Codeは、Windows, Mac, Linuxのいずれのプラットフォームでも使用でき、プログラミング作業、文書編集作業のどちらもこなせるエディタです。

**プログラミング**

複数のファイルを同時編集する場合、画面（ペイン）分割が、ウィンドウ右上のアイコンからワンクリックで操作できます。また画面の隅にドラッグ・ドロップすることでも同様の操作ができます。

**文書編集**

マークダウン文書の編集時には、編集中の文書とプレビュー画面を同時表示できます。

右上のプレビューアイコンをクリックすると、編集画面とプレビュー画面に同時表示できます。また画面のスクロールはどちらの画面からでも可能であり、効率的で快適な文書編集操作が可能です。

**差分比較**

文章の差分を比較して、編集することができます。

ctrl + shift + pでコマンドラインを立ち上げ、compareを打ち込んで差分比較を実行

エクスプローラーで右クリックして、差分比較を実行

## まとめ

プログラミングエディタVisual Studio Codeは、Windows, Mac, Linuxのいずれのプラットフォームでも使用でき、プログラミング作業、文書編集作業のどちらもこなせるエディタです。
