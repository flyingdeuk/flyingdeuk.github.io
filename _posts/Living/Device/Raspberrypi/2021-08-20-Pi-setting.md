---
title: Raspberry Pi Setting - 라즈베리파이 기본 설정법 (모니터, 키보드 없이)
author: FlyingDeuk
date: 2021-08-20 20:55:00 +0800
categories: [Living]
tags: [usefulthing, linux, raspberrypi]
pin:
---

![pi](/img/living/pi/pi.jpg)

`FlyingDeuk's`
> 라즈베리파이는 여러 가지 방법으로 사용이 가능하다. 미디어 서버, 게임기, 모니터나 디스플레이를 달아서 데스크탑처럼 모터나 카메라, 센서등을 연결해서 Iot 기반의 제어 장치로도 가능하다. <br>
내가 사용하는 한도내에서의 기본 설정만을 설명한다. (초보자이기때문에... 그 이상은 아직 해보지않았다.)

## 라즈베리파이 기본 설정법
이전 포스팅을 바탕으로 VNC를 활용한 GUI의 형태나 SSH를 활용한 CLI의 형태 그리고 순수 명령어로도 가능하지만 CLI에 익숙해지기 위해서... SSH 기준으로 설명한다.

### VNC 활용 GUI 설정법
VNC로 접속해서 해당 기능을 누르면 됨...

![setting](/img/living/pi/setting1.jpg)
>**기본 설정** -> **RaspberryPi Configuration** <br>
원도우, MAC과 유사하나 좀 후지다...ㅎㅎㅎ

![setting](/img/living/pi/setting2.jpg)
>여러가지 Configuration이 가능하다. CLI보다는 훨씬 편하고 익숙하지만... 실제 설정은 CLI로 해보자...

### SSH 활용 CLI 설정법
Terminal이나 Powershell로 SSH에 접속하자. <br>
**ssh pi@192.168.xx.xx**

```
~ » ssh pi@192.168.xx.xx     255 ↵ DeUk@Deukhyeonui-MacBook-Air
pi@flyingdeuk.iptime.org's password:
Linux raspberrypi 5.10.52-v7l+ #1441 SMP Tue Aug 3 18:11:56 BST 2021 armv7l

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sun Aug 22 19:25:24 2021 from 65.74.16.71
pi@raspberrypi:~ $
```

#### sudo raspi-config

```
pi@raspberrypi:~ $ sudo raspi-config
```

![setting](/img/living/pi/setting3.jpg)
>세부 항목들은 아래에 알아본다. (필요한 것들 위주로만 설명예정!)

#### System Options
![setting](/img/living/pi/setting4.jpg)

다양한 옵션이 있지만 필요한 건...
- **Password** : pi의 Password를 변경한다. (다 알고있는 암호는 불안하니 변경한다.) -> **pi ID도 지울 예정이라 다음 포스팅을 따라 갈 예정이라면 의미 없음...**
- **Hostname** : 이 컴퓨터의 이름을 변경한다. **raspberrypi** -> **원하는 이름**
>재부팅되며 결과는...

```
pi@deuktest:~ $
```
>ssh 접속하면 컴퓨터 이름이 변경된 걸 알 수 있다.

#### Display Options
![setting](/img/living/pi/setting5.jpg)
- **Resoltion** : 라즈베리파이 4B는 최대 4K까지 지원한다. (4K ON은 아래 참조) -> 모니터나 TV에 연결을 한다면 해상도를 지정해준다.

#### Interface Options
![setting](/img/living/pi/setting6.jpg)
>연결을 원하는 형태를 켜면된다. SSH와 VNC 설정은 완료했으니... PASS~~

#### Performance Options
![setting](/img/living/pi/setting7.jpg)
- **GPU Memory** : KODI APP을 설치해서 사용하려면 GPU 256Mb(라즈베리파이 4B 4Gb는 512Mb 사용중) 이상이 추천된단다...
>가지고 있는 메모리의 일부를 Graphic을 위해서 사용한다.

#### Localisation Options
![setting](/img/living/pi/setting8.jpg)
사용자 위치를 설정하는 옵션이다. 이 옵션은 VNC로 GUI에서 설정하는 것이 더 편하다.
- **Locale** : 사용자의 지역을 설정하는 것으로 가장 큰 차이는 언어가 변경된다. (한국으로 설정시 정보가 한글로 표시된다. -> 한글 폰트가 설정되어 있지않아 깨지는 현상이 발생한다.)
```
  pi@deuktest:~$ sudo apt install fonts-unfonts-core
```
  >ssh에 해당 명령어로 간단하게 설치 가능하다.

- **Timezone** : 모든 기기는 UTC 기반으로 연산을 하지만 보여지는 시간대를 설정한다. **Asia**
- **keyboard** : 키보드 마우스를 연결해서 사용할 것이 아니라면 특별히 필요하지않다.
- **WLAN Country** : 라즈베리파이는 Wifi 이슈가 있다. 이 지역을 GB(영국)이나 US(미국)으로 하지않으면 wifi연결이 되지않았다. (내 기기는 현재 잘된다.) -> 혹시 문제가 있다면 유선연결후 여기에서 변경해보자.

#### Advanced Options
![setting](/img/living/pi/setting9.jpg)
- **HDMI / Composite** : 위에서 이야기한 4K를 여기서 설정이 가능하다.
>다른 설정은 필요하면 설정

#### Update
**sudo apt update / upgrade**와 같은 기능... 굳이 설정까지 들어와서 할 필요는 없는 듯...

-----

### PostScript
간단하게 설정이 가능하다. wifi 이슈만 아니면 사용하는 데는 크게 문제가 없다.
본인은 미디어서버로 wifi보다는 유선으로 사용할 목적으로 사용하기에 크게 문제점은 못 느낀다. 서버는 안보이는 곳에 두고 접속은 원격으로...

-----------

### [< Back to Raspberry Pi >](/posts/RaspberryPi/)
