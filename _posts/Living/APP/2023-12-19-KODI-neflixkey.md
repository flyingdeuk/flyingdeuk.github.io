---
title: KODI Netflix Addon 인증키로 로그인하는 법 (Feat. KODI, Neflix, NFAuthenticationKey) <2023.12.19 Updated>
author: FlyingDeuk
date: 2023-12-19 
categories: [Living]
tags: [usefulapp, mac, android, windows, linux, kodi, nfauthentication]
pin:
---

![netlfix](/img/living/kodi/netflixkey.jpg)

`FlyingDeuk's`
> FireTV에 KODI 설치후 Netflix 에드온을 사용시 로그인 문제 해결을 위한 인증키로 로그인하는 방법이다. 

`이는 FireTV에서 Netflix 계정공유 제한을 무력화시키는 방법이다.`

-----------------
## 이메일로 로그인하기
Netflix를 설치하고나서 실행하면 로그인하라는 메세지가 나온다. 

![netlfix](/img/living/kodi/netflixkey2.jpg)
- 이메일로 로그인하기를 선택하고 로그인해본다. 

![netlfix](/img/living/kodi/netflixkey1.jpg)
![netlfix](/img/living/kodi/netflixkey4.jpg)
- 이메일로 로그인된다면 그게 제일 편하다. 

![netlfix](/img/living/kodi/netflixkey3.jpg)
- 어쩐일인지 Netflix가 보안에 관련된 업데이트를 했는지 최근엔 잘 되지않는다. 

-------------

## 인증키로 로그인하기
NFAuthenticationKey를 이용해서 이메일대신 아이디를 입력하는 방법이다. 조금 귀찮기는 해도 계정공유를 무력화하기 위해서는 이 방법이 최선이다. 

![netlfix](/img/living/kodi/netflixkey5.jpg)

### NFAuthenticationKey 다운로드
이 방법은 윈도우즈 PC로 작업을 하고 난후 FireTV에 옮기기위해 여러 방법중에 핸드폰을 이용하는 방법을 소개한다. 

<https://github.com/CastagnaIT/plugin.video.netflix/wiki/Login-with-Authentication-key> -> KODI Netflix 개발자의 Github사이트로 최신판을 원한다면 위 링크에서 다운로드 받으면 된다. 

![netlfix](/img/living/kodi/netflixkey6.jpg)
- For Windows (Click to Expand)를 누르고 아래의 .zip 파일을 눌러 다운로드사이트로 간다. 

![netlfix](/img/living/kodi/netflixkey7.jpg)
- 해당 웹하드 사이트에 있는 Download This File을 눌러서 다운롣 받으면 된다. 


`현재 테스트해본 최신 파일을 바로 다운로드 받고 싶다면...`

- #### [NFAuthenticationKey_Windows_1.2.2.2.zip](/img/living/kodi/NFAuthenticationKey_Windows_1.2.2.2.zip) -> 해당 링크를 클릭후 다운로드 받으면된다. (2023.12.19 기준)

------------

### 인증키 받는 법
Netflix에 아이디를 이메일 대신 인증키의 형식으로 저장하는 방법이다. 

![netlfix](/img/living/kodi/netflixkey8.jpg)
- 다운받은 zip파일 압축을 풀어준다. .exe 실행파일하나가 있다. 

![netlfix](/img/living/kodi/netflixkey9.jpg)
- 실행시키면 시스템 정보를 건드리는 프로그램의 경우 바이러스라 판단해서 나오는 경고이나 문제가 없는 프로그램으로 "추가정보"를 눌러준다. 

![netlfix](/img/living/kodi/netflixkey10.jpg)
- 이후에 실행을 눌러서 실행해주면 된다. 

![netlfix](/img/living/kodi/netflixkey15.jpg)
- 실행하면 위와 같은 창이 뜬다. 내용을 잘 읽어보면되나 간단하다. 
    1. Chrome이 실행중이라면 꺼준다. 
    2. Start를 눌러준다. 
    3. 5일 뒤 Expired 된다는데 테스트해보진 않음. 

![netlfix](/img/living/kodi/netflixkey13.jpg)
- 위와 같은 문구와 함께 잠시 기다리면....

![netlfix](/img/living/kodi/netflixkey14.jpg)
- 보안을 위해서 시크릿 모드로 Netflix Login Page로 자동으로 뜨고 이메일등의 정보로 로그인하고 나면.... 자동으로 꺼진다....

![netlfix](/img/living/kodi/netflixkey12.jpg)
- Chrome이 자동으로 꺼진이후에 PIN 번호가 나오는 데 적어놓자...

![netlfix](/img/living/kodi/netflixkey11.jpg)
- 이전에 압축을 풀었던 폴더에 "NF Authentication.key" 파일이 만들어 진다. 

`이제는 FireTV에 옮겨야하니 윈도우 PC에서 이메일이든 클라우드를 쓰던 자신의 방법으로 내 핸드폰에 Key를 옯겨주면 다음 단계로...`

-----------------

### 아이폰/안드로이드폰 -> FireTV 인증키 전송법
두가지 기기에 대해서 테스트를 완료했다. 본인이 가지고 있는 기종 것만 참고하면 된다.  

#### 아이폰
Documents 어플 활용법

#### 안드로이드폰
File Explore 어플 활용법






------

## Netflix Addon
### 로그인
계정에 로그인 정보 넣어서 사용하면됨.

![kodi_addon](/img/living/kodi/netflix_set.jpg)

### 옵션
좌측에 있는 옵션은 보여주는 방식에 대한 조절을 사용자가 원하는 데로 바꿀 수 있다.
>넥플렉스 어플의 정신없음이 싫은 사람은 자신 스타일대로 변경이 가능하다. <br>
하나씩 눌러 보면.. 이해가 감...<br>
개인적으로 목록 리스트 표시를 추천순이 아니라 **출시순** 으로 바꿔서 사용하고 있음. (최신 작이 상위에 올 수 있게...)

### Netflix Addon 장점
Netflix는 지역마다 서비스가 다르다. 최신 영화도 미국, 유럽, 아시아등 다르게 서비스를 한다. 이는 자막의 경우도 동일하다. 어디에서는 한글 자막을 지원하던 영화도 다른 지역에서는 지원하지 않는 경우가 많다.
> KODI의 자막 서비스로 Netflix에서 자막을 지원하지 않더라도 자동으로 자막을 찾아준다. -> **a4kSubtiles** 이용

### 자막 찾는 법
원칙적으론 자동으로 찾아야 한다. 안될 경우 수동으로...

![kodi_addon](/img/living/kodi/kodi_subtitle2.jpg)
- 자막찾기 : 내가 자막을 따로 다운 받은 경우 로컬화일을 연결
- 자막 내려받는 중 : 아래의 창이 뜨며 수동으로 검색가능.


![kodi_addon](/img/living/kodi/kodi_subtitle.jpg)
> 리스트에서 수동으로 자막을 선택 가능함.

------

#### Postscript
한국 OTT 서비스를 모아 놓아서 너무나 편리하게 설치 및 이용이 가능하다. <br>
KODI의 장점은 중간중간에 나오는 광고를 보지않아도 된다는 것과 리모컨의 화살표로 간단하게 제어가 가능하다는 것... 최고의 미디어 어플!!!

[INDEX로 돌아가기](/posts/KODI/)
