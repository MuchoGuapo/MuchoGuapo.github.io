---
title: 'CSSファイルによる体裁'
date: 2020-06-11 17:30:00
tags:
- ホームページ基礎
- CSS
categories:
- 'etc Linuxプログラミング実践'
- 'f) ホームページ基礎'
excerpt: 'ホームページの基礎知識 - CSSとは - '
cover_image : images/hexo.png
pid: homepage-basics-css
---

## サイドバーをスクロールさせず固定
![html](https://burturki.sirv.com/diy/html.png?w=300)

> [スクロールに応じてサイドバーを固定/追従させる方法！(CSSのみ)](https://takafumimegumi.com/blog/css-position-sticky)

## 画像を親要素にフィット表示させる

> [画像の高さを固定して横幅だけ伸縮させる方法](https://www.design-memo.com/coding/object-fit-property)

> [サイズがバラバラな画像をレスポンシブで縦横比を揃えて表示させる](https://qiita.com/becolomochi/items/265a7f940a1c809f5ba7)

## センタリング

> [ブロック内でブロック要素を上下左右中央揃えにする技]https://qiita.com/HiromuMasuda0228/items/6a51c2ce24c69c937092

要素によってセンタリングのパラメーターが異なるが、要素の属性は後付で変更できる。

## リストの装飾

> [CSSでリストを素敵にするlist-styleの使い方+もっと自由な作り方](https://www.sejuku.net/blog/56177)

> [コピペで使えるリストデザイン34選：CSSで箇条書きをおしゃれに](https://saruwakakun.com/html-css/reference/ul-ol-li-design)

> [リストのマークを表示しない](http://www.1uphp.com/con1/list/style-none.html)

## CSS全体 - 総論

デザインをするときは、デザイン図とパラメーター表を作成しておくとよい。

## CSS全体 - 改善と最適化

メンテナンス用CSSはディストリビューション用CSSと分けて考え、メンテナンスが終わった段階で最適化する。

Minify化によるCSSファイルサイズ削減や使われていないルールセットを削除する方法がある。

> [CSS最適化によるパフォーマンス改善](https://murashun.jp/blog/20180817-01.html)

空白やセミコロンを除去して、ファイルサイズを小さくする。

> [Gulpを利用してJavaScriptとCSSを圧縮する](https://www.takedajs.com/entry/2016/11/23/115457)

効果のない・使用しない記述を除去する。

> [HTMLとCSSのファイルを解析し、未使用のCSSをお掃除してくれる便利なツール -DropCSS](https://coliss.com/articles/build-websites/operation/javascript/unused-css-cleaner-dropcss.html)
