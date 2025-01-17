---
title: 'Netlifyによるホスティング'
date: 2020-07-07 17:30:00
tags:
- ホスティング
- 'GitHub Pages'
categories:
- '3 ブログの公開と管理方法'
- 'a) 準備作業'
excerpt: 'GitHub Pagesでホスティング、ブログ公開'
cover_image : github.png
pid: hosting-github-pages
---

# hexoで新規にブログを立ち上げ、テーマ導入し、githubPages
![netlify](https://burturki.sirv.com/diy/netlify.png?w=300)

# github pageの作り方

### 作業

1. リモートで公開リポジトリを作成
2. ローカルでファイル作成
3. git add, commit, push
4. 確認作業



### 1. リモートで公開リポジトリを作成

github上の作業



### 2. ローカルでファイル作成

#### ローカルにコピー

```
hamkaz@debian1-de-kaz:~/git$ git clone https://github.com/HamKaz/HamKaz.github.io
Cloning into 'HamKaz.github.io'...
warning: You appear to have cloned an empty repository.
```

#### フォルダができる

```
hamkaz@debian1-de-kaz:~/git$ ls
HamKaz.github.io  Org_Landscape  blog  テストソース_プラグイン  テストソース_英語  テストソース_日本語
```

#### ローカルに下りる

```
hamkaz@debian1-de-kaz:~/git$ cd H*
```

#### ローカルでファイル作成またはファイルコピー

手動作業



### 3. git add, commit, push確認作業

#### ブランチ確認

```
hamkaz@debian1-de-kaz:~/git/HamKaz.github.io$ git branch
* master
```

#### ログ確認

```
hamkaz@debian1-de-kaz:~/git/HamKaz.github.io$ git log
commit 76e63b14dc6e11201ffcc21bd49ff39dd336a26d (HEAD -> master)
Author: hamkaz <hamak88@gmail.com>
Date:   Tue Jun 30 19:25:04 2020 +0900

    2020June30-1
```

#### git add

```
hamkaz@debian1-de-kaz:~/git/HamKaz.github.io$ git add -A
```

#### git commit

``` 
hamkaz@debian1-de-kaz:~/git/HamKaz.github.io$ git commit -m 2020June30
[master (root-commit) a3de583] 2020June30
 67 files changed, 11337 insertions(+)
 create mode 100644 about/index.html
 create mode 100644 archives/2017/06/index.html
 create mode 100644 archives/2017/index.html
 create mode 100644 archives/2018/06/index.html
 create mode 100644 archives/2018/index.html
 create mode 100644 archives/2019/06/index.html
 create mode 100644 archives/2019/index.html
 create mode 100644 archives/2020/02/index.html
 create mode 100644 archives/2020/03/index.html
 create mode 100644 archives/2020/index.html
 create mode 100644 archives/index.html
 create mode 100644 categories/concept/index.html
 create mode 100644 categories/concept/thinking/index.html
 create mode 100644 categories/english/index.html
 create mode 100644 categories/english/reading/index.html
 create mode 100644 categories/english/speaking/index.html
 create mode 100644 categories/english/writing/index.html
 create mode 100644 categories/index.html
 create mode 100644 concept/thinking/Pole_Positon_for_blogger/index.html
 create mode 100644 concept/thinking/What_is_the_strategy_of_making_simple_blog/index.html
 create mode 100644 contact/index.html
 create mode 100644 css/styles.css
 create mode 100644 english/reading/What_is_the_Best_Way/index.html
 create mode 100644 english/speaking/How_to_set_up_this_theme/index.html
 create mode 100644 english/writing/Welcome_to_Hexo-theme-simple/index.html
 create mode 100644 fonts/SoukouMincho-Font/LICENSE_OFL.txt
 create mode 100644 fonts/SoukouMincho-Font/ReadMe.txt
 create mode 100644 fonts/SoukouMincho-Font/SoukouMincho-Font.zip
 create mode 100644 fonts/SoukouMincho-Font/SoukouMincho.ttf
 create mode 100644 fonts/TanukiMagic/TanukiMagic.ttf
 create mode 100644 fonts/TanukiMagic/TanukiMagic_1_21.zip
 create mode 100644 fonts/TanukiMagic/readme.txt
 create mode 100644 fonts/chogokubosogothic/chogokubosogothic.zip
 create mode 100644 fonts/chogokubosogothic/chogokubosogothic_5.ttf
 create mode 100644 fonts/chogokubosogothic/mplus-TESTFLIGHT-059/LICENSE_E
 create mode 100644 fonts/chogokubosogothic/mplus-TESTFLIGHT-059/LICENSE_J
 create mode 100644 fonts/chogokubosogothic/mplus-TESTFLIGHT-059/README_E
 create mode 100644 fonts/chogokubosogothic/mplus-TESTFLIGHT-059/README_J
 create mode 100644 fonts/nagomigokubosogothic/NagomiGokubosoGothic-ExtraLight.otf
 create mode 100644 fonts/nagomigokubosogothic/nagomigokubosogothic.zip
 create mode 100644 fonts/nagomigokubosogothic/readme.txt
 create mode 100644 images/a.jpg
 create mode 100644 images/about.jpg
 create mode 100644 images/b.jpg
 create mode 100644 images/c.jpg
 create mode 100644 images/contact.jpg
 create mode 100644 images/d.jpg
 create mode 100644 images/default.jpg
 create mode 100644 images/e.jpg
 create mode 100644 images/r1.jpg
 create mode 100644 images/r2.jpg
 create mode 100644 images/r3.jpg
 create mode 100644 index.html
 create mode 100644 page/2/index.html
 create mode 100644 recommend1/index.html
 create mode 100644 recommend2/index.html
 create mode 100644 recommend3/index.html
 create mode 100644 search.xml
 create mode 100644 sitemap.xml
 create mode 100644 tags/SEO/index.html
 create mode 100644 tags/award/index.html
 create mode 100644 tags/blogger/index.html
 create mode 100644 tags/index.html
 create mode 100644 tags/marketing/index.html
 create mode 100644 tags/party/index.html
 create mode 100644 tags/sample/index.html
 create mode 100644 tags/travel/index.html
```

#### git push

```
hamkaz@debian1-de-kaz:~/git/HamKaz.github.io$ git push -u origin master
Username for 'https://github.com': HamKaz
Password for 'https://HamKaz@github.com': 
Enumerating objects: 120, done.
Counting objects: 100% (120/120), done.
Delta compression using up to 4 threads
Compressing objects: 100% (89/89), done.
Writing objects: 100% (120/120), 65.04 MiB | 9.01 MiB/s, done.
Total 120 (delta 33), reused 0 (delta 0)
remote: Resolving deltas: 100% (33/33), done.
To https://github.com/HamKaz/HamKaz.github.io
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

#### 二回目のgit add

```
hamkaz@debian1-de-kaz:~/git/HamKaz.github.io$ git add -A
```

#### 二回目のgit commit

```
hamkaz@debian1-de-kaz:~/git/HamKaz.github.io$ git commit -m 2020June30-1
[master f06f292] 2020June30-1
 38 files changed, 259 insertions(+), 259 deletions(-)
```

#### 二回目のgit push

```
hamkaz@debian1-de-kaz:~/git/HamKaz.github.io$ git push -u origin master
Username for 'https://github.com': HamKaz
Password for 'https://HamKaz@github.com': 
Enumerating objects: 154, done.
Counting objects: 100% (154/154), done.
Delta compression using up to 4 threads
Compressing objects: 100% (53/53), done.
Writing objects: 100% (83/83), 8.96 KiB | 1019.00 KiB/s, done.
Total 83 (delta 38), reused 0 (delta 0)
remote: Resolving deltas: 100% (38/38), completed with 17 local objects.
To https://github.com/HamKaz/HamKaz.github.io
   a3de583..f06f292  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```



### 4. アクセスして確認


# github pages サブディレクトリ作成

ユーザ名.github.ioを作成

公開リポジトリ作成

github pages設定



# hexoで作ったサイトの様々な公開方法

> https://tech.qookie.jp/posts/hexo-deploy-github-pages-fast/



### 記事をローカルPCで管理 -> GitHub Pagesにデプロイ、公開

ローカルでジェネレート + git push の代わりに -> ローカルでdeployコマンド一発でgithub Pageへデプロイ、公開

ソースはローカルPCで管理、公開ディレクトリはGitHubで管理



あらかじめ入れておくもの

```
npm install hexo-deployer-git
```



GitHub Pages（トップドメイン）

```yaml
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://HamKaz.github.io
root: /
```

```yaml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/HamKaz/HamKaz.github.io.git
  branch: master
```



GitHub Pages（サブ）

```yaml
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://HamKaz.github.io/sample-page
root: /sample-page/
```

```yaml
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/HamKaz/sample-page.git
  branch: master
```



### 記事をGitHubで管理 -> GitHub Pagesにデプロイ、公開

デプロイ（GitHubで管理）

https://tech.qookie.jp/posts/hexo-deploy-github-pages-backup-version/



## 1. ~/ 

### a. hexo init

```
hamkaz@debian1-de-kaz:~/git$ hexo init okosi.net
INFO  Cloning hexo-starter https://github.com/hexojs/hexo-starter.git
Cloning into '/home/hamkaz/git/okosi.net'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 168 (delta 0), reused 0 (delta 0), pack-reused 165
Receiving objects: 100% (168/168), 32.45 KiB | 325.00 KiB/s, done.
Resolving deltas: 100% (79/79), done.
Submodule 'themes/landscape' (https://github.com/hexojs/hexo-theme-landscape.git) registered for path 'themes/landscape'
Cloning into '/home/hamkaz/git/okosi.net/themes/landscape'...
remote: Enumerating objects: 8, done.        
remote: Counting objects: 100% (8/8), done.        
remote: Compressing objects: 100% (6/6), done.        
remote: Total 1071 (delta 1), reused 5 (delta 1), pack-reused 1063        
Receiving objects: 100% (1071/1071), 3.22 MiB | 2.28 MiB/s, done.
Resolving deltas: 100% (586/586), done.
Submodule path 'themes/landscape': checked out '73a23c51f8487cfcd7c6deec96ccc7543960d350'
INFO  Install dependencies
yarn install v1.22.4
info No lockfile found.
[1/4] Resolving packages...
warning hexo > hexo-log > hexo-bunyan@2.0.0: Please see https://github.com/hexojs/hexo-bunyan/issues/17
warning hexo-renderer-stylus > stylus > css-parse > css > urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
warning hexo-renderer-stylus > stylus > css-parse > css > source-map-resolve > urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
warning hexo-renderer-stylus > stylus > css-parse > css > source-map-resolve > resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated
[2/4] Fetching packages...
info fsevents@2.1.3: The platform "linux" is incompatible with this module.
info "fsevents@2.1.3" is an optional dependency and failed compatibility check. Excluding it from installation.
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
Done in 7.81s.
INFO  Start blogging with Hexo!
```



## 2. ~/okosi.net/

### a. hexo generate / hexo server

動作確認

```
hamkaz@debian1-de-kaz:~/git$ cd okosi.net

hamkaz@debian1-de-kaz:~/git/okosi.net$ heg
INFO  Start processing
INFO  Files loaded in 209 ms
INFO  Generated: index.html
INFO  Generated: archives/index.html
INFO  Generated: fancybox/blank.gif
INFO  Generated: fancybox/jquery.fancybox.css
INFO  Generated: fancybox/jquery.fancybox.js
INFO  Generated: fancybox/jquery.fancybox.pack.js
INFO  Generated: fancybox/fancybox_loading.gif
INFO  Generated: fancybox/fancybox_loading@2x.gif
INFO  Generated: fancybox/fancybox_sprite@2x.png
INFO  Generated: fancybox/fancybox_overlay.png
INFO  Generated: archives/2020/07/index.html
INFO  Generated: fancybox/fancybox_sprite.png
INFO  Generated: archives/2020/index.html
INFO  Generated: css/fonts/FontAwesome.otf
INFO  Generated: js/script.js
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.css
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.js
INFO  Generated: fancybox/helpers/jquery.fancybox-media.js
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.css
INFO  Generated: css/fonts/fontawesome-webfont.svg
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.js
INFO  Generated: css/style.css
INFO  Generated: fancybox/helpers/fancybox_buttons.png
INFO  Generated: css/fonts/fontawesome-webfont.eot
INFO  Generated: css/fonts/fontawesome-webfont.woff
INFO  Generated: css/images/banner.jpg
INFO  Generated: css/fonts/fontawesome-webfont.ttf
INFO  Generated: 2020/07/08/hello-world/index.html
INFO  28 files generated in 590 ms

hamkaz@debian1-de-kaz:~/git/okosi.net$ hes
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
^C INFO  Farewell
```

### b. git init

```
hamkaz@debian1-de-kaz:~/git/okosi.net$ git init
Initialized empty Git repository in /home/hamkaz/git/okosi.net/.git/
```

-> 設定用ディレクトリ .gitが作成される



## 3. ~/okosi.net/themes

### a. git submodule add

自作テーマ導入

```
hamkaz@debian1-de-kaz:~/git/okosi.net$ cd themes

hamkaz@debian1-de-kaz:~/git/okosi.net/themes$ git submodule add git@github.com:HamKaz/hexo-theme-simple.git
Cloning into '/home/hamkaz/git/okosi.net/themes/hexo-theme-simple'...
remote: Enumerating objects: 503, done.
remote: Total 503 (delta 0), reused 0 (delta 0), pack-reused 503
Receiving objects: 100% (503/503), 29.05 MiB | 2.35 MiB/s, done.
Resolving deltas: 100% (280/280), done.
```

-> hexoテーマをthemesディレクトリに「サブモジュール」として導入（クローンされるとともに、設定ファイル.gitmodulesができる）

```
hamkaz@debian1-de-kaz:~/git/okosi.net/themes$ ls
hexo-theme-simple  landscape
```



## 4. ~/okosi.net/

### a. _config.ymlを修正

```
hamkaz@debian1-de-kaz:~/git/okosi.net/themes$ cd ..

hamkaz@debian1-de-kaz:~/git/okosi.net$ nano _config.yml
```

### b. publicディレクトリを消去 -> 再generate

```
hamkaz@debian1-de-kaz:~/git/okosi.net$ hexo clean
INFO  Deleted database.
INFO  Deleted public folder.

hamkaz@debian1-de-kaz:~/git/okosi.net$ touch db.json

hamkaz@debian1-de-kaz:~/git/okosi.net$ hexo generate
INFO  Start processing
INFO  Files loaded in 149 ms
INFO  Generated: index.html
INFO  Generated: archives/index.html
INFO  Generated: images/favicon.png
INFO  Generated: archives/2020/07/index.html
INFO  Generated: archives/2020/index.html
INFO  Generated: images/default.jpg
INFO  Generated: css/styles.css
INFO  Generated: 2020/07/08/hello-world/index.html
INFO  8 files generated in 46 ms

hamkaz@debian1-de-kaz:~/git/okosi.net$ hexo server
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
^C INFO  Have a nice day
```

### b. git add

```
hamkaz@debian1-de-kaz:~/git/okosi.net$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   .gitmodules
	new file:   themes/hexo-theme-simple

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
	_config.yml
	package.json
	scaffolds/
	source/
	themes/landscape/
	yarn.lock
```

### c. git add -> git commit

変更履歴を追加、確定

```
hamkaz@debian1-de-kaz:~/git/okosi.net$ git add -A

hamkaz@debian1-de-kaz:~/git/okosi.net$ git commit -m 2020July08-3
[master 329129f] 2020July08-3
 1 file changed, 1 insertion(+), 1 deletion(-)
```

### d. remote add origin

リモート先（接続先）を指定する

```
hamkaz@debian1-de-kaz:~/git/okosi.net$ git remote add origin https://github.com/HamKaz/okosi.net
```

### e. githubにリモートリポジトリを作成する

### f. git push

```
hamkaz@debian1-de-kaz:~/git/okosi.net$ git push origin master
Username for 'https://github.com': HamKaz
Password for 'https://HamKaz@github.com': 
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 296 bytes | 296.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/HamKaz/okosi.net
   c5edc60..329129f  master -> master
```

