---
layout: post
title:  "Analog - Bipolar Transistors"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Bipolar transistor들은 CMOS 대비 더 높은 gm, 더 낮은 1/f noise를 갖는다.
breakdown voltage도 더 높고, reliability도 더 높다.

대신 shot noise는 있다
이건 고주파 noise

온도센서에는 BJT가 들어가는데, 전원전압이 너무 내려가면 쓸 수가 없다.
그리고 사실 PnR을 위해서는 BJT가 없는게 낫다.

온도 센서 회로와 TSD 회로 모두 BJT를 사용한다.


TSD 내부는 어떻게 생겼나?
BJT 하나 넣어서 CTAT 특성 만들어놓고, CTAT 전압이랑 온도가 변해도 일정한 VREF 전압을 비교한다.
그리고 그 전압 차이를 온도 차이로 간주해서 온도를 측정하고, 너무 차이나면 꺼지게 만들어둔다.

고주파 활용:
BJT든 MOSFET이든, 소비 전류를 늘리면 동작 속도가 빨라진다.
전압이 변하는 속도가 증가한다는 뜻이다.

그래서 전류를 올리다보면, 전자들의 이동속도가 vsat에 도달한다.
여기서 더 빨라지려면?

MOSFET이면 channel length L을 줄여야 하고,
BJT면 Base width W_B를 줄여야 한다.

IC 집적 기술이 발전하면서 L은 아주 줄어들었지만, Base width는 그러지 못했다.
그래서 초고주파에서는 CMOS를 써야 한다.

작은 전류에서는 최대 f_t를 Gate capacitance / Base junction capacitance,
큰 전류에서는 최대 f_t를 vsat/Leff / vsat/WB가 결정한다.

MOSFET은 Ids가 늘어나면 gm/Ids가 줄어드는데, BJT는 일정하다
그리고 같은 전류라면 BJT가 MOSFET보다 gm이 크다.
그래서 작은 전류로 큰 gm이 필요한 경우라면 BJT가 유리할 수도 있다.

base current가 흐른다는게 BJT 단점이다

MOSFET이라고 아예 안흐르는건 아니다.
MOSFET oxide가 얇으면 tunneling에 의해 gate leakage가 발생한다.

이 leakage는 oxide가 얇을수록 증가하는데, tox=L/50정도니까,
L이 점점 짧아지면서 leakage가 점점 늘어나 무시하기 어렵게 됐다.

이 gate current는 BJT의 base current와 유사하지만,
gate current는 트랜지스터가 꺼져도 흐른다는 문제가 있다.

