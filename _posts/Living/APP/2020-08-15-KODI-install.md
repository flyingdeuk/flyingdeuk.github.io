---
title: KODI Install - 기본 설치법 (for Mac, Android, Windows, RaspberryPi)
author: FlyingDeuk
date: 2020-08-15 20:55:00 +0800
categories: [Living]
tags: [usefulapp, mac, android, windows, linux, kodi]
pin:
---

`FlyingDeuk's`
> 모든 형태의 기기에서 사용이 가능하다. (IOS 제외) <br>
Play store, 홈페이지에서 직접 설치가 가능하다. <br>
리눅스의 경우는 CLI에서 명령어로 설치해야하며 모든 방법은 홈페이지에서 확인 가능함. (세부 플러그인 설치법은 아래 참고...)

## KODI install
![kodi_1](/img/living/kodi/kodi_1.jpg)

KODI 공식 홈페이지  <https://kodi.tv>
> 상기의 공식사이트에 접속하면 방법을 다 알려주니 걱정이 없다.<br>
windows10, 안드로이드는 스토어에서 바로 설치가능. (자동 업데이트 지원됨)<br>
FIRE TV는 Downloader라는 어플로 주소치고 Down가능함.


![kodi_2](/img/living/kodi/kodi_2.jpg)
> 무기를 고르시오.<br>
모든 버전의 OS에서 설치 가능함.<br>
윈도우, 맥북, 라즈베리파이까지도 설치 가능하나 IOS는 탈옥을 해야함.


![kodi_3](/img/living/kodi/kodi_3.jpg)
> 본인의 사양에 맞는 버전을 선택<br>
FIRE TV의 경우 32비트가 맞음. 세부 절차는 해당 링크 참고 [Fire TV Apps Install - 추천 어플 설치법](/posts/Fire-TV1/)

### 기종별 설치법
**Windows**
- MS Store : **KODI**검색해서 설치 -> 자동을 최신버전으로 Update 됨
- kodi.tv : 32, 64bit (설정에서 비트확인) 중 선택해서 설치 -> 자동 Update 안됨

**MAC**
- kodi.tv : 설치 -> 자동 업데이트 안됨

**Android**
- Play Store : 설치 -> 자동 업데이트 됨
- kodi.tv : 32, 64bit (설정에서 비트확인) 중 맞는 버전으로 선택 설치 -> 자동 업데이트 안됨

**FIRE TV**
- kodi.tv : 32bit 버전으로 설치

**Raspberry Pi**
- Raspberry OS 기준 설치 방법이며 최근 공식 kodi.tv에는 자세한 필요 package에 대한 install 명령어가 없어졌다. (kodi는 기능상 필요한 package를 모두 설치해야 정상 작동함)
```bash
sudo apt install kodi kodi-peripheral-joystick kodi-pvr-iptvsimple kodi-inputstream-adaptive kodi-inputstream-rtmp
```
- kodi와 함께 필수 프로그램을 설치한다.
```bash
sudo apt install build-essential python-pip python-dev libffi-dev libssl-dev libnss3
```
```bash
sudo pip install setuptools wheel pycryptodomex
```
- kodi에 필요한 python과 해당 프로그램을 설치한다. 이는 kodi내에서 Netflix등의 addon이 정상 작동되게 해준다.  



#### Postscript

설치는 간단하게 이루어진다. 추후 궁금증이 있는 경우 역시 해당 공식사이트나 Googling으로 해결 가능하다. <br>

**전세계의 정말 많은 사람들이 적어놓은 것들이 많기 때문이다.**



[INDEX로 돌아가기](/posts/KODI/)
