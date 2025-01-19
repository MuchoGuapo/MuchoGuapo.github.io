---
title: 'Linux Debian10でSambaによる小規模ファイルサーバーを構築する'
date: 2020-05-15 17:30:00
tags:
- Linux
- Debian
- samba
- ファイルサーバー
- application
- アプリケーション
- 開発環境
categories:
- 'etc Linuxプログラミング実践'
- 'd) Linuxネットワーク利用'
excerpt: 'Linux Debian10にSambaをインストールしてファイルサーバーを構成しました。'
cover_image : images/programming-environment.jpg
pid: samba_file_server
---

## 多数のOSからファイル共有できるようにするには？
![linux](https://burturki.sirv.com/diy/linux.png?w=300)

複数台の異なるPCでファイル共有をしようと考えたとき、ファイルサーバーもしくはNASが必要となります。

> [ネットワークアタッチストレージ(NAS)](https://ja.wikipedia.org/wiki/%E3%83%8D%E3%83%83%E3%83%88%E3%83%AF%E3%83%BC%E3%82%AF%E3%82%A2%E3%82%BF%E3%83%83%E3%83%81%E3%83%88%E3%82%B9%E3%83%88%E3%83%AC%E3%83%BC%E3%82%B8)

LAN上にNASを構築しようとした場合、NAS専用機を購入するのではなく、自前でNASを構築するという選択をしました。

まずNAS専用OSとしてOpenMediaVaultなどを検討しましたが、要求されるハードスペックが高いなど手軽に実現できないことが分かりました。

またファイル共有プロトコルの問題もありました。各OSごとにいろいろなファイル共有プロトコルが用意されており、WindowsではSMB、Mac OSではAFP、LinuxではNFSなどがあることが分かりました。

今回、いろいろなOS間、すなわちクロスプラットフォームでファイル共有を実現するため、Linuxをサーバー、Windows・Mac OS・Linuxをクライアントとし、Sambaを使ってファイル共有機能を実現する方法について調べてみました。

## Linuxだけでファイル共有を考えた場合

Linuxではファイル共有プロトコルとしてFTP、NFS、SSH(rcp)を使います。またWindowsではCIFSかSMB、Mac OSではAFPかSMBというファイル共有プロトコルを使用します。

ではWindows、Mac OS、Linuxの全てのOSからファイル共有を実現したい場合は、サーバーをどこに置いてどのように構成したら良いでしょうか？

Windows ServerやWindows Storage Serverを使う方法、LinuxでSambaを構成する方法があることが分かりました。個人用途で手軽に実現しようとした場合、Linux上のSambaが選択肢に挙げられます。

LinuxにおけるSambaは、WindowsのSMBというWindowsネットワークの機能をLinux上に実装した（機能をコピーして実現した）もので、ファイル共有、プリンタ共有、ドメインコントロール、ドメイン参加などが実現できます。

今回は、Linuxマシンをファイルサーバーにするため、Linux上にSambaサーバーを構成、Linux、Mac、Window機をSambaクライアントにし、小規模なネットワークでのファイル共有を実現しました。

## Linux上にSambaサーバーを構成する。

### 1. インストール

Samba Serverをインストールします。

> [Install Samba Server](https://wiki.debian.org/SambaServerSimple)

### 2. Sambaデーモン

Samba Serverを常駐プロセス（デーモン化）します。

> [ubuntuでSambaの再起動](https://ohzeki.hatenablog.com/entry/20160916/1473998215)

### 3. Sambaにおけるユーザー管理

Sambaにおけるユーザー管理において、ログインユーザーはLinuxユーザーとSambaユーザーで同じとなる。しかしパスワードは**LinuxのログインパスワードとSambaのログインパスワードで異なる**点を理解する必要があります。

> [Samba fails to add a user entry, how do I fix this?](https://askubuntu.com/questions/362852/samba-fails-to-add-a-user-entry-how-do-i-fix-this)

**Sambaユーザーを作成します**

> [実は簡単！Linuxユーザの作成方法と追加方法](https://eng-entrance.com/linux-user-add)

**Sambaパスワードを設定します**

pdbeditで作成します。

> [pdbedit — SAM データベース (Samba ユーザーのデータベース) を管理する](http://www.samba.gr.jp/project/translation/3.5/htmldocs/manpages-3/pdbedit.8.html)

Sambaユーザーの一覧は、次のようにして確認します。

> [SAMBAのパスワードファイルに登録されているユーザ一覧を表示するには](http://april.fool.jp/blogs/2014/07/23/%E3%83%A1%E3%83%A2-samba%E3%81%AE%E3%83%91%E3%82%B9%E3%83%AF%E3%83%BC%E3%83%89%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AB%E7%99%BB%E9%8C%B2%E3%81%95%E3%82%8C%E3%81%A6%E3%81%84%E3%82%8B%E3%83%A6/)

## Linux上にSambaクライアント構築

### smbclientのインストール

Samba Serverをインストールします。

> [Install Samba Client](https://wiki.debian.org/SambaServerSimple)

### smbclientの使い方

> [smbclient](http://leo.ec.t.kanazawa-u.ac.jp/manuals/samba-2.2.7b-ja-1.0/ja-htmldocs/smbclient.1.html)

### Windowsからの接続



### Macからの接続
 
## まとめ


