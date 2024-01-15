---
title: FMS Effective Date 변경 기준 (Feat. 대한항공 기술부서, Jeppesen)
author: FlyingDeuk
date: 2020-08-31
categories: [Flying, FlyingSense]
tags: [flyingsense]
pin:
---

![ident](/img/flying/sense/ident.jpg)

`FlyingDeuk's`
> 항상 비행전 FMS Effective Date를 확인한다. <br>
조종사마다 의견이 분분하나 기술부서의 문의 결과이다. <br>
어디에서도 찾을 수 없었음. AIM, Jeppesen등등...

`Namu Wiki's`
> **Aeronautical Information Regulation And Control** <br>
AIRAC 은 비행시 필요로 하는 데이터이다. 이 데이터 안에는 SID 와 STAR가 있다. 또한 활주로에 대한 정보도 포함되어있으며 ILS 주파수 또는 VORDME 도 포함되어있다. 이 정보들은 공항 또는 국가에서 항로 변경 또는 항로 수정, VOR포인트를 수정 했을경우 AIRAC에 정보가 올라간다. <br>
이 데이터는 비행기 내부에있는 FMC (Flight Manager Computer)에서 사용이 된다. 구형 AIRAC Cycle를 쓰고 있는 항공기는 없지만 만약 있으면 분명히 차트에는 나오는 way point가 시현이 안 될수도 있다. <br>
또한 이 데이터는 유효기간이 있으며 이 유효기간이 지났을 경우에는 사용이 불가능하며 비행경로계획에 문제가 생긴다. 실제 항공기에서는 AIRAC Cycle이 만료되기 전에 새로운 Cycle이 올라오게 되며 이 AIRAC Cycle을 비행기 FMC에 덮어쓰인다. AIRAC 이 만료되면 기내에 FMC에서 비행기 위치를 설정할때 nav data out of date라는 문구가 하단에 나타난다. 

-----------

## AIRAC 당일 FMS NDB 변경 기준
- 대부분의 국가는 AIRAC 당일 00 UTC 기준으로 항로 및 절차 변경을 적용 중이나,
- 일부 국가(한국, 중국, 일본) 중에는 AIRAC 변경 시간을 자국의 Local Time 기준으로
AIRAC 변경사항을 적용하기 때문에 국가별 Effective 시간을 모두 준수하기가 현실적으로 어렵습니다.
- 따라서 일반적으로 출발 시간 기준 00Z 이전편의 경우 이전 AIRAC Data를 사용하고,
00Z 이후 출발편의 경우 다음 AIRAC data를 선택합니다
- AIRAC 당일 경우 관제에서 변경된 절차에 대해 Radar Vector 등의 서비스를 제공할
수도 있습니다.

>출발일자 또는 도착일자?? 기준으로 변경한다. 의견이 분분한 내용... <br>

`출발시간 기준 00Z 이후면 변경, 아니면 그냥 둬라!!!`

---------

## Jeppesen 해당 내용
Jeppesen에서도 해당 내용을 찾아보았다.
검색어 **effective date**로 찾아보면...

![ident](/img/flying/sense/ident1.jpg)
> Glossary에 해당 내용이 있다.

FAA, Canada 는 0900 UTC 기준 local time 0100 - 0600 사이를 기준으로하고 그외에는 0000 UTC 기준으로 하나 나라마다 다를 수 있다고...

`그래서 해당 effective date의 검색 결과에 나라별 Publication에도 나오는 것을 알 수 있다.`

그래서 결론은 기술부서의 문의 결과와 동일하다고 하겠다. 

-----------

[AIRAC FMS Effective Date 변경 기준 쉽게 확인하고 적용하는 법 (Feat. JEPP FD Pro)](/posts/airac/)
- FD PRO를 이용한 간단한 확인 및 적용법이 되겠다. 

-------

### [< Back to FlyingSense >](/categories/flyingsense/)
