---
title: Github Pages - Typora Markdown Editor /img 폴더 연결하기
date: 2021-07-30
categories: [Coding, Github]
tags: [github, usefulsite]
pin:
---

![typora](/img/coding/github/typora1.jpg)

`FlyingDeuk's`
> Github Pages에 블로그를 올리기 시작하면서 ATOM으로 Markdown 형식의 글을 쓰다가 보니 Markdown Preview의 기능상 불편함이 있었고 맥북이 오래되다가 보니 리소스도 딸리는 거 같아서 검색결과 사용해본 Typora Editor의 img 파일 연결법이다.

`Wiki's`
> **마크다운(markdown)**은 일반 텍스트 기반의 경량 마크업 언어다. 일반 텍스트로 서식이 있는 문서를 작성하는 데 사용되며, 일반 마크업 언어에 비해 문법이 쉽고 간단한 것이 특징이다. HTML과 리치 텍스트(RTF) 등 서식 문서로 쉽게 변환되기 때문에 응용 소프트웨어와 함께 배포되는 README 파일이나 온라인 게시물 등에 많이 사용된다.


## Typora Markdown Editor
Github Pages를 블로그로 선택한 이유는 직업 특성상 오프라인(기내)에서 쉬는 동안 시간도 보낼 겸해서 글을 쓰기 위함이였다. <br>
Markdown 형식으로 내 맥북에서 글을 쓰는 데 ATOM은 조금 불편함이 있어 가볍고 보기 편한 무료 Editor를 찾던 중 괜찮은 Editor로 설정법을 소개한다.

### Tyrora 설치
아직가지 beta 버전으로 무료로 사용할 수 있다.

![typora](/img/coding/github/typora1-1.jpg)

공식 홈페이지 : https://typora.io

### /img 폴더 연결
Typora는 가볍고 간단하게 Markdown을 편집할 수 있다. 하지만 Github Pages의 경우 폴더를 나누 관리하는 방식으로 정리를 해서 img 파일을 단순하게 하나의 폴더에 몰아 넣을 수는 없었다.

![typora](/img/coding/github/typora2.jpg)
- **/_posts** : 포스팅 내용들이 있는 폴더로 그 안에는 또 categories별로 다시 폴더로 나누어 놓았다. <br>
- **/img** : img 파일도 크기와 포스팅에 따라 나누어 놓았다.

>그러다가 보니 img 파일을 불러 오지 못하는 결과가 되었다. <br>
ATOM에서는 폴더 구조에 문제가 없지만 Typora는 연결이 어려웠다.


![typora](/img/coding/github/typora4.jpg)
>**서식** - **이미지** - **루트 경로의 이미지 사용** <br>
/img와 _posts 폴더 상위의 폴더를 선택해주면 된다. <br>
**/flyingdeuk.github.io** 폴더를 선택

### Tag 복사하기
루트 경로를 기준으로 상대경로의 형태로 상단에 Tag가 붙는다.

![typora](/img/coding/github/typora5.jpg)
>해당 Tag를 복사해서 모든 post에 붙였다.

일일이 지정하는 것보다는 tag의 경로를 복사해서 붙여주면 간단하게 img를 보면서 글을 쓸 수 있겠다.

#### PostScript
**하지만 문제가 있다. post마다 폴더로 구분을 해 놓았더니 상대 경로인 이유로 경우에 따라 ../를 추가해줘야 했다.**

하지만 상기의 방법을 이용하면 가볍게 간단하게 Github pages의 구조에서 Typora를 이용할 수 있다.
