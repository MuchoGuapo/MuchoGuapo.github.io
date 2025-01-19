---
title: 'Node.jsのパッケージ管理npmを理解する'
date: 2020-05-16 17:30:00
tags:
- Linux
- Debian
- Node.js
- パッケージ管理
- 'package manager'
- npm
- error
- エラー
categories:
- '1 LinuxとNodejsでプログラミング'
- 'c) Node.jsをインストールする'
excerpt: 'Node.jsのパッケージ管理は、npmとYarnになります。今回npmとYarnをインストールし、Node.jsのパッケージ管理への理解を深めます。またnpmコマンド実行時の警告・エラー回避方法についても調べました。'
cover_image : images/npm.jpg
pid: package_manager_npm
---

## npm - Node.jsのパッケージ管理
![nodejs](https://burturki.sirv.com/diy/nodejs.png?w=300)

npmには、オンラインリポジトリと、パッケージ管理のコマンドラインツールの２つを指す。

> [](https://nodejs.org/en/knowledge/getting-started/npm/what-is-npm/)

今回、コマンドラインツールとしてのnpmについて説明します。

## Node.jsのパッケージ管理 npm

Node.jsの標準のパッケージ管理は、npmコマンドで行います。

npmでは、`npm install`コマンドでインストールした場合、*プロジェクトのルートディレクトリ*
のpackage.jsonというファイルにインストールしたプラグインが追記されます。

## コマンドラインnpm実行時の警告・エラー

### 1. npm install - "npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents..."

**状況**

```
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.13: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
```

> [How to solve npm install throwing fsevents warning on non-Mac OS?](https://stackoverflow.com/questions/46929196/how-to-solve-npm-install-throwing-fsevents-warning-on-non-mac-os)

**原因**

MacOS限定のモジュールがnpm installによって読み込まれた。

**対策**

`OPTIONAL DEPENDENCY`と表示されて必要がないオプションモジュールなので、npm installから除外します。

**対応方法**

FoggyDay Oct 14'19 at 16:17のコメントを参照して、次のコマンドを実行します。

```bash
npm install -f
```

### 2. npm install - npm fundの表示の意味は？

パッケージの開発者への寄付を募るメッセージであり、npm fundコマンドを実行すると、どのパッケージが寄付対象であるか示してくれる。

### 3. npm install - "found 1 low severity vulnerability"

npm installコマンド実行時に、脆弱性に関する警告が発生する。npm auditコマンドで、脆弱性のあるパッケージをリストアップする。

**状況**

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

**原因**

呼び出し元のoptimistが、minimistの古いバージョンに依存しているため

**対策**

npm auditを実行して解決方法が存在するか確認する。

１．脆弱性に関する解決方法が公開されている場合、解決のためのコマンドが表示されるため、コマンドを実行して解決する（例）。

```
=== npm audit security report ===
# Run  npm update lodash --depth 2  to resolve 1 vulnerability
```

２．解決方法がない場合、npm audit fixを実行してセキュリティパッチを当てるか、それでも解決しない低度の脆弱性であれば、そのままにしておく。

そもそも未知の脆弱性が存在する場合もあり、npm auditで解決できるとは限らない。

 



```bash
npm install -g yarn
npm install yarn
yarn install
yarn upgrade
```
