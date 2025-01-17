---
title: 'Git基礎[2] クローンによる環境の再現'
date: 2020-06-24 17:30:00
tags:
- ソースコード管理
- クローン
categories:
- '3 ブログの公開と管理方法'
- 'b) gitのソース管理'
excerpt: 'クローン'
cover_image : github.png
pid: git-clone
---

## はじめに
リモートサーバーのファイルをまるごとコピーして新規にクローンを作るgit cloneコマンドについて説明します。 
![github](https://burturki.sirv.com/diy/github.png?w=300)

```
手順
1. リモートリポジトリ作成（GitHub）
2. リポジトリ操作（ローカルPC）
```

## 環境のクローン
リモートサーバーのファイルをまるごとコピーしてダウンロードし、新規ディレクトリを作成します。 

## エラーについて
**間違ったコミットとファイルを消す**
git clone -> git log -> git reset

git clone https://github.com/hamkaz/hexo-theme-simple
git reset
git log
git reset --hard



### gitダウンロード&クローン（複製）

```
hamkaz@debian1-de-kaz:~/git$ git clone https://github.com/HamKaz/hexo-theme-simpler.git
Cloning into 'hexo-theme-simpler'...
Username for 'https://github.com': hamkaz
Password for 'https://hamkaz@github.com': 
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (5/5), done.
```
