---
title: Github Pages - Visual Studio Code Editor로 이사하기 (새로운 MacBook에 설정하기)
author: FlyingDeuk
date: 2023-03-08
categories: [Coding, Github]
tags: [github, usefulsite, vscode]
pin:
---

![vscode](/img/coding/github/vscode19.jpg)

`FlyingDeuk's`
> Github Pages 블로그를 작성하면서 Githhub에서 운영하는 ATOM Editor를 잘 사용해 왔다... 그런데 최근 이제는 운영을 안한단다... 급하게 많이들 사용하고 있는 Visual Studio Code로 이사하면서 다시 초심으로 돌아가 설정하는 법을 한번 해본다. 

> 기존에 운영하던 컴퓨터에 VSCode를 설치하면 Git 설정이 되어있어 바로 사용이 가능하다. 초심으로 돌아가 새로운 컴퓨터에 다시 블로그 환경을 VSCode로 하는 방법이 되겠다. 

`Wiki's`
> **마이크로소프트 비주얼 스튜디오(Microsoft Visual Studio)** 는 마이크로소프트 윈도우, macOS에서 작동하며 다양한 언어로 프로그래밍할 수 있는 마이크로소프트의 통합 개발 환경이다. 프로그램, 웹 사이트, 웹 프로그램 등을 개발할 수 있다. 마이크로소프트에서는 비주얼 베이직, 비주얼 C#, 비주얼 J# 등 특정한 언어로만 프로그래밍할 수 있는 언어별 버전도 제공하고 있다.

-------

## Visual Studio Code 설치
설치는 어렵지 않고 URL 역시 굳이 언급하지 않아도 검색으로 설치가 가능하다. 

### Git 설치

![vscode](/img/coding/github/vscode1.jpg)
- 최초 설치이후 macOS용 GIT 설치를 요구한다. 
- 선택하면 알아서 설치과정을 알려준다. 

![vscode](/img/coding/github/vscode3.jpg)
- brew install git -> 안된다... brew가 없다. 
- homebrew를 눌러주면 설치가이드가 다시 나온다. 

> MacBook의 경우 zsh를 사용하며 brew를 설치해서 다른 리눅스와 유사한 프로그램등을 설치가 가능하다. 

![vscode](/img/coding/github/vscode4.jpg)
- Install Homebrew를 위해서 해당 설치 경로를 복사해서 Terminal에 붙여준다. (약간의 Terminal 사용법만 알면 쉬움)

> COMM + Space : SpotLight에서 Terminal 치면 실행가능. 아니면 App에서 찾으면 됨

![vscode](/img/coding/github/vscode2.jpg)
- 복사후 붙이고 Enter 치면 알아서 HomeBrew가 설치된다. 

![vscode](/img/coding/github/vscode3.jpg)
- 다시 Terminal로 돌아가서 brew install git이라 쳐준다. 
- git 설치 알아서 해줌. 

-------------

### Repository 가져오기 (Clone)
물론 Terminal에서 명령어로도 가능하겠지만 철저하게 초보의 입장에서 GUI를 가능하면 이용해 봤다. 

![vscode](/img/coding/github/vscode5.jpg)
- 레포지토리 가져오기를 누르면...

![vscode](/img/coding/github/vscode6.jpg)
- 주소를 직접 치거나... Github 사이트에서 복제를 선택이 가능하다. 

![vscode](/img/coding/github/vscode8.jpg)
- 일단 뇌피셜로 대략적인 주소를 쳐 봤다.... 역시나 안된다... git의 주소는 여러 형태로 되어 있어 매일 사용하는 사람이 아니면... 어렵다. 그래서 쉽게...

![vscode](/img/coding/github/vscode7.jpg)
- Github에서 복제로 GUI를 이용하는 걸루...

![vscode](/img/coding/github/vscode12.jpg)
- Github 에서 자동으로 VS Code와 연결시켜주는 방식으로 Github에 로그인만 하면된다. 

![vscode](/img/coding/github/vscode13.jpg)
- 열기를 누르면 자동으로 레포지토리를 다운로드 받는다. (Clone)

![vscode](/img/coding/github/vscode14.jpg)
- 믿을 수 있는 사람이냐고... 내꺼니까 그냥 OK!!

![vscode](/img/coding/github/vscode15.jpg)
- Github Pages의 퍼블리시는 master가 아니라 gh-pages에서 이루어 지므로 좌측 하단의 브렌치를 gh-pages로 변경해주면 끝...

![vscode](/img/coding/github/vscode16.jpg)
- 브렌치를 gh-pages로 변경해서 Setting이 완료된 모습


> 이로써 기존의 ATOM에서 블로그를 작성하다가 VSCode로 새로운 컴퓨터에 세팅이 끝나게 된다. 

----------

### Commit - Push 하기

테스트 삼아 이 글을 쓴다... 그런데 Commit을 위해서는 추가적인 내 증명이 필요하다. 

![vscode](/img/coding/github/vscode17.jpg)
- 내 블로그니 상관없겠지만 협업을 통한 작품을 만든다면 당연히 내가 누구인지 밝혀야 될 문제...

> 에러가 나며 설명 따라 진행하면 된다. 일반 Terminal에서는 당연히 지나야되는 과정이지만 GUI를 통한 세팅이다가 보니.. 뭐 어쨌든 시키는데로만 하면 문제가 없으니...

![vscode](/img/coding/github/vscode18.jpg)
- VSCode의 Terminal에 해당 명령어로 해 주면 끝!!!

---------

### PostScript

ATOM의 서비스가 중단되어 또 다른 새로운 경험을 해본다. VSCode가 왜 인기가 많은지 알정도로 단순히 블로그만 작성하기에 충분한 것 같다. 

