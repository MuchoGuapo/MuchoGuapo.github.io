---
title: 'Hexoの構成を理解する'
date: 2020-06-11 17:30:00
tags:
- Hexo基礎
- 表示レイアウト
- layout.ejs
categories:
- '2 Hexoでブログ作成'
- 'b) Hexoの動きを理解する'
excerpt: 'Hexoの表示レイアウトをlayout.ejsで定義する'
cover_image : images/hexo.png
pid: hexo-layout-setting
---

## サイト構造
![hexo](https://burturki.sirv.com/diy/hexo.png?w=300)

Hexoで`hexo generate`コマンドを実行する

### Hexoの動作ロジック

Hexoの動作ロジックは、EJS（Embedded Javascript）で記述します。



ブログページのレイアウト、全ページに共通の要素は、layout.ejsに記述します。また各ページ種別ごとに、インデックスページ（index.ejs）、固定ページ（page.ejs）、投稿ページ（post.ejs）、アーカイブページ（archive.ejs）、カテゴリーページ（category.ejs）、タグページ（tag.ejs）といったHTMLの生成ルールを別々に記述し、各ページの共通部品を_partialフォルダに格納し共通利用します。



各テーマではそれぞれ独特の方法でページ処理を行っており、様々な点で自分なりのカスタマイズをやってみたいと考えるようになりました。

##

と、サイトのHTMLデータが定義されます。生成（generate）手順はテンプレートで、あらかじめ記述できます。

Hexoで最初に読み込まれるテンプレートファイルはlayout.ejsです。作成する全てのWebページの見た目に統一感を出すため、`<head>`、`<body>`、`<header>`、`<footer>`など繰り返して使う要素をlayout.ejsに定義します。

例えばブログでいうと、インデックス・固定ページ・投稿ページ・アーカイブ・カテゴリー・タグのどのページでも同じようなレイアウトが適用できます。

## EJSをもっと知る

> [EJSの基本的な書き方](https://qiita.com/miwashutaro0611/items/36910f2d784ff70a527d)

## EJSでレイアウト

> [EJSでレイアウト機能を使う](https://qiita.com/kanye__east/items/87172e946471b9c71cfa)

## Generate処理の流れ（Landscape）

### 最初に読み込まれるlayout.ejs

Hexoのgenerate処理では、まず最初にlayout.ejsが読み込まれます。

HexoのデフォルトテーマLandscapeでは、次のようにレイアウトファイルlayout.ejsが定義されています。lauout.ejsは、`<Site Directory>/themes/landscape/layout`に存在し、配下の`_partial`ディレクトリのejsファイルを読み込みます。

```
_partial/head.ejs
<body>
_partial/header.ejs
body -> いずれかのejsが読み込まれる（index.ejs, archive.ejs, category.ejs, tag.ejs）
_partial/sidebar.ejs
_partial/footer.ejs
_partial/mobile_nav.ejs
_partial/after_footer.ejs
</body>
```

body部分では、ページ種別ごとに読み込まれるテンプレートejsが変わります。

### layout.ejsの次に読み込まれるejsファイル

layout.ejsを読み込んだ後のジェネレート処理では、ページ属性によって読み込まれるejsが切り替わります。

1) page.ejs <- 固定ページ, source直下の_post以外のディレクトリ
2) post.ejs <- 投稿ページ, source直下の_postディレクトリ
3) index.ejs <- トップページ, sourceにはなく、archives, categories, tagsに作用する
3a) archive.ejs <- アーカイブ一覧ページ, archive
3b) categories <- category.ejsによるカテゴリー別にまとめた各インデックス別ページ、一覧ページは作成されない 
3c) tags <- tag.ejsによるタグ別にまとめた各インデックス別ページ、一覧ページは作成されない 

ページ種別に適用するテンプレートejsがない場合、fallbackという呼び出し手順で代替のejsを探し、処理を行います。

### layoutディレクトリの各ejsの役割

hexo-generator-categoryの振る舞いとして、categoriesディレクトリ配下に子ディレクトリを作成してcategoriesリストを作成する（hexo-generator-tagも同じ、hexo-generator-archiveも似たような振る舞いをする）

layout/category.ejsの有無によっても振る舞いが異なり、

1) category.ejsがない場合にはpublic/categories直下のディレクトリにcategories一覧が作成されず、子ディレクトリを作成してcategoriesリストを作成する

2) category.ejsがある場合にはcategory.ejsを雛形として、子ディレクトリを作成してcategoriesリストを作成する

よく見かけるcategories一覧は固定ページからカスタマイズ作成されているため、希望する一覧ページを作成するには、ひと工夫が必要です。
