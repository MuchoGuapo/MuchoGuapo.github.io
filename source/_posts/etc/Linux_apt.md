---
title: 'aptインストールとエラー回避'
date: 2020-05-14 17:30:00
tags:
- Debian
- パッケージ管理
- apt
categories:
- '1 LinuxとNodejsでプログラミング'
- 'b) パッケージ管理を学ぶ'
excerpt: 'Debian/Ubuntuにおいてソフトウエアインストールはパッケージ管理aptで行います。aptによるソフトウエアインストールと、インストール履歴を扱うリポジトリ管理、そしてapt実行時の警告・エラー対策についてまとめました。'
cover_image : images/linux.png
pid: package_apt
---

## パッケージ管理 - apt
![linux](https://burturki.sirv.com/diy/linux.png?w=300)

Linux Debian、及びUbuntuなどの派生ディストリビューションでは、Aptと呼ばれるパッケージ管理、及びコマンドラインツールaptを用いてパッケージ情報の管理を行います。

> [Debian公式Wiki - Advanced Package Tool](https://wiki.debian.org/Apt)

## パッケージ管理Aptで行われること

パッケージ管理Aptでは、パッケージ情報の参照、追加、更新、削除を行います。

### JavaScript環境 - Node.js

`
aptインストール : curl, apt-get install, apt-key, tee, apt-get update
`

## aptコマンド一覧

aptコマンドの一覧と使用例は、以下のページを参照しました。

> [aptコマンドを使ったパッケージ管理](https://linuxfan.info/package-management-ubuntu)

## apt実行時の警告・エラー

### 1. apt update - 「リポジトリにファイルがありません」

**状況**

```
E: リポジトリ http://ppa.launchpad.net/webupd8team/atom/ubuntu groovy Release には Release ファイルがありません。
```

**原因**

サポート期間が切れたパッケージが残っているため

**対策**

以下のHPを参照して、サポートの切れたパッケージの更新を止めました。

> https://hombre-nuevo.com/linux/linux0020/

**対応方法**

次のコマンドでapt updateから該当のパッケージの外します。

```bash
# Using Debian, as root
sudo apt-add-repository -r ppa:webupd8team/atom
```

/etc/apt/source.listに登録されたアップデート情報が削除されます。以後、apt updateをかけてもエラーメッセージが表示されなくなります。

### 2. apt update - 「以下のパッケージが自動でインストールされましたが、もう必要とされていません」

**状況**

```
以下のパッケージが自動でインストールされましたが、もう必要とされていません:
  gyp libc-ares2 libjs-inherits libjs-is-typedarray libnode-dev libnode64
  libssl-dev libuv1 libuv1-dev nodejs-doc
これを削除するには 'apt autoremove' を利用してください。
```

**原因**

依存関係にあったパッケージが削除されたため

**対策**

必要の無くなったパッケージを削除します。

**対応方法**

apt autoremoveコマンドを実行します。

```bash
apt autoremove
```

## まとめ

パッケージ管理AptでLinuxのさまざまなパッケージを管理できます。

コマンドラインツールの追加などもaptで行います。
