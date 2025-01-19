---
title: 'RaspberryPiとublox SARA-R410MによるLTE通信 [1] モデム設定'
date: 2024-01-18 12:00:00
tags:
- RaspberryPi 
- ハードウエア制御
- ネットワーク
categories:
- '4 IoT'
- 'a) RaspberryPi'
excerpt: 'RaspberryPiによるネットワーク連動を考えた場合、低消費電力のLTEモジュールが必要です。通信時の消費電力が比較的低いSARA-R410と1NCEのSIMを使って、LTEによる少パケットの通信テストをしました。'
cover_image : linux.png
pid: raspberrypi-low-energy
---

## RaspberryPiとLTEモジュールSARA-R410M
RaspberryPiによるネットワーク連動を考えた場合、低消費電力のLTEモジュールが必要です。
通信時の消費電力が比較的低いSARA-R410と1NCEのSIMを使って、LTEによる少パケットの通信テストをしました。

![linux](https://burturki.sirv.com/diy/linux.png?w=300)

3) LTEモジュール

```
ATE0
OK

AT+CGSN
359214101745408
OK

AT+CIMI
901405114751022
OK

AT+CNUM
+CME ERROR: invalid characters in dial string
```

```
$ sudo minicom -D /dev/ttyS0 -b 115200

Welcome to minicom 2.8
OPTIONS: I18n
Port /dev/ttyS0, 21:39:45

Press CTRL-A Z for help on special keys

AT
OK

AT+CFUN=15
OK

AT+COPS=2
+UFOTASTAT: 3, 1, 0
+ULWM2MSTAT: 4, 0

AT+CGDCONT=1,"IP","iot.1nce.net"
OK

ATE0
OK

AT+UAUTHREQ=1,1,"",""
ERROR

AT+CGDCONT=1,"IP","iot.1nce.net"
OK

AT+COPS=1,2,"44020"
OK

AT+COPS?
+COPS: 0
OK

AT+CPIN?
+CPIN: READY
OK

AT+CGREG?
+CGREG: 0,0
OK

AT+CGNAPN
ERROR

AT+COPS=1,2,"44020"
OK

AT+COPS?
+COPS: 0
OK

AT+COPS=1,2,"44053"
OK

AT+COPS?
+COPS: 0
OK

AT+COPS=1,2,"44051"
OK

AT+COPS?
+COPS: 0
OK

AT+UMNOPROF=20
OK

AT+CFUN=15
OK

AT+COPS=2
OK

+UFOTASTAT: 3, 1, 0
+ULWM2MSTAT: 4, 0

AT+CGDCONT=1,"IP","iot.1nce.net"
OK

AT+UAUTHREQ=1,1,"hamak88@gmail.com","Roborobo2432"
OK

AT+COPS=0
OK

AT+CGDCONT?
+CGDCONT: 1,"IP","iot.1nce.net","0.0.0.0",0,0,0,0
OK

AT+UDNSRN=0,"yahoo.co.jp"
+CME ERROR: No connection to phone
```
