---
title: Raspberry Pi Storage Mount - USB / SD Card Memory 재부팅시 자동 Mount 하기
author: FlyingDeuk
date: 2021-07-12 20:55:00 +0800
categories: [Living]
tags: [usefulthing, linux, raspberrypi]
pin:
typora-root-url: ../../../../flyingdeuk.github.io
---

![pi](/img/living/pi/pi.jpg)

`FlyingDeuk's`
> 라즈베리파이 Booting SD의 용량이 제한적이라 추가적인 저장공간을 추가해야 한다. <br>
리눅스는 기본적으로 mount라는 명령어로 mount해야하는 데 이는 재부팅하면 다시 해줘야하는 불편함이 있어 자동으로 mount하는 방법이다. <br>

리눅스 초보로 일일이 찾아본 내용들 내가 필요했던 내용들을 좀 자세하게 적었다. 나와 같은 초보자들이 검색을 줄일 수 있다면...

`Wiki's`
> **마운트(mount)**는 컴퓨터 과학에서 저장 장치에 접근할 수 있는 경로를 디렉터리 구조에 편입시키는 작업을 말한다. 좁은 의미로는 유닉스 계열의 운영 체제에서의 mount 명령어 또는 그 명령어를 사용하는 것을 말한다. mount 명령어를 사용하면 저장 장치의 접근 경로를 원하는 위치에 생성할 수 있다. 마운트를 이용하면 분산 파일 시스템으로 확장하기가 용이하다. 사용자는 마운트된 미디어의 파일들에만 접근이 가능하다.[1]


```bash
~ » ssh pi@192.168.10.24                     255 ↵ DeUk@Deukhyeonui-MacBook-Air
pi@192.168.10.24's password:
Linux raspberrypi 5.10.17-v7l+ #1414 SMP Fri Apr 30 13:20:47 BST 2021 armv7l

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Fri May  7 16:07:26 2021

SSH is enabled and the default password for the 'pi' user has not been changed.
This is a security risk - please login as the 'pi' user and type 'passwd' to set a new password.

pi@raspberrypi:~ $

```

```
pi@raspberrypi:~ $ sudo apt update
Get:1 http://archive.raspberrypi.org/debian buster InRelease [32.6 kB]         
Get:2 http://raspbian.raspberrypi.org/raspbian buster InRelease [15.0 kB]      
Get:3 http://archive.raspberrypi.org/debian buster/main armhf Packages [378 kB]
Get:4 http://raspbian.raspberrypi.org/raspbian buster/main armhf Packages [13.0 MB]
Get:5 http://raspbian.raspberrypi.org/raspbian buster/contrib armhf Packages [58.7 kB]
Fetched 13.5 MB in 11s (1,255 kB/s)                                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
96 packages can be upgraded. Run 'apt list --upgradable' to see them.
pi@raspberrypi:~ $ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  python-colorzero
Use 'sudo apt autoremove' to remove it.
The following packages will be upgraded:
  aspell base-files bluez dillo ffmpeg firmware-atheros firmware-brcm80211
  firmware-libertas firmware-misc-nonfree firmware-realtek gpicview
  isc-dhcp-client isc-dhcp-common klibc-utils libaspell15 libavcodec58
  libavdevice58 libavfilter7 libavformat58 libavresample4 libavutil56
  libegl-mesa0 libfluidsynth1 libgbm1 libgcrypt20 libgl1-mesa-dri
  libglapi-mesa libgles2-mesa libglx-mesa0 libgnutls30 libgssapi-krb5-2
  libhogweed4 libjavascriptcoregtk-4.0-18 libk5crypto3 libklibc libkrb5-3
  libkrb5support0 liblirc-client0 liblz4-1 libmariadb3 libnettle6
  libpam-systemd libpostproc55 libraspberrypi-bin libraspberrypi-dev
  libraspberrypi-doc libraspberrypi0 libsndfile1 libswresample3 libswscale5
  libsystemd0 libudev1 libvlc-bin libvlc5 libvlccore9 libwebkit2gtk-4.0-37
  libwebp6 libwebpdemux2 libwebpmux3 libx11-6 libx11-data libx11-xcb1 libxml2
  linux-libc-dev mariadb-common mesa-va-drivers mesa-vdpau-drivers
  pi-bluetooth python-gpiozero python-spidev python3-gpiozero python3-spidev
  raspberrypi-bootloader raspberrypi-kernel raspberrypi-sys-mods
  raspberrypi-ui-mods rp-bookshelf rp-prefapps rpi-eeprom rpi-update systemd
  systemd-sysv thonny udev vlc vlc-bin vlc-data vlc-l10n vlc-plugin-base
  vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba vlc-plugin-skins2
  vlc-plugin-video-output vlc-plugin-video-splitter vlc-plugin-visualization
96 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 200 MB of archives.
After this operation, 10.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.raspberrypi.org/debian buster/main armhf dillo armhf 3.0.5-5+rpt1 [404 kB]
Get:2 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf base-files armhf 10.3+rpi1+deb10u10 [70.2 kB]
Get:3 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf systemd-sysv armhf 241-7~deb10u8+rpi1 [101 kB]
Get:6 http://archive.raspberrypi.org/debian buster/main armhf ffmpeg armhf 7:4.1.6-1~deb10u1+rpt2 [1,432 kB]
Get:4 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libpam-systemd armhf 241-7~deb10u8+rpi1 [194 kB]
Get:5 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libsystemd0 armhf 241-7~deb10u8+rpi1 [306 kB]
Get:7 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf systemd armhf 241-7~deb10u8+rpi1 [3,258 kB]
Get:17 http://archive.raspberrypi.org/debian buster/main armhf libavdevice58 armhf 7:4.1.6-1~deb10u1+rpt2 [152 kB]
Get:19 http://archive.raspberrypi.org/debian buster/main armhf libavfilter7 armhf 7:4.1.6-1~deb10u1+rpt2 [1,455 kB]
Get:25 http://archive.raspberrypi.org/debian buster/main armhf libswscale5 armhf 7:4.1.6-1~deb10u1+rpt2 [253 kB]
Get:27 http://archive.raspberrypi.org/debian buster/main armhf libavformat58 armhf 7:4.1.6-1~deb10u1+rpt2 [1,514 kB]
Get:30 http://archive.raspberrypi.org/debian buster/main armhf libavcodec58 armhf 7:4.1.6-1~deb10u1+rpt2 [8,930 kB]
Get:37 http://archive.raspberrypi.org/debian buster/main armhf libswresample3 armhf 7:4.1.6-1~deb10u1+rpt2 [118 kB]
Get:38 http://archive.raspberrypi.org/debian buster/main armhf libpostproc55 armhf 7:4.1.6-1~deb10u1+rpt2 [95.1 kB]
Get:39 http://archive.raspberrypi.org/debian buster/main armhf libavresample4 armhf 7:4.1.6-1~deb10u1+rpt2 [104 kB]
Get:40 http://archive.raspberrypi.org/debian buster/main armhf libavutil56 armhf 7:4.1.6-1~deb10u1+rpt2 [356 kB]
Get:41 http://archive.raspberrypi.org/debian buster/main armhf libraspberrypi-bin armhf 1:1.20210805-1 [341 kB]
Get:43 http://archive.raspberrypi.org/debian buster/main armhf libraspberrypi-doc armhf 1:1.20210805-1 [31.4 MB]
Get:8 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf bluez armhf 5.50-1.2~deb10u2 [764 kB]
Get:50 http://archive.raspberrypi.org/debian buster/main armhf libraspberrypi-dev armhf 1:1.20210805-1 [400 kB]
Get:51 http://archive.raspberrypi.org/debian buster/main armhf raspberrypi-kernel armhf 1:1.20210805-1 [79.6 MB]
Get:9 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf udev armhf 241-7~deb10u8+rpi1 [1,248 kB]
Get:52 http://archive.raspberrypi.org/debian buster/main armhf libraspberrypi0 armhf 1:1.20210805-1 [847 kB]
Get:53 http://archive.raspberrypi.org/debian buster/main armhf raspberrypi-bootloader armhf 1:1.20210805-1 [4,518 kB]
Get:54 http://archive.raspberrypi.org/debian buster/main armhf firmware-atheros all 1:20190114-2+rpt1 [4,012 kB]
Get:55 http://archive.raspberrypi.org/debian buster/main armhf firmware-brcm80211 all 1:20190114-2+rpt1 [4,600 kB]
Get:56 http://archive.raspberrypi.org/debian buster/main armhf firmware-libertas all 1:20190114-2+rpt1 [3,424 kB]
Get:10 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libudev1 armhf 241-7~deb10u8+rpi1 [144 kB]
Get:57 http://archive.raspberrypi.org/debian buster/main armhf firmware-misc-nonfree all 1:20190114-2+rpt1 [3,341 kB]
Get:11 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libnettle6 armhf 3.4.1-1+deb10u1 [223 kB]
Get:58 http://archive.raspberrypi.org/debian buster/main armhf firmware-realtek all 1:20190114-2+rpt1 [506 kB]
Get:59 http://archive.raspberrypi.org/debian buster/main armhf gpicview armhf 0.2.5-2+rpt1 [137 kB]
Get:60 http://archive.raspberrypi.org/debian buster/main armhf libegl-mesa0 armhf 19.3.2-1~bpo10+1~rpt4 [120 kB]
Get:61 http://archive.raspberrypi.org/debian buster/main armhf libgbm1 armhf 19.3.2-1~bpo10+1~rpt4 [67.2 kB]
Get:62 http://archive.raspberrypi.org/debian buster/main armhf libgl1-mesa-dri armhf 19.3.2-1~bpo10+1~rpt4 [5,551 kB]
Get:12 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libhogweed4 armhf 3.4.1-1+deb10u1 [130 kB]
Get:13 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libgnutls30 armhf 3.6.7-4+deb10u7 [1,049 kB]
Get:63 http://archive.raspberrypi.org/debian buster/main armhf libglx-mesa0 armhf 19.3.2-1~bpo10+1~rpt4 [167 kB]
Get:64 http://archive.raspberrypi.org/debian buster/main armhf libglapi-mesa armhf 19.3.2-1~bpo10+1~rpt4 [78.5 kB]
Get:65 http://archive.raspberrypi.org/debian buster/main armhf libgles2-mesa armhf 19.3.2-1~bpo10+1~rpt4 [49.4 kB]
Get:66 http://archive.raspberrypi.org/debian buster/main armhf liblirc-client0 armhf 0.10.1-6.3~deb10u1+rpt1 [68.1 kB]
Get:67 http://archive.raspberrypi.org/debian buster/main armhf libvlccore9 armhf 3.0.12-0+deb10u1+rpt2 [477 kB]
Get:68 http://archive.raspberrypi.org/debian buster/main armhf vlc-plugin-skins2 armhf 3.0.12-0+deb10u1+rpt2 [513 kB]
Get:69 http://archive.raspberrypi.org/debian buster/main armhf vlc armhf 3.0.12-0+deb10u1+rpt2 [142 kB]
Get:70 http://archive.raspberrypi.org/debian buster/main armhf vlc-plugin-qt armhf 3.0.12-0+deb10u1+rpt2 [1,023 kB]
Get:71 http://archive.raspberrypi.org/debian buster/main armhf vlc-plugin-video-output armhf 3.0.12-0+deb10u1+rpt2 [195 kB]
Get:72 http://archive.raspberrypi.org/debian buster/main armhf vlc-l10n all 3.0.12-0+deb10u1+rpt2 [5,669 kB]
Get:73 http://archive.raspberrypi.org/debian buster/main armhf vlc-plugin-base armhf 3.0.12-0+deb10u1+rpt2 [2,604 kB]
Get:74 http://archive.raspberrypi.org/debian buster/main armhf vlc-data all 3.0.12-0+deb10u1+rpt2 [450 kB]
Get:75 http://archive.raspberrypi.org/debian buster/main armhf libvlc5 armhf 3.0.12-0+deb10u1+rpt2 [165 kB]
Get:76 http://archive.raspberrypi.org/debian buster/main armhf vlc-bin armhf 3.0.12-0+deb10u1+rpt2 [162 kB]
Get:77 http://archive.raspberrypi.org/debian buster/main armhf libvlc-bin armhf 3.0.12-0+deb10u1+rpt2 [125 kB]
Get:78 http://archive.raspberrypi.org/debian buster/main armhf linux-libc-dev armhf 1:1.20210805-1 [1,012 kB]
Get:79 http://archive.raspberrypi.org/debian buster/main armhf mesa-va-drivers armhf 19.3.2-1~bpo10+1~rpt4 [1,980 kB]
Get:80 http://archive.raspberrypi.org/debian buster/main armhf mesa-vdpau-drivers armhf 19.3.2-1~bpo10+1~rpt4 [2,094 kB]
Get:81 http://archive.raspberrypi.org/debian buster/main armhf raspberrypi-ui-mods armhf 1.20210706 [323 kB]
Get:82 http://archive.raspberrypi.org/debian buster/main armhf raspberrypi-sys-mods armhf 20210706 [12.2 kB]
Get:83 http://archive.raspberrypi.org/debian buster/main armhf pi-bluetooth all 0.1.17 [5,608 B]
Get:84 http://archive.raspberrypi.org/debian buster/main armhf python-gpiozero all 1.6.2-1 [118 kB]
Get:85 http://archive.raspberrypi.org/debian buster/main armhf python-spidev armhf 20200602~200721-1~buster [11.8 kB]
Get:86 http://archive.raspberrypi.org/debian buster/main armhf python3-gpiozero all 1.6.2-1 [121 kB]
Get:87 http://archive.raspberrypi.org/debian buster/main armhf python3-spidev armhf 20200602~200721-1~buster [11.7 kB]
Get:88 http://archive.raspberrypi.org/debian buster/main armhf rp-bookshelf armhf 0.14 [42.6 kB]
Get:89 http://archive.raspberrypi.org/debian buster/main armhf rp-prefapps armhf 0.34 [412 kB]
Get:90 http://archive.raspberrypi.org/debian buster/main armhf rpi-eeprom armhf 12.9-1 [701 kB]
Get:91 http://archive.raspberrypi.org/debian buster/main armhf rpi-update all 20210618 [7,920 B]
Get:92 http://archive.raspberrypi.org/debian buster/main armhf thonny all 3.3.10-1+rpt1 [788 kB]
Get:93 http://archive.raspberrypi.org/debian buster/main armhf vlc-plugin-notify armhf 3.0.12-0+deb10u1+rpt2 [126 kB]
Get:94 http://archive.raspberrypi.org/debian buster/main armhf vlc-plugin-samba armhf 3.0.12-0+deb10u1+rpt2 [127 kB]
Get:95 http://archive.raspberrypi.org/debian buster/main armhf vlc-plugin-video-splitter armhf 3.0.12-0+deb10u1+rpt2 [140 kB]
Get:96 http://archive.raspberrypi.org/debian buster/main armhf vlc-plugin-visualization armhf 3.0.12-0+deb10u1+rpt2 [142 kB]
Get:14 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf liblz4-1 armhf 1.8.3-1+deb10u1 [49.7 kB]
Get:15 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libgcrypt20 armhf 1.8.4-5+deb10u1 [500 kB]
Get:16 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf isc-dhcp-client armhf 4.4.1-2+deb10u1 [295 kB]
Get:18 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf isc-dhcp-common armhf 4.4.1-2+deb10u1 [144 kB]
Get:20 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf aspell armhf 0.60.7~20110707-6+deb10u1 [214 kB]
Get:21 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libaspell15 armhf 0.60.7~20110707-6+deb10u1 [275 kB]
Get:22 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libx11-data all 2:1.6.7-1+deb10u2 [299 kB]
Get:23 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libx11-6 armhf 2:1.6.7-1+deb10u2 [689 kB]
Get:24 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libxml2 armhf 2.9.4+dfsg1-7+deb10u2 [572 kB]
Get:26 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libwebp6 armhf 0.6.1-2+deb10u1 [227 kB]
Get:28 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libwebpmux3 armhf 0.6.1-2+deb10u1 [94.0 kB]
Get:29 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf klibc-utils armhf 2.0.6-1+rpi1+deb10u1 [87.1 kB]
Get:31 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libklibc armhf 2.0.6-1+rpi1+deb10u1 [52.8 kB]
Get:32 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libx11-xcb1 armhf 2:1.6.7-1+deb10u2 [191 kB]
Get:33 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libsndfile1 armhf 1.0.28-6+deb10u1 [238 kB]
Get:34 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libfluidsynth1 armhf 1.1.11-1+deb10u1 [143 kB]
Get:35 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libgssapi-krb5-2 armhf 1.17-3+deb10u2 [136 kB]
Get:36 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libkrb5-3 armhf 1.17-3+deb10u2 [319 kB]
Get:42 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libkrb5support0 armhf 1.17-3+deb10u2 [62.4 kB]
Get:44 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libk5crypto3 armhf 1.17-3+deb10u2 [118 kB]
Get:45 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libwebpdemux2 armhf 0.6.1-2+deb10u1 [86.7 kB]
Get:46 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libwebkit2gtk-4.0-37 armhf 2.32.3-1~deb10u1+rpi1 [11.2 MB]
Get:47 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libjavascriptcoregtk-4.0-18 armhf 2.32.3-1~deb10u1+rpi1 [2,580 kB]
Get:48 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf mariadb-common all 1:10.3.29-0+deb10u1 [32.5 kB]
Get:49 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf libmariadb3 armhf 1:10.3.29-0+deb10u1 [159 kB]
Fetched 200 MB in 3min 6s (1,076 kB/s)                                         
Reading changelogs... Done
Extracting templates from packages: 100%
(Reading database ... 98616 files and directories currently installed.)
Preparing to unpack .../base-files_10.3+rpi1+deb10u10_armhf.deb ...
Unpacking base-files (10.3+rpi1+deb10u10) over (10.3+rpi1+deb10u9) ...
Setting up base-files (10.3+rpi1+deb10u10) ...
Installing new version of config file /etc/debian_version ...
(Reading database ... 98616 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_241-7~deb10u8+rpi1_armhf.deb ...
Unpacking systemd-sysv (241-7~deb10u8+rpi1) over (241-7~deb10u7+rpi1) ...
Preparing to unpack .../libpam-systemd_241-7~deb10u8+rpi1_armhf.deb ...
Unpacking libpam-systemd:armhf (241-7~deb10u8+rpi1) over (241-7~deb10u7+rpi1) ...
Preparing to unpack .../libsystemd0_241-7~deb10u8+rpi1_armhf.deb ...
Unpacking libsystemd0:armhf (241-7~deb10u8+rpi1) over (241-7~deb10u7+rpi1) ...
Setting up libsystemd0:armhf (241-7~deb10u8+rpi1) ...
(Reading database ... 98616 files and directories currently installed.)
Preparing to unpack .../systemd_241-7~deb10u8+rpi1_armhf.deb ...
Unpacking systemd (241-7~deb10u8+rpi1) over (241-7~deb10u7+rpi1) ...
Preparing to unpack .../bluez_5.50-1.2~deb10u2_armhf.deb ...
Unpacking bluez (5.50-1.2~deb10u2) over (5.50-1.2~deb10u1+rpt2) ...
Preparing to unpack .../udev_241-7~deb10u8+rpi1_armhf.deb ...
Unpacking udev (241-7~deb10u8+rpi1) over (241-7~deb10u7+rpi1) ...
Preparing to unpack .../libudev1_241-7~deb10u8+rpi1_armhf.deb ...
Unpacking libudev1:armhf (241-7~deb10u8+rpi1) over (241-7~deb10u7+rpi1) ...
Setting up libudev1:armhf (241-7~deb10u8+rpi1) ...
(Reading database ... 98615 files and directories currently installed.)
Preparing to unpack .../libnettle6_3.4.1-1+deb10u1_armhf.deb ...
Unpacking libnettle6:armhf (3.4.1-1+deb10u1) over (3.4.1-1) ...
Setting up libnettle6:armhf (3.4.1-1+deb10u1) ...
(Reading database ... 98615 files and directories currently installed.)
Preparing to unpack .../libhogweed4_3.4.1-1+deb10u1_armhf.deb ...
Unpacking libhogweed4:armhf (3.4.1-1+deb10u1) over (3.4.1-1) ...
Setting up libhogweed4:armhf (3.4.1-1+deb10u1) ...
(Reading database ... 98615 files and directories currently installed.)
Preparing to unpack .../libgnutls30_3.6.7-4+deb10u7_armhf.deb ...
Unpacking libgnutls30:armhf (3.6.7-4+deb10u7) over (3.6.7-4+deb10u6) ...
Setting up libgnutls30:armhf (3.6.7-4+deb10u7) ...
(Reading database ... 98615 files and directories currently installed.)
Preparing to unpack .../liblz4-1_1.8.3-1+deb10u1_armhf.deb ...
Unpacking liblz4-1:armhf (1.8.3-1+deb10u1) over (1.8.3-1) ...
Setting up liblz4-1:armhf (1.8.3-1+deb10u1) ...
(Reading database ... 98615 files and directories currently installed.)
Preparing to unpack .../libgcrypt20_1.8.4-5+deb10u1_armhf.deb ...
Unpacking libgcrypt20:armhf (1.8.4-5+deb10u1) over (1.8.4-5) ...
Setting up libgcrypt20:armhf (1.8.4-5+deb10u1) ...
(Reading database ... 98615 files and directories currently installed.)
Preparing to unpack .../00-isc-dhcp-client_4.4.1-2+deb10u1_armhf.deb ...
Unpacking isc-dhcp-client (4.4.1-2+deb10u1) over (4.4.1-2) ...
Preparing to unpack .../01-isc-dhcp-common_4.4.1-2+deb10u1_armhf.deb ...
Unpacking isc-dhcp-common (4.4.1-2+deb10u1) over (4.4.1-2) ...
Preparing to unpack .../02-aspell_0.60.7~20110707-6+deb10u1_armhf.deb ...
Unpacking aspell (0.60.7~20110707-6+deb10u1) over (0.60.7~20110707-6) ...
Preparing to unpack .../03-libaspell15_0.60.7~20110707-6+deb10u1_armhf.deb ...
Unpacking libaspell15:armhf (0.60.7~20110707-6+deb10u1) over (0.60.7~20110707-6) ...
Preparing to unpack .../04-libx11-data_2%3a1.6.7-1+deb10u2_all.deb ...
Unpacking libx11-data (2:1.6.7-1+deb10u2) over (2:1.6.7-1+deb10u1) ...
Preparing to unpack .../05-libx11-6_2%3a1.6.7-1+deb10u2_armhf.deb ...
Unpacking libx11-6:armhf (2:1.6.7-1+deb10u2) over (2:1.6.7-1+deb10u1) ...
Preparing to unpack .../06-dillo_3.0.5-5+rpt1_armhf.deb ...
Unpacking dillo (3.0.5-5+rpt1) over (3.0.5-5) ...
Preparing to unpack .../07-ffmpeg_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking ffmpeg (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../08-libavdevice58_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libavdevice58:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../09-libavfilter7_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libavfilter7:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../10-libswscale5_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libswscale5:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../11-libavformat58_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libavformat58:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../12-libavcodec58_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libavcodec58:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../13-libswresample3_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libswresample3:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../14-libpostproc55_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libpostproc55:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../15-libavresample4_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libavresample4:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../16-libavutil56_7%3a4.1.6-1~deb10u1+rpt2_armhf.deb ...
Unpacking libavutil56:armhf (7:4.1.6-1~deb10u1+rpt2) over (7:4.1.6-1~deb10u1+rpt1) ...
Preparing to unpack .../17-libraspberrypi-bin_1%3a1.20210805-1_armhf.deb ...
Unpacking libraspberrypi-bin (1:1.20210805-1) over (1.20210430-1) ...
Preparing to unpack .../18-libraspberrypi-doc_1%3a1.20210805-1_armhf.deb ...
Unpacking libraspberrypi-doc (1:1.20210805-1) over (1.20210430-1) ...
Preparing to unpack .../19-libraspberrypi-dev_1%3a1.20210805-1_armhf.deb ...
Unpacking libraspberrypi-dev (1:1.20210805-1) over (1.20210430-1) ...
Preparing to unpack .../20-raspberrypi-kernel_1%3a1.20210805-1_armhf.deb ...
Adding 'diversion of /boot/kernel.img to /usr/share/rpikernelhack/kernel.img by rpikernelhack'
Adding 'diversion of /boot/kernel7.img to /usr/share/rpikernelhack/kernel7.img by rpikernelhack'
Adding 'diversion of /boot/kernel7l.img to /usr/share/rpikernelhack/kernel7l.img by rpikernelhack'
Adding 'diversion of /boot/kernel8.img to /usr/share/rpikernelhack/kernel8.img by rpikernelhack'
Adding 'diversion of /boot/bcm2708-rpi-b-plus.dtb to /usr/share/rpikernelhack/bcm2708-rpi-b-plus.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2708-rpi-b-rev1.dtb to /usr/share/rpikernelhack/bcm2708-rpi-b-rev1.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2708-rpi-b.dtb to /usr/share/rpikernelhack/bcm2708-rpi-b.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2708-rpi-cm.dtb to /usr/share/rpikernelhack/bcm2708-rpi-cm.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2708-rpi-zero-w.dtb to /usr/share/rpikernelhack/bcm2708-rpi-zero-w.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2708-rpi-zero.dtb to /usr/share/rpikernelhack/bcm2708-rpi-zero.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2709-rpi-2-b.dtb to /usr/share/rpikernelhack/bcm2709-rpi-2-b.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2710-rpi-2-b.dtb to /usr/share/rpikernelhack/bcm2710-rpi-2-b.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2710-rpi-3-b-plus.dtb to /usr/share/rpikernelhack/bcm2710-rpi-3-b-plus.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2710-rpi-3-b.dtb to /usr/share/rpikernelhack/bcm2710-rpi-3-b.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2710-rpi-cm3.dtb to /usr/share/rpikernelhack/bcm2710-rpi-cm3.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2711-rpi-4-b.dtb to /usr/share/rpikernelhack/bcm2711-rpi-4-b.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2711-rpi-400.dtb to /usr/share/rpikernelhack/bcm2711-rpi-400.dtb by rpikernelhack'
Adding 'diversion of /boot/bcm2711-rpi-cm4.dtb to /usr/share/rpikernelhack/bcm2711-rpi-cm4.dtb by rpikernelhack'
Adding 'diversion of /boot/COPYING.linux to /usr/share/rpikernelhack/COPYING.linux by rpikernelhack'
Adding 'diversion of /boot/overlays/README to /usr/share/rpikernelhack/overlays/README by rpikernelhack'
Adding 'diversion of /boot/overlays/act-led.dtbo to /usr/share/rpikernelhack/overlays/act-led.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/adafruit18.dtbo to /usr/share/rpikernelhack/overlays/adafruit18.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/adau1977-adc.dtbo to /usr/share/rpikernelhack/overlays/adau1977-adc.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/adau7002-simple.dtbo to /usr/share/rpikernelhack/overlays/adau7002-simple.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ads1015.dtbo to /usr/share/rpikernelhack/overlays/ads1015.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ads1115.dtbo to /usr/share/rpikernelhack/overlays/ads1115.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ads7846.dtbo to /usr/share/rpikernelhack/overlays/ads7846.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/adv7282m.dtbo to /usr/share/rpikernelhack/overlays/adv7282m.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/adv728x-m.dtbo to /usr/share/rpikernelhack/overlays/adv728x-m.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/akkordion-iqdacplus.dtbo to /usr/share/rpikernelhack/overlays/akkordion-iqdacplus.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/allo-boss-dac-pcm512x-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-boss-dac-pcm512x-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/allo-boss2-dac-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-boss2-dac-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/allo-digione.dtbo to /usr/share/rpikernelhack/overlays/allo-digione.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/allo-katana-dac-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-katana-dac-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/allo-piano-dac-pcm512x-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-piano-dac-pcm512x-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/allo-piano-dac-plus-pcm512x-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-piano-dac-plus-pcm512x-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/anyspi.dtbo to /usr/share/rpikernelhack/overlays/anyspi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/apds9960.dtbo to /usr/share/rpikernelhack/overlays/apds9960.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/applepi-dac.dtbo to /usr/share/rpikernelhack/overlays/applepi-dac.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/at86rf233.dtbo to /usr/share/rpikernelhack/overlays/at86rf233.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/audioinjector-addons.dtbo to /usr/share/rpikernelhack/overlays/audioinjector-addons.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/audioinjector-isolated-soundcard.dtbo to /usr/share/rpikernelhack/overlays/audioinjector-isolated-soundcard.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/audioinjector-ultra.dtbo to /usr/share/rpikernelhack/overlays/audioinjector-ultra.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/audioinjector-wm8731-audio.dtbo to /usr/share/rpikernelhack/overlays/audioinjector-wm8731-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/audiosense-pi.dtbo to /usr/share/rpikernelhack/overlays/audiosense-pi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/audremap.dtbo to /usr/share/rpikernelhack/overlays/audremap.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/balena-fin.dtbo to /usr/share/rpikernelhack/overlays/balena-fin.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/cap1106.dtbo to /usr/share/rpikernelhack/overlays/cap1106.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/chipdip-dac.dtbo to /usr/share/rpikernelhack/overlays/chipdip-dac.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/cma.dtbo to /usr/share/rpikernelhack/overlays/cma.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/dht11.dtbo to /usr/share/rpikernelhack/overlays/dht11.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/dionaudio-loco-v2.dtbo to /usr/share/rpikernelhack/overlays/dionaudio-loco-v2.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/dionaudio-loco.dtbo to /usr/share/rpikernelhack/overlays/dionaudio-loco.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/disable-bt.dtbo to /usr/share/rpikernelhack/overlays/disable-bt.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/disable-wifi.dtbo to /usr/share/rpikernelhack/overlays/disable-wifi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/dpi18.dtbo to /usr/share/rpikernelhack/overlays/dpi18.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/dpi18cpadhi.dtbo to /usr/share/rpikernelhack/overlays/dpi18cpadhi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/dpi24.dtbo to /usr/share/rpikernelhack/overlays/dpi24.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/draws.dtbo to /usr/share/rpikernelhack/overlays/draws.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/dwc-otg.dtbo to /usr/share/rpikernelhack/overlays/dwc-otg.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/dwc2.dtbo to /usr/share/rpikernelhack/overlays/dwc2.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/edt-ft5406.dtbo to /usr/share/rpikernelhack/overlays/edt-ft5406.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/enc28j60-spi2.dtbo to /usr/share/rpikernelhack/overlays/enc28j60-spi2.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/enc28j60.dtbo to /usr/share/rpikernelhack/overlays/enc28j60.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/exc3000.dtbo to /usr/share/rpikernelhack/overlays/exc3000.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/fe-pi-audio.dtbo to /usr/share/rpikernelhack/overlays/fe-pi-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/fsm-demo.dtbo to /usr/share/rpikernelhack/overlays/fsm-demo.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ghost-amp.dtbo to /usr/share/rpikernelhack/overlays/ghost-amp.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/goodix.dtbo to /usr/share/rpikernelhack/overlays/goodix.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/googlevoicehat-soundcard.dtbo to /usr/share/rpikernelhack/overlays/googlevoicehat-soundcard.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-fan.dtbo to /usr/share/rpikernelhack/overlays/gpio-fan.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-ir-tx.dtbo to /usr/share/rpikernelhack/overlays/gpio-ir-tx.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-ir.dtbo to /usr/share/rpikernelhack/overlays/gpio-ir.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-key.dtbo to /usr/share/rpikernelhack/overlays/gpio-key.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-led.dtbo to /usr/share/rpikernelhack/overlays/gpio-led.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-no-bank0-irq.dtbo to /usr/share/rpikernelhack/overlays/gpio-no-bank0-irq.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-no-irq.dtbo to /usr/share/rpikernelhack/overlays/gpio-no-irq.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-poweroff.dtbo to /usr/share/rpikernelhack/overlays/gpio-poweroff.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/gpio-shutdown.dtbo to /usr/share/rpikernelhack/overlays/gpio-shutdown.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hd44780-lcd.dtbo to /usr/share/rpikernelhack/overlays/hd44780-lcd.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hdmi-backlight-hwhack-gpio.dtbo to /usr/share/rpikernelhack/overlays/hdmi-backlight-hwhack-gpio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-amp.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-amp.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-amp100.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-amp100.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-dac.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dac.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-dacplus.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplus.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-dacplusadc.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplusadc.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-dacplusadcpro.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplusadcpro.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-dacplusdsp.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplusdsp.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-dacplushd.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplushd.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-digi-pro.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-digi-pro.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hifiberry-digi.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-digi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/highperi.dtbo to /usr/share/rpikernelhack/overlays/highperi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hy28a.dtbo to /usr/share/rpikernelhack/overlays/hy28a.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hy28b-2017.dtbo to /usr/share/rpikernelhack/overlays/hy28b-2017.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/hy28b.dtbo to /usr/share/rpikernelhack/overlays/hy28b.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i-sabre-q2m.dtbo to /usr/share/rpikernelhack/overlays/i-sabre-q2m.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c-bcm2708.dtbo to /usr/share/rpikernelhack/overlays/i2c-bcm2708.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c-gpio.dtbo to /usr/share/rpikernelhack/overlays/i2c-gpio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c-mux.dtbo to /usr/share/rpikernelhack/overlays/i2c-mux.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c-pwm-pca9685a.dtbo to /usr/share/rpikernelhack/overlays/i2c-pwm-pca9685a.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c-rtc-gpio.dtbo to /usr/share/rpikernelhack/overlays/i2c-rtc-gpio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c-rtc.dtbo to /usr/share/rpikernelhack/overlays/i2c-rtc.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c-sensor.dtbo to /usr/share/rpikernelhack/overlays/i2c-sensor.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c0.dtbo to /usr/share/rpikernelhack/overlays/i2c0.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c1.dtbo to /usr/share/rpikernelhack/overlays/i2c1.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c3.dtbo to /usr/share/rpikernelhack/overlays/i2c3.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c4.dtbo to /usr/share/rpikernelhack/overlays/i2c4.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c5.dtbo to /usr/share/rpikernelhack/overlays/i2c5.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2c6.dtbo to /usr/share/rpikernelhack/overlays/i2c6.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/i2s-gpio28-31.dtbo to /usr/share/rpikernelhack/overlays/i2s-gpio28-31.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ilitek251x.dtbo to /usr/share/rpikernelhack/overlays/ilitek251x.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/imx219.dtbo to /usr/share/rpikernelhack/overlays/imx219.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/imx290.dtbo to /usr/share/rpikernelhack/overlays/imx290.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/imx378.dtbo to /usr/share/rpikernelhack/overlays/imx378.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/imx477.dtbo to /usr/share/rpikernelhack/overlays/imx477.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/iqaudio-codec.dtbo to /usr/share/rpikernelhack/overlays/iqaudio-codec.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/iqaudio-dac.dtbo to /usr/share/rpikernelhack/overlays/iqaudio-dac.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/iqaudio-dacplus.dtbo to /usr/share/rpikernelhack/overlays/iqaudio-dacplus.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/iqaudio-digi-wm8804-audio.dtbo to /usr/share/rpikernelhack/overlays/iqaudio-digi-wm8804-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/irs1125.dtbo to /usr/share/rpikernelhack/overlays/irs1125.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/jedec-spi-nor.dtbo to /usr/share/rpikernelhack/overlays/jedec-spi-nor.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/justboom-both.dtbo to /usr/share/rpikernelhack/overlays/justboom-both.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/justboom-dac.dtbo to /usr/share/rpikernelhack/overlays/justboom-dac.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/justboom-digi.dtbo to /usr/share/rpikernelhack/overlays/justboom-digi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ltc294x.dtbo to /usr/share/rpikernelhack/overlays/ltc294x.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/max98357a.dtbo to /usr/share/rpikernelhack/overlays/max98357a.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/maxtherm.dtbo to /usr/share/rpikernelhack/overlays/maxtherm.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mbed-dac.dtbo to /usr/share/rpikernelhack/overlays/mbed-dac.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mcp23017.dtbo to /usr/share/rpikernelhack/overlays/mcp23017.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mcp23s17.dtbo to /usr/share/rpikernelhack/overlays/mcp23s17.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mcp2515-can0.dtbo to /usr/share/rpikernelhack/overlays/mcp2515-can0.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mcp2515-can1.dtbo to /usr/share/rpikernelhack/overlays/mcp2515-can1.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mcp251xfd.dtbo to /usr/share/rpikernelhack/overlays/mcp251xfd.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mcp3008.dtbo to /usr/share/rpikernelhack/overlays/mcp3008.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mcp3202.dtbo to /usr/share/rpikernelhack/overlays/mcp3202.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mcp342x.dtbo to /usr/share/rpikernelhack/overlays/mcp342x.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/media-center.dtbo to /usr/share/rpikernelhack/overlays/media-center.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/merus-amp.dtbo to /usr/share/rpikernelhack/overlays/merus-amp.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/midi-uart0.dtbo to /usr/share/rpikernelhack/overlays/midi-uart0.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/midi-uart1.dtbo to /usr/share/rpikernelhack/overlays/midi-uart1.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/minipitft13.dtbo to /usr/share/rpikernelhack/overlays/minipitft13.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/miniuart-bt.dtbo to /usr/share/rpikernelhack/overlays/miniuart-bt.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mmc.dtbo to /usr/share/rpikernelhack/overlays/mmc.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mpu6050.dtbo to /usr/share/rpikernelhack/overlays/mpu6050.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/mz61581.dtbo to /usr/share/rpikernelhack/overlays/mz61581.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ov5647.dtbo to /usr/share/rpikernelhack/overlays/ov5647.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ov7251.dtbo to /usr/share/rpikernelhack/overlays/ov7251.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ov9281.dtbo to /usr/share/rpikernelhack/overlays/ov9281.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/overlay_map.dtb to /usr/share/rpikernelhack/overlays/overlay_map.dtb by rpikernelhack'
Adding 'diversion of /boot/overlays/papirus.dtbo to /usr/share/rpikernelhack/overlays/papirus.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pca953x.dtbo to /usr/share/rpikernelhack/overlays/pca953x.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pcie-32bit-dma.dtbo to /usr/share/rpikernelhack/overlays/pcie-32bit-dma.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pibell.dtbo to /usr/share/rpikernelhack/overlays/pibell.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pifacedigital.dtbo to /usr/share/rpikernelhack/overlays/pifacedigital.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pifi-40.dtbo to /usr/share/rpikernelhack/overlays/pifi-40.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pifi-dac-hd.dtbo to /usr/share/rpikernelhack/overlays/pifi-dac-hd.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pifi-dac-zero.dtbo to /usr/share/rpikernelhack/overlays/pifi-dac-zero.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pifi-mini-210.dtbo to /usr/share/rpikernelhack/overlays/pifi-mini-210.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/piglow.dtbo to /usr/share/rpikernelhack/overlays/piglow.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/piscreen.dtbo to /usr/share/rpikernelhack/overlays/piscreen.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/piscreen2r.dtbo to /usr/share/rpikernelhack/overlays/piscreen2r.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pisound.dtbo to /usr/share/rpikernelhack/overlays/pisound.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pitft22.dtbo to /usr/share/rpikernelhack/overlays/pitft22.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pitft28-capacitive.dtbo to /usr/share/rpikernelhack/overlays/pitft28-capacitive.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pitft28-resistive.dtbo to /usr/share/rpikernelhack/overlays/pitft28-resistive.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pitft35-resistive.dtbo to /usr/share/rpikernelhack/overlays/pitft35-resistive.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pps-gpio.dtbo to /usr/share/rpikernelhack/overlays/pps-gpio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pwm-2chan.dtbo to /usr/share/rpikernelhack/overlays/pwm-2chan.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pwm-ir-tx.dtbo to /usr/share/rpikernelhack/overlays/pwm-ir-tx.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/pwm.dtbo to /usr/share/rpikernelhack/overlays/pwm.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/qca7000.dtbo to /usr/share/rpikernelhack/overlays/qca7000.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rotary-encoder.dtbo to /usr/share/rpikernelhack/overlays/rotary-encoder.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-backlight.dtbo to /usr/share/rpikernelhack/overlays/rpi-backlight.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-cirrus-wm5102.dtbo to /usr/share/rpikernelhack/overlays/rpi-cirrus-wm5102.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-dac.dtbo to /usr/share/rpikernelhack/overlays/rpi-dac.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-display.dtbo to /usr/share/rpikernelhack/overlays/rpi-display.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-ft5406.dtbo to /usr/share/rpikernelhack/overlays/rpi-ft5406.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-poe-plus.dtbo to /usr/share/rpikernelhack/overlays/rpi-poe-plus.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-poe.dtbo to /usr/share/rpikernelhack/overlays/rpi-poe.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-proto.dtbo to /usr/share/rpikernelhack/overlays/rpi-proto.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-sense.dtbo to /usr/share/rpikernelhack/overlays/rpi-sense.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpi-tv.dtbo to /usr/share/rpikernelhack/overlays/rpi-tv.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rpivid-v4l2.dtbo to /usr/share/rpikernelhack/overlays/rpivid-v4l2.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/rra-digidac1-wm8741-audio.dtbo to /usr/share/rpikernelhack/overlays/rra-digidac1-wm8741-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sainsmart18.dtbo to /usr/share/rpikernelhack/overlays/sainsmart18.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sc16is750-i2c.dtbo to /usr/share/rpikernelhack/overlays/sc16is750-i2c.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sc16is752-i2c.dtbo to /usr/share/rpikernelhack/overlays/sc16is752-i2c.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sc16is752-spi0.dtbo to /usr/share/rpikernelhack/overlays/sc16is752-spi0.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sc16is752-spi1.dtbo to /usr/share/rpikernelhack/overlays/sc16is752-spi1.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sdhost.dtbo to /usr/share/rpikernelhack/overlays/sdhost.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sdio.dtbo to /usr/share/rpikernelhack/overlays/sdio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/seeed-can-fd-hat-v1.dtbo to /usr/share/rpikernelhack/overlays/seeed-can-fd-hat-v1.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/seeed-can-fd-hat-v2.dtbo to /usr/share/rpikernelhack/overlays/seeed-can-fd-hat-v2.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sh1106-spi.dtbo to /usr/share/rpikernelhack/overlays/sh1106-spi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/si446x-spi0.dtbo to /usr/share/rpikernelhack/overlays/si446x-spi0.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/smi-dev.dtbo to /usr/share/rpikernelhack/overlays/smi-dev.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/smi-nand.dtbo to /usr/share/rpikernelhack/overlays/smi-nand.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/smi.dtbo to /usr/share/rpikernelhack/overlays/smi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi-gpio35-39.dtbo to /usr/share/rpikernelhack/overlays/spi-gpio35-39.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi-gpio40-45.dtbo to /usr/share/rpikernelhack/overlays/spi-gpio40-45.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi-rtc.dtbo to /usr/share/rpikernelhack/overlays/spi-rtc.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi0-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi0-1cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi0-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi0-2cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi1-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi1-1cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi1-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi1-2cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi1-3cs.dtbo to /usr/share/rpikernelhack/overlays/spi1-3cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi2-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi2-1cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi2-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi2-2cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi2-3cs.dtbo to /usr/share/rpikernelhack/overlays/spi2-3cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi3-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi3-1cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi3-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi3-2cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi4-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi4-1cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi4-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi4-2cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi5-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi5-1cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi5-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi5-2cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi6-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi6-1cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/spi6-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi6-2cs.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ssd1306-spi.dtbo to /usr/share/rpikernelhack/overlays/ssd1306-spi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ssd1306.dtbo to /usr/share/rpikernelhack/overlays/ssd1306.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ssd1331-spi.dtbo to /usr/share/rpikernelhack/overlays/ssd1331-spi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ssd1351-spi.dtbo to /usr/share/rpikernelhack/overlays/ssd1351-spi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/superaudioboard.dtbo to /usr/share/rpikernelhack/overlays/superaudioboard.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/sx150x.dtbo to /usr/share/rpikernelhack/overlays/sx150x.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/tc358743-audio.dtbo to /usr/share/rpikernelhack/overlays/tc358743-audio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/tc358743.dtbo to /usr/share/rpikernelhack/overlays/tc358743.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/tinylcd35.dtbo to /usr/share/rpikernelhack/overlays/tinylcd35.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/tpm-slb9670.dtbo to /usr/share/rpikernelhack/overlays/tpm-slb9670.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/uart0.dtbo to /usr/share/rpikernelhack/overlays/uart0.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/uart1.dtbo to /usr/share/rpikernelhack/overlays/uart1.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/uart2.dtbo to /usr/share/rpikernelhack/overlays/uart2.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/uart3.dtbo to /usr/share/rpikernelhack/overlays/uart3.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/uart4.dtbo to /usr/share/rpikernelhack/overlays/uart4.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/uart5.dtbo to /usr/share/rpikernelhack/overlays/uart5.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/udrc.dtbo to /usr/share/rpikernelhack/overlays/udrc.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/ugreen-dabboard.dtbo to /usr/share/rpikernelhack/overlays/ugreen-dabboard.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/upstream-pi4.dtbo to /usr/share/rpikernelhack/overlays/upstream-pi4.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/upstream.dtbo to /usr/share/rpikernelhack/overlays/upstream.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-fkms-v3d-pi4.dtbo to /usr/share/rpikernelhack/overlays/vc4-fkms-v3d-pi4.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-fkms-v3d.dtbo to /usr/share/rpikernelhack/overlays/vc4-fkms-v3d.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-kms-dpi-at056tn53v1.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-dpi-at056tn53v1.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-kms-dsi-7inch.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-dsi-7inch.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-kms-dsi-lt070me05000-v2.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-dsi-lt070me05000-v2.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-kms-dsi-lt070me05000.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-dsi-lt070me05000.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-kms-kippah-7inch.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-kippah-7inch.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-kms-v3d-pi4.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-v3d-pi4.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-kms-v3d.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-v3d.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vc4-kms-vga666.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-vga666.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/vga666.dtbo to /usr/share/rpikernelhack/overlays/vga666.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/w1-gpio-pullup.dtbo to /usr/share/rpikernelhack/overlays/w1-gpio-pullup.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/w1-gpio.dtbo to /usr/share/rpikernelhack/overlays/w1-gpio.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/w5500.dtbo to /usr/share/rpikernelhack/overlays/w5500.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/wittypi.dtbo to /usr/share/rpikernelhack/overlays/wittypi.dtbo by rpikernelhack'
Adding 'diversion of /boot/overlays/wm8960-soundcard.dtbo to /usr/share/rpikernelhack/overlays/wm8960-soundcard.dtbo by rpikernelhack'
Unpacking raspberrypi-kernel (1:1.20210805-1) over (1.20210430-1) ...
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 5.10.17+ /boot/kernel.img
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 5.10.17-v7+ /boot/kernel7.img
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 5.10.17-v7l+ /boot/kernel7l.img
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 5.10.17-v8+ /boot/kernel8.img
Preparing to unpack .../21-libraspberrypi0_1%3a1.20210805-1_armhf.deb ...
Unpacking libraspberrypi0 (1:1.20210805-1) over (1.20210430-1) ...
Preparing to unpack .../22-raspberrypi-bootloader_1%3a1.20210805-1_armhf.deb ...
Adding 'diversion of /boot/start.elf to /usr/share/rpikernelhack/start.elf by rpikernelhack'
Adding 'diversion of /boot/start_cd.elf to /usr/share/rpikernelhack/start_cd.elf by rpikernelhack'
Adding 'diversion of /boot/start_db.elf to /usr/share/rpikernelhack/start_db.elf by rpikernelhack'
Adding 'diversion of /boot/start_x.elf to /usr/share/rpikernelhack/start_x.elf by rpikernelhack'
Adding 'diversion of /boot/fixup.dat to /usr/share/rpikernelhack/fixup.dat by rpikernelhack'
Adding 'diversion of /boot/fixup_cd.dat to /usr/share/rpikernelhack/fixup_cd.dat by rpikernelhack'
Adding 'diversion of /boot/fixup_db.dat to /usr/share/rpikernelhack/fixup_db.dat by rpikernelhack'
Adding 'diversion of /boot/fixup_x.dat to /usr/share/rpikernelhack/fixup_x.dat by rpikernelhack'
Adding 'diversion of /boot/bootcode.bin to /usr/share/rpikernelhack/bootcode.bin by rpikernelhack'
Adding 'diversion of /boot/start4.elf to /usr/share/rpikernelhack/start4.elf by rpikernelhack'
Adding 'diversion of /boot/start4cd.elf to /usr/share/rpikernelhack/start4cd.elf by rpikernelhack'
Adding 'diversion of /boot/start4db.elf to /usr/share/rpikernelhack/start4db.elf by rpikernelhack'
Adding 'diversion of /boot/start4x.elf to /usr/share/rpikernelhack/start4x.elf by rpikernelhack'
Adding 'diversion of /boot/fixup4.dat to /usr/share/rpikernelhack/fixup4.dat by rpikernelhack'
Adding 'diversion of /boot/fixup4cd.dat to /usr/share/rpikernelhack/fixup4cd.dat by rpikernelhack'
Adding 'diversion of /boot/fixup4db.dat to /usr/share/rpikernelhack/fixup4db.dat by rpikernelhack'
Adding 'diversion of /boot/fixup4x.dat to /usr/share/rpikernelhack/fixup4x.dat by rpikernelhack'
Adding 'diversion of /boot/LICENCE.broadcom to /usr/share/rpikernelhack/LICENCE.broadcom by rpikernelhack'
Unpacking raspberrypi-bootloader (1:1.20210805-1) over (1.20210430-1) ...
Preparing to unpack .../23-libxml2_2.9.4+dfsg1-7+deb10u2_armhf.deb ...
Unpacking libxml2:armhf (2.9.4+dfsg1-7+deb10u2) over (2.9.4+dfsg1-7+deb10u1) ...
Preparing to unpack .../24-libwebp6_0.6.1-2+deb10u1_armhf.deb ...
Unpacking libwebp6:armhf (0.6.1-2+deb10u1) over (0.6.1-2) ...
Preparing to unpack .../25-libwebpmux3_0.6.1-2+deb10u1_armhf.deb ...
Unpacking libwebpmux3:armhf (0.6.1-2+deb10u1) over (0.6.1-2) ...
Preparing to unpack .../26-firmware-atheros_1%3a20190114-2+rpt1_all.deb ...
Unpacking firmware-atheros (1:20190114-2+rpt1) over (1:20190114-1+rpt11) ...
Preparing to unpack .../27-firmware-brcm80211_1%3a20190114-2+rpt1_all.deb ...
Unpacking firmware-brcm80211 (1:20190114-2+rpt1) over (1:20190114-1+rpt11) ...
Preparing to unpack .../28-firmware-libertas_1%3a20190114-2+rpt1_all.deb ...
Unpacking firmware-libertas (1:20190114-2+rpt1) over (1:20190114-1+rpt11) ...
Preparing to unpack .../29-firmware-misc-nonfree_1%3a20190114-2+rpt1_all.deb ...
Unpacking firmware-misc-nonfree (1:20190114-2+rpt1) over (1:20190114-1+rpt11) ...
Preparing to unpack .../30-firmware-realtek_1%3a20190114-2+rpt1_all.deb ...
Unpacking firmware-realtek (1:20190114-2+rpt1) over (1:20190114-1+rpt11) ...
Preparing to unpack .../31-gpicview_0.2.5-2+rpt1_armhf.deb ...
Unpacking gpicview (0.2.5-2+rpt1) over (0.2.5-2) ...
Preparing to unpack .../32-klibc-utils_2.0.6-1+rpi1+deb10u1_armhf.deb ...
Unpacking klibc-utils (2.0.6-1+rpi1+deb10u1) over (2.0.6-1+rpi1) ...
Preparing to unpack .../33-libklibc_2.0.6-1+rpi1+deb10u1_armhf.deb ...
Unpacking libklibc:armhf (2.0.6-1+rpi1+deb10u1) over (2.0.6-1+rpi1) ...
Preparing to unpack .../34-libegl-mesa0_19.3.2-1~bpo10+1~rpt4_armhf.deb ...
Unpacking libegl-mesa0:armhf (19.3.2-1~bpo10+1~rpt4) over (19.3.2-1~bpo10+1~rpt3) ...
Preparing to unpack .../35-libgbm1_19.3.2-1~bpo10+1~rpt4_armhf.deb ...
Unpacking libgbm1:armhf (19.3.2-1~bpo10+1~rpt4) over (19.3.2-1~bpo10+1~rpt3) ...
Preparing to unpack .../36-libx11-xcb1_2%3a1.6.7-1+deb10u2_armhf.deb ...
Unpacking libx11-xcb1:armhf (2:1.6.7-1+deb10u2) over (2:1.6.7-1+deb10u1) ...
Preparing to unpack .../37-libgl1-mesa-dri_19.3.2-1~bpo10+1~rpt4_armhf.deb ...
Unpacking libgl1-mesa-dri:armhf (19.3.2-1~bpo10+1~rpt4) over (19.3.2-1~bpo10+1~rpt3) ...
Preparing to unpack .../38-libglx-mesa0_19.3.2-1~bpo10+1~rpt4_armhf.deb ...
Unpacking libglx-mesa0:armhf (19.3.2-1~bpo10+1~rpt4) over (19.3.2-1~bpo10+1~rpt3) ...
Preparing to unpack .../39-libglapi-mesa_19.3.2-1~bpo10+1~rpt4_armhf.deb ...
Unpacking libglapi-mesa:armhf (19.3.2-1~bpo10+1~rpt4) over (19.3.2-1~bpo10+1~rpt3) ...
Preparing to unpack .../40-libsndfile1_1.0.28-6+deb10u1_armhf.deb ...
Unpacking libsndfile1:armhf (1.0.28-6+deb10u1) over (1.0.28-6) ...
Preparing to unpack .../41-libfluidsynth1_1.1.11-1+deb10u1_armhf.deb ...
Unpacking libfluidsynth1:armhf (1.1.11-1+deb10u1) over (1.1.11-1) ...
Preparing to unpack .../42-libgles2-mesa_19.3.2-1~bpo10+1~rpt4_armhf.deb ...
Unpacking libgles2-mesa:armhf (19.3.2-1~bpo10+1~rpt4) over (19.3.2-1~bpo10+1~rpt3) ...
Preparing to unpack .../43-libgssapi-krb5-2_1.17-3+deb10u2_armhf.deb ...
Unpacking libgssapi-krb5-2:armhf (1.17-3+deb10u2) over (1.17-3+deb10u1) ...
Preparing to unpack .../44-libkrb5-3_1.17-3+deb10u2_armhf.deb ...
Unpacking libkrb5-3:armhf (1.17-3+deb10u2) over (1.17-3+deb10u1) ...
Preparing to unpack .../45-libkrb5support0_1.17-3+deb10u2_armhf.deb ...
Unpacking libkrb5support0:armhf (1.17-3+deb10u2) over (1.17-3+deb10u1) ...
Preparing to unpack .../46-libk5crypto3_1.17-3+deb10u2_armhf.deb ...
Unpacking libk5crypto3:armhf (1.17-3+deb10u2) over (1.17-3+deb10u1) ...
Preparing to unpack .../47-libwebpdemux2_0.6.1-2+deb10u1_armhf.deb ...
Unpacking libwebpdemux2:armhf (0.6.1-2+deb10u1) over (0.6.1-2) ...
Preparing to unpack .../48-libwebkit2gtk-4.0-37_2.32.3-1~deb10u1+rpi1_armhf.deb ...
Unpacking libwebkit2gtk-4.0-37:armhf (2.32.3-1~deb10u1+rpi1) over (2.30.6-1~deb10u1+rpi1) ...
Preparing to unpack .../49-libjavascriptcoregtk-4.0-18_2.32.3-1~deb10u1+rpi1_armhf.deb ...
Unpacking libjavascriptcoregtk-4.0-18:armhf (2.32.3-1~deb10u1+rpi1) over (2.30.6-1~deb10u1+rpi1) ...
Preparing to unpack .../50-liblirc-client0_0.10.1-6.3~deb10u1+rpt1_armhf.deb ...
Unpacking liblirc-client0:armhf (0.10.1-6.3~deb10u1+rpt1) over (0.10.1-6.3~deb10u1) ...
Preparing to unpack .../51-mariadb-common_1%3a10.3.29-0+deb10u1_all.deb ...
Unpacking mariadb-common (1:10.3.29-0+deb10u1) over (1:10.3.27-0+deb10u1) ...
Preparing to unpack .../52-libmariadb3_1%3a10.3.29-0+deb10u1_armhf.deb ...
Unpacking libmariadb3:armhf (1:10.3.29-0+deb10u1) over (1:10.3.27-0+deb10u1) ...
Preparing to unpack .../53-libvlccore9_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking libvlccore9:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../54-vlc-plugin-skins2_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-plugin-skins2:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../55-vlc_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../56-vlc-plugin-qt_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-plugin-qt:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../57-vlc-plugin-video-output_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-plugin-video-output:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../58-vlc-l10n_3.0.12-0+deb10u1+rpt2_all.deb ...
Unpacking vlc-l10n (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../59-vlc-plugin-base_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-plugin-base:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../60-vlc-data_3.0.12-0+deb10u1+rpt2_all.deb ...
Unpacking vlc-data (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../61-libvlc5_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking libvlc5:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../62-vlc-bin_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-bin (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../63-libvlc-bin_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking libvlc-bin:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../64-linux-libc-dev_1%3a1.20210805-1_armhf.deb ...
Unpacking linux-libc-dev:armhf (1:1.20210805-1) over (4.18.20-2+rpi1) ...
Preparing to unpack .../65-mesa-va-drivers_19.3.2-1~bpo10+1~rpt4_armhf.deb ...
Unpacking mesa-va-drivers:armhf (19.3.2-1~bpo10+1~rpt4) over (19.3.2-1~bpo10+1~rpt3) ...
Preparing to unpack .../66-mesa-vdpau-drivers_19.3.2-1~bpo10+1~rpt4_armhf.deb ...
Unpacking mesa-vdpau-drivers:armhf (19.3.2-1~bpo10+1~rpt4) over (19.3.2-1~bpo10+1~rpt3) ...
Preparing to unpack .../67-raspberrypi-ui-mods_1.20210706_armhf.deb ...
Unpacking raspberrypi-ui-mods (1.20210706) over (1.20201210+nmu1) ...
Preparing to unpack .../68-raspberrypi-sys-mods_20210706_armhf.deb ...
Unpacking raspberrypi-sys-mods (20210706) over (20210310) ...
Preparing to unpack .../69-pi-bluetooth_0.1.17_all.deb ...
Unpacking pi-bluetooth (0.1.17) over (0.1.15) ...
Preparing to unpack .../70-python-gpiozero_1.6.2-1_all.deb ...
Unpacking python-gpiozero (1.6.2-1) over (1.5.1) ...
Preparing to unpack .../71-python-spidev_20200602~200721-1~buster_armhf.deb ...
Unpacking python-spidev (20200602~200721-1~buster) over (20190221~182651-1) ...
Preparing to unpack .../72-python3-gpiozero_1.6.2-1_all.deb ...
Unpacking python3-gpiozero (1.6.2-1) over (1.5.1) ...
Preparing to unpack .../73-python3-spidev_20200602~200721-1~buster_armhf.deb ...
Unpacking python3-spidev (20200602~200721-1~buster) over (20190221~182651-1) ...
Preparing to unpack .../74-rp-bookshelf_0.14_armhf.deb ...
Unpacking rp-bookshelf (0.14) over (0.9) ...
Preparing to unpack .../75-rp-prefapps_0.34_armhf.deb ...
Unpacking rp-prefapps (0.34) over (0.33) ...
Preparing to unpack .../76-rpi-eeprom_12.9-1_armhf.deb ...
Unpacking rpi-eeprom (12.9-1) over (12.3-1) ...
Preparing to unpack .../77-rpi-update_20210618_all.deb ...
Unpacking rpi-update (20210618) over (20200409) ...
Preparing to unpack .../78-thonny_3.3.10-1+rpt1_all.deb ...
Unpacking thonny (3.3.10-1+rpt1) over (3.3.6-1+rpt1) ...
Preparing to unpack .../79-vlc-plugin-notify_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-plugin-notify:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../80-vlc-plugin-samba_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-plugin-samba:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../81-vlc-plugin-video-splitter_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-plugin-video-splitter:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Preparing to unpack .../82-vlc-plugin-visualization_3.0.12-0+deb10u1+rpt2_armhf.deb ...
Unpacking vlc-plugin-visualization:armhf (3.0.12-0+deb10u1+rpt2) over (3.0.12-0+deb10u1+rpt1) ...
Setting up python-spidev (20200602~200721-1~buster) ...
Setting up rp-prefapps (0.34) ...
Setting up libx11-xcb1:armhf (2:1.6.7-1+deb10u2) ...
Setting up libgles2-mesa:armhf (19.3.2-1~bpo10+1~rpt4) ...
Setting up libgbm1:armhf (19.3.2-1~bpo10+1~rpt4) ...
Setting up python-gpiozero (1.6.2-1) ...
Setting up libaspell15:armhf (0.60.7~20110707-6+deb10u1) ...
Setting up firmware-atheros (1:20190114-2+rpt1) ...
Setting up firmware-misc-nonfree (1:20190114-2+rpt1) ...
update-initramfs: deferring update (trigger activated)
Setting up libjavascriptcoregtk-4.0-18:armhf (2.32.3-1~deb10u1+rpi1) ...
Setting up linux-libc-dev:armhf (1:1.20210805-1) ...
Setting up isc-dhcp-client (4.4.1-2+deb10u1) ...
Setting up systemd (241-7~deb10u8+rpi1) ...
Setting up vlc-l10n (3.0.12-0+deb10u1+rpt2) ...
Setting up raspberrypi-sys-mods (20210706) ...
Setting up python3-spidev (20200602~200721-1~buster) ...
Setting up raspberrypi-kernel (1:1.20210805-1) ...
Removing 'diversion of /boot/kernel.img to /usr/share/rpikernelhack/kernel.img by rpikernelhack'
Removing 'diversion of /boot/kernel7.img to /usr/share/rpikernelhack/kernel7.img by rpikernelhack'
Removing 'diversion of /boot/kernel7l.img to /usr/share/rpikernelhack/kernel7l.img by rpikernelhack'
Removing 'diversion of /boot/kernel8.img to /usr/share/rpikernelhack/kernel8.img by rpikernelhack'
Removing 'diversion of /boot/bcm2708-rpi-b-plus.dtb to /usr/share/rpikernelhack/bcm2708-rpi-b-plus.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2708-rpi-b-rev1.dtb to /usr/share/rpikernelhack/bcm2708-rpi-b-rev1.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2708-rpi-b.dtb to /usr/share/rpikernelhack/bcm2708-rpi-b.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2708-rpi-cm.dtb to /usr/share/rpikernelhack/bcm2708-rpi-cm.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2708-rpi-zero-w.dtb to /usr/share/rpikernelhack/bcm2708-rpi-zero-w.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2708-rpi-zero.dtb to /usr/share/rpikernelhack/bcm2708-rpi-zero.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2709-rpi-2-b.dtb to /usr/share/rpikernelhack/bcm2709-rpi-2-b.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2710-rpi-2-b.dtb to /usr/share/rpikernelhack/bcm2710-rpi-2-b.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2710-rpi-3-b-plus.dtb to /usr/share/rpikernelhack/bcm2710-rpi-3-b-plus.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2710-rpi-3-b.dtb to /usr/share/rpikernelhack/bcm2710-rpi-3-b.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2710-rpi-cm3.dtb to /usr/share/rpikernelhack/bcm2710-rpi-cm3.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2711-rpi-4-b.dtb to /usr/share/rpikernelhack/bcm2711-rpi-4-b.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2711-rpi-400.dtb to /usr/share/rpikernelhack/bcm2711-rpi-400.dtb by rpikernelhack'
Removing 'diversion of /boot/bcm2711-rpi-cm4.dtb to /usr/share/rpikernelhack/bcm2711-rpi-cm4.dtb by rpikernelhack'
Removing 'diversion of /boot/COPYING.linux to /usr/share/rpikernelhack/COPYING.linux by rpikernelhack'
Removing 'diversion of /boot/overlays/README to /usr/share/rpikernelhack/overlays/README by rpikernelhack'
Removing 'diversion of /boot/overlays/act-led.dtbo to /usr/share/rpikernelhack/overlays/act-led.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/adafruit18.dtbo to /usr/share/rpikernelhack/overlays/adafruit18.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/adau1977-adc.dtbo to /usr/share/rpikernelhack/overlays/adau1977-adc.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/adau7002-simple.dtbo to /usr/share/rpikernelhack/overlays/adau7002-simple.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ads1015.dtbo to /usr/share/rpikernelhack/overlays/ads1015.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ads1115.dtbo to /usr/share/rpikernelhack/overlays/ads1115.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ads7846.dtbo to /usr/share/rpikernelhack/overlays/ads7846.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/adv7282m.dtbo to /usr/share/rpikernelhack/overlays/adv7282m.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/adv728x-m.dtbo to /usr/share/rpikernelhack/overlays/adv728x-m.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/akkordion-iqdacplus.dtbo to /usr/share/rpikernelhack/overlays/akkordion-iqdacplus.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/allo-boss-dac-pcm512x-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-boss-dac-pcm512x-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/allo-boss2-dac-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-boss2-dac-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/allo-digione.dtbo to /usr/share/rpikernelhack/overlays/allo-digione.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/allo-katana-dac-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-katana-dac-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/allo-piano-dac-pcm512x-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-piano-dac-pcm512x-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/allo-piano-dac-plus-pcm512x-audio.dtbo to /usr/share/rpikernelhack/overlays/allo-piano-dac-plus-pcm512x-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/anyspi.dtbo to /usr/share/rpikernelhack/overlays/anyspi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/apds9960.dtbo to /usr/share/rpikernelhack/overlays/apds9960.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/applepi-dac.dtbo to /usr/share/rpikernelhack/overlays/applepi-dac.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/at86rf233.dtbo to /usr/share/rpikernelhack/overlays/at86rf233.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/audioinjector-addons.dtbo to /usr/share/rpikernelhack/overlays/audioinjector-addons.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/audioinjector-isolated-soundcard.dtbo to /usr/share/rpikernelhack/overlays/audioinjector-isolated-soundcard.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/audioinjector-ultra.dtbo to /usr/share/rpikernelhack/overlays/audioinjector-ultra.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/audioinjector-wm8731-audio.dtbo to /usr/share/rpikernelhack/overlays/audioinjector-wm8731-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/audiosense-pi.dtbo to /usr/share/rpikernelhack/overlays/audiosense-pi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/audremap.dtbo to /usr/share/rpikernelhack/overlays/audremap.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/balena-fin.dtbo to /usr/share/rpikernelhack/overlays/balena-fin.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/cap1106.dtbo to /usr/share/rpikernelhack/overlays/cap1106.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/chipdip-dac.dtbo to /usr/share/rpikernelhack/overlays/chipdip-dac.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/cma.dtbo to /usr/share/rpikernelhack/overlays/cma.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/dht11.dtbo to /usr/share/rpikernelhack/overlays/dht11.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/dionaudio-loco-v2.dtbo to /usr/share/rpikernelhack/overlays/dionaudio-loco-v2.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/dionaudio-loco.dtbo to /usr/share/rpikernelhack/overlays/dionaudio-loco.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/disable-bt.dtbo to /usr/share/rpikernelhack/overlays/disable-bt.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/disable-wifi.dtbo to /usr/share/rpikernelhack/overlays/disable-wifi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/dpi18.dtbo to /usr/share/rpikernelhack/overlays/dpi18.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/dpi18cpadhi.dtbo to /usr/share/rpikernelhack/overlays/dpi18cpadhi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/dpi24.dtbo to /usr/share/rpikernelhack/overlays/dpi24.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/draws.dtbo to /usr/share/rpikernelhack/overlays/draws.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/dwc-otg.dtbo to /usr/share/rpikernelhack/overlays/dwc-otg.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/dwc2.dtbo to /usr/share/rpikernelhack/overlays/dwc2.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/edt-ft5406.dtbo to /usr/share/rpikernelhack/overlays/edt-ft5406.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/enc28j60-spi2.dtbo to /usr/share/rpikernelhack/overlays/enc28j60-spi2.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/enc28j60.dtbo to /usr/share/rpikernelhack/overlays/enc28j60.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/exc3000.dtbo to /usr/share/rpikernelhack/overlays/exc3000.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/fe-pi-audio.dtbo to /usr/share/rpikernelhack/overlays/fe-pi-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/fsm-demo.dtbo to /usr/share/rpikernelhack/overlays/fsm-demo.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ghost-amp.dtbo to /usr/share/rpikernelhack/overlays/ghost-amp.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/goodix.dtbo to /usr/share/rpikernelhack/overlays/goodix.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/googlevoicehat-soundcard.dtbo to /usr/share/rpikernelhack/overlays/googlevoicehat-soundcard.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-fan.dtbo to /usr/share/rpikernelhack/overlays/gpio-fan.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-ir-tx.dtbo to /usr/share/rpikernelhack/overlays/gpio-ir-tx.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-ir.dtbo to /usr/share/rpikernelhack/overlays/gpio-ir.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-key.dtbo to /usr/share/rpikernelhack/overlays/gpio-key.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-led.dtbo to /usr/share/rpikernelhack/overlays/gpio-led.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-no-bank0-irq.dtbo to /usr/share/rpikernelhack/overlays/gpio-no-bank0-irq.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-no-irq.dtbo to /usr/share/rpikernelhack/overlays/gpio-no-irq.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-poweroff.dtbo to /usr/share/rpikernelhack/overlays/gpio-poweroff.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/gpio-shutdown.dtbo to /usr/share/rpikernelhack/overlays/gpio-shutdown.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hd44780-lcd.dtbo to /usr/share/rpikernelhack/overlays/hd44780-lcd.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hdmi-backlight-hwhack-gpio.dtbo to /usr/share/rpikernelhack/overlays/hdmi-backlight-hwhack-gpio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-amp.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-amp.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-amp100.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-amp100.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-dac.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dac.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-dacplus.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplus.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-dacplusadc.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplusadc.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-dacplusadcpro.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplusadcpro.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-dacplusdsp.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplusdsp.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-dacplushd.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-dacplushd.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-digi-pro.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-digi-pro.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hifiberry-digi.dtbo to /usr/share/rpikernelhack/overlays/hifiberry-digi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/highperi.dtbo to /usr/share/rpikernelhack/overlays/highperi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hy28a.dtbo to /usr/share/rpikernelhack/overlays/hy28a.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hy28b-2017.dtbo to /usr/share/rpikernelhack/overlays/hy28b-2017.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/hy28b.dtbo to /usr/share/rpikernelhack/overlays/hy28b.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i-sabre-q2m.dtbo to /usr/share/rpikernelhack/overlays/i-sabre-q2m.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c-bcm2708.dtbo to /usr/share/rpikernelhack/overlays/i2c-bcm2708.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c-gpio.dtbo to /usr/share/rpikernelhack/overlays/i2c-gpio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c-mux.dtbo to /usr/share/rpikernelhack/overlays/i2c-mux.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c-pwm-pca9685a.dtbo to /usr/share/rpikernelhack/overlays/i2c-pwm-pca9685a.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c-rtc-gpio.dtbo to /usr/share/rpikernelhack/overlays/i2c-rtc-gpio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c-rtc.dtbo to /usr/share/rpikernelhack/overlays/i2c-rtc.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c-sensor.dtbo to /usr/share/rpikernelhack/overlays/i2c-sensor.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c0.dtbo to /usr/share/rpikernelhack/overlays/i2c0.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c1.dtbo to /usr/share/rpikernelhack/overlays/i2c1.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c3.dtbo to /usr/share/rpikernelhack/overlays/i2c3.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c4.dtbo to /usr/share/rpikernelhack/overlays/i2c4.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c5.dtbo to /usr/share/rpikernelhack/overlays/i2c5.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2c6.dtbo to /usr/share/rpikernelhack/overlays/i2c6.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/i2s-gpio28-31.dtbo to /usr/share/rpikernelhack/overlays/i2s-gpio28-31.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ilitek251x.dtbo to /usr/share/rpikernelhack/overlays/ilitek251x.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/imx219.dtbo to /usr/share/rpikernelhack/overlays/imx219.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/imx290.dtbo to /usr/share/rpikernelhack/overlays/imx290.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/imx378.dtbo to /usr/share/rpikernelhack/overlays/imx378.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/imx477.dtbo to /usr/share/rpikernelhack/overlays/imx477.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/iqaudio-codec.dtbo to /usr/share/rpikernelhack/overlays/iqaudio-codec.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/iqaudio-dac.dtbo to /usr/share/rpikernelhack/overlays/iqaudio-dac.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/iqaudio-dacplus.dtbo to /usr/share/rpikernelhack/overlays/iqaudio-dacplus.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/iqaudio-digi-wm8804-audio.dtbo to /usr/share/rpikernelhack/overlays/iqaudio-digi-wm8804-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/irs1125.dtbo to /usr/share/rpikernelhack/overlays/irs1125.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/jedec-spi-nor.dtbo to /usr/share/rpikernelhack/overlays/jedec-spi-nor.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/justboom-both.dtbo to /usr/share/rpikernelhack/overlays/justboom-both.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/justboom-dac.dtbo to /usr/share/rpikernelhack/overlays/justboom-dac.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/justboom-digi.dtbo to /usr/share/rpikernelhack/overlays/justboom-digi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ltc294x.dtbo to /usr/share/rpikernelhack/overlays/ltc294x.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/max98357a.dtbo to /usr/share/rpikernelhack/overlays/max98357a.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/maxtherm.dtbo to /usr/share/rpikernelhack/overlays/maxtherm.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mbed-dac.dtbo to /usr/share/rpikernelhack/overlays/mbed-dac.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mcp23017.dtbo to /usr/share/rpikernelhack/overlays/mcp23017.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mcp23s17.dtbo to /usr/share/rpikernelhack/overlays/mcp23s17.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mcp2515-can0.dtbo to /usr/share/rpikernelhack/overlays/mcp2515-can0.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mcp2515-can1.dtbo to /usr/share/rpikernelhack/overlays/mcp2515-can1.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mcp251xfd.dtbo to /usr/share/rpikernelhack/overlays/mcp251xfd.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mcp3008.dtbo to /usr/share/rpikernelhack/overlays/mcp3008.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mcp3202.dtbo to /usr/share/rpikernelhack/overlays/mcp3202.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mcp342x.dtbo to /usr/share/rpikernelhack/overlays/mcp342x.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/media-center.dtbo to /usr/share/rpikernelhack/overlays/media-center.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/merus-amp.dtbo to /usr/share/rpikernelhack/overlays/merus-amp.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/midi-uart0.dtbo to /usr/share/rpikernelhack/overlays/midi-uart0.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/midi-uart1.dtbo to /usr/share/rpikernelhack/overlays/midi-uart1.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/minipitft13.dtbo to /usr/share/rpikernelhack/overlays/minipitft13.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/miniuart-bt.dtbo to /usr/share/rpikernelhack/overlays/miniuart-bt.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mmc.dtbo to /usr/share/rpikernelhack/overlays/mmc.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mpu6050.dtbo to /usr/share/rpikernelhack/overlays/mpu6050.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/mz61581.dtbo to /usr/share/rpikernelhack/overlays/mz61581.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ov5647.dtbo to /usr/share/rpikernelhack/overlays/ov5647.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ov7251.dtbo to /usr/share/rpikernelhack/overlays/ov7251.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ov9281.dtbo to /usr/share/rpikernelhack/overlays/ov9281.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/overlay_map.dtb to /usr/share/rpikernelhack/overlays/overlay_map.dtb by rpikernelhack'
Removing 'diversion of /boot/overlays/papirus.dtbo to /usr/share/rpikernelhack/overlays/papirus.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pca953x.dtbo to /usr/share/rpikernelhack/overlays/pca953x.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pcie-32bit-dma.dtbo to /usr/share/rpikernelhack/overlays/pcie-32bit-dma.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pibell.dtbo to /usr/share/rpikernelhack/overlays/pibell.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pifacedigital.dtbo to /usr/share/rpikernelhack/overlays/pifacedigital.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pifi-40.dtbo to /usr/share/rpikernelhack/overlays/pifi-40.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pifi-dac-hd.dtbo to /usr/share/rpikernelhack/overlays/pifi-dac-hd.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pifi-dac-zero.dtbo to /usr/share/rpikernelhack/overlays/pifi-dac-zero.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pifi-mini-210.dtbo to /usr/share/rpikernelhack/overlays/pifi-mini-210.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/piglow.dtbo to /usr/share/rpikernelhack/overlays/piglow.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/piscreen.dtbo to /usr/share/rpikernelhack/overlays/piscreen.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/piscreen2r.dtbo to /usr/share/rpikernelhack/overlays/piscreen2r.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pisound.dtbo to /usr/share/rpikernelhack/overlays/pisound.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pitft22.dtbo to /usr/share/rpikernelhack/overlays/pitft22.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pitft28-capacitive.dtbo to /usr/share/rpikernelhack/overlays/pitft28-capacitive.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pitft28-resistive.dtbo to /usr/share/rpikernelhack/overlays/pitft28-resistive.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pitft35-resistive.dtbo to /usr/share/rpikernelhack/overlays/pitft35-resistive.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pps-gpio.dtbo to /usr/share/rpikernelhack/overlays/pps-gpio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pwm-2chan.dtbo to /usr/share/rpikernelhack/overlays/pwm-2chan.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pwm-ir-tx.dtbo to /usr/share/rpikernelhack/overlays/pwm-ir-tx.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/pwm.dtbo to /usr/share/rpikernelhack/overlays/pwm.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/qca7000.dtbo to /usr/share/rpikernelhack/overlays/qca7000.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rotary-encoder.dtbo to /usr/share/rpikernelhack/overlays/rotary-encoder.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-backlight.dtbo to /usr/share/rpikernelhack/overlays/rpi-backlight.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-cirrus-wm5102.dtbo to /usr/share/rpikernelhack/overlays/rpi-cirrus-wm5102.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-dac.dtbo to /usr/share/rpikernelhack/overlays/rpi-dac.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-display.dtbo to /usr/share/rpikernelhack/overlays/rpi-display.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-ft5406.dtbo to /usr/share/rpikernelhack/overlays/rpi-ft5406.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-poe-plus.dtbo to /usr/share/rpikernelhack/overlays/rpi-poe-plus.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-poe.dtbo to /usr/share/rpikernelhack/overlays/rpi-poe.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-proto.dtbo to /usr/share/rpikernelhack/overlays/rpi-proto.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-sense.dtbo to /usr/share/rpikernelhack/overlays/rpi-sense.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpi-tv.dtbo to /usr/share/rpikernelhack/overlays/rpi-tv.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rpivid-v4l2.dtbo to /usr/share/rpikernelhack/overlays/rpivid-v4l2.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/rra-digidac1-wm8741-audio.dtbo to /usr/share/rpikernelhack/overlays/rra-digidac1-wm8741-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sainsmart18.dtbo to /usr/share/rpikernelhack/overlays/sainsmart18.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sc16is750-i2c.dtbo to /usr/share/rpikernelhack/overlays/sc16is750-i2c.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sc16is752-i2c.dtbo to /usr/share/rpikernelhack/overlays/sc16is752-i2c.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sc16is752-spi0.dtbo to /usr/share/rpikernelhack/overlays/sc16is752-spi0.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sc16is752-spi1.dtbo to /usr/share/rpikernelhack/overlays/sc16is752-spi1.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sdhost.dtbo to /usr/share/rpikernelhack/overlays/sdhost.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sdio.dtbo to /usr/share/rpikernelhack/overlays/sdio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/seeed-can-fd-hat-v1.dtbo to /usr/share/rpikernelhack/overlays/seeed-can-fd-hat-v1.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/seeed-can-fd-hat-v2.dtbo to /usr/share/rpikernelhack/overlays/seeed-can-fd-hat-v2.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sh1106-spi.dtbo to /usr/share/rpikernelhack/overlays/sh1106-spi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/si446x-spi0.dtbo to /usr/share/rpikernelhack/overlays/si446x-spi0.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/smi-dev.dtbo to /usr/share/rpikernelhack/overlays/smi-dev.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/smi-nand.dtbo to /usr/share/rpikernelhack/overlays/smi-nand.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/smi.dtbo to /usr/share/rpikernelhack/overlays/smi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi-gpio35-39.dtbo to /usr/share/rpikernelhack/overlays/spi-gpio35-39.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi-gpio40-45.dtbo to /usr/share/rpikernelhack/overlays/spi-gpio40-45.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi-rtc.dtbo to /usr/share/rpikernelhack/overlays/spi-rtc.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi0-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi0-1cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi0-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi0-2cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi1-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi1-1cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi1-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi1-2cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi1-3cs.dtbo to /usr/share/rpikernelhack/overlays/spi1-3cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi2-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi2-1cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi2-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi2-2cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi2-3cs.dtbo to /usr/share/rpikernelhack/overlays/spi2-3cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi3-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi3-1cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi3-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi3-2cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi4-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi4-1cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi4-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi4-2cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi5-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi5-1cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi5-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi5-2cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi6-1cs.dtbo to /usr/share/rpikernelhack/overlays/spi6-1cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/spi6-2cs.dtbo to /usr/share/rpikernelhack/overlays/spi6-2cs.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ssd1306-spi.dtbo to /usr/share/rpikernelhack/overlays/ssd1306-spi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ssd1306.dtbo to /usr/share/rpikernelhack/overlays/ssd1306.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ssd1331-spi.dtbo to /usr/share/rpikernelhack/overlays/ssd1331-spi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ssd1351-spi.dtbo to /usr/share/rpikernelhack/overlays/ssd1351-spi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/superaudioboard.dtbo to /usr/share/rpikernelhack/overlays/superaudioboard.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/sx150x.dtbo to /usr/share/rpikernelhack/overlays/sx150x.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/tc358743-audio.dtbo to /usr/share/rpikernelhack/overlays/tc358743-audio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/tc358743.dtbo to /usr/share/rpikernelhack/overlays/tc358743.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/tinylcd35.dtbo to /usr/share/rpikernelhack/overlays/tinylcd35.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/tpm-slb9670.dtbo to /usr/share/rpikernelhack/overlays/tpm-slb9670.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/uart0.dtbo to /usr/share/rpikernelhack/overlays/uart0.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/uart1.dtbo to /usr/share/rpikernelhack/overlays/uart1.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/uart2.dtbo to /usr/share/rpikernelhack/overlays/uart2.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/uart3.dtbo to /usr/share/rpikernelhack/overlays/uart3.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/uart4.dtbo to /usr/share/rpikernelhack/overlays/uart4.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/uart5.dtbo to /usr/share/rpikernelhack/overlays/uart5.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/udrc.dtbo to /usr/share/rpikernelhack/overlays/udrc.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/ugreen-dabboard.dtbo to /usr/share/rpikernelhack/overlays/ugreen-dabboard.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/upstream-pi4.dtbo to /usr/share/rpikernelhack/overlays/upstream-pi4.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/upstream.dtbo to /usr/share/rpikernelhack/overlays/upstream.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-fkms-v3d-pi4.dtbo to /usr/share/rpikernelhack/overlays/vc4-fkms-v3d-pi4.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-fkms-v3d.dtbo to /usr/share/rpikernelhack/overlays/vc4-fkms-v3d.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-kms-dpi-at056tn53v1.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-dpi-at056tn53v1.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-kms-dsi-7inch.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-dsi-7inch.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-kms-dsi-lt070me05000-v2.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-dsi-lt070me05000-v2.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-kms-dsi-lt070me05000.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-dsi-lt070me05000.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-kms-kippah-7inch.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-kippah-7inch.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-kms-v3d-pi4.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-v3d-pi4.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-kms-v3d.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-v3d.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vc4-kms-vga666.dtbo to /usr/share/rpikernelhack/overlays/vc4-kms-vga666.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/vga666.dtbo to /usr/share/rpikernelhack/overlays/vga666.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/w1-gpio-pullup.dtbo to /usr/share/rpikernelhack/overlays/w1-gpio-pullup.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/w1-gpio.dtbo to /usr/share/rpikernelhack/overlays/w1-gpio.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/w5500.dtbo to /usr/share/rpikernelhack/overlays/w5500.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/wittypi.dtbo to /usr/share/rpikernelhack/overlays/wittypi.dtbo by rpikernelhack'
Removing 'diversion of /boot/overlays/wm8960-soundcard.dtbo to /usr/share/rpikernelhack/overlays/wm8960-soundcard.dtbo by rpikernelhack'
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 5.10.52+ /boot/kernel.img
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 5.10.52+ /boot/kernel.img
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 5.10.52-v7+ /boot/kernel7.img
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 5.10.52-v7+ /boot/kernel7.img
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 5.10.52-v7l+ /boot/kernel7l.img
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 5.10.52-v7l+ /boot/kernel7l.img
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 5.10.52-v8+ /boot/kernel8.img
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 5.10.52-v8+ /boot/kernel8.img
Setting up libkrb5support0:armhf (1.17-3+deb10u2) ...
Setting up mariadb-common (1:10.3.29-0+deb10u1) ...
Setting up raspberrypi-ui-mods (1.20210706) ...
Setting up libklibc:armhf (2.0.6-1+rpi1+deb10u1) ...
Setting up firmware-brcm80211 (1:20190114-2+rpt1) ...
Setting up python3-gpiozero (1.6.2-1) ...
Setting up libx11-data (2:1.6.7-1+deb10u2) ...
Setting up firmware-realtek (1:20190114-2+rpt1) ...
update-initramfs: deferring update (trigger activated)
Setting up liblirc-client0:armhf (0.10.1-6.3~deb10u1+rpt1) ...
Setting up rpi-update (20210618) ...
Setting up udev (241-7~deb10u8+rpi1) ...
update-initramfs: deferring update (trigger activated)
Setting up libwebp6:armhf (0.6.1-2+deb10u1) ...
Setting up libmariadb3:armhf (1:10.3.29-0+deb10u1) ...
Setting up raspberrypi-bootloader (1:1.20210805-1) ...
Removing 'diversion of /boot/start.elf to /usr/share/rpikernelhack/start.elf by rpikernelhack'
Removing 'diversion of /boot/start_cd.elf to /usr/share/rpikernelhack/start_cd.elf by rpikernelhack'
Removing 'diversion of /boot/start_db.elf to /usr/share/rpikernelhack/start_db.elf by rpikernelhack'
Removing 'diversion of /boot/start_x.elf to /usr/share/rpikernelhack/start_x.elf by rpikernelhack'
Removing 'diversion of /boot/fixup.dat to /usr/share/rpikernelhack/fixup.dat by rpikernelhack'
Removing 'diversion of /boot/fixup_cd.dat to /usr/share/rpikernelhack/fixup_cd.dat by rpikernelhack'
Removing 'diversion of /boot/fixup_db.dat to /usr/share/rpikernelhack/fixup_db.dat by rpikernelhack'
Removing 'diversion of /boot/fixup_x.dat to /usr/share/rpikernelhack/fixup_x.dat by rpikernelhack'
Removing 'diversion of /boot/bootcode.bin to /usr/share/rpikernelhack/bootcode.bin by rpikernelhack'
Removing 'diversion of /boot/start4.elf to /usr/share/rpikernelhack/start4.elf by rpikernelhack'
Removing 'diversion of /boot/start4cd.elf to /usr/share/rpikernelhack/start4cd.elf by rpikernelhack'
Removing 'diversion of /boot/start4db.elf to /usr/share/rpikernelhack/start4db.elf by rpikernelhack'
Removing 'diversion of /boot/start4x.elf to /usr/share/rpikernelhack/start4x.elf by rpikernelhack'
Removing 'diversion of /boot/fixup4.dat to /usr/share/rpikernelhack/fixup4.dat by rpikernelhack'
Removing 'diversion of /boot/fixup4cd.dat to /usr/share/rpikernelhack/fixup4cd.dat by rpikernelhack'
Removing 'diversion of /boot/fixup4db.dat to /usr/share/rpikernelhack/fixup4db.dat by rpikernelhack'
Removing 'diversion of /boot/fixup4x.dat to /usr/share/rpikernelhack/fixup4x.dat by rpikernelhack'
Removing 'diversion of /boot/LICENCE.broadcom to /usr/share/rpikernelhack/LICENCE.broadcom by rpikernelhack'
Setting up aspell (0.60.7~20110707-6+deb10u1) ...
Setting up libk5crypto3:armhf (1.17-3+deb10u2) ...
Setting up rp-bookshelf (0.14) ...
Setting up libglapi-mesa:armhf (19.3.2-1~bpo10+1~rpt4) ...
Setting up libvlccore9:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up libraspberrypi0 (1:1.20210805-1) ...
Setting up firmware-libertas (1:20190114-2+rpt1) ...
Setting up libx11-6:armhf (2:1.6.7-1+deb10u2) ...
Setting up isc-dhcp-common (4.4.1-2+deb10u1) ...
Setting up libkrb5-3:armhf (1.17-3+deb10u2) ...
Setting up libsndfile1:armhf (1.0.28-6+deb10u1) ...
Setting up mesa-va-drivers:armhf (19.3.2-1~bpo10+1~rpt4) ...
Setting up klibc-utils (2.0.6-1+rpi1+deb10u1) ...
Setting up libwebpmux3:armhf (0.6.1-2+deb10u1) ...
Setting up libxml2:armhf (2.9.4+dfsg1-7+deb10u2) ...
Setting up vlc-data (3.0.12-0+deb10u1+rpt2) ...
Setting up thonny (3.3.10-1+rpt1) ...
Setting up vlc-plugin-notify:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up vlc-plugin-video-output:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up vlc-plugin-samba:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up mesa-vdpau-drivers:armhf (19.3.2-1~bpo10+1~rpt4) ...
Setting up systemd-sysv (241-7~deb10u8+rpi1) ...
Setting up libfluidsynth1:armhf (1.1.11-1+deb10u1) ...
Setting up gpicview (0.2.5-2+rpt1) ...
update-alternatives: using /usr/bin/gpicview to provide /usr/bin/display (display) in auto mode
Setting up libwebpdemux2:armhf (0.6.1-2+deb10u1) ...
Setting up vlc-plugin-video-splitter:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up libgl1-mesa-dri:armhf (19.3.2-1~bpo10+1~rpt4) ...
Setting up libvlc5:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up libraspberrypi-doc (1:1.20210805-1) ...
Setting up dillo (3.0.5-5+rpt1) ...
Setting up libraspberrypi-bin (1:1.20210805-1) ...
Setting up libavutil56:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up bluez (5.50-1.2~deb10u2) ...
Setting up vlc-plugin-visualization:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up libegl-mesa0:armhf (19.3.2-1~bpo10+1~rpt4) ...
Setting up libgssapi-krb5-2:armhf (1.17-3+deb10u2) ...
Setting up libpostproc55:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up libraspberrypi-dev (1:1.20210805-1) ...
Setting up libwebkit2gtk-4.0-37:armhf (2.32.3-1~deb10u1+rpi1) ...
Setting up vlc-plugin-qt:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up libvlc-bin:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up libpam-systemd:armhf (241-7~deb10u8+rpi1) ...
Setting up rpi-eeprom (12.9-1) ...
Setting up libswscale5:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up libglx-mesa0:armhf (19.3.2-1~bpo10+1~rpt4) ...
Setting up vlc-plugin-skins2:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up pi-bluetooth (0.1.17) ...
Job for hciuart.service failed because the control process exited with error code.
See "systemctl status hciuart.service" and "journalctl -xe" for details.
Job for hciuart.service failed because the control process exited with error code.
See "systemctl status hciuart.service" and "journalctl -xe" for details.
Setting up vlc-bin (3.0.12-0+deb10u1+rpt2) ...
Setting up libswresample3:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up libavresample4:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up libavcodec58:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up libavformat58:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up libavfilter7:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up vlc-plugin-base:armhf (3.0.12-0+deb10u1+rpt2) ...
Setting up vlc (3.0.12-0+deb10u1+rpt2) ...
Setting up libavdevice58:armhf (7:4.1.6-1~deb10u1+rpt2) ...
Setting up ffmpeg (7:4.1.6-1~deb10u1+rpt2) ...
Processing triggers for desktop-file-utils (0.23-4) ...
Processing triggers for mime-support (3.62) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.31.4-3) ...
Processing triggers for libc-bin (2.28-10+rpi1) ...
Processing triggers for man-db (2.8.5-2) ...
Processing triggers for dbus (1.12.20-0+deb10u1) ...
Processing triggers for shared-mime-info (1.10-1) ...
Processing triggers for install-info (6.5.0.dfsg.1-4+b1) ...
Processing triggers for initramfs-tools (0.133+deb10u1) ...
Processing triggers for dictionaries-common (1.28.1) ...
Processing triggers for libvlc-bin:armhf (3.0.12-0+deb10u1+rpt2) ...
pi@raspberrypi:~ $

```

```
pi@raspberrypi:~ $ sudo raspi-config
```


```
pi@raspberrypi:~ $ sudo apt install fonts-unfonts-core
패키지 목록을 읽는 중입니다... 완료
의존성 트리를 만드는 중입니다       
상태 정보를 읽는 중입니다... 완료
다음 패키지가 자동으로 설치되었지만 더 이상 필요하지 않습니다:
  python-colorzero
Use 'sudo apt autoremove' to remove it.
다음 새 패키지를 설치할 것입니다:
  fonts-unfonts-core
0개 업그레이드, 1개 새로 설치, 0개 제거 및 0개 업그레이드 안 함.
14.9 M바이트 아카이브를 받아야 합니다.
이 작업 후 34.3 M바이트의 디스크 공간을 더 사용하게 됩니다.
받기:1 http://ftp.harukasan.org/raspbian/raspbian buster/main armhf fonts-unfonts-core all 1:1.0.2-080608-16 [14.9 MB]
내려받기 14.9 M바이트, 소요시간 1분 55초 (129 k바이트/초)                      
Selecting previously unselected package fonts-unfonts-core.
(데이터베이스 읽는중 ...현재 98827개의 파일과 디렉터리가 설치되어 있습니다.)
Preparing to unpack .../fonts-unfonts-core_1%3a1.0.2-080608-16_all.deb ...
Unpacking fonts-unfonts-core (1:1.0.2-080608-16) ...
fonts-unfonts-core (1:1.0.2-080608-16) 설정하는 중입니다 ...
Processing triggers for fontconfig (2.13.1-2) ...
pi@raspberrypi:~ $

```

```
pi@raspberrypi:~ $ sudo apt autoremove
패키지 목록을 읽는 중입니다... 완료
의존성 트리를 만드는 중입니다       
상태 정보를 읽는 중입니다... 완료
다음 패키지를 지울 것입니다:
  python-colorzero
0개 업그레이드, 0개 새로 설치, 1개 제거 및 0개 업그레이드 안 함.
이 작업 후 130 k바이트의 디스크 공간이 비워집니다.
계속 하시겠습니까? [Y/n] y
(데이터베이스 읽는중 ...현재 98845개의 파일과 디렉터리가 설치되어 있습니다.)
Removing python-colorzero (1.1) ...
pi@raspberrypi:~ $
```

```
pi@raspberrypi:/home $ sudo passwd root
새  암호:
새  암호 재입력:
passwd: 암호를 성공적으로 업데이트했습니다
pi@raspberrypi:/home $
```


## P.S
쓰다보니 너무 장황하게 쓴거 같다. 초보로 고생한 내용들을 쓰다가 보니...

어쨌든 Windows에 익숙했던 단어들이 다르게 쓰이는 경우를 경험할 수 있어서 나름 재미있었다.
> HDD, SSD, CD-ROM 등도 개념은 비슷하니 검색해보면 쉽게 될 듯...

[INDEX로 돌아가기](/posts/RaspberryPi/)
