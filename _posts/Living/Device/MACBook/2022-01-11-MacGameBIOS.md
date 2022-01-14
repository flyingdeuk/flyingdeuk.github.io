---
title: MAC Book Free Game Emulator OpenEmu BIOS Pack Update - 맥북 OpenEmu BIOS 팩 업데이트 법 (Feat. FinalFantasy VIII)
author: FlyingDeuk
date: 2022-01-11
categories: [Living]
tags: [usefulapp, mac, openemu, game]
---

![game](/img/living/macbook/bios2.jpg)

`FlyingDeuk's`
> 오랜전 PS1의 추억의 게임을 돌려보기로 했다. FinalFantasy 8이다. <br>
열심히 파일을 정리하고 만들고 났더니 실행이 안된다. BIOS문제란다. 업데이트하는 법이 아래에 있다.

개발자 사이트에서 제공하지 않는 것을 보니... 이유는 잘 모르겠지만...

`Wiki's`
> **바이오스(BIOS; Basic Input/Output System)** 는 운영 체제 중 가장 기본적인 소프트웨어이자 컴퓨터의 입출력을 처리하는 펌웨어다. 사용자가 컴퓨터를 켜면 시작되는 프로그램으로 주변 장치(하드웨어)와 컴퓨터 운영 체제(소프트웨어) 사이의 데이터의 흐름을 관리한다. 펌웨어(firmware)의 한 종류로서 IBM호환 컴퓨터의 경우에 전원이 공급되면 시작되는 부팅 절차에서 하드웨어 초기화를 수행하고, 운영체제나 응용 프로그램에게 런타임 서비스(컴퓨터 프로그램의 실행을 지원하는 서비스)를 제공한다. 바이오스 펌웨어는 PC에 내장되어 있어서 전원이 인가되면 실행이 시작되는 최초의 프로그램이다. 바이오스라는 이름은 1975년도에 사용된 CP/M 운영체제의 Basic Input/Output System에서 유래하였다. 원래는 IBM의 소유였으나 많은 회사들이 원본 프로그램을 분석(리버스 엔지니어링)하여 호환 프로그램을 개발하였다. 현대 PC에서 바이오스는 하드웨어 부품을 초기화하고 검사하는 역할, 부트로더 또는 대용량 저장장치에 저장된 운영체제를 RAM으로 읽어오는 기능을 수행한다.

## 문제의 발생
앞선 포스팅에서 파일을 정리하고 나서 **Drag and Drop**하니 이런 메세지가 뜬다.... -> **Googling~~~**

![game](/img/living/macbook/bios4.jpg)
```
To run this core you need the following:
PlayStation SCPH-5500 (v3.0 Japan) BIOS
"scph5500.bin"
PlayStation SCPH-5501 (v3.0 America) BIOS
"scph5501.bin"
PlayStation SCPH-5502 (v3.0 Europe) BIOS
"scph5502.bin"
```

### 개발자 메뉴얼

![game](/img/living/macbook/bios5.jpg)

<https://github.com/OpenEmu/OpenEmu/wiki/User-guide:-BIOS-files>
> 개발자 메뉴얼에도 해당 내용만 있을 뿐 해당 파일은 없다... -> **다시 Googling~~**


## BIOS Pack 다운로드
구글해서 찾은 결과이다.

![game](/img/living/macbook/bios1.jpg)

<https://archive.org/details/OpenEmuBIOSPack>
> 해당 파일을 다운로드하고 나서 압축을 풀고 역시나 **Drag and Drop**해주면 성공~~

### 결과
자동으로 BIOS가 설치되고 결과를 확인 할 수 있다.

![game](/img/living/macbook/bios3.jpg)

#### FinalFantasy VIII
![game](/img/living/macbook/bios6.jpg)
> 지금보니 화질이 영.... 괜히 고생만 한거 같음... 기대가 무너짐...

------

#### PostScript

위의 방법으로 BIOS 까지 업데이트했으니.. 다른 추억의 게임에 도전해야겠다. 좀더 나은 그래픽의...

[MAC Book Free Game Emulator OpenEmu CD Game - 맥북 OpenEmu 여러장의 CD 게임 돌리기 (Feat. FinalFantasy VIII)](/posts/MacGameCD/)

[INDEX로 돌아가기](/posts/MacGame/)
