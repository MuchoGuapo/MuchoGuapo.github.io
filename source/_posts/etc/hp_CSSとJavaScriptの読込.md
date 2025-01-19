---
title: 'サイトデザインをCSS、JavsScriptでカスタマイズする'
date: 2020-06-02 17:30:00
tags:
- CSS読込
- JavaScript読込
categories:
- '2 Hexoでブログ作成'
- 'c) Hexoに機能追加する'
excerpt: 'Hexoの記事で記事に適用するCSSやJavaScriptを読み込む。'
cover_image : images/hexo.png
pid: embedded-CSS-or-Javascript-to-post
---

## Hexo CSS JS Front-matterから自動で読み込む
![html](https://burturki.sirv.com/diy/html.png?w=300)

>  Hexoで記事ごとに適用するCSSやJSファイルをFront-matterから自動で読み込む
>
> https://pixelog.net/post/xumh8c5si7/

## 記事mdで外部md読み込み

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2$ npm install hexo-include-markdown --save
+ hexo-include-markdown@1.0.2
added 1 package from 1 contributor, removed 1 package and audited 532 packages in 8.339s

6 packages are looking for funding
  run `npm fund` for details

found 2 low severity vulnerabilities
  run `npm audit fix` to fix them, or `npm audit` for details
```

source/_posts/hello-world.md

```
---
title: Hello World
---

## include sample

Please load another markdown file with the following code.

<!-- md template.md -->
```

source/_ template/template.md

```
### include me ?

Here is the `template.md`'s content . This content is read from an external markdown file.
```


## 任意のURLの貼り付け

指定したURLの情報を展開し、カード形式に出力してくれるプラグイン。

> https://github.com/minamo173/hexo-tag-link-preview

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2/themes/tranquilpeak$ npm install hexo-tag-link-preview
npm WARN react-flip-move@2.9.14 requires a peer of react@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@2.9.14 requires a peer of react-dom@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.

+ hexo-tag-link-preview@1.2.4
added 24 packages from 56 contributors and audited 691 packages in 6.958s

13 packages are looking for funding
  run `npm fund` for details

found 95 vulnerabilities (56 low, 6 moderate, 33 high)
  run `npm audit fix` to fix them, or `npm audit` for details
```



```
hamkaz@debian1-de-kaz:~/js/hexo/blog2/themes/tranquilpeak$ npm audit fix
npm WARN deprecated request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142

> node-sass@4.14.1 install /home/hamkaz/js/hexo/blog2/themes/tranquilpeak/node_modules/node-sass
> node scripts/install.js

Cached binary found at /home/hamkaz/.npm/node-sass/4.14.1/linux-x64-72_binding.node

> node-sass@4.14.1 postinstall /home/hamkaz/js/hexo/blog2/themes/tranquilpeak/node_modules/node-sass
> node scripts/build.js

Binary found at /home/hamkaz/js/hexo/blog2/themes/tranquilpeak/node_modules/node-sass/vendor/linux-x64-72/binding.node
Testing binary
Binary is fine
npm WARN react-flip-move@2.9.14 requires a peer of react@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@2.9.14 requires a peer of react-dom@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.

+ jquery@3.5.1
+ jsdom@16.2.2
+ node-sass@4.14.1
+ gitalk@1.6.2
added 18 packages from 17 contributors, removed 17 packages, updated 56 packages and moved 1 package in 14.18s

7 packages are looking for funding
  run `npm fund` for details

fixed 95 of 95 vulnerabilities in 691 scanned packages
```



```
hamkaz@debian1-de-kaz:~/js/hexo/blog2/themes/tranquilpeak$ npm audit
                                                                                
                       === npm audit security report ===                        
                                                                                
found 0 vulnerabilities
 in 692 scanned packages
```

Usage

```
{% linkPreview https://www.amazon.com/ _blank nofollow %}
```

.md

そのまま貼り付け



hexo generate

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2$ hexo generate
INFO  Start processing
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
Nunjucks Error:  [Line 3, Column 4] unknown block tag: linkPreview
    =====               Context Dump               =====
    === (line number probably different from source) ===
  1 | {% asset_img kiri-no-ii.jpg 'キリのいい' %}
  2 | 
  3 | {% linkPreview https://www.amazon.com/ _blank nofollow %}
    =====             Context Dump Ends            =====
    at formatNunjucksError (/home/hamkaz/js/hexo/blog2/node_modules/hexo/lib/extend/tag.js:99:13)
    at /home/hamkaz/js/hexo/blog2/node_modules/hexo/lib/extend/tag.js:121:34
    at tryCatcher (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/util.js:16:23)
    at Promise._settlePromiseFromHandler (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/promise.js:547:31)
    at Promise._settlePromise (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/promise.js:604:18)
    at Promise._settlePromise0 (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/promise.js:649:10)
    at Promise._settlePromises (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/promise.js:725:18)
    at _drainQueueStep (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/async.js:93:12)
    at _drainQueue (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/async.js:86:9)
    at Async._drainQueues (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/async.js:102:5)
    at Immediate.Async.drainQueues [as _onImmediate] (/home/hamkaz/js/hexo/blog2/node_modules/bluebird/js/release/async.js:15:14)
    at processImmediate (internal/timers.js:456:21)
```



npm install

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2/themes/tranquilpeak$ npm install
npm WARN react-flip-move@2.9.14 requires a peer of react@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@2.9.14 requires a peer of react-dom@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.

audited 692 packages in 4.554s

15 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```



npm install -f

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2/themes/tranquilpeak$ npm install -f
npm WARN using --force I sure hope you know what you are doing.
npm WARN react-flip-move@2.9.14 requires a peer of react@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@2.9.14 requires a peer of react-dom@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.

audited 692 packages in 4.527s

15 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```



どうもreact-flip-moveがないと警告

そこでインストール

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2/themes/tranquilpeak$ npm i -S react-flip-move
npm WARN react-flip-move@2.9.14 requires a peer of react@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@2.9.14 requires a peer of react-dom@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@3.0.4 requires a peer of react@>=16.3.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@3.0.4 requires a peer of react-dom@>=16.3.x but none is installed. You must install peer dependencies yourself.

+ react-flip-move@3.0.4
added 1 package from 1 contributor, updated 1 package and audited 693 packages in 4.597s

15 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```



どうもreactとreact-domがないと警告

そこでreactをインストール

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2/themes/tranquilpeak$ npm install react --save
npm WARN react-flip-move@2.9.14 requires a peer of react@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@2.9.14 requires a peer of react-dom@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@3.0.4 requires a peer of react-dom@>=16.3.x but none is installed. You must install peer dependencies yourself.

+ react@16.13.1
added 1 package and audited 694 packages in 4.737s

15 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

次にreact-domをインストール

```
hamkaz@debian1-de-kaz:~/js/hexo/blog2/themes/tranquilpeak$ npm install react-dom --save
npm WARN react-flip-move@2.9.14 requires a peer of react@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.
npm WARN react-flip-move@2.9.14 requires a peer of react-dom@0.13.x || 0.14.x || 15.x.x but none is installed. You must install peer dependencies yourself.

+ react-dom@16.13.1
added 2 packages and audited 696 packages in 4.993s

15 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```