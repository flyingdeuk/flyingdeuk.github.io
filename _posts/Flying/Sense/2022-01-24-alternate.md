---
title: Alternate Airport IFR Weather Minima - 교체공항 IFR 기상제한의 해석
author: FlyingDeuk
date: 2022-01-24
categories: [Flying, FlyingSense]
tags: [northamerica, edto, alternate, airport, flyingsense]
pin:
---

![alternate](/img/flying/sense/alternate.jpg)

`FlyingDeuk's`
> 교체공항이라함은 쉽게 말해서 계획된 목적지에 착륙하지 못하는 상황에서 고려되는 Plan B 공항을 말한다. <br>
Plan B라는 의미에 맞게 Flight Plan에도 해당 상황에 대한 보수적인 고려가 포함되어있다. (교체공항까지 가는 상황에서의 연료등등...)<br>

모든 산업에 안전계수가 포함되듯 비행 계획의 단계에서 교체공항 선정에는 법적인 Requirement 가 포함된다. 이에 대한 고려사항이 아래에 있다.

`Jeppesen's`
> **ALTERNATE AERODROME (ICAO)** — An aerodrome to which an aircraft may proceed when it becomes either impossible or inadvisable to proceed to or to land at the aerodrome of intended landing. Alternate aerodromes include the following:
>- Take-Off Alternate — An alternate aerodrome at which an aircraft can land should this become necessary shortly after take-off and it is not possible to use the aerodrome of departure.
>- En Route Alternate — An aerodrome at which an aircraft would be able to land after experiencing an abnormal or emergency condition while en route.
>- Destination Alternate — An alternate aerodrome to which an aircraft may proceed should it become impossible or inadvisable to land at the aerodrome of intended landing.
>- Note : The aerodrome from which a flight departs may also be an en route or a destination alternate aerodrome for that flight.
>- ETOPS En Route Alternate — A suitable and appropriate alternate aerodrome at which an aeroplane would be able to land after experiencing an engine shutdown or other abnormal or emergency condition while en route in an ETOPS operation.

## Alternate Airport IFR Weather Minima
Dispatcher에 의해서 작성 및 고려가 되나 이는 조종사의 검토를 통해서 Confirm 되어야 한다.
> 항상 해석에 어려운 부분이 존재해서 정리해보고자 한다.

### 중요한 개념 이해
영단어 하나하나의 정확한 의미를 이해하는 것이 중요하다.

#### for pre-flight and/or in-flight planning
![alternate](/img/flying/sense/alternate1.jpg)
이 규정은 교체공항을 선정하는 규정이다. 즉 비행을 위한 계획 FlightPlan의 Requirement라고 생각하면 된다.
- for pre-flight : 지상 계획 단계에서 역시 상기의 Requirement가 충족해야 Plan 즉 항로를 정할 수 있는 것이다.
- in-flight planning : 공중에서도 마찬가지이다. 즉각적인 Divert가 요구되는 상황이 아니면 지속적으로 교체공항의 상기 규정을 충족하는지 여부를 모니터하고 항로 수정등의 고려가 요구된다.

`실제 비상상황에 직면하면 Nearest Suitable Airport가 원칙이다. 즉 상기의 규정은 더이상 의미가 없어지고 실제 Actual Minima를 고려해서 Divert Airport를 정해야 하는 것이다.` -> ATL 거주 Delta 항공사 기장님의 조언

#### Facility
공항내에 설치되어 있는 계기접근 절차에 필요한 장비를 의미한다.
- 접근절차에 중복 사용되지않는 장비는 각각 하나를 의미한다. ex) ILS 18, ILS 36는 각각 다른 Facility로 2개의 Facility로 인정된다.
- 양쪽 활주로에 동시 사용가능한 장비는 그냥 하나의 Facility이다. ex) VOR 18, VOR 36는 그냥 VOR 하나의 Facility이다. 최근 GPS도 여기에 해당된다.

#### Different Runway  
RWY xx와 같이 다른 숫자를 갖는 활주로를 Different Runway라 칭한다. 활주로의 갯수를 의미하는 것이 아님.
- 하나의 활주로 Rwy 36, 반대쪽 Rwy 18은 다른 활주로로 두개의 Runway가 된다.

#### Suitable Runway
항공기의 기종에 따른 착륙 성능, 바람 또는 다른 기상 조건에 부합하는 활주로를 의미함.
- Rwy 36 정풍 20kts 기상이면 Rwy 18은 배풍으로 착륙이 불가능하다. Rwy 18은 Not Suitable Runway가 된다.

`Different Suitable Runway` -> **다른 활주로 숫자에 기종별 착륙가능한 기상 상태**

#### Higher Minima
상기에 명시된 조건들로 구해진 Minima들 중에 보수적으로 높은 Minima를 선택하라는 의미임.
- Rwy 36 min 220ft, Rwy 18 min 205ft 라면 220ft가 Minima로 선정된다.

--------

### Note 사항의 이해
NOTE 사항을 하나씩 쉽게 이해해본다.

#### Note 1
![alternate](/img/flying/sense/alternate5.jpg)
미국 FAA의 공항들 **Airport Info**에 보면 **FOR FILING AS ALTERNATE**로 명시된 공항에 적용하는 사항이다.  

**KLCK(LCK) Airport Info Chart**

![alternate](/img/flying/sense/alternate10.jpg)
> 즉 **FOR FILING AS ALTERNATE**가 명시되어 있는 공항이라도 공항 차트의 Minima를 사용하는 것이 아니라 상기의 규정을 사용해야하며!!! <br>
상기 규정을 사용하더라도 **Airport Info** 상의 **NA**로 명시된 절차는 제외시켜야한다.

좀 더 보수적인 회사의 규정을 사용하되 해당 공항에 Alternate로 명시되지않는 것은 또 보수적으로 제외시켜라...

#### Note 2
![alternate](/img/flying/sense/alternate6.jpg)
> 위에서 설명한 대로 GPS는 과거 VOR접근과 유사하게 하나의 Facility로 봐야한다. 즉, VOR Rwy36, VOR Rwy18은 하나의 Facility로 운영되는 2개의 절차이나 하나로 봐야한다.

#### Note 3, 4, 5
![alternate](/img/flying/sense/alternate7.jpg)

**Note 3**
- different Runway이에 대한 언급 : 활주로 하나에 Rwy 36, Rwy 18이 있다면 different runway이다.

**Note 4**
- 규정의 CAT II/III Minima는 engine inoperative시 적용가능한 항공기에 적용해야한다. 즉 엔진 Fail 상황에서도 CAT III가 가능한 항공기에 한해서 적용해야한다.

**Note 5**
- Suitable에 관한 설명으로 Wind Limits를 고려해서 활주로를 선정해야한다.

### 적용법
각각의 항목에 적용하는 방법이다. 중요한 문구를 잘 봐야한다.

![alternate](/img/flying/sense/alternate2.jpg)

적어도 한개의 작동가능한 항법 시설(Facility)이 있는 경우
- MDA or DA + 400ft
- VIS + 1600m(1SM)
> 여기까지는 크게 어려움이 없다.



![alternate](/img/flying/sense/alternate3.jpg)

적어도 2개의 작동가능한 항법 시설(Facility)에 different suitable runway 접근절차 Minima중 Higher를 선정한다... 어렵다~~~


### Example
**활주로하나 2개이상의 Facility 좋은 기상**

활주로가 하나인 경우 2개 이상의 Facility가 필요하므로 ILS, GPS, VOR등의 접근 절차가 있고 항공기 성능 바람 또는 기상이 Suitable한 경우...

1. 만약 RWY 36-18 가 있는데 RWY 36에 205ft, RWY 18에 215ft라면 Different Suitable Runway의 Higher가 적용되어 RWY 18의 215 + 200 = 415ft Ceiling Minimum을 적용하면됨

2. 만약 RWY 36-18 가 있는데 RWY 36에 205ft, 410ft 그리고 RWY 18에 215ft, 420ft로 4개의 Minimum이 설정되어 있다면 Different
Suitable Runway의 Higher개념을 적용하여 양 방향에서 가장 낮은 2개를 비교하여 Higher 한 RWY 18의 215 + 200 = 415ft Ceiling Minimum을 적용하면됨

**활주로 한방향이 바람, 기상등의 이유로 사용불가시**

바람 또는 기상 등 이유로 어느 한 쪽 방향을 쓸 수 없다면 Different의 의미가 사라지므로 그 상위의 조건을 적용하여 낮은 Minimum에 400ft를 더한다. RWY36만 사용 가능하다면 205ft + 400 = 605ft Ceiling Minimum을 적용하면됨.


**추가로 예를 들어**

4개의 활주로를 보유한 공항에 각 각 Different Suitable Runway가 4개일 경우 RWY 36에 205ft, RWY09에 210ft, RWY18에 215ft, RWY27에 220ft라면 가장 낮은 RWY 36 Minimum 205ft 보다 Higher한 RWY09 Minimum 210ft를 적용하여 210 + 200 = 410ft Ceiling Minimum을 적용하면됨.

--------

### 실제 EDTO Alternate Airport 적용
실제 EDTO Alternate은 해당 링크에 따로 프스팅한다.

[Pacific EDTO Alternate Airport - 북미 태평양 EDTO ALT 공항](/posts/edto/) -> 바로가기

----

### PostScript
실제 기상이 205ft, 210ft로 보고 되지도 않을 뿐더라 이러한 과정은 어디까지나 혹시나 발생할 수 있는 상황의 대비라고 할 수 있겠다. <br>

일반적인 ILS 접근의 HAT(Height Above Touch)은 대략 200ft 정도이고 None Precision App의 HAA(Height Above Airport)는 대략 400-500ft 부근에서 설정된다고 가정하면...

EDTO Airport의 +400ft 조건을 고려하더라도 대략 1000ft정도 이상의  Ceiling이라면 Alternate Airport로 충분히 선정이 가능하다...

**즉 Ceiling이 1000ft 보다 낮거나 시정이 많이 떨어지는 날씨가 예보된다면 EDTO Alternate Airport의 면밀한 Check가 필요하지만 VFR이상의 날씨라면 전혀 문제가 없겠다.**

[INDEX로 돌아가기](/categories/flyingsense/)
