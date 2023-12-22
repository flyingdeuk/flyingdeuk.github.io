---
title: KODI Netflix Addon 인증키로 로그인하는 법 By 안드로이드폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey) <2023.12.19 Updated>
author: FlyingDeuk
date: 2023-12-19 
categories: [Living]
tags: [usefulapp, mac, android, windows, linux, kodi, nfauthentication]
pin:
---

![netlfix](/img/living/kodi/netflixkey.jpg)

`FlyingDeuk's`
> FireTV에 KODI 설치후 Netflix 에드온을 사용시 로그인 문제 해결을 위한 인증키로 로그인하는 방법이다. 삼성등의 안드로이드폰을 활용한 방법!!! 

>Xiaomi Mi Stick에도 설치해봤으나 되지 않는다. FireTV만 가능한 방법이다.

`이는 FireTV에서 Netflix 계정공유 제한을 무력화시키는 방법이다.`

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 아이폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/post/KODI-netflixkey/) -> 아이폰은 해당 링크를 클릭하면된다. 

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

----------

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
    3. 5일 뒤 Expired 되지만 한번 로그인에 사용했으면 이후는 자동 로그인되니 문제없음.  

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

## 안드로이드폰 -> FireTV 인증키 전송법
두가지 기기에 대해서 테스트를 완료했다. 본인이 가지고 있는 기종 것만 참고하면 된다.

-----------

### CX 파일 탐색기 어플 활용

![netlfix](/img/living/kodi/netflixkey1-1.jpg)
- 다른 어플도 있을 수 있으나 파일관리 및 서버기능을 포함하는 추천 어플로 해 보았다. 

![netlfix](/img/living/kodi/netflixkey1-2.jpg)
- 안드로이드폰내의 다운로드 폴더에 NFAuthenticationKey 파일을 저장해 준다.  

![netlfix](/img/living/kodi/netflixkey1-3.jpg)
- 다운로드에 파일을 확인해 준뒤...


![netlfix](/img/living/kodi/netflixkey1-4.jpg)
- 네트워크 기능중에 "네트워크 액세스"를 눌러준다. 

![netlfix](/img/living/kodi/netflixkey1-5.jpg)
- 포트나 비밀번호는 알아서 정해준 뒤 시작을 눌러준다. 


`이는 가정내에서 같은 공유기를 사용하는 경우 가능하다.`

![netlfix](/img/living/kodi/netflixkey1-6.jpg)
- FTP서버 방식에 주소는 위와 같다. 통상 안드로이드폰이 공유기로 부터 받은 IP 주소가 서버주소가 된다.

------------

### 안드로이드폰 -> FireTV 전송법
FireTV에서 파일에 접근하는 방법이다. 

![netlfix](/img/living/kodi/netflixkey23.jpg)
- FireTV의 KODI의 설정으로 진입한다.

![netlfix](/img/living/kodi/netflixkey24.jpg)
- 파일 관리자를 열어 서버의 리스트에 아이폰을 올린다. 

![netlfix](/img/living/kodi/netflixkey25.jpg)
- "소스추가"를 눌러준다. 

![netlfix](/img/living/kodi/netflixkey26.jpg)
- 여러가지 네트워크 소스들이 많아 탐색을 눌러준다. 

![netlfix](/img/living/kodi/netflixkey27.jpg)
- "네트워크 위치 추가"를 눌러주고 확인을 눌러준다. 

![netlfix](/img/living/kodi/netflixkey30.jpg)
- 오른쪽의 작은 화살표를 눌러 안드로이드폰의 네트워크 형식에 맞는 FTP서버를 선택해주고 위의 주소와 암호를 넣어준다. 

![netlfix](/img/living/kodi/netflixkey29.jpg)
- 주소는 숫자만을 입력해주면 된다. http://는 생략!!!
    - 사용자명, 비밀번호, 포트번호를 넣어주면 된다. 

![netlfix](/img/living/kodi/netflixkey31.jpg)
- 저장된 방식을 확인해주고...

![netlfix](/img/living/kodi/netflixkey32.jpg)
- 이름을 지정해주면 네트워크 소스가 추가된다. 

--------------

### Netflix 인증키 로그인 방법

![netlfix](/img/living/kodi/netflixkey35.jpg)
- Netflix 에드온을 실행해준다. 

![netlfix](/img/living/kodi/netflixkey5.jpg)
- 인증키 로그인을 선택.

![netlfix](/img/living/kodi/netflixkey36.jpg)
- 위에서 설정한 FTP 방식의 주소를 선택

![netlfix](/img/living/kodi/netflixkey37.jpg)
- Key를 받은 핸드폰 기본 저장소 device를 선택. 

![netlfix](/img/living/kodi/netflixkey38.jpg)
- 여러 폴더중에서 Download를 선택. 

![netlfix](/img/living/kodi/netflixkey39.jpg)
- NFAuthencation Key를 선택해준다. 

![netlfix](/img/living/kodi/netflixkey43.jpg)
- 위에서 기억해둔 PIN 을 넣어주면 이메일 ID의 인증과정이 통과가 된다. 

![netlfix](/img/living/kodi/netflixkey44.jpg)
- ID는 Pass 되었으니 암호를 넣어주면 된다. 

-----------

![netlfix](/img/living/kodi/netflixkey45.jpg)
- 로그인에 성공되었고 공유계정중 내가 사용하는 계정을 선택해서 사용하면 됨. 

![netlfix](/img/living/kodi/netflixkey46.jpg)
- KODI의 Netflix는 화려하지 않아 사용하지 않았었다. 하지만 공유계정을 사용하기 위한 것이니... 해당 Category를 선택한다. 

![netlfix](/img/living/kodi/netflixkey47.jpg)
- 목록으로 된 리스트는 보기가 좋아않다... 리모컨의 왼쪽 방향키를 눌러주면 옵션으로 진입이 가능하다. 
- 여기서 목록을 본인이 원하는 표시 형식으로 바꿔 주면 조금은 유사한 화면을 볼 수 있다. 

![netlfix](/img/living/kodi/netflixkey48.jpg)
- 이정도면 괜찮다. 

![netlfix](/img/living/kodi/netflixkey49.jpg)
- 테스트 중 자막이 나오지않았다. 초기 설정이 안되어있어서... 리모컨의 선택 버튼을 눌러주면 아래에 옵션이 니온다. 자막 모양의 아이콘을 선택.

![netlfix](/img/living/kodi/netflixkey50.jpg)
- 자막 사용을 설정해주고 한글 자막이 안나오는 경우 Korean으로 변경해주면 된다. 

`이제는 공유계정을 사용하거나 해외 체류시에도 한가구 제한없이 Netflix를 즐길 수 있다.`

------

#### Postscript
정말 많은 사람들이 OTT 유행에 많은 회사에 가입하고 있는 상황에서 이런 행보는 조금은 이해가 가지않는다... 우리나라만 그런지는 모르겠지만 유투브 가족계정도 안되고... 언제 다른 방법으로 막힐 지는 모르겠으나... 참 씁쓸하다. 

[INDEX로 돌아가기](/posts/KODI/)
