---
title: Flight Plan - FMS DATA 검증 Part 2. (WIND DATA 입력법) <2024.3.24 Updated>
author: FlyingDeuk
date: 2024-03-24
categories: [Flying, FlyingSense]
tags: [flyingsense, flightplan, fms, wind]
pin:

---

![inputwind](/img/flying/sense/totaldistance.png)


`FlyingDeuk's`
> Part 1 에서 RTE의 검증과 LEG의 검증 이후에 총 거리에 대한 검증을 하는 방법을 알아보았다...<br>
항상 비행에 대한 포스팅은 망설여진다... 그래서 오래 걸리기는 했으나 누군가 필요한 사람에게 도움이 되기를 바라며... Part 2를 시작해본다. 

`Wiki's`
> 비행계획(飛行計劃) 또는 플라이트 플랜(영어: flight plan)은 항공기가 비행을 때 항공 관서 (항공 교통 관제 기관 등)에 통보하는 비행에 대한 계획이다.

>비행 관리 시스템(飛行管理 - , 영어: flight management system, FMS)은 컴퓨터 동작 도움으로 조종사에 비행을 위한 업무를 도와주는 항공전자 시스템의 한 부분이다. 비행 관리 컴퓨터(FMC, Flight Management Computer), 자동 비행 시스템(AFS, Auto Flight System), 위성 항법 시스템(INS/GPS Navigation System including), 전자식 비행 계기(EFIS, Electronic Flight Instrument System)로 구성된다.

------------

# WIND DATA 입력
> 매번 만나는 새로운 기장님들에게 물어본다... 국제선은 왜 Wind Data를 넣을 까요???

> 그에 대한 대부분의 답은 FOD와 ETA를 좀더 정확하게 하기 위해서라는 답이 대부분이며 나도 예전에는 그렇게 생각했었다...

`조금만 생각을 전환해보자... Flight Plan이 어떻게 만들어지는 지... 우리는 왜 힘들게 바람을 입력해야하는 지...`

## Flight Plan
조금은 원론적인 이야기일 수는 있다. 하지만 조금은 더 본질에 접근하는 것이 아닌지 모른다.

![inputwind](/img/flying/sense/inputwind1.jpg)
- 일반적인 Flight Plan의 모습이다. 여기에 표시된 총 TRIP FUEL과 총 TIME은 오른쪽의 총 DIST에 의해서 산정이 될까를 먼저 생각해보면 좋을 거같다. 

![inputwind](/img/flying/sense/inputwind2.jpg)
- Plan의 본문을 보자... 항공기 무게에 따른 상승가능한 고도 + ATC가 인가가능한 고도 + TURB 예보등을 고려해서 고도를 Dispatch한다. Dispatcher가 통상은 그러한 것으로 알고있다...(정확하게는 추적해보지는 않음)
- 위에 명시되었던 FUEL, TIME은 결국은 Dispatcher가 계획한 고도와 그 고도의 온도와 바람의 영향으로 산정이 된다는 것은 여기까지 정독을 했다면 이해가 갈 것으로 예상이 된다. 

`어찌 보면 잠시 생각해보면 당연한 이야기를 우리는 간과하고 있었는지도 모른다... 바람과 온도와 항공기 무게등의 고려 요소가 결국은 CRZ 고도와 연료 소모 그리고 소요 시간을 결정할 수 밖에 없다는 것은 상식적일 수 밖에는 없다.`


![inputwind](/img/flying/sense/inputwind3.jpg)
- Plan의 Header 부분은 보면 평균풍이 나와 있다. 우리는 이,착륙에는 정풍이 유리하지만 Enroute에서는 배풍이 유리하다. Wind -92는 경로상 평균 92kts의 정풍이 분다는 이야기다...
- 그 아래의 DIST와 NAM이 이 이야기의 핵심일 수도 있다. 

`NAM` 은 무엇인가??
- Nautical Air Mail이라 나올 뿐 자세한 이야기는 없다...

네이버 블로그에서 찾아 보았다. 플톱스님의 포스팅으로 NAM을 구하는 방법은 아래와 같다. 

 포스팅 "Wind Range Correction (NM -> NAM)" -> <https://m.blog.naver.com/fltops/191578052>
- 포스팅에 감사드립니다. 

> 결국은 계획된 고도와 그 고도의 온도 그리고 바람에 따라 Nautical Air Mile이 선정되며 그에 따라 연료와 시간이 산정된다. 

> 즉 LEG에 바람을 넣어야 되는 이유는 조금 보수적 원론적으로 **작성된 Flight Plan**의 조건을 Plan과 FMS에 똑같이 넣어줘서 오류가 생기는 지 검증하는 작업인 것이다. 

---------

## FMS 
위의 내용을 이해했다면 이제는 FMS를 한번 살펴보자. 

B737의 절차를 알아본다. 

![inputwind](/img/flying/sense/inputwind4.jpg)
- FMS에 Performance에 TOC(Top of Climb)의 바람과 온도를 넣어준다. (이는 추가 바람을 입력하지 않더라도 모든 LEG WIND의 Initial 값을 넣어주는 효과가 있다. 즉 모든 LEG가 같은 값으로 다 복사된다.)

![inputwind](/img/flying/sense/inputwind5.jpg)
- 상기의 입력된 바람이 Default와 같이 입력이 Small Font로 되고 이후는 다시 넣어주는 값이 Large Font로 들어가게된다. (PERF INT에 TOC 바람을 넣지않으면 모두가 000/00으로 표시된다. 

`위에서 언급한데로 Flight Plan의 연료와 시간은 결국은 해당 고도의 온도와 바람을 기준으로 같은 로직으로 계산된 것이므로 조종사는 Flight Plan과 FMS의 데이터를 동일하게 맞춰 오류가 있는 지 동일하게 계산되는 지 확인하는 것이 결국은 조종사에 의해서 이루어지는 검증 절차의 이유이다... Part 2.`

------------

# Postscript
결국은 조종사의 역할은 같은 알고리즘으로 계산되는 Plan의 컴퓨터에서 작성된 Plan을 실제 운항할 항공기의 FMS에 입력하여 같은 지 오류가 있는지를 판단하는 역할을 수행한다고 이해하면 쉽지않을 까 생각한다. 

> 약간의 생각의 전환으로 이해를 하면 더 잘 되는 경우라 할 까...

추가적으로 WIND DATA를 입력하는 다른 TIP정도 언급을 하고 싶다. 

-----

## 평균풍 입력하는 방법
예전 B777의 초기 시절 WIND DATA가 자동 업로드되지않는 경우 사용하는 방법이다. 일일이 넣기에는 너무 장거리라...

![inputwind](/img/flying/sense/inputwind6.jpg)
- Plan의 평균 온도와 평균 바람을 기준으로...

LA의 KLAX를 FIX Page에 입력하면 Bearing과 Distance가 나온다...

이 값을 LEG Page의 첫번째 Fix에 Bearing과 평균바람을 넣어주면 모든 LEG에 복사가 된다... 지점별 바람 온도는 다르겠지만 간단하게 평균 풍과 평균 온도로 대략적인 Plan의 오류를 검증할 수 있다....

> B737에서도 유사하게 이용하는 경우가 있는 거 같다. 
- 위와 같은 방법으로 목적지의 대략적인 방향 (Bearing)과 평균 바람을 입력해서 그냥 운항하는 경우이다...

> 위에서 명시된 내용과 Plan의 작성법을 이해했다면 다분히 오류가 발생할 수 있다는 점에 이해가 될 것이라 판단이 든다... 이전에 포스팅했던 RTA의 경우 더 많은 오류가 발생하게 된다...

### [B737 FMS LEG WINDDATA Error - Wind Data의 치명적인 오류 (Feat. RTA, CRZ CLIMB)](/posts/B737-winddata/)

이야기가 길어지니 배가 산으로....

다음은 STEP CLIMB으로....

----------

### [< Back to FlyingSense >](/categories/flyingsense/)
