---
title: (Android)Fire TV 해외에서 한국TV 보기(Fire TV VPN 설정법)-UsefulAPP
author: FlyingDeuk
date: 2020-12-17 20:55:00 +0800
categories: [Living, APP]
tags: [UsefulAPP, Android]
pin:
---

![fire](/img/living/fire/vpn/vpn.jpg)

`FlyingDeuk's`
> 호텔에서의 Entertainment를 위해 사용중인 Fire TV에서 한국 방송을 보고 싶다는 욕구에 연구해 본 결과이다. <br>
Fire TV는 Setup Box의 특성상 VPN설정이 패드나 핸드폰보다는 까다롭다고 하겠다. <br>
Amazon App Store의 정식 App을 사용하는 방법이다. <br>
다소 복잡할 수 있지만 live로 한국 방송을 본다는 건.... <br>
**NETFLIX 역시 한국 조건으로 시청이 가능하다.**



## 필수 App 설치

### AirVPN
로그인해서 사용해야하나 OpenVPN profile을 무료로 올려서 사용할 수 있다.

![vpn](/img/living/fire/vpn/vpn1.jpg)
>Home 화면에서 좌측으로 이동하여 검색에 "open vpn"을 검색한다. <br>
AirVPN 설치 <br>

### ES File Explorer
Google Play Store에서는 보안이슈로 삭제되었으나 Amazon App Store에는 아직 있다. 활용도 높은 파일관리자.

![vpn](/img/living/fire/vpn/vpn2.jpg)
>검색에서 "File" 검색해서 설치.

### DOWNLOADER
인터넷 공간의 화일을 Fire TV에 Download할 수 있는 유일한 App.

![vpn](/img/living/fire/vpn/vpn3.jpg)
>검색을 통해서 설치하거나 App - Categories - Utilities 에서도 설치가능함. 쉬운 방법으로 설치.

---------

## VPN 실행

### OPENVPN Profile 다운
무수히 많은 Profile 중에 본인이 7개 정도 인기도가 높은 걸루 저장소에 저장해놓음.

![vpn](/img/living/fire/vpn/vpn4.jpg)
>DOWNLOADER 실행하고 URL입력

![vpn](/img/living/fire/vpn/vpn5.jpg)
>`flyingdeuk.github.io/kodi` 입력후 이동

![vpn](/img/living/fire/vpn/vpn6.jpg)
>상기와 같이 여러개의 Addon을 지나 아래의 Profile을 모두 다운받는다. <br>
VPN 주소는 유동적이므로 여러개중에 잘되는 하나를 골라야함.

### Profile 실행
Profile을 AirVPN으로 연결해서 App안에 저장하는 방법임.

![vpn](/img/living/fire/vpn/vpn7.jpg)
>미리 받아놓은 "ES File Explorer"을 실행한다. <br>
**최초 실행시 유료버전에 대한 내용이 나온다. 맨 오른쪽위의 "X" 눌러서 가볍게 무시해주면 됨.** <br>
Internal Storage -> **Downloader** 풀더로 진입(Download 아님)


![vpn](/img/living/fire/vpn/vpn8.jpg)
>받은 화일을 길게 눌러 선택 <br>
우측 맨 밑의 옵션을 선택하여 **OPEN AS**로 실행할 App을 선택

![vpn](/img/living/fire/vpn/vpn9.jpg)
>**Other** 선택

![vpn](/img/living/fire/vpn/vpn10.jpg)
>**Import OpenVPN profile** 선택하고 아래의 **Always**선택하면 상기의 작업은 한번만 하면됨.

바로 AirVPN이 열리고 profile이 자동으로 저장됨.
![vpn](/img/living/fire/vpn/vpn11.jpg)
>**테스트 결과 211.207.163.98이 현재는 잘 연결됨** <br>
여러개의 profile을 해보고 잘 연결되고 속도가 잘 나오는 걸 사용하면됨. <br>
**아래에 열어본 모든 Profile들이 있으므로 나중에 다시 연결해볼 수 있음.** <br>
다른 장소도 지속적으로 test해 보고 feedback을 올릴 예정임.


![vpn](/img/living/fire/vpn/vpn12.jpg)
>우측의 Connection Status에 연결 정보로 상태를 확인하거나 Disconnect할 수 있음.

---------------

## Enjoy Your Stay!

### SILK Browser
최근 한국 서비스중에 WAVVE, TVING, SPOTV등은 무료회원 가입만으로도 실시간 720p화질까지는 무료로 시청이 가능하다.

#### SPOTV now
스포츠 전문 서비스
![vpn](/img/living/fire/vpn/vpn13.jpg)
>**spotvnow.co.kr** <br>
**반드시 위에 있는 데스크탑 화면으로 시청해야 어플을 따로 깔아야한다는 요구가 없이 시청이 가능하다.**


![vpn](/img/living/fire/vpn/vpn14.jpg)

#### TVING

![vpn](/img/living/fire/vpn/vpn15.jpg)
>실시간 TV, TVING TV 무료!!

#### WAVVE
>LIVE 채널 일부를 제외하고 무료시청가능!!

![vpn](/img/living/fire/vpn/vpn16.jpg)
>DOWNLOADER 실행하고 URL입력

#### KODI Addon
KODI addon의 해당 addon에서도 시청이 가능함.

![vpn](/img/living/fire/vpn/vpn.jpg)
>아래의 Posting 참고! <br>
  [KODI 1. 기본 설치 & 설정법](https://flyingdeuk.github.io/posts/KODI-install/)<br>
  [KODI 2. 에드온 설치 및 설정법](https://flyingdeuk.github.io/posts/KODI-addon/)

### 여담(PostScript)
한달에 10불 정도의 유료로 VPN을 사용하면 위의 고생을 안해도 된다. <br>
자주 사용하는 편이 아니라면 위의 방법으로 무료로 VPN을 사용할 수 있겠다. <br>
문제는 profile이 유동적이라 스스로가 얻는 방법을 한번 알아볼 예정이다.

**다음은 한국 본인의 공유기에 VPN을 걸어서 사용하는 방법을 Posting할 예정이다.**
>이는 노트북, 패드, 핸드폰에 해당한다.
