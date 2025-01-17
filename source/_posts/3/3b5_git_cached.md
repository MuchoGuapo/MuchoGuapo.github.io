---
title: 'Git基礎[5] gitでのキャッシュ管理'
date: 2022-10-09 10:00:00
tags:
- ソースコード管理
- キャッシュ削除
- git_cached
categories:
- '3 ブログの公開と管理方法'
- 'b) gitのソース管理'
excerpt: 'キャッシュ管理'
cover_image : github.png
pid: git-cached-git-ignore
---

## はじめに
リモートサーバーに新規ファイルをアップロードする方法について、gitコマンドcommit, pushを用いて設定します。 
![github](https://burturki.sirv.com/diy/github.png?w=300)

```
手順
1. リモートリポジトリ作成（GitHub）
2. リポジトリ操作（ローカルPC）
```

## 1. リポジトリ操作（ローカルPC）

### 作業ディレクトリ作成
ローカルPC内で、作業ディレクトリを作成し、作業ディレクトリでファイル作成・編集します。

### gitコマンドによる初期化
```
$ git init
Initialized empty Git repository in /home/user/blog/source/.git/
```

### リモートリポジトリとローカルの紐付け
```
$ git remote add origin https://github.com/user/blog-source.git
```

### 変更履歴の登録
```
$ git add -A
$ git add --all
```

### リモートの状態確認
修正ファイル、新規ファイルが確認できる。
```
$ git status
```

### コミット操作（変更の確定）
```
$ git commit -m 2020June30
$ git commit .
```

### コミット履歴（ログ）の確認
```
$ git log
```

### プッシュ操作（リモートサーバーへのアップロード）
```
$ git push origin master
```

### リモート（サーバー側）確認
GitHubへpushできていることを確認

## エラーについて
**push an existing repository from the command line**
既存のリポジトリにプッシュした場合、

**src refspec master does not match any**
新たなローカルPCからpushした場合、このエラーが発生

**fatal: Authentication failed for 'https://github.com/hamkaz/source-hamkaz.git/'**

https通信でのアップロードは現在サポートしなくなったので、認証エラー

-> git remote set-url origin git@github.com:

-> git remote set-url origin git@github.com:(ユーザー名)/(リポジトリ名).git

-->> git pullもgit pushもできるようになる。
