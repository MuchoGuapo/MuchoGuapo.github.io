---
title: '1c) Node.jsのインストール'
date: 2020-05-14 17:30:00
tags:
- JavaScript環境
- Node.js
categories:
- '1 LinuxとNodejsでプログラミング'
- 'b) Node.jsとHexoのインストール'
excerpt: 'JavaScriptのアプリケーション開発のため、JavaScript実行環境Node.jsをインストールしました。Linux Debian10にインストール手順とセットアップ方法について調べてみました。'
cover_image : nodejs.png
pid: framework_nodejs
---

## JavaScript環境 - Node.js
Node.jsはJavaScriptの実行環境で、Googleによって開発されました。
![nodejs](https://burturki.sirv.com/diy/nodejs.png?w=300)

Node.js上ではいろいろなアプリケーションを開発することができます。例えばJavaScriptで記述されたサーバーサイドアプリケーションの構築、JavaScriptをベースとしたネットワークアプリケーション作成などを行うことができます。

> [Node.js公式ページ（日本語）](https://nodejs.org/ja/)

公式ページによれば、Node.jsのインストール方法にはパッケージ、コマンドラインなどいろいろな方法が用意されています。

> [Node.js Binary Distribution](https://github.com/nodesource/distributions/blob/master/README.md#debinstall)

コマンドラインのインストール方法により、Node.jsをインストールしました。

## インストールに必要なコマンド

curl、bash、apt-get update、apt-get install、apt-key、echo、tee

## インストール手順

1. インストールパッケージのダウンロード
2. Node.jsのインストール

（npm以外にYarnを必要とする場合）
3. Yarnの認証キー取得、リポジトリに設定
4. 安定バージョンに固定
5. OSのリポジトリ更新とYarnのインストール

## インストール方法

```bash
# Using Debian, as root
curl -sL https://deb.nodesource.com/setup_14.x | bash -
apt-get install -y nodejs
```

## yarnの追加インストール

```bash
# Using Debian, as root
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -

echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
deb https://dl.yarnpkg.com/debian/ stable main

sudo apt-get update && sudo apt-get install yarn
```

## インストール結果とバージョン確認

JavaScript環境Node.jsと、パージョン管理npm、Yarnのインストール結果とバージョン確認です（2020年7月補足）。

```
node -v
v14.5.0

npm -v
6.14.5

yarn -v
1.22.4
```

## まとめ

JavaScript環境Node.jsは、さまざまなネットワークアプリケーションのベースとなっています。Windows, Mac, Linuxのいずれのプラットフォームでも安定して動作します。

Node.js上のJavaScriptでWebアプリケーションやサイトジェネレーターなどを構築することができ、さまざまなWeb技術習得に役立てられます。
