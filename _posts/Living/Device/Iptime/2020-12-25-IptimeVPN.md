---
title: IPTIME 공유기 VPN - 아이피타임 한국 VPN(우리집) 접속하기
author: FlyingDeuk
date: 2020-12-24 20:55:00 +0800
categories: [Living]
tags: [usefulthing, iptime, vpn]
pin:
---

`FlyingDeuk's`
> 해외에서 한국 OTT 서비스를 보기란 쉽지않다. 하지만 내가 사용하는 집 공유기에 VPN을 걸면 모든 서비스를 무료로 이용할 수 있다. <br>
어떤 어플도 유료 서비스도 필요없다. <br>
Netflix 역시 나라마다 서비스가 달라지니 한국에서와 동일한 조건으로 시청이 가능하다.

해당 내용은 [IPTIME 공유기 외부(해외)에서 접속하기](/posts/IptimeSet/) 이후의 내용임.

내 공유기의 DDNS 주소값은 **deuktest.iptime.org** 가 된다.

`Wiki's`
>**가상사설망(假想私設網) 또는 VPN(영어: virtual private network)** 은 공중 네트워크를 통해 한 회사나 몇몇 단체가 내용을 바깥 사람에게 드러내지 않고 통신할 목적으로 쓰이는 사설 통신망이다.[1] 가상 사설망에서 메시지는 인터넷과 같은 공공망 위에서 표준 프로토콜을 써서 전달되거나, 가상 사설망 서비스 제공자와 고객이 서비스 수준 계약을 맺은 후 서비스 제공자의 사설망을 통해 전달된다.

## VPN 설정법
IPTIME의 설정에 접속한다. (외부든 내부든 상관없음)

![vpn](/img/living/iptime/iptimevpn.jpg)
>고급 설정 - 툭수 기능 - VPN 서버설정

#### VPN 서버설정
PPTP 서버 : 실행 클릭, 암호화 사용 클릭 (안드로이드 계열에서 주로 사용) <br>
L2TP 서버 : 실행 클릭, 추가적인 비밀키 입력 (IOS 계열에서 주로 사용) <br>
**적용** 누르는 거 잊지말자...

#### VPN 접속 계정 추가
VPN 접속 계정 : 아이디 아무거나 <br>
VPN 접속 암호 : 알아서 <br>
할당 될 IP 주소 : 통상 맨 뒷자리는 접속한 순서대로 배정한다. 2-254 정도가 default 값임. (뒷쪽을 배정하면 문제없음) -> 200을 선택



## 아이패드(IOS) VPN 사용하기
![vpn](/img/living/iptime/iptimevpn5.jpg)
>설정 - 일반 - VPN <br>
`VPN 구성 추가`

![vpn](/img/living/iptime/iptimevpn6.jpg)
>서버는 내 공유기 주소 deuktest.iptime.org<br>
상기 IPTIME 설정에 넣은 내용들을 넣어준다. <br>
L2TP 방식이라 비밀 키를 추가로 넣어야한다.

이제 VPN 연결을 누르고 한국 OTT 사이트(또는 APP)에 들어가서 시청하면 끝!!!

## 안드로이드 VPN 사용하기
![vpn](/img/living/iptime/iptimevpn10.jpg)
>설정 - 네트워크 및 인터넷 - VPN

![vpn](/img/living/iptime/iptimevpn11.jpg)
>"+" 추가

![vpn](/img/living/iptime/iptimevpn12.jpg)
>PPTP 방식으로 암호화 선택, 사용자 아이디, 비번만 넣어주면 됨.


## MAC OS VPN 사용하기
맥북에서는 이유는 잘 모르겠으나 잘 안된다. ㅜ.ㅜ
> 보안상 애플이 싫어하는 방식이라나 뭐라나...

## 한국 OTT Test

#### TVING(tving.com)
![vpn](/img/living/iptime/iptimevpn20.jpg)
>어플 설치 없이 보기 위해서는 데스크탑 버전으로 보기를 해야 어플 설치창이 뜨지않는다. <br>
잘 나온다.

#### SPOTV NOW(spotvnow.co.kr)
![vpn](/img/living/iptime/iptimevpn21.jpg)
>데스크탑 버전에 상관없이 잘나온다.

#### WAVVE(wavve.com)
![vpn](/img/living/iptime/iptimevpn22.jpg)
>데스크탑 버전이든 모바일이든 앱 설치를 요구한다. 잘 안된다. <br>
개인 PAD는 앱 설치하면 볼 수 있다.

#### Netflix
한국에서 시청가능한 조건, Contents 및 자막 동일한 조건에서 시청 가능하다.
>단, 어플없이 보기위해서는 데스크탑 버전으로 보면된다.

#### Safari에서 데스크탑 버전 옵션위치
![vpn](/img/living/iptime/iptimevpn23.jpg)
>글자 크기 모양을 누르면 옵션이 나오고 그 아래에서 선택 가능함.



## PostScript
물론 현재의 인터넷 상태에 따라서 Streaming에는 제한이 따를 수 밖에 없다. 하지만 다른 방법으로 시도한 무료 VPN 보다 안정성과 속도 역시 괜찮은 거 같다.<br>

>전문적인 견해는 몰라서...




[INDEX로 돌아가기](/posts/Iptime/)
