---
layout: post
title:  "Analog - Bandgap Reference"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Bandgap Voltage Reference는 PVT variation이나 loading 상황에 관계없이 일정한 전압을 주려고 쓴다.

Bandgap reference에는 BJT랑 저항이 들어가기 때문에 면적이 많이 필요하다. 그래서 비싸다.
그리고 noise, precision specification을 원하는 수준까지 올리려면 power가 많이 필요할 수 있다.

bandgap에는 3종류가 있다.
BJT, MOSFET, 2TR

2TR은 NMOS 2개로 Bandgap을 만든 경우고, power 소비가 적어야 할때 쓴다.

MOSFET으로 bandgap을 만들때에는 weak inversion region을 쓴다. BJT처럼 exponential하니까.

그 외 회로에서도 power를 적게 써야 할 때 가끔 weak inversion region을 쓴다.

weak inversion region은 gm이 부족하지 않나?
이건 W 키우면 된다.
그럼 면적 손해가 일어나지 않나?
L 줄이면 된다.

캐패시턴스가 작을수록 트랜지스터의 f_T가 크다.
전압을 크게 넣으면 f_T가 커진다는 어조로 적혀있는데, 이거 확인좀

왜 MOS로 bandgap 많이 안만들고 BJT 쓰냐?
MOS로 만들면 공정 variation이 좀 크다.

