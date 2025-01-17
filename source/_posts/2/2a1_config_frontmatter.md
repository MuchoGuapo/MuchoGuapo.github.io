---
title: 'コンフィグとフロントマター'
date: 2020-06-11 03:45:00
tags:
- Hexo
- コンフィグ
- フロントマター
- タグ
categories:
- '2 Hexoでブログ作成'
- 'a) Hexoの初期設定'
excerpt: 'Hexoの動作を決定する設定ファイル（_config.yml）について調べてみました。'
cover_image : hexo.png
pid: hexo_config_frontmatter_tag
---

## Hexoの設定、コンフィグとフロントマター
![hexo](https://burturki.sirv.com/diy/hexo.png?w=300)

Hexoでは、コンフィグ、フロントマター、タグの３つを用いてhtmlファイルの生成を制御します。

## (1) コンフィグファイル

コンフィグでは、一つはサイト全体のコンフィグ、もう一つはテーマのコンフィグです。あらかじめ、これらのコンフィグに設定を書き込むと、htmlファイルの生成をhexoで制御できます。

### hexo generate時にrenderさせない

```_config.yml
skip_render:
- _posts/twentytwenty.js
```

### パーマリンク設定

> [パーマリンクの大切さ](https://mag.nioufuku.net/2019/01/05/programming/00014-hexo-edit-url/)

> [/を取り除くこと](https://qiita.com/shosho/items/83689107d8621a96fd9e)

### Hexo No Layoutエラーを回避する

> [_config.yml（コンフィグ）に適切なテーマ名が設定されていない](https://github.com/ppoffice/hexo-theme-hueman/issues/73)

```_config.yml
theme:
- landscape -> (現在使用のテーマ名)
```

## (2) フロントマター

Hexoの記事を書くには、マークダウンファイルの冒頭に、フロントマターと呼ぶ設定を書いておきます。この設定はyaml形式で記述し、マイナス記号3つで囲み、箇条書き形式で記載します。

日付や概要を書き込みます。

### CSSやJSなど読み込み指定する

> [Hexoで記事ごとに適用するCSSやJSファイルをFront-matterから自動で読み込む](https://pixelog.net/post/xumh8c5si7/)

### 独自パラメータを追加する

Front-matterのヘッダ部分に指定した値は、テンプレート内では`post.XXXXX`という形で取得でき、独自パラメータによる制御ができます。

```javascript
  <% if (post.show_meta != false) { %>
    （投稿時間やカテゴリ・タグなどの出力部分）
  <% } %>

<% if (post.show_share != false) { %>
    （シェアリンクの出力部分）
  <% } %>
```

### パラメータの引き渡し方

ずっと固定ページで特定のカテゴリーのみを抜き出すカードを作りたかったが、なかなか実現できなかった。突破口は２つであった。
一つはHexo公式ページのHexo Variables、もう一つは下記のページでやり取りされている内容である。

> [Change HTML for list_categories and list_tags?](https://github.com/hexojs/hexo/issues/3050#)

tcroweの27 Feb 2018のポストによると、こんなふうにページが所有する変数の値を見ることができるとある。

```
<% site.categories.each(function(item) { %>
  name: <%=item.name%><hr>
  id: <%=item._id%><hr>
  slug: <%=item.slug%><hr>
  path: <%=item.path%><hr>
  permalink: <%=item.permalink%><hr>
  posts: <%=typeof item.posts%><hr>
  count: <%=item.length%><hr>
  <br><br>
<% }) %>
```

## (3) マークダウン内に書き込むタグ

引用や注記、テーマによっては概要

### 目次作成

#### プラグイン

hexo-tocというプラグインをインストールする

`npm install hexo-toc --save`

### テンプレートのカスタマイズ

プラグインに脆弱性がある

> https://github.com/bubkoo/hexo-toc

テンプレートをカスタマイズする方法を調べた。

> [postページで目次を自動生成](https://gazee.net/hexo/hexo-add-toc/)


## Hexoの設定、コンフィグとフロントマター
![hexo](https://burturki.sirv.com/diy/hexo.png?w=300)

Hexoでは、コンフィグ、フロントマター、タグの３つを用いてhtmlファイルの生成を制御します。

## (1) コンフィグファイル

コンフィグでは、一つはサイト全体のコンフィグ、もう一つはテーマのコンフィグです。あらかじめ、これらのコンフィグに設定を書き込むと、htmlファイルの生成をhexoで制御できます。

### hexo generate時にrenderさせない

```_config.yml
skip_render:
- _posts/twentytwenty.js
```

### パーマリンク設定

> [パーマリンクの大切さ](https://mag.nioufuku.net/2019/01/05/programming/00014-hexo-edit-url/)

> [/を取り除くこと](https://qiita.com/shosho/items/83689107d8621a96fd9e)

### Hexo No Layoutエラーを回避する

> [_config.yml（コンフィグ）に適切なテーマ名が設定されていない](https://github.com/ppoffice/hexo-theme-hueman/issues/73)

```_config.yml
theme:
- landscape -> (現在使用のテーマ名)
```

## (2) フロントマター

Hexoの記事を書くには、マークダウンファイルの冒頭に、フロントマターと呼ぶ設定を書いておきます。この設定はyaml形式で記述し、マイナス記号3つで囲み、箇条書き形式で記載します。

日付や概要を書き込みます。

### CSSやJSなど読み込み指定する

> [Hexoで記事ごとに適用するCSSやJSファイルをFront-matterから自動で読み込む](https://pixelog.net/post/xumh8c5si7/)

### 独自パラメータを追加する

Front-matterのヘッダ部分に指定した値は、テンプレート内では`post.XXXXX`という形で取得でき、独自パラメータによる制御ができます。

```javascript
  <% if (post.show_meta != false) { %>
    （投稿時間やカテゴリ・タグなどの出力部分）
  <% } %>

<% if (post.show_share != false) { %>
    （シェアリンクの出力部分）
  <% } %>
```

### パラメータの引き渡し方

ずっと固定ページで特定のカテゴリーのみを抜き出すカードを作りたかったが、なかなか実現できなかった。突破口は２つであった。
一つはHexo公式ページのHexo Variables、もう一つは下記のページでやり取りされている内容である。

> [Change HTML for list_categories and list_tags?](https://github.com/hexojs/hexo/issues/3050#)

tcroweの27 Feb 2018のポストによると、こんなふうにページが所有する変数の値を見ることができるとある。

```
<% site.categories.each(function(item) { %>
  name: <%=item.name%><hr>
  id: <%=item._id%><hr>
  slug: <%=item.slug%><hr>
  path: <%=item.path%><hr>
  permalink: <%=item.permalink%><hr>
  posts: <%=typeof item.posts%><hr>
  count: <%=item.length%><hr>
  <br><br>
<% }) %>
```

## (3) マークダウン内に書き込むタグ

引用や注記、テーマによっては概要

### 目次作成

#### プラグイン

hexo-tocというプラグインをインストールする

`npm install hexo-toc --save`

### テンプレートのカスタマイズ

プラグインに脆弱性がある

> https://github.com/bubkoo/hexo-toc

テンプレートをカスタマイズする方法を調べた。

> [postページで目次を自動生成](https://gazee.net/hexo/hexo-add-toc/)
