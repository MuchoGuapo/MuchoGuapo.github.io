---
title: 'Hexoの考え方を理解する'
date: 2020-05-13 17:30:00
tags:
- 静的サイトジェネレーター
- Hexo
- Webページ
categories:
- '2 Hexoでブログ作成'
- 'a) Hexoをインストールする'
excerpt: '静的サイトジェネレーターHexoでサイトを立ち上げて、サイト生成の仕組みを調べてみました。'
cover_image : images/hexo.png
pid: website_starting_with_hexo
---

## Hexoでサイト作成
![hexo](https://burturki.sirv.com/diy/hexo.png?w=300)

### Hexoとは？
Hexoは、サイト作成を簡単化、自動化するもので、サイトジェネレータと呼ばれます。

サーバーでのリアルタイム処理を要しないサイトに向いています。

## Hexoの仕組みを理解
Hexoは次の構成で動作します。

```
静的ページジェネレーター - Hexo
エンジン - Node.js
パッケージマネージャー - npm
言語 - Javascript
```

Hexoの動作はJavaScriptで記述します。

### 静的サイトジェネレーターとは？
静的サイトジェネレーターは、マークダウンファイルをサイトデータに変換します。

静的サイトジェネレーターの考え方は、あらかじめサイトデータを生成して、サーバーにデプロイする形を採ります。

WordpressではPHPで動的に生成ルールを記述しますが、静的サイトジェネレーターは、各種の言語でHTMLの生成ルールを決めておき、サイトの共通要素、各個別ページの要素ごとにHTMLを生成、CSS・JSとともに出力します。

## Hexoのディレクトリ構造

```
~/（ブログ名）
L node_modules
L public
L scafffolds
L source
​	L _draft
​	L _post
L themes
_config.yml
db.json
package-lock.json
package.json
```

## 固定ページの新規作成

scaffoldの雛形がコピーされる。

```
hexo new page “タイトル”
```

## 投稿ページの新規作成

scaffoldの雛形がコピーされる。

```
hexo new post “記事タイトル”
```

## ファイルはどこにできるか？

```
固定ページ
(プロジェクト名)  >  source  >  （ページ名称のディレクトリ）配下
```

```
投稿ページ
(プロジェクト名)  >  source  >  _posts配下
```

## テーマの変更

```
_config.yml
Extensionsコメント
theme: 以降を変更するテーマ名に書き換える
```

## Hexoのエラー要因
Hexoのテーマやプラグインには、リンク切れやメンテナンス放棄されているものもあります。
脆弱性が解決できず、使用上の注意を要する場合があります。

またテーマやプラグインのインストールとアンインストールを繰り返すと、動作が不安定になる場合があります。npmのパッケージ管理package.jsonへの追記・削除が正常に行われない場合に発生するようです。

## まとめ
Hexoでは、Javascriptを書き換えることで、生成データの見た目や動作を自由に変更できます。Web上に文献がたくさん存在するため、先人の知識や経験を参照して自己解決できます。

ロースペックのPC上のLinux上で、Javascript、Node.jsを不具合なく動作させることができ、コスト（導入・学習・金銭）をかけずにプログラミングを学習できます。

またLinuxのパッケージ管理方法はプログラム開発に向いているため、Linuxでの構築コスト（手間と時間）は最も少なくて済みます。