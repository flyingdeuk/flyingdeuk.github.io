---
title: MAC Book Terminal Theme by ohmyzsh - 터미널 테마 변경하기
date: 2021-07-14
categories: [Living]
tags: [mac, usefulthing]
pin:
typora-root-url: ../../../../flyingdeuk.github.io
---

![macbook](/img/living/macbook/terminal0.jpg)

`FlyingDeuk's`
>맥북은 ZSH를 기본으로 사용한다. 순정 ZSH는 파일 특성에 따른 색 구분등이 없이 하나의 색으로 표현되어 밋밋해서 효율성이 떨어진다. <br>
개인적으로 순정을 좋아하고 지저분하게 여러 프로그램들을 설치하는 것을 좋아하지 않아 순정내에서 최대한 활용하는 방법을 찾아서 남긴다.

`Wiki's`
> **ZSH** Z 셸(Z shell, zsh)은 상호작용 로그인 셸이자 셸 스크립트를 위한 강력한 명령 줄 인터프리터로 사용할 수 있는 유닉스 셸이다. Zsh는 bash, ksh, tcsh의 일부 기능을 포함하여 수많은 개선 사항이 갖추어진 확장형 본 셸이다.


## TERMINAL Theme 변경 by oh-my-zsh

순정 Terminal을 그대로 사용하면서 간단한 색정도만을 입히고 싶어 설치했다.

![macbook](/img/living/macbook/terminal.jpg)

### Theme 설치 - Install
curl, wget을 사용하여 간단하게 설치가 가능하다.
OS에 무관하게 다운받으면 됨 (공식 사이트 내용)

```
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
또는
```
$ sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```
공식 사이트 :
https://ohmyz.sh/ <br>

공식 Github : https://github.com/ohmyzsh/ohmyzsh

> 설치중 Share 폴더의 security 즉 권한문제로 에러가 났으며 그에 대한 정보를 알려준다. (물론 Text로...) <br>
에러나 이상이 있을 경우는 해결 방법을 자세히 알려준다.

### Theme 적용

여러가지 Theme의 예시를 사진으로 보여줘. 마음에 드는 Theme를 골라 이름만 변경해주면 됨. 아직까지 Git을 Coding에 사용하는 단계가 아니라 모르겠지만 Terminal 내에 Git 정보 표시여부를 중요하게 생각하는 듯함.

테마 적용 사이트 : https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

![macbook](/img/living/macbook/terminal2.jpg)
>`af-magic` Theme 를 선택


```
$ sudo vim ~/.zshrc
.
.
.
# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
ZSH_THEME="af-magic"

.
.
.
```
>**.zshrc** 에 해당 내용을 수정해주면 간단하게 Theme 변경이 가능하다. <br>
일부 좀더 화려한 Theme는 Font 이슈가 있어 다른 프로그램을 하나더 깔아야 할 수도 있다. (지져분 한거 싫어 Simply한걸루 선택)


### Theme 삭제 - Uninstall

oh-my-zsh의 프로그램 내에 Uninstall 이 있어 그대로 사용하면 된다. (.zshrc의 설정 내용을 수정해야 하기 때문에 해당 Uninstall을 사용해서 지워야 되는 듯)

```
sudo chmod 777 ~/.oh-my-zsh/tools/uninstall.sh
```
> .xxx는 숨김 폴더를 의미한다. 해당 숨김 폴더의 실행 권한을 열어준다.


```
~/.oh-my-zsh/tools/uninstall.sh
```
> 해당 숨김 폴더내의 Uninstall.sh 를 실행.

## P.S
초보자로... 하나씩 알아가는 것... 재미있네...
무엇보다 GUI만 사용하다가 CLI의 매력을 조금씩 알아가는 듯하다.


[INDEX로 돌아가기](/posts/Macbook/)
