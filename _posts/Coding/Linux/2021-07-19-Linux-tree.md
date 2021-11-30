---
title: Linux(debian) - OS의 기본 구조
date: 2021-07-19
categories: [Coding, Linux]
tags: [linux]
pin:
---


![com](/img/coding/linux/tree.jpg)

`FlyingDeuk's`

>Linux는 기본이 CLI(Command Line Interface)이다. <br>우리가 일반적으로 경험하는 Windows, Mac OS에서 처럼 GUI와는 다르게 Text안에서의 구조를 알고 있으면 특유의 CLI의 장점 최대한 사용할 수 있겠다.

`Wiki's`

>파일시스템은 여러 디렉터리가 있는 하나의 [루트 트리](https://ko.wikipedia.org/wiki/나무_그래프)로 등장한다.[[1\]](https://ko.wikipedia.org/wiki/유닉스_파일시스템#cite_note-Ritchie-1) [디스크 파티션](https://ko.wikipedia.org/wiki/디스크_파티션), 이동식 미디어, [네트워크 자원](https://ko.wikipedia.org/wiki/공유_자원) 등 별도의 볼륨을 별도의 트리로 주소화(마치 [도스](https://ko.wikipedia.org/wiki/도스)와 [윈도우](https://ko.wikipedia.org/wiki/마이크로소프트_윈도우)에서 하는 것처럼, 각 "드라이브"가 드라이브 문자를 가짐으로써 파일 시스템 트리의 루트를 나타내는 것)하는 대신 이러한 볼륨들은 디렉터리를 [마운트](https://ko.wikipedia.org/wiki/Mount_(유닉스))시킴으로써 볼륨의 파일 시스템 트리가 더 큰 트리의 디렉터리로 보이게 만든다.[[1\]](https://ko.wikipedia.org/wiki/유닉스_파일시스템#cite_note-Ritchie-1) 전체 트리의 루트가 `/`로 표시된다.



## Linux의 기본 구조

Command Line으로 구성된 OS인 만큼 각각의 폴더에 기본적인 기능이 포함되어있다.

```bash
drwxr-xr-x   1 root root   180  7월 31 09:10 .
drwxr-xr-x   1 root root   180  7월 31 09:10 ..
drwxr-xr-x   2 root root  4096  6월 25 15:37 RaspController
lrwxrwxrwx   1 root root     7 12월  2  2020 bin -> usr/bin
drwxr-xr-x   6 root root  4096  1월  1  1970 boot
drwxr-xr-x  18 root root  3940  7월 22 20:15 dev
drwxr-xr-x   1 root root   280  7월 30 07:15 etc
drwxr-xr-x   1 root root    60  7월 20 18:37 home
lrwxrwxrwx   1 root root     7 12월  2  2020 lib -> usr/lib
drwx------   2 root root 16384 12월  2  2020 lost+found
drwxr-xr-x   3 root root  4096  6월 25 17:52 media
drwxr-xr-x   2 root root  4096 12월  2  2020 mnt
drwxr-xr-x   1 root root    60 12월 22  2020 opt
dr-xr-xr-x 214 root root     0  1월  1  1970 proc
drwx------   1 root root    80  7월 23 17:01 root
drwxr-xr-x  31 root root   900  7월 31 11:40 run
lrwxrwxrwx   1 root root     8 12월  2  2020 sbin -> usr/sbin
drwxr-xr-x   3 root root  4096 12월 20  2020 srv
dr-xr-xr-x  12 root root     0  1월  1  1970 sys
drwxrwxrwt   1 root root   340  7월 31 11:17 tmp
drwxr-xr-x   1 root root   120 12월  2  2020 usr
drwxr-xr-x   1 root root   180 12월  2  2020 var
```

> 라즈베리파이의 ROOT 폴더의 기본 구조
> 리눅스의 공통적인 구조만 설명한다.

```bash
$ man hier
```

> **hierarchy** 계층구조의 manual로 자세한 내용을 알 수 있다.

### /bin 과 /usr/bin

Binary의 약자로 OS의 최소한의 정상적인 구동을 위해 필요한 프로그램이 들어있는 폴더.<br> cat, chmod, chown, cp, date, echo, kill, ln, ls, mkdir, etx 와같은 기초적인 프로그램들이 포함되어 있다.

/usr/bin은 사용자에 의해 비슷한 목적을 갖는 프로그램이 추가된 폴더이다.

### /sbin 과 /usr/sbin

/bin, /usr/bin과 유사하지만 Root 사용자 권한이 필요한 프로그램이 있는 폴더.

### /boot

시스템 부팅에 필요한 파일이 들어 있는 폴더

### /dev

device의 약자로 이전에 말했던 모든것은 파일이다 라는 모토에맞게 키보드, 마우스, 프린터등과같은 디바이스들을 파일 또는 디렉토리의 형태로 dev 폴더 안에 존재하기때문에 표준 입출력(ex. ‘cat /boot/vmlinuz > /dev/dsp’)을 통해 읽기 쓰기도 가능하며 디렉토리 어디에서든 접근할 수 있음.



### /etc

etc 폴더는 대부분의 설정 파일이 위치함. 리눅스의 전신인 유닉스의 초창기에는 부팅과 관련한 모든 설정정보는 boot 폴더 디바이스와 관련된 설정 정보는 dev 폴더에 위치했지만 시간이 지나며 etcetera라는 이름의 etc 폴더를 만들어 설정 정보를 따로 보관하게 되었단다. 이후 시간이 지나며 etc 뜻 그 자체처럼 시스템 전체에서 사용하는 설정과 같은 엑스트라 데이터들이 저장되는 폴더가 되었음.



### /lib

커널모듈, 시스템에 필요한 라이브러리 등이 위치함.



### /proc

proc에는 각 프로세스 이름에 따라 수많은 폴더들이 존재하고 현재 실행되는 프로세스에 대한 정보와 데이터가 담겨있다. (실제 디스크 공간에는 존재하지않는 가상의 디렉토리). 현재 cpu에서의 사용값, IO포트 등등 프로세스에대한 다양한 정보들이 있음.

### /media 와 /mnt

두개 다 파일시스템이 마운팅되는 포인트라는 점에서는 비슷하지만 Media는 OS에서 자동으로 마운팅해주는 포인트로 주로 사용되며 Mnt는 사용자가 직접 마운트하는 경로로 사용됨. 예를들어 컴퓨터에 USB꽂아 OS에 자동으로 마운팅된다면 주로 Media 폴더 내에 마운팅 포인트가 생성되지만 외부에 있는 디스크등을 직접 명령어를 통해 마운트한다면 Mnt 디렉토리에 위치함.



### /srv

srv 디렉토리는 서버를 위한 폴더. 주로 FTP, SFTP, RSync와 같은 프로토콜을 이용하여 외부 사용자와의 공유를 위해 사용되며 다른디렉토리에비해 비교적 외부 사용자들이 쉽게 접근할 수 있는 폴더임.

### /sys

sys와 유사하며 실제 디스크의 물리적 영역이 아닌 RAM을 기반으로한 파일시스템. 현재 커널 데이터에 대한 구조 속성등 현재 시스템 전반에 대한 내용을 제공함. RAM 기반으로 매번 다시 시작할때마다 새로 생성됨.



### /tmp

세션정보나 혹은 워드프로세서에서 작업한다면 현재까지 저장되지 않은 현재 작업내용등을 임시로 저장되는 폴더.



### /usr

user 각 유저 이름에 맞는 폴더이름이 생성되어있으며 각 폴더마다 bin, sbin, share, lib과같이 각 유저들이 사용할 수 있는 폴더들이 위치함. 주로 시스템에서 가장 많은 영역을 차지하며 루트유저와 자기 자신만 접근가능함. usr는 사실 하나의 파티션이 아니라 각각의 유저별로 다른 파티션으로 존재하기때문에 다른사용자들이 사용할 수 있도록 마운트할 수 있지만 이 경우 수정은 불가능함.

### /opt

크롬브라우저, 안드로이드 스튜디오등과 같은 써드파티 어플리케이션에 대한 설치 디렉토리로 사용됨.



### /var

기타 모든 다용도로 사용될 수 있는 파일들이 저장되며 로그파일, 데이터베이스 캐싱파일, 웹서버 이미지 파일등이 위치할 수 있으며 파일의 크기가 추후 계속 확장될 수 있을경우 더욱 적합함.
