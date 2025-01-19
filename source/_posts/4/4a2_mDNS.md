---
title: '[2] VisualStudio CodeによるSSH接続'
date: 2024-01-18 12:00:00
tags:
- RaspberryPi 
- VisualStudioCode
- RemoteDevelopment
- SSH
categories:
- '4 IoT'
- 'a) RaspberryPi'
excerpt: 'VisualStudio CodeでSSH接続したリモートPCのファイル編集を行います。VScodeにRemoteDevelopmentというExtensionsを入れて、SSH接続したリモートRaspPiのファイル編集を行います。IoT機器が増えてきた場合、リモート接続してファイル編集し、動作を変えることを目的として、RemoteDevelopmentの中のRemoteSSHを使って、接続テストを行い、詰まりがちな問題点について整理しました。'
cover_image : linux.png
pid: vscode-remote-ssh
---

## VisualStudio CodeのRemoteSSH
SSH接続したリモートPCのファイル編集を行います。VScodeにRemoteDevelopmentというExtensionsを入れて、SSH接続したリモートRaspPiのファイル編集を行います。IoT機器が増えてきた場合、リモート接続してファイル編集し、動作を変えることを目的として、RemoteDevelopmentの中のRemoteSSHを使って、接続テストを行い、詰まりがちな問題点について整理しました。

![vscode](https://burturki.sirv.com/diy/vscode.png?w=300)

### エラー : Could not resolve hostname
DNS解決がうまく行っていない。つまり、ルーター上で管理されているIoT機器の名前が更新されていない。

```
ssh: Could not resolve hostname hogehoge.local: \202\273\202~
```

1. リモートPC側 : nslookup sudo apt-get install dnsutils
mDNS Apple Avahi

2. ローカルPC側 : PCのネットワークアダプタの無効化=>有効化
※参考 https://zenn.dev/skou/articles/261852065d9a27

### エラー
C:\Users\hoge\.ssh\ssh_config

Unable to open 'Settings'
The remote host's archtecture iis not supported

C:\Users\hoge\.ssh\configを修正して、ローカルLinuxからリモートPi3にアクセスできた

### エラー : UnsupportedArch
```
UnsupportedArch
You selected "linux" as the platform - this will be stored in the setting "remote.SSH.remotePlatform" and can be changed there if needed.
```

Armv6非対応、メモリ512MBのため、リモートPCであるPiZero WHには接続できない。 
