---
title: 'Hexoのエラーに対処する'
date: 2020-06-11 03:45:00
tags:
- Hexo初心者
- エラー回避
categories:
- '2 Hexoでブログ作成'
- 'a) Hexoをインストールする'
excerpt: 'Hexoがよくわからない段階でエラーが発生すると、パニックになってしまう。Hexoでよく発生するエラーの回避方法を解説します。'
cover_image : images/hexo.png
pid: hexo-error-solving
---

## Hexoエラー
![hexo](https://burturki.sirv.com/diy/hexo.png?w=300)

### エラー1 Could not open db.json
```
hamkaz@debian1-de-kaz:~/js/hexo/blog2$ hexo generate
FATAL [hexo-include-markdown] Could not open db.json .
Error: [hexo-include-markdown] Could not open db.json .
    at ReadFileContext.callback (/home/hamkaz/js/hexo/blog2/node_modules/hexo-include-markdown/lib/orverwriteCache.js:22:15)
    at FSReqCallback.readFileAfterOpen [as oncomplete] (fs.js:257:13)
```

### 原因
hexo cleanコマンドを実行直後に、空のdb.jsonを作成する。

db.jsonが削除されてしまったため。hexo cleanコマンドを実行すると、publicフォルダとともにdb.jsonが削除されてしまいます。db.jsonはhexo generateのデータベースとなっているため、一旦削除してしまうとhexo generateできなくなります。

### 対策
db.jsonを新規作成します。

`hexo clean`コマンドを実行後、すぐに`touch db.json`コマンドで空のdb.jsonコマンドを作成します。これにより、hexo generate実行が可能になります。

## エラー categories.find is not a function

### 原因
固定ページには、カテゴリー属性やタグ属性を持たせてはいけない。

hexoのテーマをlandscapeとすると、navに表示する３つのナビゲーションのマークダウンファイルがsource/_posts配下になく、またフロントマターがcategories属性をもっているためジェネレートできない。

### 対策
フロントマターからcategoriesやtag属性を削除する。

>  [categories.find is not a function](https://github.com/hexojs/hexo/issues/2379)

hardywu commented on 14 Apr 2018のコメント

> This happens when you put posts not in `source/_posts` directory. Hexo cannot generate categories variable correctly.

## エラー npm notice created a lockfile as package-lock.json. You should commit this file.
シンボリックリンクが通っていないので、ローカルを参照させる

/usr/local/lib/node_modules/hexo-multicolumn-display -> /home/hamkaz/js/hexo/hexo-multicolumn-display

## エラー npm ERR! extraneous means a package is installed but is not listed in your project's package.json.
extraneousエラーとは、package.jsonに宣言されてないよエラー

>  [npm link causes “extraneous” errors](https://stackoverflow.com/questions/40778822/npm-link-causes-extraneous-errors)

## エラー npm WARN saveError ENOENT: no such file or directory, open '/home/hamkaz/js/hexo/Hexo-plugin-test/package.json'
repositoryが無いよエラー

解決策 = package.jsonを作成する -> npm init

> [package.jsonとは？](https://qiita.com/righteous/items/e5448cb2e7e11ab7d477)

## 削除データがgenerateされてしまう

### 原因
db.jsonに過去のデータ（カスファイル）が溜まっている

### 対策
hexo cleanする。空のdb.jsonと、空のpublicディレクトリを作って、hexo generateする。

### 状況
```
hamkaz@debian1-de-kaz:~/js/hexo/blog2$ hexo generate
FATAL [hexo-include-markdown] Could not open db.json .
Error: [hexo-include-markdown] Could not open db.json .
    at ReadFileContext.callback (/home/hamkaz/js/hexo/blog2/node_modules/hexo-include-markdown/lib/orverwriteCache.js:22:15)
    at FSReqCallback.readFileAfterOpen [as oncomplete] (fs.js:257:13)
```

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2$ hexo init
FATAL [hexo-include-markdown] Could not open db.json .
Error: [hexo-include-markdown] Could not open db.json .
    at ReadFileContext.callback (/home/hamkaz/js/hexo/blog2/node_modules/hexo-include-markdown/lib/orverwriteCache.js:22:15)
    at FSReqCallback.readFileAfterOpen [as oncomplete] (fs.js:257:13)
```

## YAMLException: duclicated mapping  at  Line 118
118 skip_render が二重に宣言されている

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2$ hexo generate
FATAL duplicated mapping key at line 118, column -51:
    skip_render:
    ^
YAMLException: duplicated mapping key at line 118, column -51:
    skip_render:
    ^
    at generateError (/home/hamkaz/js/hexo/blog2/node_modules/js-yaml/lib/js-yaml/loader.js:167:10)
    at throwError (/home/hamkaz/js/hexo/blog2/node_modules/js-yaml/lib/js-yaml/loader.js:173:9)
    at storeMappingPair (/home/hamkaz/js/hexo/blog2/node_modules/js-yaml/lib/js-yaml/loader.js:335:7)
    at readBlockMapping (/home/hamkaz/js/hexo/blog2/node_modules/js-yaml/lib/js-yaml/loader.js:1098:9)
    at composeNode (/home/hamkaz/js/hexo/blog2/node_modules/js-yaml/lib/js-yaml/loader.js:1359:12)
    at readDocument (/home/hamkaz/js/hexo/blog2/node_modules/js-yaml/lib/js-yaml/loader.js:1525:3)
    at loadDocuments (/home/hamkaz/js/hexo/blog2/node_modules/js-yaml/lib/js-yaml/loader.js:1588:5)
    at Object.load (/home/hamkaz/js/hexo/blog2/node_modules/js-yaml/lib/js-yaml/loader.js:1614:19)
    at Hexo.yamlHelper (/home/hamkaz/js/hexo/blog2/node_modules/hexo/lib/plugins/renderer/yaml.js:7:15)
    at Hexo.tryCatcher (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/util.js:16:23)
    at Hexo.<anonymous> (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/method.js:15:34)
    at /home/hamkaz/js/hexo/blog2/node_modules/hexo/lib/hexo/render.js:75:22
    at tryCatcher (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/util.js:16:23)
    at Promise._settlePromiseFromHandler (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/promise.js:547:31)
    at Promise._settlePromise (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/promise.js:604:18)
    at Promise._settlePromise0 (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/promise.js:649:10)
    at Promise._settlePromises (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/promise.js:729:18)
    at _drainQueueStep (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/async.js:93:12)
    at _drainQueue (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/async.js:86:9)
    at Async._drainQueues (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/async.js:102:5)
    at Immediate.Async.drainQueues [as _onImmediate] (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/async.js:15:14)
    at processImmediate (internal/timers.js:456:21)
```
