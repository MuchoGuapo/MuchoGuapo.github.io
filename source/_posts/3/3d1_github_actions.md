---
title: 'GitHub Actions[1] GitHub Actionsによるデプロイ自動化'
date: 2024-01-17 19:00:00
tags:
- GitHub_Actions
- デプロイ自動化
- ワークフロー
categories:
- '3 ブログの公開と管理方法'
- 'd) ブログ運用の効率化'
excerpt: 'ブログのデプロイ作業では、ローカルPCからリモートサーバーへのプッシュ作業が特に手間でした。ソースコードをCommitするたびにリモートのGitHub Pagesに直接デプロイできるようGitHub Actionsによるデプロイ自動化を試みました'
cover_image : github.png
pid: deploy-automation-github-actions
---

## はじめに
ブログのデプロイ作業の自動化を、GitHub Actionsで実現しました。サブモジュールの取扱についても学びました。 
![github](https://burturki.sirv.com/diy/github.png?w=300)

```
手順
1. GitHub Pagesの段取り
2. GitHub ActionsでリモートサーバーのVMでHexoを実行する
3. サブモジュールの取扱はsshでなく、httpsで参照すべし
```

## 1. GitHub Pagesの段取り
### GitHub Pagesは、１つのアカウントに付き１つのページ
ユーザー名.github.ioというリポジトリをまずは作成する。

### GitHub Pagesのビルドとデプロイ方法:GitHub Actionsに変更
デフォルトでは、GitHub Pagesのビルドとデプロイはブランチのソースからのデプロイとなっている。
ソースの変更を確定（コミット）するたびに、自動でビルドとデプロイするため、GitHub Actionsにビルドとデプロイの手順を記載する。

### GitHub Actionsは、ymlファイルを.github/workflows/において管理する
Hexo - デプロイ - GitHub Pagesを参考に、ビルドとデプロイのワークフローを記載したymlファイルを、~/.github/workflow/の下に作成する。

## 2. GitHub ActionsでリモートサーバーのVMでHexoを実行する
### VMによるワークフロー実行
GitHub Actionsでは、ymlファイルに記載されたワークフローをVM仮想マシン上で実行処理する。

### Node.jsのバージョン管理
Hexo本体だけでなく、テーマやプラグインなどを管理するpackage.jsonの依存関係の管理とともに、Node.jsのバージョン管理を行う。

## 3. サブモジュールの取扱はsshでなく、httpsで参照すべし
### 開発者としてのssh接続・使用者としてのhttps接続
GitHubのリポジトリは目的によりssh接続とhttps接続を使い分ける。
例えば、Hexoでブログのテーマを参照する場合、git cloneするが、これをサブモジュール登録する場合は必ずhttps接続でクローンする。
