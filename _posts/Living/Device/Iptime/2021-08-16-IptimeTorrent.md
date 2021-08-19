---
title: IPTIME 공유기 Torrent - Torrent 머신으로 사용하기(영화 다운로드)
author: FlyingDeuk
date: 2021-08-16 20:55:00 +0800
categories: [Living]
tags: [usefulthing, iptime, torrent]
pin:
---
![torrent](/img/living/iptime/torrentand1.jpg)

`FlyingDeuk's`
> 어느 회사의 공유기든지 최근들어 USB 포트로 서버 기능을 지원하는 제품들이 많이 출시되어있다. (KT에서 주는 공유기도 이러한 기능을 갖고 있는 경우도 있다.) <br>
지속 포스팅하겠지만 이러한 기능을 이용하면 간단한 방법으로 나만의 CLOUD(서버)를 구축할 수 있다.<br>
노트북으로 USB에 영화를 다운 받고 다시 공유기 뒤편에 꽂고 하는 것은 너무 건거로우니 직접 다운받고 바로 볼 수 있는 방법을 소개한다.

본인의 공유기 뒷편에 USB 포트가 있는 지 확인해보면 알 수 있다. (검은색은 USB 2.0, 파란색이라면 UBS 3.0) <br>

`Wiki's`
>**비트토렌트(영어: BitTorrent, 축약형 BT)** 는 P2P(peer-to-peer) 파일 전송 프로토콜의 이름이자 그것을 이용하는 응용 소프트웨어의 이름이다. 비트토렌트를 이용하면 파일을 인터넷 상에 분산하여 저장하여 놓고 다수의 접속을 사용하여 여러 곳에서 동시에 파일을 가져오게 되어 전송 속도가 빨라진다.


해당 내용은 [IPTIME 공유기 외부(해외)에서 접속하기](/posts/IptimeSet/) 이후의 내용임.

내 공유기의 DDNS 주소값은 **deuktest.iptime.org** 가 된다.

## Torrent 머신 설정법
서버 역할을 하는 일종의 PC(일반적인 고사양보다는 낮은 등급)에 자료 저장을 Torrent라는 방식으로 하는 컴퓨터를 의미함. NAS라는 머신도 이에 해당한다고 볼 수 있다. (요즘 나오는 NAS는 해당 기능을 대부분 가지고 있음)

### IPTIME 기능 설정
![torrent](/img/living/iptime/torrent1.jpg)

지난 포스팅 처럼 로그인...

- 192.168.0.1(집에서 내부 아이피 주소로)
- deuktest.iptime.org:1234(집 또는 외부에서 DNS 주소로)
  >자세한 내용은 이전 포스팅 참조...

![torrent](/img/living/iptime/torrent2.jpg)
> **관리도구!!!**

![torrent](/img/living/iptime/torrent3.jpg)
> **고급설정** -> **USB/서비스 관리**

USB 서비스 관리 항목이 있다는 건 공유기에 USB 포트가 있고 해당 기능을 사용할 수 있다는 의미이다.

![torrent](/img/living/iptime/torrent4.jpg)
> **장치관리** 연결된 USB의 정보를 확인이 가능하다.

#### USB 포멧 결정
일반적인 포멧은 NTFS, FAT32, exFAT정도가 가장 많이 사용된다.
- FAT32 : 가장 호환성이 좋으나(모든 기기에서 인식에 문제가 없음) 4GB 이상 저장 불가
- exFAT : 4GB이상 저장이 가능하나 호환성이 다소 떨어짐 (일부 기기에서 인식 불가)
- NTFS : exFAT 보다는 호환성이 다소 개선됨 NTFS가 그래도 가장 나은듯함.

#### IPTIME Torrent 기능 설정

가장 중요한 건 해당 서비스는 **deuktest.ipdisk.co.kr**의 주소로 된다는 것이다. <br>
DNS 주소는 **deuktest.iptime.org**였으나 서버 서비스의 주소는 상기의 주소이니 주의가 필요하다.

![torrent](/img/living/iptime/torrent5.jpg)

**ipDISK 주소 관리** : 이전 포스팅의 DNS 설정했으면 정상등록으로 표시됨 <br>
**토렌트** : 해당 기능을 실행으로 설정
- **사용자 ID** : 토렌트 로그인을 위한 ID
- **포트번호** : 9091이 기본 포트이나 보안을 위해 변경이 추천됨 (9000번대를 사용하면 문제없음)
- **다운로드 폴더** : 해당 USB에 기본 저장 장소를 설정하면됨 (다운로드 받을 때 변경이 가능함)

**토렌트 웹UI 접속** : 쉬게 말해 인터넷 브라우져로 접속하게 해준다. 그냥 주소를 처도됨. (아래 내용 참고) <br>
**토렌트 접속기 다운로드** : 전용 프로그램을 다운로드해도 되나 핸드폰 어플이 더 편리함 (아래 내용 참고)

### IPTIME Torrent 활용
모든 기기에서 사용이 가능하나 안드로이드 핸드폰이 제일 편하다. 내가 사용하는 방법

#### Windows, MAC - 인터넷 브라우져 사용
상기의 웹UI 접속을 누르거나 주소로 IPTIME에 접근이 가능하다. <br>
Utorrent 포스팅을 했다. 리눅스에서는 Transmission이 더 유용하고 유명하다.

![torrent](/img/living/iptime/torrent6.jpg)

**deuktest.ipdisk.co.kr:9091** IPTIME 서버주소 + 포트번호
>DNS 주소와는 조금 다르니 주의!!! <br>
좌측 상단의 열기 아이콘을 누르면 파일을 선택할 수 있다. <br>
그 아래 대상 폴더를 추가로 변경이 가능하다.


##### Torrent 파일 찾기
Utorrent 포스팅에서 언급했듯이 Google에 한글로 **"토렌트"** 를 치면 한글 사이트들이 영어로 **"torrent"** 를 치면 영어 사이트들이 뜬다.

![torrent](/img/living/iptime/torrent7.jpg)
>본인이 마음에 드는 사이트를 눌러서 들어가면 됨(추천사이트들...)

![torrent](/img/living/iptime/torrent8.jpg)
>작은 화살표를 누르면 해당 사이트로 들어갈 수 있다.

![torrent](/img/living/iptime/torrent9.jpg)

**다운로드 링크** : xxx.torrent 파일을 받을 수 있는 다른 링크로 연결된다. (사이트마다 다름) <br>
**마그넷 링크** : 주소값을 그냥 링크로 연결한다. 추후에 안드로이드 폰으로 쉽게 접근이 가능한 방법.
>일단 브라우져를 이용한 방법은 xxx.torrent가 필요하다.

![torrent](/img/living/iptime/torrent10.jpg)
>어쩐지 찝찝하다 자꾸 연결되니... Download를 눌러 다운로드...

정말 다양한 토렌트 사이트들이 있다. 대부분은 회원가입 보다는 사이트 유입 광고비를 목적으로 한다... 본인에게 맞는 사이트하나정도는 북마크 해놓는 것도 좋을 듯...

##### 파일 다운로드

![torrent](/img/living/iptime/torrent11.jpg)
>토렌트 파일은 .torrent 확장자를 가지고 있다.

![torrent](/img/living/iptime/torrent12.jpg)
>파일 선택에서 해당 파일을 지정해주면 됨.

 ![torrent](/img/living/iptime/torrent13.jpg)
>이 과정은 웹 브라우져로 IPTIME에 토렌트 파일을 올려주어 IPTIME내에서 파일이 다운로드 되는 과정이다. <br>
영화가 다운로드 되고 있는 상태를 나타내어 준다.

![torrent](/img/living/iptime/torrent14.jpg)
>공유기의 제어를 위한 작은 컴퓨터에 서버의 기능을 넣고 과도하게 사용하다가 보면 공유기 자체의 성능 저하를 일으킬 수 있는 듯하다. 소프트웨어로 속도 제한을 해둔것을 볼 수 있다.

테스트해보면 평균 3-4Mb/s 정도의 속도를 낸다. 4Gb정도의 영화는 15분 정도가 소요되었다.<br>
라즈베리파이에서는 10-15Mb/s 정도 속도가 난다. (다른 포스팅 참조)

![torrent](/img/living/iptime/torrent15.jpg)
>Utorrent 포스팅에서도 언급했듯이... 업로드 자체가 좀 불편한 사람들은 확실하게 토렌트 파일을 지우는 게 추천된다. <br>
파일을 유지한다는 것은 내 자료를 다른 사람들과도 공유한다는 것을 의미한다.


### 안드로이드 OS - Transmission Remote APP 사용
일반적으로 BitTorrent나 Utorrent가 유명하지만 리눅스에서는 Transmission Daemon이라는 프로그램에 의해서 위와 같은 웹 UI를 지원한다.

#### 추천어플 - Transmission Remote

![torrent](/img/living/iptime/torrentand1.jpg)
>Transmisson이란 검색어로 많은 어플들이 존재하지만 지금 쓰고있는 이 어플이 제일 나은듯하다.

#### Transmission Remote 사용법
실행후 새 서버 추가...

![torrent](/img/living/iptime/torrentand4.jpg)
>좌측상단을 눌러 **서버 추가**를 눌러준다.

![torrent](/img/living/iptime/torrentand2.jpg)
>본인의 정보를 조건에 맞게 넣어준다.

![torrent](/img/living/iptime/torrentand3.jpg)
>위의 브라우져 방법으로 다운받고 있는 상황이 그대로 보여진다. <br>

같은 IPTIME에 다른 방식으로 연결되더라도 현재 진행 상황을 알 수 있다.

##### 마그넷 연결
위에서 이야기한데로 토렌트 파일을 다운받아 업로드해도 되지만... 마그넷이 조금 더 편하다.

![torrent](/img/living/iptime/torrentand6.jpg)
>위에서 설명한 방법으로 토렌트사이트에 들어가서 토렌트 파일이 아닌 **magnet**링크를 누르면 주소값만을 전달이 가능하다.

![torrent](/img/living/iptime/torrentand7.jpg)
>바로 **Torrent Remote**로 연결되며 저장위치 변경 역시 가능하다.

![torrent](/img/living/iptime/torrentand8.jpg)
>마그넷 링크는 특성상 파일 식별에 조금 시간이 걸린다. 그 이후는 일반 토렌트 파일과 같다.

![torrent](/img/living/iptime/torrentand9.jpg)
>다운로드가 완료 되면 해당 파일을 눌러 **토렌트 삭제**로 업로드 방지...

![torrent](/img/living/iptime/torrentand10.jpg)
>이때 리스트에서 삭제 누르면 된다. 업로드 방지!!!


### IPAD OS, IOS - 브라우져 사용
사용방법은 Windows, MAC과 동일한 브라우져를 사용하는 법이다.

![torrent](/img/living/iptime/torrentipad1.jpg)
>사파리에서 주소치면됨....

![torrent](/img/living/iptime/torrentipad2.jpg)
>**파일 선택**을 눌러 **탐색** 선택

![torrent](/img/living/iptime/torrentipad3.jpg)
>미리 다운받아 놓은 곳을 **파일**에서 찾아서 선택

![torrent](/img/living/iptime/torrentipad4.jpg)

![torrent](/img/living/iptime/torrentipad5.jpg)
>**Upload**누르면 내 IPTIME으로 전송된다.

이제 즐기면 된다....


## PostScript
호텔방에서는 FIRE TV의 KODI EXODUS를 이용하면 최신 영화보는 데 크게 문제가 없다. 간혹 EXODUS에 없는 영화나 예전 영화들은 위의 방법으로 내 서버에 다운받고 FTP를 이용해서 보기도 한다. <br>
원리나 작동 방법을 이해하면 그 활용도는 무궁무진하다. <br>

**재방송을 보고 싶을 때 놓친 예능이 있을때도 파일을 내려받는 것이 지겨운 광고를 보는 시간보다 덜 걸리는 듯하다.**

다음 병기로 라즈베리파이를 구매하고 나서는 IPTIME은 더이상 쓰지않는다... Wifi에 집중해라. 서버는 다른 것을 쓸 테니...


[INDEX로 돌아가기](/posts/Iptime/)
