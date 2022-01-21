---
title: KODI Media Server DLNA, UPnP, SMB, FTP - 코디 미디어 서버(소스) 연결하기 (for Mac, Android, Windows)
author: FlyingDeuk
date: 2021-08-12 20:55:00 +0800
categories: [Living]
tags: [usefulapp, mac, android, windows, kodi]
pin:
---


`FlyingDeuk's`
> KODI에 비디오, 음악, 사진과 같은 파일을 연결하려면 해당 기기에 저장된 데이터를 사용할 수 있겠지만 본인의 서버를 무선으로 연결해서 사용도 가능하다. <br>
요즘 NAS도 많이 들 사용하는 추세라... 본인은 IPTIME 공유기의 미디어 서버, 라즈베리파이의 서버 기능으로 연결해서 사용중이다. <br>
다음엔 라이브러리 연결이라는 재미난 포스팅을 할 계획이다.

대표적인 프로토콜로 DLNA(UPnP), SAMBA, FTP 정도만 설명하겠다.
- DLNA(UPnP) : 가정내 같은 공유기에 연결된 모든 기기에 데이터를 로그인 없이 전송하는 방식(단 컨텐츠의 제한이 있음. 비디오, 음악, 사진)
- SAMBA : 윈도우 네트워크로 불리운다. 역시 가정내 같은 공유기에 연결된 기기 사이에서 로그인과 권한을 통해서 파일을 공유한다.
- FTP : 대표적인 파일 전송 프로토콜로 외부에서도 접속이 가능하다. DNS 역할을 해주는 공유기가 있으면 무료로 가능하다.

## KODI Media Source 연결
위의 방법외에도 다양한 방법이 있다. 내가 주로 사용하는 방법 3가지만 소개한다.

### FTP 연결
일반적으로 공유기에서 제공하는 주소값으로 외부에서 연결 가능하다. ([IPTIME 공유기 DDNS - 외부/해외에서 접속하는 법](/posts/IptimeSet/))

![src](/img/living/kodi/source1.jpg)
>**설정** -> **파일 관리자** <br>
모든 연결을 총괄한다고 생각하면 쉬움.

![src](/img/living/kodi/source2.jpg)
> **소스 추가** <br>
위에 보이는 **kodi** 이전 포스팅에서 생성된 Repository.... **LEXAR** 는 이 맥북에 연결된 USB이다.

![src](/img/living/kodi/source3.jpg)
> 기본적으로 **탐색** 을 누르면 추천되는 연결 방법등으로 기본으로 볼 수 있다. <br>
없음은 그냥 본인이 다 알아서 주소를 넣어야하는...

![src](/img/living/kodi/source4.jpg)
>FTP의 경우는 본인이 직접 입력해야한다. **네트워크 위치 추가...**

![src](/img/living/kodi/source5.jpg)
>서버 주소, 포트, 사용자명, 비밀번호를 입력하고 확인

그리고 나서 마음에 드는 이름을 지어주면 된다. DEUKFTP...

### SAMBA 연결
가정내 연결이다. 그래서 그냥 내부 IP주소를 넣거나 자동 검색되는 넘을 사용하면 된다.
![src](/img/living/kodi/source3.jpg)
>역시나 **탐색**...

![src](/img/living/kodi/source6.jpg)
>원래는 **원도우 네트워크(SMB)** 를 누르면 자동으로 검색이 되야한다... 안된다... <br>

![src](/img/living/kodi/source7.jpg)
>FTP와 동일하게 **네트워크 위치 추가...** <br>
여기서도 **-탐색**을 누르면 되야하는 데... 안된다. <br>
메뉴얼로 내부 IP 주소 (공유기의 IP주소를 넣으면 된다. **192.168.0.1** 같은...), 사용자명, 비밀번호를 넣는다.

역시나 이름을 지어주면 끝... DEUKSMB...

### DLNA(UPnP) 연결
스마트 TV등에서 유용하게 사용할 수 있는 형식 단순하나 보안에는 취약함... 하지만 편하다...

#### DLNA(UPnP) 기능켜기
처음엔 OFF 상태이다. 기능을 켜줘야 정상작동함.

![src](/img/living/kodi/source8.jpg)
>**설정** -> **서비스** 해당 기능을 켜준다. <br>
나중에 포스팅할지는 모르겠지만 KODI Remote APP으로 제어를 위해서는 원격제어 허용을 해주면 된다.

#### DLNA(UPnP) 연결
![src](/img/living/kodi/source3.jpg)
> 역시나 **탐색**

![src](/img/living/kodi/source9.jpg)
>**UPnP** 라는 항목이 생겼다.  

![src](/img/living/kodi/source10.jpg)
>자동으로 인식해서 보여준다. <br>
DLNA는 자동인식이 안되면 연결할 수가 없다... 다음에 나옴...

![src](/img/living/kodi/source11.jpg)
>복잡한 주소는 알아서 붙는다.... 자동인식이 안되면 어찌... ㅎㅎㅎ

역시 이름은 알아서... DEUKDLNA...

### KODI Source 사용
Source를 모두 연결했다. 이중에 하나의 방식으로만 연결해도 사용에는 문제가 없다. <br>
본인은 FTP를 주로 사용한다. 외국 호텔방에서 써야하니...

![src](/img/living/kodi/source12.jpg)
>이제는 KODI내의 모든 기능. 비디오, 음악, 사진등의 특히 라이브러리같은 곳에서 마음대로 연결된 소스로 연결이 가능해 졌다.

---------------

### PostScript
비디오 라이브러리, 음악 라이브러리에서도 각각 소스를 설정할 수 있다. 하지만 상기의 방법을 사용하면 모든 영역에서 한번의 연결로 두루 사용이 가능하다.


[INDEX로 돌아가기](/posts/KODI/)
