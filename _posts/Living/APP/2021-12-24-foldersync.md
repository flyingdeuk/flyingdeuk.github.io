---
title: Android Autosync for Cloud - 안드로이드 클라우드 서버 자동 동기화 어플 (Feat. FolderSync)
author: FlyingDeuk
date: 2021-12-24 20:55:00 +0800
categories: [Living]
tags: [usefulapp, android, autosync]
pin:
---

![search](/img/living/app/foldersync1.jpg)

`FlyingDeuk's`
> Autosync 기능은 기본적으로 내가 원격의 구글 Cloud에 특정 파일을 저장할 때 아이패드에서 저장한 내용을 내 핸드폰이나 내 컴에서 다시 다운받을 필요없이 변화를 감지하여 똑같은 상태를 유지해주는 기능이다. -> 안드로이드에서는 Autosync의 기능을 특정 어플에서 지원하지 않는다... 개별 기능의 어플을 설치해야 가능한다.

`Wiki's`
>**구글 싱크(Google Sync)** 는 G메일, 구글 연락처, 구글 캘린더를 PC, 모바일 장치 메일, 캘린더, 주소록 응용 프로그램과 OTA 동기화 기능을 제공했던 구글의 파일 동기화 서비스이다.[1][2] Microsoft® Exchange ActiveSync®를 이용하여 서비스 사용자들이 자신들의 구글 앱 메일, 연락처, 캘린더를 자신들의 모바일 장치와 동기화할 수 있게 하였으며 사용자들은 또한 들어오는 메시지와 앞으로의 미팅에 대한 알림을 커스터마이즈할 수 있었다.[3][4] 구글 싱크는 PC, 맥, 리눅스, 안드로이드, 블랙베리, 심비안 S60, 아이폰, 아이패드, 윈도우 모바일 등의 장치와 동작했다.[5] 구글 싱크는 2009년 2월 발표되었으며[6] 비즈니스에 속하지 않은 사용자들에 대해서는 2012년 12월 중단하였다.[7]

## 클라우드 서비스의 이해
많은 회사들이 Cloud 서비스를 일정 부분 무료로 제공한다. <br>
지금까지 브랜드별로 사용해본 결과는
- Google : 15 GB
- Apple : 5 GB
- Microsoft : 5 GB
- 네이버 : 25 GB
- 다음 : 50 GB (서비스 종료)
- Dropbox : 2 GB (조건에 따라 무료로 늘려줌.. 예) 친구 초대등등...)
> 중국 서버들은 2 TB, 10 TB를 제공한다... 대륙의 클라스이나.. 패스~~~

### Google Drive
![search](/img/living/app/foldersync4.jpg)
> 구글 클라우드내에서 저장된 파일들을 보면 아래와 같다.

![search](/img/living/app/foldersync2.jpg)
> 내 드라이브는 특정 폴더만을 클라우드에 올리는 방식이다.

![search](/img/living/app/foldersync3.jpg)
> 컴퓨터는 내 PC의 특정 지점(폴더)를 동기화하는 방식이다.

**FolderSync는 이중에 내 드라이브의 내용만이 동기화가 가능하다.**

## FolderSync
클라우드에 있는 파일을 지속적으로 점검해서 로컬(내기기)에 새로운 파일을 리모트(클라우드)에 올리는 어플이다. 그중 무료이며 설정이 편한 것을 사용 중이다.

### FolderSync 일반사항
가장 기본은 처음 설치후 계정등록후 Sync를 설정하는 것이겠지만 차례대로 설정한다.

#### 홈
![search](/img/living/app/foldersync5.jpg)
> **홈**에서는 동기화의 상태나 계정 동기화 폴더등의 정보를 할 수 있다.

#### 폴더쌍
![search](/img/living/app/foldersync6.jpg)
> 헌재 설정한 **Autosync**의 폴더 정보를 보여준다.

#### 계정
![search](/img/living/app/foldersync7.jpg)
> **계정** 클라우드 동기화를 위한 계정 등록 사항을 할 수 있다.

#### 정보
![search](/img/living/app/foldersync8.jpg)
> 일반적인 정보와 기본 설정을 알려줌...

### FolderSync 세부 설정법
![search](/img/living/app/foldersync9.jpg)
> 최초 사용을 위해서 본인의 클라우드 계정에 로그인을 해줘야함...

![search](/img/living/app/foldersync10.jpg)
> 위의 계정의 폴더중 하나를 지정해서 Autosync 설정을 해준다.
- 로컬폴더 - 원격폴더 : 로컬폴더는 내 핸드폰, 원격폴더는 클라우드이 폴더... 한방향으로 할것인지 양방향으로 할것인지를 결정한다. (수정사항을 어떻게 반영할 것인지 결정)

![search](/img/living/app/foldersync11.jpg)
> **기본적으로 자동감지는 유료다... 즉 어느 곳이든 수정이 이루어지면 감시하고 있다가 동기화(Sync)를 진행한다...**
-> 이는 감시를 위한 배터리 감소등등의 부작용이 많으니.. 하루 한번정도...

![search](/img/living/app/foldersync12.jpg)
- 동기화 삭제 : 예를 들어 내폰에는 기 저장된 파일이 있는데... 서버에서는 삭제된 경우 내폰의 파일을 삭제할 것인지를 결정하는 옵션
- 기존 파일 덮어쓰기 : 내 폰이든 서버에서든 변화가 생겼을 경우 어느 것을 우선 다운 받을지를 결정...
- 로컬 및 원격 파일이 모두 수정 된 경우 : 서버의 파일도 변경되고 내 폰의 파일도 변경된 경우 어느 것을 Primary로 남길 것인지를 결정...

![search](/img/living/app/foldersync13.jpg)
- 전체동기화에서 제외 : 여러개의 동기화 계정 및 폴더가 있을 때 한방에 할 건지 결정하는 옵션
- 없는 경우 로컬 동기화 폴더 생성 : 서버에 새로운 폴더가 생성되더라도 내 폰에 같은 폴더를 만들지 말지...

![search](/img/living/app/foldersync14.jpg)
> 알아서 선택...

![search](/img/living/app/foldersync15.jpg)
> 동기화 결과에 대한 알림 설정

**위의 설정을 상황에 맞게 설정하면 서버에 있는 내 자료들을 편의에 맞게 동기화해서 동일하게 유지가 가능하다**

-----------

### PostScript
예전에는 항상 USB 를 항상 가지고 다는 것이 유행이였다... <br>
하지만 최근에는 클라우드에 저장하고 자신만의 파일을 관리하는 것이 대세인듯... Autosync는 자동 동기화를 통해서 사람의 노력을 줄여준다.

----------

### [< Back to ANDROID BEST APP >](/posts/AndroidAPP/)
