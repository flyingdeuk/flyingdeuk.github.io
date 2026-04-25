---
title: Fire TV "Your advert-supported plan is not availiable in this region", "회원님의 광고형 멤버십은 이 지역에서 제공되지 않습니다" 해결 방법 (Feat. Fire TV, IPTIME, Wireguard) <2026.4.25 Updated>
author: FlyingDeuk
date: 2026-04-25 
categories: [Living]
tags: [usefulapp, android, firetv, iptime, wireguard]
pin:
---

![fire](/img/living/fire/wire13.png)

`FlyingDeuk's`
> 이전 Netflix의 한가구 제한을 풀기위한 노력을 했으나 이제는 더이상 불가능하다. 그런 이유로 제일 저렴한 네이버 멤버십으로 한달 4900원에 시청하고 있으나... <br>
일부 동남아에서는 광고형 저가 멤버십이 없는 관계로 매번 시청이 어려워 방법을 찾게 되었다. 

해당 방법을 사용하는 조건은 다음과 같다. 
- 광고형 Netflix를 이용하는 사람. 
- 가정내 사설 공유기를 사용하는 경우
- 해당 공유기에 Wireguard server의 기능을 가지고 있는 경우. 

`Fire TV는 특성상 다른 VPN을 무료로 이용하기에는 어려움이 있어 알아본 결과이다.`

`Wiki's`
> 와이어가드(WireGuard)는 암호화된 가상사설망(VPN)을 구현하는 통신 프로토콜이자 자유-오픈 소스 소프트웨어로, 사용 편의성, 고속 성능 및 낮은 공격 표면을 목표로 설계되었다.[3] 두 가지 일반적인 터널링 프로토콜인 IPsec 및 OpenVPN보다 더 작고 더 나은 성능을 목표로 한다.[4] 와이어가드 프로토콜은 UDP를 통해 트래픽을 전달한다.
2020년 3월, 소프트웨어의 리눅스 버전은 안정적인 프로덕션 릴리스에 도달하여 리눅스 5.6 커널에 통합되었으며 일부 리눅스 배포판에서는 이전 리눅스 커널로 백포트되었다. 리눅스 커널 구성 요소는 GNU GPL 버전 2에 따라 라이선스가 부여된다. 다른 구현은 GPLv2 또는 기타 자유-오픈 소스 라이센스에 따른다.
와이어가드라는 이름은 제이슨 A. 돈필드(Jason A. Donenfeld)의 등록 상표이다.
-----------

# PART 1. IPTIME
아주 기본적인 공유기 연결후 설정법은 내용 길이상 생략하겠다. 

- ### [IPTIME 공유기 DDNS - 외부/해외에서 접속하는 법](/posts/IptimeSet/) 
    - 외부에서 접속하는 법은 이미 포스팅되어있음.

> 물론 가정내에서 연결시에는 필요는 없다. 

------------

![fire](/img/living/fire/wire14.PNG)
- 편의상 핸드폰 어플을 이용하는 방법을 소개한다. 
- 관리도구 - 전체 설정 - VPN 설정 - WireGuard 서버 설정

-------

![fire](/img/living/fire/wire19.PNG)
- 일단 실행을 눌러주고 나머지는 건드리지 않아도 됨. 
- 아래로 내려서 더하기(추가) 버튼을 눌러준다. 
- 피어 추가 자동으로 그냥 두고 이름은 알아서 입력

------

![fire](/img/living/fire/wire15.PNG)
- QR이 나오지만 파일을 이용할 거라 아래의 피어설정 다운로드를 누른다. 
- 핸드폰에 따라 다르겠지만 아이폰의 경우는 해당 폴더에 저장된다. 

----------

![fire](/img/living/fire/wire16.PNG)
- 파일 어플에서 해당 위치에 가보면 잘 저장이 되어있다. 
- 확장자는 .conf 파일이다. 

> 일단계는 성공

----------

# PART 2. Google Drive
Fire TV에 파일 전송을 하는 방법중 어디서나 가능한 방법을 선택했다. 모두가 가능한 방법
- 핸드폰에 저장된 conf 파일을 드라이브로 옮긴다. 

-----------

![fire](/img/living/fire/wire17.PNG)
- 드라이브 어플을 열고 아래의 더하기를 눌러준다. 다음 파일 업로드 - 탐색

-------

![fire](/img/living/fire/wire18.PNG)
- 폴더 위치를 찾아도 되나 conf 파일은 거의 없으므로 conf로 검색하면 바로 내 폰에 있는 파일을 빠르게 찾을 수 있다. 
- 업로드할 본인 드라이브의 폴더를 정하고 업로드 후 확인!!!

------------

# PART 4. Downloader
Fire TV의 기본 브라우져는 Viewer전용이다. 인터넷상에서 파일을 Down 받으려면 해당 어플이 필요하며 이미 포스팅되어 있다. 

-----

![fire](/img/living/fire/wire7.jpg)
- 만약 Downloader가 없다면 Fire TV APP Store에서 설치하면 된다. 
- 주소창에 Google.com 로그인을 해준다. 그중에 드라이브를 선택

-------

![fire](/img/living/fire/wire8.jpg)
- 업로드한 폴더를 찾아가면 파일 이름은 안보이고 네모난 형태만 보인다. 일반적인 문서나 이미지 파일이아니라서....

-------

![fire](/img/living/fire/wire9.jpg)
- 미리보기 할 수 없는 파일이며 다운로드 선택

-----

![fire](/img/living/fire/wire10.jpg)
- 다운로드된 위치만 확인하고 DONE 누르면 된다. 

-------------

# PART 5. WG VPN
Fire TV의 무료 어플로 간단하고 안정적이다. 

![fire](/img/living/fire/wire1.jpg)
- 간단하게 돋보기로 검색!!!

![fire](/img/living/fire/wire2.jpg)
- Wireguard를 검색

![fire](/img/living/fire/wire3.jpg)
- WG VPN을 설치하고 실행한다. 

![fire](/img/living/fire/wire4.jpg)
- 우측 상단의 더하기를 눌러 파일을 추가해준다. 

![fire](/img/living/fire/wire11.jpg)
- 다운로드

![fire](/img/living/fire/wire12.jpg)
- 파일을 선택하면 저장이 된다. 

![fire](/img/living/fire/wire5.jpg)
- conf 파일이 Fire TV에 추가되었다. 해당 파일을 눌러 CONNECT 시켜주면 된다. 

![fire](/img/living/fire/wire6.jpg)
- 집에 있는 IPTIME에 연결되었으며 이제 Fire TV는 한국에 있는 샘이 된다. 

'전 세계 어디서든 한국에서 보는 것도 동일하게 시청이 가능하다.'


---------

## PostScript
여러가지 무료 VPN 사용법을 이미 포스팅했다. 물론 다른 방법으로 Fire TV를 연결하는 것도 있으나 일반적인 유저의 접근이 쉽지 않을 거 같아서... 조금은 안정적이고 쉬운 방법을 소개한다. 물론 나두 사용하기 위한....

'WireGuard 프로그램, 어플등을 사용하면 노트북, 아이패드, 아이폰, 안드로이드폰등등 모두 응용이 가능하다.' 


-------

### [< Back to FireTV STick >](/posts/FireTV/)
