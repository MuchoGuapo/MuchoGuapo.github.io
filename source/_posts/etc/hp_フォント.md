---
title: 'フォントファイルによる体裁'
date: 2020-06-11 17:30:00
tags:
- ホームページ基礎
- フォント
categories:
- 'etc Linuxプログラミング実践'
- 'f) ホームページ基礎'
excerpt: 'サイトの雰囲気を決めるフォント'
cover_image : images/hexo.png
pid: website-font-setting
---

## サイトのフォントを指定する
![html](https://burturki.sirv.com/diy/html.png?w=300)

head要素で指定する。方法としては、head要素でCDNのネット配信版を使用するか、ダウンロードして組み込んで使用する。

## Webフォント

Webフォントを使うか、組み込みフォントを使う。Googleのwebフォントは使用許諾の上、無料で使用できる。

ネット配信できるCDN方式

ダウンロードして全フォントを組み込むか、ジェネレート時に使用するフォントだけ組み込んでGulpでサイズを小さくする方法とどちらかを選ぶことができる。
Gulpで公開時に使いたいフォントだけサブセット化して組み込むことができる。

> [gulp + fonttoolsでフォントのサブセットを作成する](http://chlono.e-whs.net/gulp-create-font-subset/)

Googleフォントのサイトで好きなフォントを選び、 embeddedボタンを押してコピーし、head要素に貼り付ける

1. <Head>〜</head>の中に、<link href~> 以下をコピペする

```html
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP&family=Sawarabi+Mincho&display=swap" rel="stylesheet">
```

```CSS
font-family: 'Noto Sans JP', sans-serif;
```

## フリーフォント

フリーフォント、ライセンスを確認する

> [たぬき油性マジック;ttf](http://tanukifont.com/tanuki-permanent-marker/)

> [なごみ極細ゴシック;otf](http://font.websozai.jp/line-font2-mihon.html)

フリーフォントで字詰め情報を持たせる

> [Noto Serif CJK（源ノ明朝）の font-feature-settings:palt 対応サブセットフォントを作る](https://qiita.com/sygnas/items/89e4a3a8dee79e6159c6)
