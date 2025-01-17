---
title: 'プラグインとヘルパー'
date: 2020-06-21 17:30:00
tags:
- Hexo
- プラグイン
- ヘルパー
- 機能拡張
- 多言語化
- ページ変数
categories:
- '2 Hexoでブログ作成'
- 'a) Hexoの初期設定'
excerpt: 'Hexoのプラグインで機能拡張する。ヘルパーで、i18nによる多言語対応、ページ変数を表示する。'
cover_image : hexo.png
pid: hexo-plugin
---

## Hexo Plugin 作成
![hexo](https://burturki.sirv.com/diy/hexo.png?w=300)

> https://morizyun.github.io/blog/hexo-plugin-amazon-jp-link/index.html



### プロジェクトのフォルダを作成します。

```
mkdir hexo-<プラグイン名> && cd hexo-<プラグイン名>
```



### npm moduleの設定を行います。

```
npm init
```



### entry pointになる`index.js`を作成します。

```
hexo.extend.tag.register('custom_tag', function(args){
  var message = args[0];
  return `
custom_tag: ${message}`;
});
```

※注 作成したpluginをローカルでテストするために「**[npm link の手順 / morizyun GitBook](http://morizyun.github.io/javascript/node-js-npm-command-npm-link.html)**」を実行してください。



### `package.json`に以下を追加してください。

(`0.0.1`は適切なバージョンに書き換えてください)

```
"dependencies": {
  "hexo-<プラグイン名>": "^0.0.1",
}
```

これでローカルのnpmライブラリが紐付けられた状態になります。



### テスト

`hexo server`上でさきほどのタグを使えることを試してみます。
hexoのテンプレートの中に`{％ custom_tag hoge ％}`と書いてください。(％は半角に変更してください)
``

```
hoge
```

が表示されれば成功です。



## npmへのpush

npmでpublishするのは次のコマンドです。

```
npm publish
```

Hexoのプラグインを作るのはちょうどよいJavaScriptの勉強の題材になりそうです。

Happy Hacking!

## Hexoのプラグイン開発

> [Hexoのプラグインの作成手順](https://morizyun.github.io/blog/hexo-plugin-amazon-jp-link/index.html)

> [npm link](https://morizyun.github.io/javascript/node-js-npm-command-npm-link.html)

> [npm linkにsu権限が必要な理由](https://stackoverflow.com/questions/30529525/why-do-i-have-to-call-npm-link-as-administrator/38946326)

## Hexoのプラグイン作成手順

> https://morizyun.github.io/blog/hexo-plugin-amazon-jp-link/index.html

### フォルダ構造を決める

```
~/git							<- プロジェクトルートdir
​	L blog					<- hexoブログのルートdir
​	L hexo-multicol	<- hexoプラグインのルートdir
```

### 作業ディレクトリ作成

プロジェクトのルートdirを決め、1) hexo init blog、2) mkdir hexo-multicol を実行する

```
$ mkdir hexo-multicol && cd hexo-multicol
```

### プラグイン作成

entry pointになる`index.js`を作成します。

```
hexo.extend.tag.register('custom_tag', function(args){
  var message = args[0];
  return `
custom_tag: ${message}`;
});
```

## プラグインを使えるようにする

### 依存関係の設定

npm initで依存関係dependencyを定義する

```
$ npm init
```

### シンボリックリンク設定

プラグインdir側からグローバルにシンボリックリンクを貼る。npm linkを実行する、シンボリックリンクの場所が/usr/localになるためroot権限が必要。
suコマンドで入って、npm linkする

```
# npm link
```

### dependencyに新しいプラグインを追加

開発中のプラグインを追加する

```
"dependencies": {
  "hexo-<プラグイン名>": "^0.0.1", <-間に追加する ","を忘れないように
}
```

### プラグインを認識させる

npm link hexo-multicolで認識させる

```
$ npm link hexo-multicol
```

リンクが生成される。/usr/local/lib/node_modules/hexo-multicol -> /home/hamkaz/git/hexo-multicol

### パッケージ追加

`package.json`に追加。ローカルのnpmライブラリが紐付けられた状態になる。

```
"dependencies": {
  "hexo-<プラグイン名>": "^0.0.1",
}
```

### テスト

hexoのテンプレートで`{％ custom_tag hoge ％}`と書く。

## 一般公開

### npmへのpush

Hexoのプラグインを作成、npm publishコマンドで公開。

```
npm publish
```



## まとめ

便利だと思ってHexoのプラグインを当ててみたところジェネレートの動作不具合を起こしたり、プラグインそのものの脆弱性が解決できない場合があることも分かりました。


# 多言語対応
![hexo](https://burturki.sirv.com/diy/hexo.png?w=300)

Hexoでは表示する言語を切り替えることができる。ポイントは、多言語対応ファイルi18n、ヘルパーによる参照

ソフトウエアの国際化はi18nと呼ばれ、ソフトウエアの多言語対応が可能になる。

Hexoだとthemes配下のlanguagesにあり、各国語に対応できる。

Hexoでは下記の方法で埋め込む

<%= __('author_icon') %>

## Hexoのヘルパー

Hexoのテンプレートでは、繰り返し使用する関数などのソースコードをヘルパーで簡単に呼び出すことができます。
ヘルパーはスニペット（再利用可能なソースコード）を呼び出して、テンプレートで使用することができます。

> [Hexo helpers](https://hexo.io/api/helper.html)

ヘルパーをテンプレートに記述すると、よく使用する処理コードを簡単にコールできます。
引数と返り値を持った関数をヘルパーに定義できます。

> [Hexo で helper 的な共通関数を定義する](https://matsuoshi.hatenablog.com/entry/2018/12/30/000000)

> [Hexoタグ作成のトリック](https://blog.masuqat.net/2017/12/18/hexo-custom-tag-plugin-tips/)


## ページ種別をヘルパーで判別させてみる

テンプレートが読み込まれたとき、どのようなページ種別をもつか知りたいときがある。
ヘルパーには、あらかじめこのような関数が用意されている。

### 考え方

例えば、is_archive, is_category, is_tag, is_homeというヘルパーを使うと、現在のテンプレートが処理するページ種別を取得することができる。
layout.ejsが呼び出すページ種別を知るため、判別ルール`is_home() == true`で条件判別させてlayout.ejsの処理時に表示させた。

```
<p>is_archive:  <%- is_archive() %>   </p><hr>
<p>is_category: <%- is_category() %>  </p><hr>
<p>is_tag:      <%- is_tag() %>       </p><hr>
<p>is_home:     <%- is_home() %>      </p><hr>
<p>is_post:     <%- is_post() %>      </p><hr>
<p>is_page:     <%- is_page() %>      </p><hr>
```

### 結果

**投稿に関するページ**

||home|post|page|archive|category|tag|
|----|----|----|----|----|----|----|
||index.ejs|post.ejs|page.ejs|archive.ejs|category.ejs|tag.ejs|
|index(トップ)|○||||||
|post(記事ページ)|^|○|||||
|page(固定ページ)|^|^|○||||
|archive(アーカイブ)|^|^|^|○|||

**アーカイブに関するページ**

||home|post|page|archive|category|tag|
|----|----|----|----|----|----|----|
||index.ejs|post.ejs|page.ejs|archive.ejs|category.ejs|tag.ejs|
|archive(アーカイブ)||||○|||
|tag(タグ)||||^|○||
|category(カテゴリー)||||^|^|○|

ページ種別に該当の（専用）テンプレートが存在しない場合、fallback（テンプレートの代用処理）でテンプレート処理を行う。

## ヘルパーとパンくずリスト

> [Hexoでプラグインを使わずパンくずリストを表示する](https://pixelog.net/post/xzr273/)

