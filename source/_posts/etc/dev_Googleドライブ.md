---
title: 'GoogleDriveをLinux上にマウントしてローカルファイルのように使う'
date: 2020-06-17 17:30:00
tags:
- Linux
- Debian
- 'Google Drive'
- オンラインストレージ
- クラウドストレージ
- mount
- マウント
- ローカルファイル
categories:
- 'etc Linuxプログラミング実践'
- 'e) 開発支援ツール'
excerpt: 'Google DriveをLinux Debian10上にマウントして、ローカルファイルを扱うようにしました。'
cover_image : images/google-drive.jpg
pid: google_drive_storage
---

## Google Drive - オンラインストレージ

Google Driveは、ブラウザベースで利用できる使い勝手のいいオンラインストレージです。

Linux上の仮想ファイルシステムとして、Google DriveをLinux上にマウントしました。

## オンラインストレージのローカルシステムへのマウント

Googleからは公式にアナウンスされていませんが、Linux Debian10にはgnomeの機能として、Googleアカウントへのログイン機能が用意されています。

> [各種オンラインストレージのLinuxマウント](https://medium.com/okano/ubuntuで利用できるオンラインストレージまとめ-ee44d5699371)

gnome-online-accountsを利用することで接続が可能になります。

gnome-online-accountsは、コマンドラインから次のようにして呼び出します。

```bash
sudo apt install gnome-online-accounts
```

またGUIからは次のようにして呼び出します。

設定 > オンラインアカウント -> Googleアカウントを登録する

## 使用方法

OSに用意されているアイコン「ファイル（Files）」をクリックして開くと、Google Driveへマウントされ、アクセスできるようになっています。
