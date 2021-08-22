---
title: Raspberry Pi Install - 라즈베리파이 OS 설치법 (모니터, 키보드 없이)
author: FlyingDeuk
date: 2021-08-17 20:55:00 +0800
categories: [Living]
tags: [usefulthing, linux, raspberrypi]
pin:
---

![pi](/img/living/pi/pi.jpg)

`FlyingDeuk's`
> 처음 라즈베리파이를 사서 우분투를 설치하려고 많이 노력했다. 리눅스 중에는 우툰투가 가장 보편적이라하여...<br>
결국은 라즈베리파이 OS에 정착했다. 모든 OS는 하드웨어의 종류에 맞게 Modify가 필요한데... 라즈베리파이에는 라즈베리파이 OS가 제일 가볍고 좋은 듯하다..

처음부터 자세하게 포스팅을 하고 싶었지만 다시 설치할 용기가 않났다... 근데 전원문제로 initramfs에 빠졌다... 복구실패... 처음부터 포스팅할 수 있는 기회를 얻게 되었다. ㅜ.ㅜ

`Wiki's`
> **라즈베리 파이 OS(영어: Raspberry Pi OS)** 는 라즈베리 파이 재단이 개발한 라즈베리 파이 전용 운영 체제이다. 과거에는 라즈비안(영어: Raspbian)이라는 이름을 사용하였다. 2015년 이후로 라즈베리 파이 재단에 의해 라즈베리 파이 단일 보드 컴퓨터 계열을 위한 주 운영 체제로서 공식 지원을 받고 있다.[1] 라즈베리 파이 OS는 마이크 톰슨(Mike Thompson)과 피터 그린(Peter Green)이 독립 프로젝트로 개발한 것이다.[2] 최초 빌드는 2012년 6월에 완성되었다.[3] 이 운영 체제는 현재도 활발히 개발되고 있다. 라즈베리 파이 OS는 라즈베리 파이 계열의 저성능 ARM CPU에 상당히 최적화되어 있다.


## 라즈베리파이 OS 설치
구입 초반에는 라즈베리안이라는 이름이였다가 라즈베리파이 OS로 최근에 변경되었다. <br>
설치를 위해서는 Micro SD 카드가 필요하다. 4Gb 정도면 OS는 설치가 가능하니 본인의 사용계획에 맞춰 SD 카드 구매하면 된다.

### 라즈베리파이 OS 다운로드
공식 사이트 : https://www.raspberrypi.org

![install](/img/living/pi/install1.jpg)

>기존에는 다른 이미저 프로그램을 많이 이용했었다. 최근에는 공식사이트의 Imager를 사용하면 된다.<br>
본인의 OS(MAC, Windows, Ubuntu)에 맞게 Imager 설치하면 된다.


![install](/img/living/pi/install2.jpg)

>라즈베리파이에 설치가능한 모든 OS를 선택 가능하다. <br>


![install](/img/living/pi/install3.jpg)

>OS와 Storage 선택하면 알아서 다운로드와 굽기를 해준다.


모니터와 키보드 없이 원격 접속을 위해서는 다음 과정이 필요하다.

### ssh, wifi_supplicant.conf 파일 추가

![install](/img/living/pi/install4.jpg)

SD 카드는 구워지고 나면 자동으로 마운트가 해제된다. 다시 마운트 시키면...<br>
**BOOT** 라는 이름으로 구워지며... Root에 해당 파일 2개를 추가하면 된다.

#### ssh 파일
명령어(CLI)로 원격 접속을 위해서는 ssh 파일이 필요하다.
- **Windows** : 메모장에서 내용없는 ssh.txt 파일을 저장하고나서 확장자 .txt를 지워준다.
- **MAC** : 순정 Finder에서는 빈 txt 파일 작성이 안된다. 아무 txt 파일을 구해서 해당 내용을 다 지우고나서 .txt를 지워준다.

#### wifi_supplicant.conf
**이더넷(랜선)을 유선으로 연결하는 경우에는 생략해도 된다.**  <br>

위와 같은 방법으로 wifi_supplicant.txt를 만들어준다. -> 내용 넣어주고 -> .txt를 .conf로 바꿔준다.


**wifi_supplicant.conf**
```bash
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
network={
    ssid="wifi_이름"
    psk="wifi_비밀번호"
}
```

### 라즈베리파이 부팅
SD 카드를 삽입하고 전원을 켜면 된다.
>첫 부팅시에는 시간이 10-15분 정도 소요된다.

### PostScript
라즈베리파이 OS에는 기본 서버(명령어로만 제어), 데스크탑(GUI), 데스크탑 with recommended software(오피스, 각종 프로그램) 3가지에서 선택하면 되고... <br>
그외 NAS용, 게임 에뮬레이터용, 3rd Party(우분투 등) 다양한 소프트웨어를 설치할 수 있다. <br>
 모니터와 키보드없이 사용하는 경우는 recommended software는 불필요한거같다. <br>

 그냥 데스크탑 버전에 KODI는 별도로 설치하고 NAS는 가벼운 ftp로만 사용하고 있다. 각자 본인의 용도에 맞는 OS를 설치하면 되겠다.

 [INDEX로 돌아가기](/posts/RaspberryPi/)
 
