---
title: Cruise Altitude(Step Climb) 적용 기준
author: FlyingDeuk
date: 2020-09-02
categories: [Flying, FlyingSense]
tags: [flyingsense]
pin:
---

`FlyingDeuk's`
> 민간항공에서는 안전이 최우선이지만 경제적인 것을 배제할 수 없다. <br>
특히 장거리 비행의 경우 Step Climb하는 이유이다. <br>
이를 위해 항공기 제작사에서는 다음과 같은 개념을 적용하여 운영하게 제작된다. <br>

![crz](/img/flying/sense/crz.jpg)

## CRZ ALT(Step Climb)

### OPT ALT - calculation of OPT altitude is based on
- gross weight, cost index, cruise speed schedule, and cruise cg.
- Wind and temperature deviations from standard day are not used in the calculation.
- The optimum altitude is not calculated during an RTA cruise segment.

`즉 항공기 무게, CG, Cost Index에 따른 최적의 고도임. 바람과 온도는 고려하지 않는다.`

    Cost Index : 시간과 연료를 고려한 수.


### MAX ALT – displays maximum altitude based on:
- current gross weight minus calculated fuel burn to climb to MAX altitude
- temperature
- number of engines operating
- cruise reference thrust limit default set by airline (CRZ or CLB)
- speed (ECON, LRC, SEL, or CO)
- residual rate of climb default set by airline (range: 100 to 999 feet per minute)
- disregards altitude or speed constraints
- cruise CG

`즉 항공기 구조 및 엔진의 성능등의 항공기 성능으로 상승가능한 최대 고도임.`

### RECMD ALT
- displays the most economical altitude to fly for the next 250 - 500 nm based on gross weight, cruise speed schedule, and entered forecast winds and temperatures at cruise altitudes.
- The FMC evaluates altitudes between 9,000 feet below the current CRZ ALT and up to MAX altitude.
- Recommended altitudes are consistent with the specified step size and step climb schedule.
- If the step size is zero, the recommended cruise level is calculated assuming a 2,000 feet step size.
- The recommended altitude is set to the CRZ ALT when within 200 nm of the T/D or within 500 nm of the destination airport. The recommended altitude is not calculated during an RTA cruise segment.

`즉 OPT ALT에 입력되거나 측정된 바람과 온도에 따른 추천되는 고도임. 당연히 상승후 일정시간이 경과해야 상승에 사용된 연료를 절감하니 목적지 근처에서는 필요가 없어진다.`

-------

[INDEX로 돌아가기](/categories/flyingsense/)
