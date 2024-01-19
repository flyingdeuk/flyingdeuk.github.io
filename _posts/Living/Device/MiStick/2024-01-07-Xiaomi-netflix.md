---
title: Xiaomi Stick Netflix 한 가구 제한 무력화 방법 (Feat. 계정공유, KODI, NFAuthenticationKey_Windows) <2024.01.07 Updated>
author: FlyingDeuk
date: 2024-01-07 
categories: [Living]
tags: [usefulapp, xiaomi, android, firetv, netflix, kodi]
pin:
---

![fire](/img/living/fire/kodinetflix.jpeg)

`FlyingDeuk's`
> Netflix가 2023년 11월부터 한가구에 해당하지않는 계정에 대해서 제한을 걸기 시작했다. 이로 인해서 지인 및 가족들과 계정을 공유해서 사용하기 위해서는 5000원을 더 납부해야만 한다. <br>
이에 방법을 모색하던 중 알아낸 방법을 공유한다. 모바일 기기의 경우는 제외가 되어 문제가 없으나 Xiaomi와 같은 TV OS 계열은 모두가 제한의 대상이 된다. 

한 가구 인정의 조건은 다음과 같다. 대략...
- 한 가구내에서 같은 인터넷을 사용해야한다. 
- Portable Device의 경우 한달에 한번은 한 가구내 인터넷에 접속해야한다. 
- 여행중 임을 증명해야한다.

`아래의 방법으로 Xiaomi의 경우 KODI를 사용해서 위의 제한을 회피할 수 있다.`


-----------

## Xiaomi Stick Netflix 계정공유 사용법
해당 내용은 이미 Xiaomi Stick를 사용하고 있다는 가정에서 시작한다. 그렇지 않는 경우는 해당 블로그에서 초기 사용법을 찾아보길 바란다. 

### Xiaomi Stick KODI Netflix 에드온을 이미 사용하고 있는 경우
이전 포스팅들로 이미 한국 OTT 에드온을 설치한 사람이라면 아래의 포스팅만 보면 된다. 

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 아이폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/posts/KODI-netflixkey/) -> 아이폰은 해당 링크를 클릭하면된다. 

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 안드로이드폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/posts/KODI-netflixkey1/) -> 안드로이드폰은 해당 링크를 클릭하면된다. 

--------------

## KODI 설치 
한국 실시간 TV, 모든 회사의 무료 영화나 드라마 시리즈를 보기위해서는 KODI의 설치가 필요하다. <br>
Xiaomi Stick의 경우 앱스토어에서 바로 설치 및 업데이트가 가능하다. 

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

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 아이폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/posts/KODI-netflixkey/) -> 아이폰은 해당 링크를 클릭하면된다. 

- #### [KODI Netflix Addon 인증키로 로그인하는 법 By 안드로이드폰 (Feat. FireTV, KODI, Neflix, NFAuthenticationKey)](/posts/KODI-netflixkey1/) -> 안드로이드폰은 해당 링크를 클릭하면된다. 


-----------

## KODI Netflix Addon MSL Error 해결법
로그인 완료후 영상을 보려고 하며 아래와 같은 오류가 발생한다. 

![msl](/img/living/mistick/msl1.jpg)


### Xiaomi Stick ESN 넘버
요즘 휴대기기든 단말기든 넷플릭스 시청을 위해서는 인가 받은 ESN 식별 번호로 인증하는 듯하다. 

![msl](/img/living/mistick/msl2.jpg)
- 설정 - 기기 환경설정 - 정보 에 해당 내용이 있다. (적을 필요없이 사진 한장만 찍어놓으면 된다. 스마트한 시대~~~)

---------

### KODI Netflix Addon ESN 수정
이유는 모르겠지만 FireTV와는 다르게 다른 ESN 번호가 에드온에 자동으로 저장되는 것이 문제였다. 

![msl](/img/living/mistick/msl5.jpg)
- 에드온들중에 Netflix 에드온을 꾹 눌러 설정으로 진입한다. 

![msl](/img/living/mistick/msl4.jpg)
- 좌측하단의 "표준"으로되어 있는 기본 값을 고급으로 변경해주고 "고급설정"에서 "ESN/Widevine 설정"을 눌러준다. 

![msl](/img/living/mistick/msl3.jpg)
- ESN 변경을 눌러 나오는 팝업창에서 위에서 찍어든 ESN 넘버를 넣어주면 된다. 
- ESN 넘버가 엄청 길지만 앞부분의 일부만 변경해주면 된다. 


![msl](/img/living/mistick/msl7.jpg)
> 이제 샤오미 미스틱도 한가구 제한 없이 시청이 가능하다. 

--------

### PostScript
본인은 직업의 특성상 해외에 체류를 많이 하는 것도 있고... 부모님에게 드린 공유계정이 막히게 되어 방법을 알아보았다. 추후 넷플릭스에서 또 어떤 방법을 사용할 지는 모르겠으나 일단 Xiaomi Stick에서는 해당 방법으로 시청이 가능하다. 물론 Mobile Device는 공유계정의 제한을 받지않으니 문제가 없다...

>예전부터 우리나라 가전의 스마트기능이 성능도 좋지않고 해서 일반 비 스마트 TV (패널만 좋은...)를 구매후 FireTV/Xiaomi Stick을 스마트 기능으로 사용해왔다... 다시한번 이게 더 좋은 방법이라는 것이 입증된 듯... 스마트 TV에서는 상기의 방법이 불가능하기 때문이다...


-----------

### [< Back to MiStick >](/posts/MiStick/)
