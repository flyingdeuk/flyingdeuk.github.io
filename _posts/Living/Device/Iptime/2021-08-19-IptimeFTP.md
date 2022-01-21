---
title: IPTIME 공유기 FTP - 아이피타임 FTP 파일 관리 및 스트리밍(for MAC, IOS, Windows, Android)
author: FlyingDeuk
date: 2021-08-19 20:55:00 +0800
categories: [Living]
tags: [usefulthing, iptime, ftp]
pin:
---

`FlyingDeuk's`
> 오래된 가장 많이 사용하는 형식이 FTP가 아닐까 생각한다. https는 웹 페이지를 위한 형식이라면 FTP는 파일에 집중하는 프로토콜이라 하겠다. <br>
서버는 외부에서 사용해야하는 게 그 목적이니 FTP가 제일 활용도는 높을 것같다.

프로그램에 따라 다르겠지만 스트리밍이 주인 어플이 있고 파일 관리가 주인 어플이 있다. 파일관리 위주의 어플의 경우는 스트리밍이 안된다고 생각하면 된다.

`Wiki's`
>**파일 전송 프로토콜(File Transfer Protocol, FTP)** 은 TCP/IP 프로토콜을 가지고 서버와 클라이언트 사이의 파일 전송을 하기 위한 프로토콜이다. 파일 전송 프로토콜은 TCP/IP 프로토콜 테이블의 응용 계층에 속하며, 역사는 오래 되었지만 지금도 인터넷에서 자주 사용된다.

**IPTIME 설정 페이지 로그인은 더이상 설명하지 않겠다. 이전 포스팅 참조.**

## IPTIME FTP 설정
USB 서버 기능을 갖는 대부분의 제품에는 해당 기능이 있다.

![ftp](/img/living/iptime/ftp.jpg)

ftp는 외부에서 접속하는 게 주기능이니 DDNS 설정은 필수다. 이전 포스팅 참조

#### [IPTIME 공유기 DDNS - 외부/해외에서 접속하는 법](/posts/IptimeSet/)

- **설정 페이지** : **deuktest.iptime.org** -> 공유기 자체에 연결하는 주소 (포트포워드등 다른 기기를 연결할 때)

- **ftp 페이지** : **deuktest.ipdisk.co.kr** -> 공유기 ftp, 토렌트등 공유기 자체 기능에 연결하는 주소
>**USB 서비스 관리** -> **서비스 설정** -> **ipDISK/FTP 서비스**
- **서버주소** : "**deuktest.ipdisk.co.kr : 포트**" 의 형식이 된다. (기본포트는 포트 생략 가능)
- **FTP 포트** : **21**이 기본포트이다. 보안을 위해서는 자신만의 포트 번호로 바꾸는 것이 좋다.
- **사용자 설정** : 읽고 쓰기의 권한, 사용자 ID, 암호, 폴더를 한정에서 사용할 수 있다. 대부분의 서버가 그러하듯이 관리자는 읽고 쓰기 일반 사용자는 읽기만 허용하면 된다.

이로써 설정은 끝이다.... 이제 연결만 하면...

## 파일 관리
FTP 서버내의 파일을 관리하는 방법이다. 가능하면 순정 기능 내에서 간단하게 사용하는 방법들 위주로 소개한다. <br>
기본은 파일을 다운로드하는 게 대부분이고 스트리밍은 다른 어플을 사용해야한다.

### Windows
기본 지원되는 순정 기준의 방법이다.

- [Windows FTP SAMBA - 파일 탐색기로 FTP SAMBA 연결하기](/posts/win-ftp/)

### MAC Book
기본 지원되는 순정 기준...

- [MAC Book FTP Finder - 초간단 순정 FTP 파인더에서 사용하기](/posts/Mac-ftp/)

### IOS
아쉽게도 순정 "파일"엡에서는 불가능하다. Document 무료어플에선 가능하다.

![ftp](/img/living/ipad/iptv.jpg)
>다양한 기능에 무료 어플!!

![ftp](/img/living/iptime/ftp5.jpg)
>**+ Add Connection** 으로 여러가지 서버에 연결 가능함.

![ftp](/img/living/iptime/ftp6.jpg)
> 주소 **deuktest.ipdisk.co.kr**, 사용자이름, 비밀번호 넣으면 끝!!!

Document는 PDF 뷰어로 유명하나 AutoSync등의 다양한 기능을 가지고 있다. 놀라운 건 스트리밍까지 된다. -> 최근들어 자막이 잘 나오지 않는 것 같다. 업데이트후 사라진 건지... 안될땐 아래 참조...


### Android
가볍고 무료인 CX 파일 탐색기로 쉽게 이용가능하다. (안드로이드는 순정이랄게 없으니...)

![ftp](/img/living/iptime/ftp1.jpg)
>무료이면서 다양한 기능을 제공한다. 내 모든 서버는 이 어플에서 해결하는 편이다. 모바일이 대세...

![ftp](/img/living/iptime/ftp2.jpg)
>**네트워크** -> **+** : 서버 추가

![ftp](/img/living/iptime/ftp3.jpg)
> FTP 선택

![ftp](/img/living/iptime/ftp4.jpg)
> 주소 **deuktest.ipdisk.co.kr**, 사용자이름, 비밀번호 넣으면 끝!!!

## 스트리밍
스트리밍이 된다는 것은 결국엔 파일관리까지 된다는 이야기임. 다운로드 역시 당연하다.

### Windows, MAC Book, IOS, Android(FIRE TV)
요즘 나오는 대부분의 동영상 플레이어들은 네트워크 기능을 가지고 있어서 쉽게 메뉴에서 찾아 볼 수 있다.

내가 쓰는 VLC, KODI 정도만 소개한다.

#### VLC Player
![ftp](/img/living/ipad/iptv5.jpg)

![ftp](/img/living/iptime/ftp7.jpg)
>**네트워크** 항목에서 **연결하기** 눌러 정보만 넣어주면 된다. <br>
동영상 플레이어이기 때문에 자막도 문제 없이 재생된다.


가끔 폴더의 한글이 깨지는 현상이 있을 수 있다.
>설정의 제일 아래에 FTP 폰트에서 UTF-8을 선택하던지 다른 걸루 바꿔주면 해결이 가능하다.

#### KODI
내가 제일 좋아하는 어플... 해당 포스팅 참조하면 된다.


- #### [KODI Media Server DLNA, UPnP, SMB, FTP - 미디어 서버(소스) 연결하기](/posts/KODI-source/)

- #### [KODI Movies Library - 영화 라이브러리 설정법](/posts/KODI-library/)

- #### [KODI Movies Library AutoUpdate - 영화 라이브러리 자동 업데이트, 라이브러리 정리 사용법](/posts/KODI-autoupdate/)

- #### [KODI Movies Library The Movie DataBase - TMDB 영화 라이브러리 데이터베이스 연결법](/posts/KODI-tmdb/)
> 개인 Netflix를 만들수 있다...

-------

## PostScript
해외 호텔에서의 사용이 많은 만큼 FTP 방식을 주로 사용한다. 스트리밍을 지원해주는 어플들이 많아져서 FTP도 다운로드없이 스트리밍으로 볼 수 있다는 것 자체가 너무 편해진 느낌이다.

친한 지인에게도 아이디 몇 개 나눠주고 생색내는 것도 하나의 방법... 단 너무 사용자가 많으면... 공유기는 성능이 떨어지니... 라즈베리파이 한대 구매하는 것도.. 다른 포스팅 참조...

[INDEX로 돌아가기](/posts/Iptime/)
