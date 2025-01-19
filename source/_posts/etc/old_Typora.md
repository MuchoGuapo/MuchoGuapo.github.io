---
title: 'マークダウンエディタ Typora'
date: 2020-05-16 17:30:00
tags:
- マークダウンエディタ
- Typora
categories:
- '1 LinuxとNodejsでプログラミング'
- 'a) ツールをインストールする'
excerpt: 'マークダウンエディタTyporaを、Linux Debian10にインストールしました。インストールに必要な手順を解説します。'
cover_image : images/typora.png
pid: editor_typora
---

## マークダウンエディタ - Typora
Typoraは、Windows, Mac, Linuxのプラットフォーム上で使用できるマークダウンエディタで、シンプルで洗練されたマークダウンエディタです。
![typora](https://burturki.sirv.com/diy/typora.png?w=300)

> https://typora.io/

マークダウン専用のエディタを用意する目的で、今回Typoraをインストールしました。

**Typora**

`
aptインストール : wget, apt-key, add-apt-repository, apt-get update, apt-get install
`

## インストールに必要なコマンド

add-apt-repository、aptまたはapt-get、apt-key、curl

## インストール手順

1. コマンドwgetをインストール
2. Typoraの認証キーをインストール
3. コマンドadd-apt-repositoryをインストール
4. リポジトリにTyporaを追加
5. リポジトリを更新
6. Typoraをインストール

## インストール方法

### 1. コマンドwgetをインストール

```bash
# Using Debian, as root
sudo apt-get install wget
```

### 2. Typoraの認証キーをインストール

```bash
# Using Debian, as root
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
```

### 3. コマンドadd-apt-repositoryをインストール

```bash
# Using Debian, as root
sudo apt-get install software-properties-common
```

### 4. OSのリポジトリに追加

```bash
# Using Debian, as root
sudo add-apt-repository 'deb https://typora.io/linux ./'
```

### 5. OSのリポジトリを更新

```bash
# Using Debian, as root
sudo apt-get update
```

### 6. Typoraをインストール

```bash
# Using Debian, as root
sudo apt-get install typora
```

## まとめ

Typoraは、Minimalと名付けられた通りとてもシンプルで洗練された感じのマークダウンエディタです。

文書の編集とプレビューが同時にでき、目次の字下げもわかりやすく、内容に集中して文書を作成できます。
