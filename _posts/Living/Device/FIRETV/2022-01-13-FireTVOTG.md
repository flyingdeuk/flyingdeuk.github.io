---
title: Fire TV Stick for OTG Cable - Fire TV에 개인 USB 메모리 연결법 (Feat. OTG 케이블)
author: FlyingDeuk
date: 2022-01-13 20:55:00 +0800
categories: [Living]
tags: [usefulapp, android, firetv]
pin:
---

![otg](/img/living/fire/otg15.jpg)

`FlyingDeuk's`
> 해외 호텔에서 Fire Tv를 사용하다가 보면 인터넷이 너무 느려 원하느는 영화를 보기엔 끊김이나 Buffing의 문제로 답답할 때가 있다. <br>
블로그에 이미 포스팅한 Utorrent를 이용한 자료를 다운받은 자료가 있는 경우... Fire TV 외의 다른 기기가 없는 경우를 대비해서 포스팅한다. <br>
자신의 구미에 있는 Contents를 USB에 담아서 가지고 다니는 경우 간단하게 볼 수 있는 방법이 되겠다.  

하지만 문제가 있다... 국내 Fire TV 사용자들 역시 캠핑이나 인터넷이 안되는 상황에서 영상을 보길 원할 때... 사용 가능한 방법이라 생각해서 포스팅 했으나... 자막이 smi, srt등 끌어 오지를 못한다. <br>
하지만 요즘엔 자막이 내장된 국내 소스가 많으니 그런 경우는 문제가 없겠다. <br>

**이터널스 Eternals,2021.1080p.KOR.FHDRip.H264.AAC-JTC** - > 요즘의 **KOR** 이나 **KOR SUB**가 붙은 파일은 그냥 봐도 된다. 한국 영화도 역시 자막이 없으니 가능하겠다.

`Wiki's`
> **USB 온더고(USB On-The-Go, USB OTG)** 는 2001년 말에 동의한 뒤 나중에 개정된 USB 2.0 규격에 제공된 한 기능으로, 컴퓨터를 통하지 않더라도 자료를 주고받을 수 있게 하는 USB 형식의 프로토콜이다. 이러한 규격을 만족하는 물리적 장치는 OTG 포트라고도 한다.

- 즉, USB를 핸드폰이든 패드든 안드로이드 기기에 꽂으면 인식된다. 윈도우처럼...

## OTG 케이블 구매 (FireTV 2세대, 3세대 이후 기기만 해당)
본인은 전자제품의 종류도 다양하고 가격도 저렴한 AliExpress에서 구매함...

![otg](/img/living/fire/otg13.jpg)
> 두개 묶음으로 2.42불에 구매했다. 찾아보니 국내에서는 개당 2000-3000원에 구매가 가능하다.

![otg](/img/living/fire/otg14.jpg)
> 연결은 다른 안드로이드 핸드폰이나 패드와 같이 연결하면된다. <br>
전원이 연결 가능한 넘으로...

## FireTV Stick 안드로이드 OTG (FireTV 2세대, 3세대 이후 기기만 해당)
Fire TV의 OS인 안드로이드는 기본적으로 OTG 서비스를 제공한다. 즉 USB 저장소를 기본적으로 허용한다. (물론 애플도 요즘은...)

![otg](/img/living/fire/otg1.jpg)
>이전에 포스팅했던 ES File Explore가 필요하다. (FireTV Update 이후 제한됨)

### ES File Explorer
Google Play Store에서는 보안이슈로 삭제되었으나 Amazon App Store에는 아직 있다. 활용도 높은 파일관리자이며 FireTV 유일하게 OTG를 인식하는 어플이다.

![vpn](/img/living/fire/vpn/vpn2.jpg)
>검색에서 "File" 검색해서 설치.

![otg](/img/living/fire/otg10.jpg)
> 설치후 사용시 위와 같은 화면이 나오면 **우측 끝**으로 이동후 **X** 눌러주면 됨.

![otg](/img/living/fire/otg3.jpg)
> OTG에 개인의 USB를 연결하면 위와 같이 **Local** -> **USB xxx**와 같이 인식된다.

![otg](/img/living/fire/otg4.jpg)
> 해당 **USB xxx**를 누르면 **Open** or **Unmount** 선택이 가능하며 **Open**을 눌러준다.

![otg](/img/living/fire/otg5.jpg)
> **access** 둘중 원하는 것을 눌러준다... 큰 의미는 없다...

![otg](/img/living/fire/otg9.jpg)

`USB Storage Problem!!!`
- FAT 32 : 안드로이드에 친화적이기는 하나 4GB의 용량 제한으로 고화질 영화는 인식을 못함.
- exFAT : 고용량을 지원하나 안드로이드는 인식을 못함.
- NTFS : 윈도우 고용량을 지원함....

> 위와 같이 CANCEL을 누르면 그냥 읽기는 가능해서 고용량화질을 그대로 볼 수 있음.

![otg](/img/living/fire/otg6.jpg)
> 선택한 이후 본인의 저장소에서 원하는 영상을 눌러주면 된다. <br>
물론 프로그램에 따라 사진일수도 음악일수도 영화일수도 있다.

![otg](/img/living/fire/otg7.jpg)
> 영화 파일을 예로들어 선택하면...

![otg](/img/living/fire/otg8.jpg)
> **Open** 할 어플을 선택한다.

![otg](/img/living/fire/otg11.jpg)
> 이제 인터넷의 속도와 관계없이 내가 소유한 영상으로 보면된다.

### KODI 자동 자막 적용
FireTV의 필수품 KODI의 자막 검색을 이용해 봤지만.. 안된다...

![otg](/img/living/fire/otg12.jpg)
> 영화의 Meta Date Base에 검색이 불가능하다... 이는 Neflix를 미주에서 자막 검색해 볼때와 비슷하다... 아직은 이유를 모르겠다.

-------

#### PostScript
최근의 TV들은 USB 메모리만을 꽂아도 영상을 볼 수 있다.. 그런데 대부분은 Video Codec의 업데이트가 이루어지지않아서... 요즘의 고화질 고압축 영상들은 인식을 못한다... 그래서 FireTV에 기본 업데이트에 의한 최신 자막으로 USB 메모리를 이용한 영상을 보는 법을 알아본 결과이다. <br>

![otg](/img/living/fire/otg2.jpg)
> 이전 버전에서는 **Setting** -> **My Fire TV** -> **Storage** 에 **USB** 저장소가 나왔었단다... 지금은 Not...

개인이 소장한 자료를 3000원 정도만 투자하면 볼 수 있는 방법이기는 하나... 자막이 내장된 영상이 아니면 안되는 것이 아쉽긴하다... 혹여나 필요한 사용자가 있기를 바라며 포스팅을 마친다.

[INDEX로 돌아가기](/posts/FireTV/)
