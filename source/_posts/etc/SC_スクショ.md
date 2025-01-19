---
title: 'スクリーンショット・動画キャプチャ'
date: 2020-05-15 17:30:00
tags:
- 動画キャプチャ
- スクリーンショット
categories:
- 'etc Linuxプログラミング実践'
- 'b) Linuxの操作Tips'
excerpt: 'パソコン上のいろいろな操作を記録しておきたいと思うことが増えてきました。LinuxパソコンにDebian10を入れて画像や動画を記録するため、スクリーンショットを撮る方法と動画をキャプチャする方法について調べてみました。'
cover_image : images/linux.png
pid: screenshot_video-capture
---

## スクリーンショット（静止画）
![linux](https://burturki.sirv.com/diy/linux.png?w=300)

画面操作や画面表示結果を記録するには、スクリーンショットを撮ったり、動画キャプチャすることがかかせません。

Linux Debian10と相性のいいソフトウエアをテストするため、スクリーンショットにgnome-screenshotを、動画キャプチャにSimpleScreenRecorderをテストしました。

## gnome-screenshot - スクリーンショット

gnome-screenshotはデフォルトでインストールされており、メニュー > アクセサリからスクリーンショットを選択して起動します。

設定を変更することで、画面全体、現在のウィンドウを選択、取得する領域を選択、と選ぶことが出来ます。


## SimpleScreenRecorder - 動画キャプチャ

SimpleScreenRecorderは、aptコマンドでインストールします。

> [Maarten Baert's website - SimpleScreenRecorder](https://www.maartenbaert.be/simplescreenrecorder/)

インストール方法は、上記HPのDownload > Debian/Ubuntuの項目を参照しました。

```bash
# run as root
sudo add-apt-repository ppa:maarten-baert/simplescreenrecorder
$ sudo apt-get update
$ sudo apt-get install simplescreenrecorder
```

## その他、動画に関するソフトウエア

動画の視聴 - VLC player

動画の編集 - Kdenlive, OpenShot Video Editor, Shotcut

動画の公開 - YouTube, Vimeo

動画からの字幕起こし、字幕挿入 - vrewブラウザ版
