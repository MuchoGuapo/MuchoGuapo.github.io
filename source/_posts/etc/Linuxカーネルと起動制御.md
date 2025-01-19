---
title: 'Linuxのカーネルと起動制御'
date: 2020-05-15 17:30:00
tags:
- Linux
- Kernel
- GRUB
- ブートローダー
categories:
- 'etc Linuxプログラミング実践'
- 'a) Linuxをより深く知る'
excerpt: 'Linuxでは目的に応じて起動するKernelをカスタマイズできます。起動時に読み込まれるKernelのうち、エラーを吐くKernelの調べ方、起動を遅延させるKernelへの対応方法を調べます。'
cover_image : images/linux.png
pid: kernel_and_boot_procedure
---

## カーネル - Linuxの中核プログラム群
Linuxの安定起動、起動高速化を図るためには、カーネルを知ることが重要です。
![linux](https://burturki.sirv.com/diy/linux.png?w=300)

Linuxのカーネル（Kernel）は、ハードウエアとアプリケーションをつなぐ重要な役割を果たします。

> [Debian GNU/Linux インストールガイド](https://www.debian.org/releases/stable/armhf/install.pdf.ja)

Linuxのブートローダーは、カーネル(vmlinuz)とRAMディスク(initramfs)を読み込んだ後、各Kernelを順次起動します。

## ベースマシンの構成
今回実験用に古いデスクトップPCにLinuxをインストールしました。
ベースマシンはHP Compaq 8200 Eliteで、ハードウエア仕様は次のとおりです。

```
CPU : Intel Core i3-2100 3.10GHz (64KB x 2 / 256KB x 2 / 3072KB x 1)
RAM : 16384 MB DDR3 / 1333 MHz XMM1 8192 MB / XMM3 8192 MB
HDD : WDC WD2500 250GB
```

Linux/Debian10の構成内容は、以下のとおりです。

```
x86_64
Linux/x86 4.19.118 Kernel Configuration
Compiler: gcc-8 (Debian 8.3.0-6) 8.3.0
```

## ハードディスクの起動構成

HDDの起動構成は、古い考え方のBIOS・MBRから、最近主流のUEFI・GPTへと変更しました。HP Compaq 8200 eliteはUEFI対応PCですので、LinuxなどOSのクリーンインストールを行うとGPTになります。

UEFIでは、ブート領域を制御できます。LinuxとWindowsの両方をインストールすると、デュアルブートの知識も身につきます。

### GRUB - ブートローダー

Debian10のブートローダーはGRUBです。

GRUBは/etc/default/grubに書かれた起動手順により、OSカーネル(vmlinuz)とRAMディスク(initramfs)を読み込みます。

```
BOOT_IMAGE=/boot/vmlinuz-4.19.0-9-amd64
```

## Systemd - Kernel起動

Debian10は、SystemdでKernelを起動制御します。

Systemdは「モジュール、起動スクリプト、初期化プロセス」と順番に起動します。

> [Systemd positon statement](https://wiki.debian.org/Debate/initsystem/systemd)

モジュールとして「メモリ管理、プロセス管理、デバイスドライバー、システムコールとセキュリティ」をハンドルします。

> [Linuxの自動起動の設定方法を解説](https://eng-entrance.com/linux_startup)

Systemdの起動パフォーマンスは、コマンドsystemd-analyzeで確認できます。

> [Linux起動パフォーマンスを確認する(systemd-analyze)](https://www.linuxmaster.jp/linux_skill/2020/02/linuxsystemd-analyze.html)

## systemd-analyze

**起動合計時間**

```bash
systemd-analyze
```

```message
Startup finished in 2.729s (kernel) + 1min 2.812s (userspace) = 1min 5.542s 
graphical.target reached after 1min 2.663s in userspace
```

**モジュールごとの起動時間**

```bash
systemd-analyze blame
```

```message
37.252s plymouth-quit-wait.service                           
14.012s snapd.service                                        
13.423s dev-sda2.device                                      
13.061s networkd-dispatcher.service                          
 9.753s accounts-daemon.service                              
 8.775s udisks2.service                                      
 7.194s NetworkManager-wait-online.service                   
 7.140s polkit.service                                       
 6.611s systemd-journal-flush.service                        
 6.254s dev-loop6.device                                     
 5.819s NetworkManager.service                               
 5.776s dev-loop3.device                                     
 5.723s dev-loop5.device                                     
 5.622s dev-loop4.device                                     
 5.489s dev-loop1.device                                     
 5.380s dev-loop2.device                                     
 5.346s dev-loop0.device                                     
 5.334s avahi-daemon.service                                 
 5.198s switcheroo-control.service                           
 5.189s thermald.service                                     
 5.187s systemd-logind.service                               
 5.182s wpa_supplicant.service                               
 4.199s systemd-udevd.service                                
 3.150s systemd-resolved.service                             
 3.075s gpu-manager.service                                  
 2.969s ModemManager.service                                 
 2.196s rsyslog.service                                      
 2.183s grub-initrd-fallback.service                         
 2.005s plymouth-start.service                               
 1.970s apport.service                                       
 1.911s grub-common.service                                  
 1.697s packagekit.service                                   
 1.527s gdm.service                                          
 1.166s e2scrub_reap.service                                 
 1.080s pppd-dns.service                                     
 1.043s systemd-modules-load.service                         
  911ms systemd-tmpfiles-setup.service                       
  843ms apparmor.service                                     
  748ms systemd-sysusers.service                             
  615ms snap-core18-1705.mount                               
  590ms systemd-tmpfiles-setup-dev.service                   
  582ms systemd-sysctl.service                               
  581ms snap-core18-1754.mount                               
  564ms keyboard-setup.service                               
  564ms systemd-journald.service                             
  560ms modprobe@drm.service                                 
  545ms systemd-udev-trigger.service                         
  530ms systemd-timesyncd.service                            
  520ms upower.service                                       
  498ms snap-gnome\x2d3\x2d34\x2d1804-24.mount               
  489ms ufw.service                                          
  483ms snapd.seeded.service                                 
  480ms user@1000.service                                    
  473ms systemd-random-seed.service                          
  456ms snap-gnome\x2d3\x2d34\x2d1804-33.mount               
  450ms snapd.apparmor.service                               
  430ms swapfile.swap                                        
  286ms kerneloops.service                                   
  281ms snap-gtk\x2dcommon\x2dthemes-1506.mount              
  237ms colord.service                                       
  216ms systemd-fsck@dev-disk-by\x2duuid-07B7\x2d632A.service
  173ms plymouth-read-write.service                          
  163ms systemd-remount-fs.service                           
  146ms setvtrgb.service                                     
  140ms snap-snap\x2dstore-433.mount                         
  113ms kmod-static-nodes.service                            
  112ms snap-snapd-7264.mount                                
   84ms dev-hugepages.mount                                  
   83ms dev-mqueue.mount                                     
   83ms systemd-update-utmp.service                          
   82ms sys-kernel-debug.mount                               
   81ms sys-kernel-tracing.mount                             
   74ms openvpn.service                                      
   67ms console-setup.service                                
   40ms boot-efi.mount                                       
   36ms rtkit-daemon.service                                 
   28ms systemd-user-sessions.service                        
   26ms user-runtime-dir@1000.service                        
   16ms alsa-restore.service                                 
   14ms systemd-update-utmp-runlevel.service                 
    4ms sys-fs-fuse-connections.mount                        
    3ms sys-kernel-config.mount                              
    1ms snapd.socket          
```


## dmesg - Kernel出力メッセージ

Kernelからの出力メッセージはコマンドdmesgで確認でき、「正常起動、もしくは警告・エラー」といった情報を読み取れます。

コマンド`dmesg | grep -i err`で確認できるエラーメッセージは次のとおりです。

### 1. 独立ハードウエア監視 - IPMI

IPMIは、OSから分離・独立してハードウエアの管理と監視を行う機能です。

```bash: 'dmesg | grep -i err'
[    0.158866] ipmi:dmi: Base address is zero, assuming no IPMI interface
```

「本機には、IPMIインタフェースがない」というメッセージを出力しています。

### 2. 電源制御 - ACPI error

ACPIは、OSの電源管理制御機能です。

```bash: 'dmesg | grep -i err'
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.023902] ACPI: Using IOAPIC for interrupt routing
[    0.033206] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.033250] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.033295] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.033344] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.033386] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.033431] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.033478] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.033523] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
```

通常の使用では問題がないが、OSの電源管理制御は使用できない可能性があり、OS側のKernelを読み込まないようにする、BIOSを更新する、といった対策が必要となります。

## その他のメッセージ

> [BIOSのアップデートを要求するメッセージ](https://bbs.archlinux.org/viewtopic.php?id=157969)

```
[    0.008659] core: PEBS disabled due to CPU errata, please upgrade microcode
```

> [BIOSのHyperThreadThread機能](https://lore.kernel.org/patchwork/patch/518426/)

```
[    0.017374] core: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
```

> [チップセット関係](https://www.suse.com/support/kb/doc/?id=000018235)
```
[    0.055503] pci 0000:00:02.0: BIOS left Intel GPU interrupts enabled; disabling
```

> [タッチパネルi2c関係（本機にはない）](https://community.intel.com/t5/Embedded-Intel-Core-Processors/i801-smbus-interrupt-timeout-on-Broadwell-DE/td-p/215987)
```
[    1.305336] i801_smbus 0000:00:1f.3: SMBus using PCI interrupt
```

> [イーサネットドライバ読込](https://forums.ubuntulinux.jp/viewtopic.php?id=20361)

```
[    1.324761] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
```

> [読み取り専用で再マウント](https://qastack.jp/ubuntu/563668/how-to-fix-ext4-fs-sda1-re-mounted-opts-errors-remount-ro)

```
[    6.103439] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
```

> [性能解析ツールの調整不足](https://tech.akat.info/?p=1770)
```
[16604.904299] perf: interrupt took too long (2510 > 2500), lowering kernel.perf_event_max_sample_rate to 79500
[21866.505539] perf: interrupt took too long (3139 > 3137), lowering kernel.perf_event_max_sample_rate to 63500
```

##　起動しているが、時間のかかるモジュール

DHCP、固定IP、IPv6については、PC本体だけの問題でなく、ルーターとのやりとりに時間がかかっているため、これはLANの整備を進める必要があると分かりました。

## まとめ

Linuxの安定起動・起動高速化を図るため、Kernelの挙動についてdmesgで調査し、できる限りの対策を採ってみました。
