---
title: Raspberry Pi 4B(4GB) - 작지만 강력한 성능의 미니 컴퓨터
author: FlyingDeuk
date: 2020-08-16 20:55:00 +0800
categories: [Living, Device]
tags: [usefulthing, linux, raspberrypi]
pin:
---

![pi](/img/living/pi/pi.jpg)

`FlyingDeuk's`
> 영국에서 개발도상국에 배포하기 위한 미니 컴퓨터를 개발하게 되었고 저렴한 가격에 최소의 성능으로 모두가 컴퓨터를 접하고 경험하게 하기위해 판매되기 시작함.<br>
초기 USD 30 정도의 가격으로 시작해서 현재는 USD 50 정도로 성능과 함께 가격도 상승됨.

`Wiki's`
>라즈베리 파이(영어: Raspberry Pi)는 영국 잉글랜드의 라즈베리 파이 재단이 학교와 개발도상국에서 기초 컴퓨터 과학의 교육을 증진시키기 위해 개발한 신용카드 크기의 싱글 보드 컴퓨터이다.

## 내가 쓰는 라즈베리파이
작년에 라즈베리파이 4B를 구매해서 사용하고 있다. (중고나라 4만원)
- OS : raspberry OS (가장 가볍고 최적화되어 있는 정식 OS) <br>
- SSH : 원격제어(CLI)로 기기를 제어할 때 사용
- VNC : 원격제어(GUI)로 모니터 키보드 마우스 없이 사용 <br>
- KODI : 영화보는 용도로 사용 <br>
- Transmission-Daemon : 토렌트 다운로드용으로 사용 <br>
- vsftpd : ftp server로 사용 <br>
- minidlna : TV에 영화를 바로 공유하는 데 사용 <br>

## INDEX

### 기본 설치 및 설정

- #### [Raspberry Pi Install - 라즈베리파이 OS 설치법 (모니터, 키보드 없이)](/posts/Pi-install/)

- #### [Raspberry Pi SSH - 라즈베리파이 SSH CLI 원격제어법, DHCP 설정 (모니터, 키보드 없이)](/posts/Pi-ssh/)

  ##### - [Raspberry Pi SSH RSA key - 라즈베리파이 SSH 암호없이 접속하기](/posts/Pi-ssh-keygen/)

- #### [Raspberry Pi VNC - 라즈베리파이 VNC GUI 원격제어법, DHCP 설정 (모니터, 키보드 없이)](/posts/Pi-vnc/)

- #### [Raspberry Pi Setting - 라즈베리파이 기본 설정법 (모니터, 키보드 없이)](/posts/Pi-setting/)

- #### [Raspberry Pi User - 라즈베리파이 사용자 추가법 (pi ID 삭제법)](/posts/Pi-user/)
  ##### - [Raspberry Pi User - 라즈베리파이 pi 이름 변경법](/posts/Pi-changepi/)

  ##### - [Raspberry Pi sudo - sudo 암호입력 없이 사용하기](/posts/Pi-sudo/)

- #### [Raspberry Pi Port Forward - 라즈베리파이 외부/해외에서 접속하기 (포트포워드)](/posts/Pi-port/)

- #### [Raspberry Pi Storage Mount - USB / SD Card Memory 재부팅시 자동 Mount 하기](/posts/Pi-mount/)

### 미디어/파일 서버 설정

- #### [Raspberry Pi DLNA/UPnP - 라즈베리파이 DLNA/UPnP 미디어 서버로 사용하기(by minidlna)](posts/Pi-dlna/)

- #### [Raspberry Pi FTP - 라즈베리파이 ftp 파일서버로 사용하기(by vsftpd)](/posts/Pi-ftp/)

- #### [Raspberry Pi transmission - 라즈베리파이 토렌트(Torrent) 머신으로 사용하기(by transmission-daemon)](/posts/Pi-trans/)
  ##### - [Raspberry Pi transmission - Transmission-Daemon 소유권(권한) 문제 해결법](/posts/Pi-trans-own/)

### 미디어 센터 설정

- #### [Raspberry Pi KODI - KODI Media Center 설치법 (by Terminal)](/posts/Pi-kodi/)

  ##### - [Raspberry Pi KODI VNC Control - KODI VNC로 Control하는 법 (by Direct Capture Mode)](/posts/Pi-kodi-vnc/)
