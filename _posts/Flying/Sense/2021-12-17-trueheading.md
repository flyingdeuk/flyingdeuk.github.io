---
title: POLAR Route True Course - 폴라 루트 True Course 사용시기에 대하여
author: FlyingDeuk
date: 2021-12-17
categories: [Flying, FlyingSense]
tags: [flyingsense]
pin:
---

![true](/img/flying/sense/trueheading1.jpg)

`FlyingDeuk's`
> Polar Route에 진입하면서 H/D Index를 Magnetic에서 True Index로 놓아야 하는 시기가 있다. 캐나다에서 진입시에는 특별히 명시된 Nxx의 위도 좌표가 없어서 애매했는 데... 심사관님의 도움으로 그 이유를 알게 되어 포스팅 한다.

`Wiki's`
> **True North : 진북(真北)** 은 지구 표면을 따라 지리적인 북극을 향하는 방향을 말한다. 진북은 지구표면에서 지구 자기장이 가리키는 자북과는 달리 지도 투영법에서 자오선을 따라 북쪽으로 가는 방향이다.

> **Magnetic North 자북극(磁北極) 또는 자북(磁北)** 은 지구의 자기장이 수직의 아래 방향으로 가리키는 지구 표면의 지점으로, 시간이 지남에 따라 점점 이동한다. 자북은 흔히 '지자기 북극(Geomagnetic pole)'과 혼동되기도 한다.

## BackGround
### Area of Magnetic Unreliability (AMU)
- Compass which gives direction by the lateral magnetic field of earth cannot be used in the Polar region for navigation purposes.
  > 북위가 높아 자북을 신뢰할 수 없는 지역을 이야기하며 N74이상을 대략적으로 지칭한다.

### Key Hole Area
- It is the Area of Magnetic Unreliability information stored in FMS Data. This region is named by the shape of keyhole that the boundary line of this region resembles. When aircraft enters this region, FMC convert to True Heading mode automatically.
  > 항공기 FMS상에서 자북을 신뢰할 수 없는 지역으로 정의된 열쇠구멍형태의 구역으로 해당 구역으로 진입하면 FMC가 자동으로 True Heading으로 전환이 된다. <br>
  **항공기 제작사에 따라 다르다. Ex) Airbus, Boeing**


## CANADA AREA (NCA : Northern Control Area)
통상적으로 북미에서 이륙해 Polar에 진입하기 위해서는 캐나다를 경유하게 된다.

![true](/img/flying/sense/trueheading2.jpg)

뉴역에서 이륙해서 Polar로 진입한다.
> **NCA Boundary Operation Notes** 를 보면 **True Track**을 사용한다는 정보가 나와있다.

![true](/img/flying/sense/trueheading3.jpg)
> 과거에 사용하던 항로지도에서도 역시 항로 Course 자체가 NCA부터는 True Course로 되어 있는 것을 알 수 있다.

![true](/img/flying/sense/trueheading4.jpg)
**JEPPESEN CANADA State Rules and Procedure** 에서도 해당 내용을 찾아볼 수 있다. -> **Airspace Requirements and Procedures**

## Rusia Magadan AREA
Polar를 경유해서 러시아 Magadan으로 주로 한국으로 들어옴.

![true](/img/flying/sense/trueheading5.jpg)

**JEPPESEN상에서 규정은 찾지 못했으나 과거 지도를 기준으로 74N 아래는 Magnetic Course로 항로가 구성되어 있다.**

## 결론
- **바로 상기의 이유로 Polar 진입시 Nxx의 위도기준이 아닌 NCA에 진입하면서는 항법을 위해서 True Course를 사용해야한다.**

- **러시아 지역에서는 대략 74N 아래는 Magnetic Course로 환원한다.**

--------

### PostScript
무엇이든 궁금한게 있으면 우리는 족보라 불리우는 누군가의 정리 자료를 먼저 뒤지기 마련이다. 규정을 찾아보는 습관이 중요한 이유가 되겠다.

**이 포스팅도 찾는 방법에 대한 안내이지 족보가 되기를 바라는 것은 아니다...**

-------

### [< Back to FlyingSense >](/categories/flyingsense/)
