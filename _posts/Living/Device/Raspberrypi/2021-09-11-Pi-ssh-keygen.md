---
title: Raspberry Pi SSH RSA key - 라즈베리파이 SSH 암호없이 접속하기(모니터, 키보드 없이)
author: Flyingdeuk
date: 2021-09-11 20:55:00 +0800
categories: [Living]
tags: [usefulthing, linux, raspberrypi]
pin:
---

![pi](/img/living/pi/pi.jpg)

`Flyingdeuk's`
> 라즈베리파이(리눅스 서버)의 제어를 위해서는 SSH가 주로 쓰이는 듯하다. <br>
하지만 접속할 때마다 포트번호 붙이는 것도 귀찮은데... 매번 암호를 넣는 것 역시 좀 불편하다. <br>
검색중 RSA key를 이용한 자동 로그인에 대해서 알게되어 적어본다.

여러가지 보안 방법중에 특정 암호된 key를 서로 공유해서 자동으로 사용자를 인식하는 방법임.

`Wiki's`
> **RSA 암호** 는 공개키 암호시스템의 하나로, 암호화뿐만 아니라 전자서명이 가능한 최초의 알고리즘으로 알려져 있다. RSA가 갖는 전자서명 기능은 인증을 요구하는 전자 상거래 등에 RSA의 광범위한 활용을 가능하게 하였다.

## SSH RSA key
개념을 이해하는 것이 먼저다. Client에서 RSA key를 Server에 저장하는 방식이다.
- client(맥북) : Server를 제어할 PC (Windows, MAC Book...)
- Server(라즈베리파이) : 제어의 대상이 되는 PC (라즈베리파이(리눅스) 등등...)

### SSH keygen (RSA key 만들기)
Client PC(맥북) Terminal에서 해당 작업을 수행한다. (Windows는 Powershell)

#### $ ssh-keygen
ssh RSA key 생성 명령어

```bash
$ ssh-keygen                                
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/deuktest/.ssh/id_rsa):
```
>RSA key를 생성후 어디에 저장할 것인지를 묻는다. <br>
사용자의 Home폴더 /.ssh (default)에 그냥 저장하는 게... 그냥 엔터!!



```bash
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```
>RSA에 대한 추가적인 암호를 추가할 수 있다...<br>
그럼 또 암호를 넣아야하니... 패스... RSA key의 누출을 우려한다면...

```bash
Your identification has been saved in /Users/deuktest/.ssh/id_rsa.
Your public key has been saved in /Users/deuktest/.ssh/id_rsa.pub.
The key fingerprint is:
.
.
.
```
>Client PC(맥북) 사용자 Home폴더 /.ssh 에 key가 저장되었다...

```bash
~/.ssh $ ls -al                                    
total 24
drwx------   5 deuktest  staff   160  9 13 14:53 .
drwxr-xr-x+ 64 deuktest  staff  2048  9 13 14:53 ..
-rw-------   1 deuktest  staff  2622  9 13 14:53 id_rsa
-rw-r--r--   1 deuktest  staff   588  9 13 14:53 id_rsa.pub
-rw-r--r--   1 deuktest  staff   213  8 22 19:25 known_hosts
```
>~/.ssh 에 해당 내용이 추가된 것을 알 수 있다.


### SSH RSA key를 Server로 전송
이제 Client PC에서 작성한 RSA key를 서버(라즈베리파이)로 전송해주면 된다.

#### $ ssh-copy-id
ssh RSA key를 Server 주소로 전송한다.
- ssh-copy-id deuktest@192.168.xx.xx
- ssh-coyp-id  deuktest@deuktest.iptime.org
>같은 형식으로 ssh 접속과 같은 서버 주소를 붙여주면 끝!!

```bash
$ ssh-copy-id deuktest@deuktest.iptime.org
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/Users/deuktest/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
deuktest@deuktest.iptime.org's password:

Number of key(s) added:        1

Now try logging into the machine, with:   "ssh 'deuktest@deuktest.iptime.org'"
and check to make sure that only the key(s) you wanted were added.
```

### 자동 접속 (without Password)

기존과 같은 방식으로 ssh에 로그인하면 암호입력없이 바로 접속이 되는 것을 볼 수 있을 것이다.

-------

### PostScript
노트북은 통상 자신만의 PC이고 자신만의 세계라는 개념이 강한 것 같다. 내 노트북엔 이와 같은 방식으로 key를 저장하여 사용하는 것도 나쁘진 않은 것같다.


[INDEX로 돌아가기](/posts/RaspberryPi/)
