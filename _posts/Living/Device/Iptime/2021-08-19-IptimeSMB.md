---
title: IPTIME 공유기 SAMBA - 아이피타임 SMB 파일 관리 및 스트리밍(for MAC, IOS, Windows, Android)
author: FlyingDeuk
date: 2021-08-19 20:55:00 +0800
categories: [Living]
tags: [usefulthing, iptime, SMB]
pin:
---

`FlyingDeuk's`
> SAMBA는 윈도우에서 주로 네트워크로 사용하던 방식으로 같은 공유기에 연결된 기기끼리만 사용하는 점과 자동 검색이 되는 점은 DLNA와 유사하나 사용자 권한등의 보안기능은 FTP와 닮아있다.
집안(로컬)에서 모든 파일을 자유롭게 사용하는 DLNA와 FTP의 중간정도 위치라고 보면된다.

집안 VPN 사용하면 외부에서도 SAMBA 연결이 가능하다고는 하나 그럴바엔 FTP를 쓰는게 더 좋은 방법이 아닐까 생각한다.

`Wiki's`
>**삼바(samba)** 는 Windows 운영체제를 사용하는 PC에서 Linux 또는 UNIX 서버에 접속하여 파일이나 프린터를 공유하여 사용할 수 있도록 해 주는 소프트웨어이다. 1991년 호주의 박사과정 학생이었던 앤드루 트리젤(Andrew Tridgell)이 개발하였다.

**IPTIME 설정 페이지 로그인은 더이상 설명하지 않겠다. 이전 포스팅 참조.**

## IPTIME SAMBA 설정
USB 서버 기능을 갖는 대부분의 제품에는 해당 기능이 있다.

![smb](/img/living/iptime/smb.jpg)

같은 공유기에 연결된 기기끼리의 통신으로 IP주소나 서버이름으로 접속이 가능하며 자동 검색이 가능하다.

- **서버이름** : 해당 이름으로 검색이되면 안될 시는 공유기 IP주소로 연결가능함 (**192.168.x.x**)
- **사용자 설정** : 읽고 쓰기의 권한, 사용자 ID, 암호, 폴더를 한정에서 사용할 수 있다. 대부분의 서버가 그러하듯이 관리자는 읽고 쓰기 일반 사용자는 읽기만 허용하면 된다.

이로써 설정은 끝이다.... 이제 연결만 하면...

## 파일 관리
SAMBA 서버내의 파일을 관리하는 방법이다. 가능하면 순정 기능 내에서 간단하게 사용하는 방법들 위주로 소개한다. <br>
기본은 파일을 다운로드하는 게 대부분이고 스트리밍은 다른 어플을 사용해야한다.

### MAC Book
자동 검색이 되며 로그인만 하면 편하게 사용이 가능하다.

![smb](/img/living/iptime/smb1.jpg)
>네트워크를 누르면 자동으로 검색됨. **아이콘**이 정말..ㅋㅋㅋ 윈도우를 싫어하는가 봄...

![smb](/img/living/iptime/smb2.jpg)
>**다음으로 연결** 을 눌러 로그인하면됨.

![smb](/img/living/iptime/smb3.jpg)
>이제 사용하면 됨...

### Windows
위의 경우와 유사하게 네트워크에서 자동으로 검색되면 로그인해서 사용해도 되나 안되면 아래의 방법을 사용해서 직접 넣어주면 된다.

- [Windows FTP SAMBA - 파일 탐색기로 FTP SAMBA 연결하기](/posts/win-ftp/)

### IOS
순정 "파일"엡에서도 파일관리가 가능하다. 애플이 많이 개방적이 되었다.

![smb](/img/living/iptime/smb4.jpg)
>**파일**앱에서 **...** 옵션 버튼을 누른다. (숨겨놓은 느낌) <br>
**서버에 연결** 을 누른다.

![smb](/img/living/iptime/smb5.jpg)
>역시나 자동 검색 안된다. 주소를 넣자... **192.168.xx.xx**

![smb](/img/living/iptime/smb5-1.jpg)
>**등록 사용자**로 로그인...

![smb](/img/living/iptime/smb6.jpg)
>이제 사용하면 된다.

하지만 애플의 패쇄성은... 파일앱에서도 되는게 있고 안되는게 있으니...

### Android
가볍고 무료인 CX 파일 탐색기로 쉽게 이용가능하다. (안드로이드는 순정이랄게 없으니...)

![ftp](/img/living/iptime/ftp1.jpg)
>무료이면서 다양한 기능을 제공한다. 내 모든 서버는 이 어플에서 해결하는 편이다. 모바일이 대세...

![ftp](/img/living/iptime/ftp2.jpg)
>**네트워크** -> **+** : 서버 추가

![smb](/img/living/iptime/smb7.jpg)
>**원격 저장소** -> **로컬 네트워크**

![smb](/img/living/iptime/smb8.jpg)
>역시 자동 검색이 된다... 선택

![smb](/img/living/iptime/smb9.jpg)
>로그인후 사용!!!

## 스트리밍
스트리밍이 된다는 것은 결국엔 파일관리까지 된다는 이야기임. 다운로드 역시 당연하다.

### Windows, MAC Book, IOS, Android(FIRE TV)
요즘 나오는 대부분의 동영상 플레이어들은 네트워크 기능을 가지고 있어서 쉽게 메뉴에서 찾아 볼 수 있다.

내가 쓰는 VLC, KODI 정도만 소개한다.

#### VLC Player
![ftp](/img/living/ipad/iptv5.jpg)

![smb](/img/living/iptime/smb10.jpg)
>**네트워크**만 누르면 자동으로 검색 결과를 보여줌..

![smb](/img/living/iptime/smb11.jpg)
> 로그인하고 사용하면 끝~~~

동영상 플레이어이기 때문에 자막도 문제 없이 재생된다.

#### KODI
내가 제일 좋아하는 어플... 해당 포스팅 참조하면 된다.


- #### [KODI Media Server DLNA, UPnP, SMB, FTP - 미디어 서버(소스) 연결하기](/posts/KODI-source/)

- #### [KODI Movies Library - 영화 라이브러리 설정법](/posts/KODI-library/)

- #### [KODI Movies Library AutoUpdate - 영화 라이브러리 자동 업데이트, 라이브러리 정리 사용법](/posts/KODI-autoupdate/)

- #### [KODI Movies Library The Movie DataBase - TMDB 영화 라이브러리 데이터베이스 연결법](/posts/KODI-tmdb/)
> 개인 Netflix를 만들수 있다...

-------

## PostScript
FTP와 DLNA의 중간정도 인듯하다. 자동검색은 되나 모든 파일을 정리할 수 있는... 그러나 해외에서의 사용은 안된다...

간단하게 집에서 사용하기는 무난하다...

-----------

### [< Back to IPTIME >](/posts/Iptime/)
