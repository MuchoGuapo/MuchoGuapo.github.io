---
title: 'Linux Debian10でSSHを設定する'
date: 2020-05-15 17:30:00
tags:
- リモート操作
- 認証ログイン
- SSH
categories:
- 'etc Linuxプログラミング実践'
- 'd) Linuxネットワーク利用'
excerpt: 'SSHで他のPCからログインする方法を設定します。'
cover_image : images/ssh.jpg
pid: command_ssh
---

## SSH - 認証ログイン
![linux](https://burturki.sirv.com/diy/linux.png?w=300)

ネットワーク経由で他のPCからセキュアにログインする場合、SSHを使用します。

> [SSHサーバー構築](https://www.mk-mode.com/blog/2017/08/06/debian-9-ssh-installation/#)

最初、SSH接続はパスワード認証方式で行います。
接続できることを確認したら、鍵認証方式に切り替えます。

## サーバー側設定

### 1. SSHサーバのインストール

```bash
apt install ssh
```

### 2. 設定ファイル/etc/ssh/sshd_config

```
#Port 22
Port 9999                         # <= 適当に変更

# rootユーザーのログインはパスワード認証以外のみ許可する
PermitRootLogin without-password

# SSHプロトコル ver.2 で公開鍵認証を許可する
PubkeyAuthentication yes

# パスワード認証を許可する(rootユーザー以外に適用)
PasswordAuthentication yes

# チャレンジレスポンス認証を拒否する
ChallengeResponseAuthentication no

# PAMを使用する
UsePAM yes

AllowUsers root                   # <= ログイン可能なユーザを明示的に設定
AllowUsers hamkaz                 # <=     〃
```

### 3. SSHサーバ再起動

```bash
systemctl restart ssh
```

### 4. パスワード方式によるSSH接続

```bash
ssh -p 9999 hoge@192.168.11.3
```

## パスワード方式から鍵認証方式に切り替える

### 1. クライアント側で鍵ペアの生成

```bash
ssh-keygen
```

## 2. サーバー側にクライアントの鍵ペアを設定

## 3. クライアントから鍵認証でSSH接続
