---
title: MAC Book Free Game Emulator OpenEmu CD Game - 맥북 OpenEmu 여러장의 CD 게임 돌리기 (Feat. FinalFantasy VIII)
author: FlyingDeuk
date: 2022-01-11
categories: [Living]
tags: [usefulapp, mac, openemu, game]
---

![game](/img/living/macbook/bios2.jpg)

`FlyingDeuk's`
> 오랜전 PS1의 추억의 게임을 돌려보기로 했다. FinalFantasy 8이다. <br>
그 당시에는 실사와 유사한 그래픽으로 놀라운 게임이였는데... 지금 보면 허접하다... 추억은 추억으로 두는 것이...

FinalFantasy VIII 을 열심히 다운로드 받았는데... 인식을 못한다. <br>
**그에 대한 해결법이다.**

`Wiki's`
> **디스크 이미지(Disk image)** 는 기록 미디어 안에 있는 내용이 저장된 파일을 가리킨다. 이러한 디스크 이미지는 일부 압축 프로그램을 사용하여 압축 파일을 풀듯이 풀 수도 있으며, 별도의 가상 CD/DVD 소프트웨어를 이용하여 마치 실제 CD/DVD 미디어를 사용하는 것처럼 에뮬레이트하는 데 쓸 수도 있다. 이러한 이미지를 드라이브에서 사용하는 것을 마운트라고 한다. 플로피 디스크 이미지의 경우 램 디스크를 사용할 수도 있다.

CUE/BIN 파일에 대한 정리를 해줘야 디스크로 인식한다.


## CUE/BIN 파일 정리
해당 내용은 OpenEmu 프로그래머의 설명서에 잘 나와있다... 찾는데 엄청고생함...

### 개발자 설명서
![game](/img/living/macbook/cd1.jpg)

<https://github.com/OpenEmu/OpenEmu/wiki/User-guide:-CD-based-games>
> 우측의 목차로 궁금한 사항들을 찾아보면된다. (리스트 뒤쪽에 숨어있어서... 못찾음...)

### cue m3u 파일 생성하기
여러개의 디스크로 나누어진 게임을 다운받고 압축을 해제하면 아래와 같은 결과가 대부분이다.

- Final Fantasy VIII (USA) (Disc 1).bin
- Final Fantasy VIII (USA) (Disc 1).cue
> bin은 메인 이미지 파일이다. cue는 bin 파일의 형태를 알려주는 파일...(cue 파일이 아에 없는 경우도 있다.)

#### cue 파일 생성
cue 가 있든 없든 만들어주면 된다. txt 편집기에서 파일을 만들고 확장자를 cue로 변경해주면 된다.

```
FILE "Final Fantasy VIII (USA) (Disc 1).bin" BINARY
  TRACK 01 MODE2/2352
    INDEX 01 00:00:00
```

#### m3u 파일 생성
cue 파일과 동일한 방법으로 txt 편집기에서 아래와 같이 만들고 나서 확장자를 m3u로 변경해준다.

```
Final Fantasy VIII (USA) (Disc 1).cue
Final Fantasy VIII (USA) (Disc 2).cue
Final Fantasy VIII (USA) (Disc 3).cue
Final Fantasy VIII (USA) (Disc 4).cue
```

#### 결과
정리한 이후에 하나의 폴더에 모아 주었다.

![game](/img/living/macbook/cd2.jpg)
> 이제 해당 결과물을 OpenEmu에 **Drag and Drop**해 주면 된다.

------
#### PostScript
해당 결과물을 Drag and Drop해주면 될 줄 알았다. 그런데 또 문제가 터졌다... BIOS문제... 다음 포스팅에 해결방법이 있다.

[MAC Book Free Game Emulator OpenEmu BIOS Pack Update - 맥북 OpenEmu BIOS 팩 업데이트 법 (Feat. FinalFantasy VIII)](/posts/MacGameBIOS/)

[INDEX로 돌아가기](/posts/MacGame/)
