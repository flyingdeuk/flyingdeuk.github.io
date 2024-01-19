---
title: Raspberry Pi KODI VNC Control - 라즈베리파이 KODI VNC로 Control하는 법 (모니터, 키보드없이 by Direct Capture Mode)
author: FlyingDeuk
date: 2021-08-30 20:55:00 +0800
categories: [Living]
tags: [usefulthing, linux, raspberrypi]
pin:
---

![pi](/img/living/pi/pi.jpg)

`FlyingDeuk's`
> 라즈베리파이를 사용하면서의 기본 Concept는 하드웨어 적인 연결 없이 모니터, 키보드없이 사용하는 것...<br>
하지만 4K를 지원하고 130인치의 프로젝터를 영화용으로 사용하는 환경에서  UHD의 유혹을... <br>
TV에는 연결하더라도... Control은 물리적인 키보드가 없기에.. 알아본 방법...

`Wiki's`
>**VNC(Virtual Network Computing, 가상 네트워크 컴퓨팅)** 는 컴퓨터 환경에서 RFB 프로토콜을 이용하여 원격으로 다른 컴퓨터를 제어하는 그래픽 데스크톱 공유 시스템이다. 자판과 마우스 이벤트를 한 컴퓨터에서 다른 컴퓨터로 전송시켜서 네트워크를 거쳐 그래픽 화면을 갱신하는 방식을 제공한다.
VNC와 RFB는 미국과 다른 국가들에서 RealVNC Ltd.의 등록 상표이다.

## 라즈베리파이 KODI Control by VNC
경험해본 사람은 알겠지만 라즈베리파이에서 KODI를 실행하면(VNC의 원격데스크탑에서...) 모래 시계만 보일뿐... KODI의 실행은 눈으로 확인이 어렵다.
>이는 다른 layer로 kodi가 실행되기 때문에 VNC로는 확인이 어렵다...

**VNC로 라즈베리파이로 접속해서 해당 설정을 리모트(원격)으로 변경해주면 된다.**

### VNC 설정 for KODI
VNC에서 KODI의 overlay화면을 보기위한 설정은 아래와 같다.

![kodi-vnc](/img/living/pi/kodi-vnc1.jpg)
>리눅스 작업표시줄과 같은 상단의 VNC Server 아이콘을 눌러 옵션을 눌려준다. <br>
**Options...**


![kodi-vnc](/img/living/pi/kodi-vnc2.jpg)
>**Troubleshooting** -> **Enable direct capture mode** <br>

화면을 direct capture mode로.... 어쨌든 Overlay된 화면도 잘 보여주게 된다.

![kodi-vnc](/img/living/pi/kodi-vnc3.jpg)
> 바탕화면에서 실행하든 Terminal에서 실해하든... KODI의 실행화면을 볼 수 있다...

##### VNC, Windows 원격데스크탑, Chrome 원격데스크탑등 모든 유사한 프로그램들은 모두 다 같이 소리에 대한 전송은 없다... 화면만 있을 뿐...

----

## PostScript
본인의 집에 130인치 프로젝터를 거실에 연결하고 라즈베리파이를 서버로(LAN선이 거실 프로젝터 옆에 있어...) 미디어 서버로 같이 사용할 목적을 설정을 하다가 보니 알게 된 사항이라고나 할까...<br>
라즈베리파이를 컨트롤할 방법이 VNC 밖에 없는데.. <br>

**영화 보려고 KODI를 실행했더니... VNC는 모래시계... 프로젝터는 KODI... Control이 안된다...**

>위의 설정으로 VNC화면에서 KODI의 화면도 Overlay가능하고... Control도 가능하다... 화면에 나오니...

-----------

### [< Back to Raspberry Pi >](/posts/RaspberryPi/)
