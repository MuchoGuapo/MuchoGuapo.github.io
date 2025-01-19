---
title: '[1] ハードウエア制御とネットワークのためのRaspberryPi'
date: 2024-01-18 12:00:00
tags:
- RaspberryPi 
- ハードウエア制御
- ネットワーク
categories:
- '4 IoT'
- 'a) RaspberryPi'
excerpt: 'IoT機器によるハードウェア制御とネットワーク連動を考えた場合、価格と市場流動性（入手しやすさ）からRaspberryPiが最も入手しやすい現状です。開発環境がLinuxをベースに整えられ、制御盤へ組み込みしやすく、低消費電力が特筆されるArmv7のRaspberryPiを検討しました。'
cover_image : linux.png
pid: raspberrypi-low-energy
---

## ハードウエア制御とネットワークのためのRaspberryPi
IoT機器によるハードウェア制御とネットワーク連動を考えた場合、価格と市場流動性（入手しやすさ）からRaspberryPiが最も入手しやすい現状です。
開発環境がLinuxをベースに整えられ、制御盤へ組み込みしやすく、低消費電力が特筆されるArmv7のRaspberryPiを検討しました。

![linux](https://burturki.sirv.com/diy/linux.png?w=300)

```
■話題
1. 消費電力が特筆されるArmv6世代のRaspberryPi Zero
2. 消費電力と開発環境、動作速度がバランスするArmv8世代のRaspberryPi 3 Model B+
3. 消費電力限界とその他の条件から見たRaspberryPi選定
```

## ものごとの始まり
オークションで中古のRaspberryPiを2台入手した。RaspberryPi Zero WH(PiZero), RaspberryPi 3 ModelB+(Pi3)である。

## 1. 消費電力が特筆されるArmv6世代のRaspberryPi Zero
まずはRaspberryPi Zero WH(PiZero)である。
Armv6世代のPiZeroは消費電力も少なく、RAMメモリの少なくて済む負荷の低い開発では軽快に動作した。

特にPythonは安定して動作し、ハードウエア制御やスクレイピングで、RaspberryPiそのものに慣れることができた。
特にスクレイピングでは、凝った抽出条件にも軽快な動作速度をみせた。

## 2. 消費電力と開発環境、動作速度がバランスするArmv8世代のRaspberryPi 3 Model B+
オークションで中古のRaspberryPiをもう1台入手した。RaspberryPi 3 ModelB+(Pi3)である。
LTEモジュール（HAT）とIoT専用SIMを動作させることが目的である。
Armv8世代のRaspberryPi 3 Model B+は、RAMメモリも1GBとなり、Node.jsを導入してRaspberryPiそのものに慣れることにした。

Pi3は、マルチコアでCPU負荷をかけられるが、同時に消費電力も上がる。
この世代から以降よく目にするのが、電力が足りないという文句である。
私もundervoltage警告がコンソール状に表示されるなど困った。
例えばアイドル時の電流で見てみると次の通り。

```
raspberry pi zero ; armv6 150mA
=> raspberry pi 3 model B+ ; armv7 460mA
```
ここに、負荷が高くなったときの突入電流を考えると、電源周りを強化しない限り、一時的に電圧降下が生じてしまう。

## 3. 消費電力限界とその他の条件から見たRaspberryPi選定
### 消費電力
PiZeroでは、512MBのRAMメモリと低消費電力のため、ちょっとした負荷の低いプログラム開発には十分である。
Pi3では、RAMメモリとマルチスレッドCPUのため、負荷の高い開発を行うことができる。
一方で消費電力が上がるというデメリットがあり、Pi3には5V3A供給できるUSB電源アダプタが必要である。

### PythonとNode.js
IoTでよく使われる開発言語として、PythonとJavaScriptが挙げられる。
Pythonは、PiZeroの512MBの少ないRAM上で軽快に動作し、消費電力も少なくなくて済む。
Node.jsは、Pi3では、RAMメモリを食いCPU負荷の高いによる開発を行うことができるが、一方で消費電力が上がるというデメリットがある。

### VisualStudio Codeと、FTPライクなフレームワークの使い分け
RaspberryPiは、開発環境的に見てリモートPCである。
リモートPCのプログラミングを、ローカル側で行うには、SSH接続が必要である。

VisualStudio Codeには、Microsoftから提供されているRemote DevelopmentというExtensionsがある。
リモートPCにSSH接続し、あたかもローカルPCでプログラム開発しているようにリモートPC上のファイルを編集でき、プログラム開発が飛躍的に効率化するExtensionsである。

Armv6とメモリの制約から、Remote Developmentは、PiZeroでは動作しない。Pi3では動作する。

## 動作の遅いPCでプログラムのチューニングによる高速化
PiZeroは、動作が遅いと言われているが、プログラミング技法によってことが体感できる。
特にスクレイピングでは、Beautiful soupで抽出する要素は、プログラムの組み方によって動作速度が如実に変化する。

そこでわざとPiZeroで開発し、動作速度が向上する

### 最新のPythonがRaspberryPiで動作しなくなった
仮想環境コンテナ

## まとめ
PiZeroで今まで行っていたPythonライブラリ開発を、徐々にPi3に移行し、Node.jsによる開発も並行して行うことにした。
