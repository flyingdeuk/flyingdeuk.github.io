---
title: Raspberry Pi User - 라즈베리파이 pi 이름 변경법
author: FlyingDeuk
date: 2021-08-21 20:55:00 +0800
categories: [Living]
tags: [usefulthing, linux, raspberrypi]
pin:
---

![pi](/img/living/pi/pi.jpg)

`FlyingDeuk's`
> 이전에 기본 계정을 다른 계정으로 대체해서 삭제하는 법을 포스팅했다. <br>
직접 해보지는 않았지만 pi의 계정이름만 변경하는 것이 더 손쉬울수 있어 작성해본다.

`Wiki's`
>**컴퓨터 운영 체제에서 슈퍼유저(superuser), 운용 관리자[1] 또는 루트(root)** 는 시스템 관리자가 제어하는 특별한 사용자 계정을 위해 사용되는 용어이다. 다중 사용자 운영 체제가 아닌 오래된 운영 체제(MS-DOS, 윈도우 9x)에서 개인, 가정용으로 고안된 것으로 슈퍼 사용자 계정을 굳이 구별하지는 않는다. 어떠한 사용자라도 효율적으로 시스템 관리 권한을 얻을 수 있다. 관리자 권한을 일반 사용자 권한과 구별하면 운영 체제가 바이러스와 다른 악성 소프트웨어를 막을 수 있다.

## 라즈베리파이 pi 이름 변경하기
기본 관리자인 pi를 변경하기 위해서는 root로 로그인해야 가능하다.
>이 방법 역시 모니터 키보드없이 원격으로 해결하는 방법이다. (모니터 키보드없이 쓰고 있기 때문이다.)

### root 암호 등록
최초에는 root암호가 등록되어 있지 않다. root암호를 등록해야한다.

#### sudo passwd root
```
$ sudo passwd root
```
>SSH로 접속한 상태에서 암호를 등록한다.

### SSH 설정 변경
ssh는 기본적으로 보안 때문인지 root의 원격접속이 제한되어 있다.

#### sudo vim /etc/ssh/sshd_config

```
# Authentication:

#LoginGraceTime 2m
#PermitRootLogin prohibit-password
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10
```
>**PermitRootLogin yes** 로 변경한다.

- 해당 목적이 끝나고 나면 원래대로 돌려 좋는 것이 좋을 듯함...

#### sudo service sshd restart
ssh 서비스를 재시작해서 변동 사항을 반영
```
$ sudo service sshd restart
```

```
$ exit
```
>pi 계정에서 로그아웃한다.

### root로 접속
pi 변경을 위해서 root로 접속한다.
#### ssh root@192.168.xx.xx
```
$ ssh root@192.168.xx.xx
```

### pi 이름 변경
usermod로 이름 변경해준다.

#### usermod -l newname pi
로그인 아이디를 변경
```
usermod -l deuktest pi
```

#### usermod -m -d /home/newname newname
/home/pi 폴더의 모든 내용을 새로운 이름으로 변경 및 이동
```
usermod -m -d /home/deuktest deuktest
```

내가 직접해 본것은 아니지만 검색의 결과이다. 다음 기회가 되면 해볼 생각임...

-----

### PostScript
좀 더 손쉬운 방법이라 생각이 든다. 이럼으로써 root 계정 암호도 겸사겸사 만들게도 되었다.



[INDEX로 돌아가기](/posts/RaspberryPi/)
