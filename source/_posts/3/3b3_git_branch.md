---
title: 'Git基礎[3] ブランチの管理'
date: 2020-06-29 17:30:00
tags:
- ブランチ
- フェッチ
- マージ
categories:
- '3 ブログの公開と管理方法'
- 'b) gitのソース管理'
excerpt: 'リポジトリ運用とブランチ操作。プル（フェッチとマージ）'
cover_image : github.png
pid: git-branch
---

## はじめに
いきなりコミットとプッシュしないで、他のブランチで様子を見る。
![github](https://burturki.sirv.com/diy/github.png?w=300)

プル（フェチしてマージ）して、コミットし直して、あらためてプッシュする。

### 1. 作業ブランチ作成
```
$ git branch develop
```

### 現在のブランチを確認
```
git branch
  develop
* master
```

### ブランチの切り替え
```
$ git checkout develop
```

### 状態確認（ステータス）
```
$ git status
```

### ブランチ間の差分
```
$ git diff
```

### 2. ブランチ統合
ローカルでフェッチしてマージし、コミット情報をリモートにあげる。

> 考え方
>
> https://backlog.com/ja/git-tutorial/stepup/05/

まずは、ローカルPCのdevelopブランチからmasterブランチへ統合（merge）を行う。

リモートサーバーのすべてのファイルの変更履歴を取得（フェチ）して、ローカルPCに取り込みマージすることをプルと言います。

環境を取り込んでマージする
git pull -> git add -> git commit -> git status -> git push

```
git pull
git add index.html
git commit -m "add new file"
git status
git push
```