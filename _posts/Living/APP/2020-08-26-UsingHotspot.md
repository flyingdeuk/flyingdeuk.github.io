---
title: Wifi Storage for Android - 휴대폰을 무선 저장소로 사용하기 (Feat. Hotspot, ftp)
author: FlyingDeuk
date: 2020-08-26 20:55:00 +0800
categories: [Living, APP]
tags: [usefulapp, android, ios]
pin:
---

![set](/img/living/hotspot/hotspot_main.jpeg)

`FlyingDeuk's`
> Hotspot은 기본적으로 핸드폰의 LTE 데이터를 다른 기기에 공유해서 인터넷을 하게 해주는 기능이다. <br>
이 기능을 잘 활용하면 내 안드로이드 핸드폰에 저장된 내용을 wifi를 통해 공유하는 휴대용 저장소가 된다.  <br>
시중에 나와있는 무선 하드, 무선 저장소의 기능을 내 핸드폰으로 구현이 가능하다.

Wifi 수신기는 기본적으로 송신의 기능도 가지고 있다. <br>
`더이상 USB는 가지고 다니지 말자.`

`Wiki's`
> **핫스팟 또는 핫스폿(영어: hotspot)** 은 스마트폰, 노트북을 포함한 이동 단말기로 라우터 등 무선 액세스 포인트가 설치된 지역에서 무선 네트워크(WLAN)에 접속하여 초고속 인터넷과 각종 콘텐츠를 이용할 수 있게 하는 서비스 가능 지점이다. 보통 특정 지역에서 무선 접근 범위를 최대화하기 위해 공공장소의 천장, 벽이나 기타 전략적 위치에 설치된 하나 이상의 접근점(AP)으로 구성된다. 따라서 핫스팟 구역의 사용자는 노트북 컴퓨터를 이용하여 인터넷에 접속할 수 있다.

### 추천 어플

| 준비물          |                |
|:-------------------------|:-----------------|
| ![cx](/img/living/hotspot/cx.jpg)                               |__안드로이드 추천 어플__ <br> - 파일 서버 기능 필요 <br> - ftp, samba등        |
| ![cx](/img/living/hotspot/document.jpg) |__아이패드 추천 리더기__ <br> - 파일 클라이언트 기능 필요 <br> - ftp, samba등 |

> 유사한 기능의 어플은 다 사용이 가능함.

-----

### Hotspot 설정
Hotspot은 기본적으로 핸드폰의 모바일 데이터(인터넷)을 다른 휴대기기에서 wifi로 연결해 사용하기 위한 방법중에 하나임. (애플은 테더링이라 부름)<br>
그러나 어플을 활용하면 핸드폰 내부 저장소에 접근할 수 있음.  <br>

`모바일 데이터 소모를 원치않는다면 비행모드에서 할 것을 추천함. 중요!!` => 기내에서 사용추천(핸드폰 저장 영화 감상등...)


1. 비행기 모드 켜기.
2. 와이파이 켜기.
3. 아래의 사항 따라하기.

![set](/img/living/hotspot/phone_hotspot_menu.jpg)
> **설정** -> **네트워크 및 인터넷** 메뉴 진입

![set](/img/living/hotspot/phone_hotspot_menu1.jpg)
> **핫스팟 및 테더링** 진입 <br>
참고로 핫스팟 설정이 완료되고 나면 위와같이 wifi 수신기는 자동으로 꺼진다. 송신기가 켜지므로...


![set](/img/living/hotspot/phone_hotspot_ps.jpg)
>핫스팟 사용으로 누르고 뭔하는 이름과 비밀번호를 설정한다. <br>
집에 있는 공유기 설정과 유사함.

![set](/img/living/hotspot/phone_hotspot.jpg)
>한번만 설정해주면 상단 메뉴에서 언제든지 핫스팟을 켜고 끌수 있다.

-----

### CX 파일 탐색기 실행
CX 탐색기 말고도 대부분의 안드로이드 탐색기에는 PC와의 연결 등의 메뉴로 해당 기능을 수행할 수 있음.

![set](/img/living/hotspot/cx1.jpg)
>**네트워크** -> **PC에서 액세스** 진입

![set](/img/living/hotspot/cx2.jpg)
>**포트번호** 기본값은 2100임 (ftp의 경우) -> 기억!! <br>
`시작` -> 파일 전송 서비스 시작됨.

![set](/img/living/hotspot/cx3.jpg)
>해당 주소를 컴퓨터나 아이패드등의 인터넷 브라우져로 실행하면... <br>

__폴더 형태로 핸드폰의 저장소에 접근해서 다운로드나 실행등을 할 수 있음.__


-------


### 아이패드 설정
아이패드를 대표로 설명함. <br>

다른 기기들보다 아이폰 아이패드 계열은 보안에 복잡하여 브라우져 형태보다는 어플로 진입하는 게 더욱 추천됨.

`핸드폰에 저장된 문서, 영화, 음악등을 패드에서 볼 수 있음`

![set](/img/living/hotspot/ipad_wifi.jpg)
>핫스팟에 저장한 이름의 wifi에 연결 (비밀번호 입력)

![set](/img/living/hotspot/ipad_add.jpg)
> 추천되는 Document 어플 실행 <br>
`+ Add Connection` 주변 네트워크에 연결하는 기능

![set](/img/living/hotspot/ipad_ftp.jpg)
>탐색기마다 다르겠지만 CX탐색기는 ftp를 사용함.

![set](/img/living/hotspot/ipad_adress.jpg)
>핸드폰에 써있는 IP 주소 즉 192.168.---.--- 형태의 주소 입력 <br>
포트 번호도 입력

### 결과
핸드폰 탐색기에서의 폴더를 동일하게 탐색하며 무선 저장소로 사용!!!

![set](/img/living/hotspot/result.jpg)
>영화나 음악, 문서등을 모두 이용가능함.

----

### PostScript
아이패드나 아이폰은 음악과 영화와 같은 컨텐츠이 저작권이 강해 파일을 저장하거나 꺼내기가 불편하게 되어있음. 이와 같은 방식을 활용하면 안드로이드로 편하게 다운받은 파일들을 큰화면으로 즐길수 있고 저장도 편하게 할 수 있음.

@ 바로가기 : [uTorrent 사용법(어플 소개)](/posts/UsingUTorrent/)

[INDEX로 돌아가기](/posts/Android/)
