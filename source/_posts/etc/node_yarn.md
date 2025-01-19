---
title: 'YarnによるNodejsのパッケージ管理'
date: 2020-05-16 17:30:00
tags:
- Nodejs
- パッケージ管理
- yarn
categories:
- '1 LinuxとNodejsでプログラミング'
- 'c) Node.jsをインストールする'
excerpt: 'Node.jsのパッケージ管理npmとYarnを使ってNode.jsのパッケージ管理方法を理解するとともに、npm install時に発生する警告やエラーメッセージの回避方法について調べてみました。'
cover_image : images/nodejs.png
pid: package_npm_yarn
---

## npmとyarn - Node.jsのパッケージ管理
![nodejs](https://burturki.sirv.com/diy/nodejs.png?w=300)

JavaScriptの実行環境Node.jsでは、Node.js上で動作するプラグインやツールなどをパッケージ管理npmやyarnで管理します。

npmとはNode.jsのデフォルトのパッケージ管理で、２つの意味を持ちます。一つはNode.jsのオンラインリポジトリを指し、もう一つはコマンドラインツールnpmを指します。

Node.jsのパッケージはコマンドラインツールnpmを使ってインストールします。npm自体はNode.jsをインストールすると同時にインストールされます。

> [Node.js公式サイト：What is npm?](https://nodejs.org/en/knowledge/getting-started/npm/what-is-npm/)

npmのオンラインリポジトリでは、Node.jsで開発されたアプリケーションやプラグイン・ツールをパッケージ管理します。コミュニティや個人で開発されたオープンソースパッケージが利用できます。

Node.jsの普及に伴い、npmによるパッケージ管理はインストール速度やセキュリティといった点で問題があることが分かりました。

こうしたnpmの諸問題を解決するため、Facebook、GoogleなどによってYarnというパッケージ管理方法が新たに発表されました。

> [参考サイト：Yarn：Facebook発のパッケージマネジャーはnpmに代わるスタンダードになるか](https://www.webprofessional.jp/yarn-vs-npm/)

Node.jsのパッケージ管理であるnpmとyarnを正しく理解するため、調べてみました。

## Node.jsのパッケージ管理 npm

Node.jsの標準のパッケージ管理方法はnpmです。

`npm install`コマンドでインストールされたパッケージは管理ファイルとしてpackage.jsonで管理されます。

package.jsonはパッケージのインストール履歴として機能し、*プロジェクトのルートディレクトリ*に配置されます。

初めてのインストール時にpackage.jsonが作成され、新たなパッケージの追加・既存のパッケージの更新時には現存するpackage.jsonが追記されます。

## もう一つのパッケージ管理 Yarn

Node.jsのパッケージ管理は、yarnコマンドで行うことができます。

> [Yarnとは](https://qiita.com/lelouch99v/items/c97ff951ca31298f3f24)

Facebookの提供するNode.jsパッケージ管理で、npmのpackage.jsonと互換性があります。yarnコマンド実行後は、ファイルyarn.lockが作成されます。

## Node.jsのもう一つのパッケージ管理 Yarn

Yarnはnpmのパッケージ管理方法と互換性を持ちます。パッケージの追加・更新時には既存のpackage.jsonに追記するとともに、yarn.lockファイルを生成して、yarn側でもパッケージ管理を行います。

> [参考サイト：Yarnとは](https://qiita.com/lelouch99v/items/c97ff951ca31298f3f24)

## npm install実行時に見かけるエラーと警告

npm install実行時にはさまざまな警告やエラーメッセージを見かけます。ここでは、これらの警告・エラーメッセージへの基本的な対処方法を調べました。

### "found 1 low severity vulnerability"

インストールしたパッケージモジュールに脆弱性がある場合、配布元から報告された脆弱性に関するメッセージが表示されます。

脆弱性（vulnerability）に関するメッセージが表示された場合、`npm audit`を実行します。このコマンドでは、脆弱性のあるパッケージのリストアップと、解決方法の有無が確認できます。

```
                                                                          
                       === npm audit security report ===                        
                                                                                
┌──────────────────────────────────────────────────────────────────────────────┐
│                                Manual Review                                 │
│            Some vulnerabilities require your attention to resolve            │
│                                                                              │
│         Visit https://go.npm.me/audit-guide for additional guidance          │
└──────────────────────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ Low           │ Prototype Pollution                                          │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ minimist                                                     │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=0.2.1 <1.0.0 || >=1.2.3                                    │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ hexo                                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ hexo > swig-templates > optimist > minimist                  │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://npmjs.com/advisories/1179                            │
└───────────────┴──────────────────────────────────────────────────────────────┘
found 1 low severity vulnerability in 253 scanned packages
  1 vulnerability requires manual review. See the full report for details.
```

上記のメッセージでは、optimistという呼び出し元モジュールがminimistの古いバージョンに依存しているため、警告メッセージを発しています。

静寂性に関する警告が表示された場合、`npm audit`コマンドを実行して、解決方法の存在を確認します。

* a) 解決コマンドが表示される場合
* b) 解決コマンドが表示されない場合
* c) 対策中の場合

**a) 解決コマンドが表示される場合**

脆弱性に対する解決方法が公開されている場合、次のようなメッセージが表示されます。

```
=== npm audit security report ===
# Run  npm update lodash --depth 2  to resolve 1 vulnerability
```

表示されたコマンドを実行すると、解決済みのモジュールに更新されます。

**b) 解決に導くコマンドが表示されない場合**

npm audit fixを実行するとモジュールがバージョンアップされ、脆弱性の程度を下げることができる場合があります。

**c) 対策中の場合**

対策中の場合にはセキュリティレポートが表示されません。低度の脆弱性であれば、配布元から解決方法が提示されるまでそのまま運用しますが、セキュリティに関する注意が必要になります。

* ※ 注意事項として、未知の脆弱性に対しては`npm audit`で解決できません。


### "npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents..."

インストールするパッケージによっては、OS依存ファイルに対する警告メッセージが表示される場合があります。下記の例ではfseventsにおいてMac OSに依存するモジュールを警告しています。

```
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.13: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
```

`OPTIONAL DEPENDENCY`と表示された場合、Linuxではインストールの必要がないモジュール（オプションモジュール）を除外できます。

> [参考サイト：How to solve npm install throwing fsevents warning on non-Mac OS?](https://stackoverflow.com/questions/46929196/how-to-solve-npm-install-throwing-fsevents-warning-on-non-mac-os)

※ FoggyDay Oct 14'19 at 16:17のコメントを参照

対策としては、OPTIONAL DEPENDENCYと表示されたオプションモジュールを除外インストールするため、`npm install -f`コマンドを実行します。

### "npm fund"

npm fundとはパッケージの開発者への寄付を募るメッセージです。npm fundコマンドを実行すると、どのパッケージが寄付対象であるか示されます。

## まとめ

npmとyarnはどちらか一方を使用しなければならないというわけではなく、混在して使用できます。

Yarnを用いると、パッケージモジュールのインストールが早くなり、インストール時のスクリプト実行が抑えられてセキュリティが確保されることから、yarnを使う動きが広がっているようです。
