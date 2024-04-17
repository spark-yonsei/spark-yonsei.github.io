---
layout: post
title:  "Scaling"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---

scale돼서 크기가 작아진 CMOS공정, 즉 scaled CMOS공정은:

크기가 작으니 input capacitance는 작아진다.
그렇다고 크기 줄인다고 RF performance가 계속 좋아지는 것은 아닌 것이,

interconnect parasitic때문에 또 악화된다.
실제로는 45nm, 28nm CMOS 정도가 성능이 최대치를 갖는 지점이다.
이거보다 작으면 소자들이 parasitic gate capacitance, resistance에 크게 영향받는다.
그래서 RF performance가 안좋아진다.
그래서 RF에서는 더 줄이는게 의미가 없다.