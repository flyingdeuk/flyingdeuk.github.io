---
title: Fire TV Netflix 한 가구 제한 무력화 방법 (Feat. 계정공유, KODI, NFAuthenticationKey_Windows) <2023.12.15 Updated>
author: FlyingDeuk
date: 2023-12-15 
categories: [Living]
tags: [usefulapp, android, firetv, netflix, kodi]
pin:
---

![fire](/img/living/fire/kodinetflix.jpeg)

`FlyingDeuk's`
> Netflix가 2023년 11월부터 한가구에 해당하지않는 계정에 대해서 제한을 걸기 시작했다. 이로 인해서 지인 및 가족들과 계정을 공유해서 사용하기 위해서는 5000원을 더 납부해야만 한다. <br>
이에 방법을 모색하던 중 알아낸 방법을 공유한다. 모바일 기기의 경우는 제외가 되어 문제가 없으나 FireTV와 같은 TV OS 계열은 모두가 제한의 대상이 된다. 

한 가구 인정의 조건은 다음과 같다. 대략...
- 한 가구내에서 같은 인터넷을 사용해야한다. 
- Portable Device의 경우 한달에 한번은 한 가구내 인터넷에 접속해야한다. 
- 여행중 임을 증명해야한다.

`아래의 방법으로 FireTV의 경우 KODI를 사용해서 위의 제한을 회피할 수 있다.`

-----------

## FireTV Netflix 계정공유 사용법
해당 내용은 이미 FireTV를 사용하고 있다는 가정에서 시작한다. 그렇지 않는 경우는 해당 블로그에서 초기 사용법을 찾아보길 바란다. 

### FireTV KODI Netflix 에드온을 이미 사용하고 있는 경우
이전 포스팅들로 이미 한국 OTT 에드온을 설치한 사람이라면 아래의 포스팅만 보면 된다. 

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 아이폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/post/KODI-netflixkey/) -> 아이폰은 해당 링크를 클릭하면된다. 

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 안드로이드폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/post/KODI-netflixkey1/) -> 안드로이드폰은 해당 링크를 클릭하면된다. 

--------------

## KODI 섪치를 위한 필수 어플 설치법
Downloader와 KODI, KODI내 Netflix만 설치하면 된다. 

### DOWNLOADER 설치
**KODI** 설치를 위해서는 반드시 필요한 프로그램 <br>
INTERNET은 기본적으로 다운로드 기능이 없음. 그래서 파일을 다운받고 싶을 때는 이 어플을 이용해야함.

![fire](/img/living/fire/down.jpg)
>**Home - Apps - Categories - UTILITY** 또는 **Search** 에서 **"Downloader"** 검색해서 설치하면 됨.

![fire](/img/living/fire/down1.jpg)
>설치후 실행하면됨

![fire](/img/living/fire/down2.jpg)
>주소입력창에 사이트 주소입력후 어떤 파일이든 다운로드가 가능하고 apk의 설치파일의 경우 설치도 가능함.

kodi뿐 아니라 인터넷 상에서 모든 형식의 파일을 다운로드하는 데는 Downloader를 사용해야 파일을 저장할 수 있다.

------------

## KODI 설치 
한국 실시간 TV, 모든 회사의 무료 영화나 드라마 시리즈를 보기위해서는 KODI의 설치가 필요하다. <br>
Opensource 즉 무료로 모든 것을 이용할 수 있다.

### KODI 설치전 사전 작업 - Apps from Unkown Sources
일반적으로 요즘 기기들은 모두 APP STORE를 경유하도록 한다. 하지만 APP STORE에 올리지 않는 좋은 어플도 많다. <br>
신뢰할 수 있는 사이트의 경우는 허용해도 전혀 문제가 없다.

![fire](/img/living/fire/unknown3.jpg)
>기본적으로 모든 안드로이드 디바이스는 공식 APP STORE를 거치치않는 어플에 대해서 설치는 가능하나 옵션을 선택해줘야한다. <br>
여기에서 설정으로 자동 연결되나 안되는 경우는 아래의 방법으로 설정을 변경해 주면 된다.

이점이 안드로이드가 애플보다 확장성이 좋은 이유이나 불법 소프트웨어를 조심해야 되는 이유가 되기도 한다.

![fire](/img/living/fire/unknown.jpg)
>**Home - Settings - My Fire TV**

![fire](/img/living/fire/unknown1.jpg)
>**Developer options**

`Developer options가 보이지 않는 경우는 "About"를 7번 눌러주면 나타난다. 일종의 트릭. 모든 안드로이드 기기들은 해당 방법으로 가능하다.`

![fire](/img/living/fire/unknown2.jpg)
>**Apps from Unknown Sources를 ON으로 변경**

-----------

### KODI 다운로드 (https://kodi.tv)
Downloader 어플을 이용하면 된다. 최신 버전의 KODI 20.x를 설치한다.

![fire](/img/living/fire/down3.jpg)
>KODI 주소 입력!! **kodi.tv** 만 입력하면 됨<br>

![old](/img/living/kodi/kodi_old.jpg)
> 상단의 **Download** Click!

![old](/img/living/kodi/kodi_2.jpg)
> FireTV는 안드로이드이니.. Android 선택

![old](/img/living/kodi/kodi19_2.jpg)
> 최신 버전은 KODI 20.x로 **32 비트**를 선택해 줘야한다. (예전 포스팅 사진을 그대로 사용함.)

![fire](/img/living/fire/down4.jpg)
>Download 완료되면 자동으로 설치를 물어본다. 자동으로 **Files**에 저장이 된다.

----------

## KODI 기본 설정
설치를 완료하고 나면 실행한다.

![kodi_main](/img/living/kodi/kodi19.jpg)
> 첫화면은 위와 같다. (19.xx 의 버전이나 최신은 20.xx이다.)

![kodi_set1](/img/living/kodi/kodi_set1.jpg)
> **Home**화면... 초기에는 영어로 표시된다. <br>
위의 **톱니바퀴모양**의 설정으로 진입

![kodi_set2](/img/living/kodi/kodi_set2.jpg)
> 시스템 설정 기본화면. <br>
파일관리자, 에드온, 인터페이스가 주로 많이 사용됨.<br>
**인터페이스**로 이동<br>

### 기본 언어 설정

![kodi_set3](/img/living/kodi/kodi_set3.jpg)
> Skin에서 Font를 Arial based로 변경 **(한글은 Arial based만 가능함)**

![kodi_set4](/img/living/kodi/kodi_set4.jpg)
- 언어 : **Korean** 변경
- 키보드 레이아웃 : **Korean 키보드** 추가

### 메인 메뉴 설정
홈(Home)화면의 항목을 원하는 것으로 변경가능함.

![kodi_skin](/img/living/kodi/kodi_skin.jpg)
> **설정** -> **인터페이스** -> **스킨** -> **스킨설정** -> **메인 메뉴 항목** <br>
메인 화면에서 원하는 항목만 켜고 끌수 있음.<br>
메인 화면 좌측의 메뉴가 바뀌는 것을 알 수 있음.<br>
**에드온**, **TV**, **즐겨찾기** 정도만 남겨두고 끄면 됨.

------------

### Unknown Source 추가

![kodi_unknown](/img/living/kodi/kodi_unknown.jpg)
> **설정** -> **시스템** -> **에드온** <br>
**알수없는 소스**를 활성화해서 Addon을 설치할 수 있게 해줌.

이 정도면 필요한 기본 설정은 끝이다. 다음은 에드온(KODI내부의 어플을 에드온이라 부름)설치가 되겠다.

----------

### KODI 에드온 설치 (flyingdeuk 저장소 연결)

![kodi_addsrc0](/img/living/kodi/kodi_addsrc0.jpg)
> **설정** 화면에서 **파일관리자**로 이동 <br>

![kodi_addsrc](/img/living/kodi/kodi_addsrc.jpg)
> **소스추가**를 눌러서 경로를 추가한다.

![kodi_addsrc1](/img/living/kodi/kodi_addsrc1.jpg)
> **없음**을 눌러 경로를 수기로 입력한다. <br>

![kodi_addsrc2](/img/living/kodi/kodi_addsrc2.jpg)

저장소 주소 : **https://flyingdeuk.github.io/kodi**

이름 **KODI**로 자동 들어가며 확인으로 완료!!!

----------

### 저장소에서 압축 파일 설치
위에서 설정한 flyingdeuk 저장소에서 압축 파일을 설치한다. 

![kodi_addon](/img/living/kodi/kodi_setup_main_addon.jpg)

>**설정** -> **에드온** <br>
>저장소 설정을 다했으므로 에드온으로 바로 진입.

![kodi_addon](/img/living/kodi/kodi_addon.jpg)

- **저장소에서 설치** : 프로그래머가 작성한 저장소에서 설치
- **압축화일에서 설치** : zip 화일(설치파일)로 직접 설치 <br>

**압축화일에서 설치**로 진입

![kodi_addon](/img/living/kodi/kodi_flyingdeuk1.jpg)
> flyingdeuk addon 저장소 이름 **kodi**로 진입 <br>

![kodi_addon](/img/living/kodi/kodi_flyingdeuk.jpg)
>**repository nightrain_v19_public.zip** : KODI 19,20 모두 사용이 가능하다. 


------------

### 저장소에서 설치
압축파일에서 zip를 설치하면 저장소에 해당 저장소가 설치된다.

#### Korea OTT Package Addons 설치
NightRain님이 작성해주신 저장소로 최신 업데이트가 잘 되고 있다.
**한번에 모두 설치가 가능하다.**

![kodi_addon](/img/living/kodi/kodi_addon.jpg)
> **저장소에서 설치** 선택 <br>

![kodi_addon](/img/living/kodi/ott.jpg)
> **Korea OTT Package for KODI 19** -> **비디오 에드온** 으로 진입 <br> 한국 OTT 모두 설정후 사용이 가능하나 이번은 Netflix에 관련된 포스팅이니... 다른 OTT는 KODI 포스팅 참조

![kodi_addon](/img/living/fire/kodinetflix1.jpg)
> 넥플릭스를 설치한다. 


-------

### KODI Netflix 로그인 및 사용방법 
아래의 링크로 본인의 핸드폰 기종에 따라 이후 로그인을 수행하면 된다. 

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 아이폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/post/KODI-netflixkey/) -> 아이폰은 해당 링크를 클릭하면된다. 

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 안드로이드폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/post/KODI-netflixkey1/) -> 안드로이드폰은 해당 링크를 클릭하면된다. 

---------

#### PostScript
본인은 직업의 특성상 해외에 체류를 많이 하는 것도 있고... 부모님에게 드린 공유계정이 막히게 되어 방법을 알아보았다. 추후 넷플릭스에서 또 어떤 방법을 사용할 지는 모르겠으나 일단 FireTV에서는 해당 방법으로 시청이 가능하다. 물론 Mobile Device는 공유계정의 제한을 받지않으니 문제가 없다...

`테스트 결과 FireTV는 해당 방법으로 계정공유의 아이디로 사용이 가능하고 Xiaomi Mi Stick의 경우는 불가능하다. `

>예전부터 우리나라 가전의 스마트기능이 성능도 좋지않고 해서 일반 비 스마트 TV (패널만 좋은...)를 구매후 FireTV를 스마트 기능으로 사용해왔다... 다시한번 이게 더 좋은 방법이라는 것이 입증된 듯... 스마트 TV에서는 상기의 방법이 불가능하기 때문이다...


[INDEX로 돌아가기](/posts/FireTV/)
