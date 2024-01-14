---
title: Flight Plan - FMS DATA 검증 Part 1. (Total Distance 확인법) <2024.1.14 Updated>
author: FlyingDeuk
date: 2024-01-14
categories: [Flying]
tags: [flyingsense, flightplan, fms, total, distance]
pin:

---

![totaldistance](/img/flying/sense/totaldistance.PNG)


`FlyingDeuk's`
> 브리핑 과정을 통해서 Flight Plan의 내용을 점검하고 난 이후 항공기에 와서는 FMS에 해당 Plan의 내용을 집어넣어야한다. 이후에는 오류가 있는 지 검증을 해야되는 데 아래의 과정은 첫번째로 이루어지는 총 거리에 대한 이야기이다. 

`Wiki's`
> 비행계획(飛行計劃) 또는 플라이트 플랜(영어: flight plan)은 항공기가 비행을 때 항공 관서 (항공 교통 관제 기관 등)에 통보하는 비행에 대한 계획이다.[1]

>비행 관리 시스템(飛行管理 - , 영어: flight management system, FMS)은 컴퓨터 동작 도움으로 조종사에 비행을 위한 업무를 도와주는 항공전자 시스템의 한 부분이다. 비행 관리 컴퓨터(FMC, Flight Management Computer), 자동 비행 시스템(AFS, Auto Flight System), 위성 항법 시스템(INS/GPS Navigation System including), 전자식 비행 계기(EFIS, Electronic Flight Instrument System)로 구성된다.

------------

## 총 거리 검증 (Total Distance)
Flight Plan의 총 거리는 크게 3개로 나눠 생각할 수 있다. 
- SID : 제일 먼 거리를 기준으로 작성됨.
- Body : 첫번째 FIX - 마지막 FIX 총 거리
- STAR : 제일 먼 거리를 기준으로 작성됨. 

> 이륙, 착륙시 제일 먼거리를 고려하는 이유는 가장 보수적으로 연료를 고려하기 위해서이다. 

---------

## SID

### Flight Plan

![totaldistance](/img/flying/sense/totaldistance8.jpg)
- 첫번째 FIX인 OSPOT까지의 거리는 제일 먼 거리를 고려해서 77NM이 된다. 
    - ex ICN RWY 34/33로 이륙후 왼쪽으로 돌아나가는 제일 긴 SID기준
### FMS

![totaldistance](/img/flying/sense/totaldistance1.jpg)
- 일반적으로 비행준비과정에서 SID를 미리 넣어놓아 SID상의 많은 FIX들을 모두 더하거나 OSPOT까지...

![totaldistance](/img/flying/sense/totaldistance2.jpg)
- OSPOT을 맨 위로 올려 Plan과 같이 만들어 주는 것이 더 좋은 방법인듯하다. 총 거리는 58NM이다.  

> B777의 경우 OSPOT을 Progress Destination에 붙이면 자동으로 현재 들어가있는 SID의 거리를 보여주나... B737에는 이 기능이 없다. 

`Plan 대비 FMS가 77-58=19NM 더 길다.`

-----------

## STAR

### Flight Plan


![totaldistance](/img/flying/sense/totaldistance9.jpg)
- 마지막 FIX인 UNZ에서 Destination인 PGUM까지의 거리는 15NM이다. 

### FMS

![totaldistance](/img/flying/sense/totaldistance3.jpg)
- 위왁 같이 UNZ - PGUM으로 STAR를 넣지않았다면 그냥 보면되나... STAR를 넣었다면 다 더하는 것보다는 위와 같이 RWY를 올려주면 PGUM과 같다. 거리는 3.3NM이다. 

`Plan 대비 FMS가 15-3.3=11.7NM 더 길다.`

----------------

## BODY

### Flight Plan

![totaldistance](/img/flying/sense/totaldistance10.jpg)
- Plan 상은 SID, STAR를 포함한 전체 거리가 1799NM이다. 

### FMS

![totaldistance](/img/flying/sense/totaldistance4.jpg)
- 이전에 SID에서 OSPOT을 제일 위로 STAR에서 UNZ - RW06L로 Modify 해 놓은 상태에서의 총 거리는 1768NM이다. 

`Plan 대비 FMS가 1799-1768=31NM 더 길다.`

### `즉 SID 거리차이(19NM) + STAR 거리차이(11.7NM=12NM) = 31NM 로 Flight Plan과 FMS입력값에는 오류가 없다.`

---------

## 오류의 원인
위와 같은 방법으로 검증을 하면 길어야 5NM이상 달라지지않는다. 장거리의 경우도 10NM을 넘지않는다... 그러면 이러한 오류가 생기는 원인은 무엇일까?

![totaldistance](/img/flying/sense/totaldistance5.jpg)
- 이 포스팅을 위한 노선 ICN-GUM의 경우 거의 일직선에 가까워서 오차가 없을 수 밖에는 없다. 
- 하지만 위의 그림과 유사하게 FIX사이가 가깝거나 선회량이 많은 경우 Fly-By의 형태로 FIX사이를 Lead Turn하게 되는데 이러한 Lead Turn들이 모이면 모일 수록 오차가 발생하게 된다. 

-------------

## Aviator 주의사항

![totaldistance](/img/flying/sense/totaldistance6.jpg)
![totaldistance](/img/flying/sense/totaldistance7.jpg)
- Paperless로 iPad를 통한 브리핑과 모든게 이루어지는 방향으로 가고 있다. 
- 총 거리는 똑같고 SID거리도 같은데... STAR거리가 명시되어 있지가 않다... 

> 회사제공 Plan PDF 형식이 사라진다면 이것도 고려가 되어야하지 않을까....



--------
## Postscript
코로나로 인해서 국제선 비행을 경험하지 못한 상태에서 교육을 받은 후배들이 위와 같은 내용을 잘 이해하지 못하는 것 같아서 포스팅을 하기로 맘을 먹었다. Flight Plan과 실제 항공기의 FMS데이터에 오류가 있다면 계획한 대로 비행을 하지 못하는 상황이 될 수도 있다. 물론 여러가지 장치들로 이상함을 감지할 수는 있지만 기초부터 차근차근 알고 적용하는 것이 더욱 중요한 듯하다. 




[INDEX로 돌아가기](/categories/flyingsense/)
