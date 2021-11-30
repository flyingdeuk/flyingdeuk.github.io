---
title: Raspberry Pi transmission - Transmission-Daemon 소유권(권한) 문제 해결법
author: FlyingDeuk
date: 2021-08-27 20:55:00 +0800
categories: [Living]
tags: [usefulthing, linux, raspberrypi]
pin:
---

![pi](/img/living/pi/pi.jpg)

`FlyingDeuk's`
> Transmission을 라즈베리파이에 설치(리눅스)해서 사용하다가 보면 권한 문제가 발생한다. <br>
그럴수 밖에 없는 것이 Transmission은 기본적으로 본인의 소유로 파일을 저장하다가 보니 권한 제한으로 인해 해당 파일을 읽을 수는 있지만 이동 및 삭제를 위해서는 권한이 필요하게 된다.

`Wiki's`
>**chown 명령어** 는 유닉스 계통 시스템에서 파일의 소유권을 바꾸기 위해서(change the owner of a file) 사용된다. 대부분의 경우, 이것은 오직 슈퍼 사용자만이 실행할 수 있다. 그들이 소유하고 있는 파일의 그룹을 바꾸고 싶어하는 권한이 없는 (일반적인) 사용자들은 chgrp을 사용해야 한다.

## Transmission-Daemon 소유권
Transmission은 파일을 다운로드 받으면서 본인의 소유로 파일을 만들게 된다. <br>
그러다가 보니 해당 파일에 대한 권한이 없는 이용자는 해당 파일을 이동/삭제가 불가능하게 된다. <br>
이를 해결하는 방법은 2가지정도로..
- Transmission의 주인을 바꾸는 방법
- Transmission을 관리자 계정의 Group으로 묶어서 사용하는 법
>본인은 잔머리를 좀 굴려 2번째 방법을 사용중이다. 첫번째 방법은 프로그램의 업데이트등으로 설정이 변경되는 경우가 있기때문에 원천적인 방법이 좀 더 쉽다.

```
-rw-rw-r-- 1 debian-transmission debian-transmission 1921372523  8월 23 07:44 '대탈출 4.E07.210822.720p-NEXT.mp4'
-rw-rw-r-- 1 debian-transmission debian-transmission 1832470233  8월 30 08:19 '대탈출 4.E08.210829.720p-NEXT.mp4'
```
  >파일의 소유자가 debian-transmission이고 그룹도 debian-transmission임을 알 수 있다.

### Transmission 주인 변경법 (user ID 변경)
권리자(Super User)의 계정으로 파일작성자를 변경한다.

#### $ sudo vim /etc/init/transmission-daemon.conf
```
setuid debian-transmission
setgid debian-transmission
```
>해당 아이디를 변경해 주면 된다고는 하는데... 최근 들어 우분투의 경우는 잘 안된단다... 아래 방법 추가...

#### $ sudo vim /etc/systemd/system/multi-user.target.wants/transmission-daemon.service
```
[Service]
User=debian-transmission
Type=notify
ExecStart=/usr/bin/transmission-daemon -f --log-error
```
>User 이름을 변경해준다.

#### $ sudo vim /etc/init.d/transmission-daemon

```
DAEMON=/usr/bin/$NAME
USER=debian-transmission
STOP_TIMEOUT=30
```
>USER 이름을 변경해준다.

##### 상기의 방법은 본인이 쓰는 방법이 아니라서... 참고해서 수정해주면 파일작성을 본인의 관리자 ID로 다운로드가 가능해서 파일관리가 가능하다.

### Transmission 관리자 그룹 지정
상기의 방법은 초보자로써 복잡하다. 설정이 또 언제 어디에 있는지를 능동적으로 바꾸기가 어렵다... 그래서

#### $ sudo vim /etc/group

```
deuktest:x:1001:debian-transmission
.
.
debian-transmission:x:124:deuktest
```
>내 관리자 ID의 group에도 debian-transmission의 group에도 각각 같은 group으로 묶었다. <br>
- 첫번째는 내가 만든 관리자 계정의 폴더에 transmission이 쓰기를 위해
- 두번째는 내가 transmission이 작성한 파일을 관리하기 위해

**transmission 설정에서 "umask" : 2로 지정해야 가능한 것임. (이전 포스팅 참조)**


#### 폴더 권한 변경
```
$ sudo chmod -R 775 /home/deuktest
```
>Transmission이 파일을 다운받는 폴더의 권한에 group쓰기 권한을 넣어주면 끝이다. (리눅스 포스팅 참조)

위와 같은 방법으로 간단하게 권한을 설정해서 다운로드파일 주인의 변경없이 group으로 관리자의 파일관리가 가능하게 되었다.

----

## PostScript
일반적으로 지금까지 사용해온 PC(Windows, MAC등)에도 역시 권한이라는 것이 존재한다. 하지만 잘 모르고 사용도 하지않는다고 하겠다. 하지만 리눅스의 서버로써의 역할로 인해 사용자 권한에 좀더 민감한 OS로 많은 것을 다시 한번 배운거 같다.

나름 재미를 느낀다.

[INDEX로 돌아가기](/posts/RaspberryPi/)
