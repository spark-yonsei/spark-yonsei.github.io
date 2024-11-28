---
layout: post
title:  "Integrated Passive Components"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---

IC를 만들기 위해서는 트랜지스터 뿐 아니라 저항, 캐패시터, 인덕터를 웨이퍼 위에 구현해야 한다.<br>
같은 저항이더라도 어떤 방식으로 구현하느냐에 따라 특성이 크게 변할 수 있다.<br>
<br>
<br>
Integrated Resistors(저항):<br>
Resistivity가 높은 박막으로 IC 내에 저항을 구현한다.<br>
<br>
저항값을 결정하는 요소는 2가지다.<br>
저항의 가로세로 길이, 저항을 이루는 물질의 Resistivity다.<br>
구현한 저항값에 편차가 생긴다면, 이 두가지 요소가 흔들린 것이다.<br>
<br>
길이 편차의 원인:<br>
균등하지 않은 etch rate,<br>
Photolithography 오차<br>
<br>
Resistivity 편차의 원인:<br>
Doping Concentration, Doping Profile<br>
Annealing Conditions<br>
Fluctuation in Film thickness<br>
<br>
<br>
저항이 설계한 대로 만들어졌더라도, 온도가 바뀌면 저항값도 바뀐다.







온도가 바뀌면 저항값도 바뀐다.
재료에 따라 저항값이 달라서,
matching을 하려면 같은 material을 써야 하고
반대 경향을 갖는 재료 2개를 써서 온도 영향을 줄일수도 있다.

걸리는 전압이 바뀌어도 저항값이 바뀐다.
Poly resistor는 전압의 영향을 적게 받고,
Diffusion resistor는 전압의 영향을 크게 받는다.

poly resistor는 parasitic capacitance를 갖는다.
저항의 W를 늘려야 matching이 더 잘되지만,
W를 늘리면 parasitic capacitance도 늘어나는 문제가 있다.

Silicide block layer는 option으로 제공된다.
sheet resistance를 크게 올려준다.





MOS resistance:
MOSFET을 저항으로 쓰려면 MOSFET을 Triode region에 갖다둬야 한다.
이 경우에는 저항이 1/gm이다.

MOSFET으로 만든 저항은 전압 영향을 많이 받는다.



Integrated Capacitor(캐패시터):
IC 내에 캐패시터를 구현하는 방법은 크게 두가지가 있다.

Parallel capacitor: Linear Capacitance

인접한 두 도체 사이의 capacitance를 이용하는 방법이다.

Poly 2장 사이에 oxide를 끼워서 만들면 Poly-Poly Capacitor
Metal 2장 사이에 oxide를 끼워서 만들면 Metal-Metal Capacitor

metal을 쓰면 더 linear해지지만 capacitance 밀도는 떨어진다.


MIM(Metal-Insulator-Metal) Capacitor:

서로 다른 층의 Metal 을 겹쳐 capacitance를 구현한다.
보통 Top metal과 바로 아래층 metal을 사용해 만든다.

Capacitance 값이 정확하고, bias voltage에 무관하게 일정한 값을 갖는다.
제조할 때 추가 Mask와 공정이 필요하다.


MOM(Metal-Oxide-Metal) Capacitor:

MOM Capacitor는 여러 층을 쌓을 수 있다.
Capcitance 값이 MIM에 비해 불안정하다.


MOM Capacitor에는 추가 Mask가 필요 없다.




MOM(Metal-Oxide-Metal) Capacitor:
Capacitance를 만들기 위해 lateral field(fringing field)를 쓴다
high density, good matching
reasonable accuracy, free in any CMOS technology

density를 늘리기 위해, high level metal들을 많이 쓴다.
bottom plate parasitic이 존재하니, 사용시 주의해야 한다

Capacitor accuracy:
Capacitor parasitics, Edge effect, oxide gradient, voltage coefficient, temperature coefficient

Capacitor parasitics:
top plate와 substrate 사이 capacitance,
bottom plate와 substrate 사이 capacitance

이렇게 parasitic capacitance가 생기는데, bottom plate가 더 가까우니
bottom plate쪽 parasitic capacitance가 더 크다.

voltage:
capacitor는 전압이 바뀌면 depletion width가 바뀐다.
junction capacitance는 전압 영향을 크게 받고,
Poly-Poly, MIM capacitance는 전압 영향을 적게 받는다.







MOS Capacitor는 Capacitance 값이 정확하지 않다.
그래도 Control voltage를 조절해서 Capacitance 값을 조절할 수 있다.

같은 면적일 경우, MOS Capacitance > MOM > MIM




Junction Capacitor: Nonlinear Capacitance

MOSFET이 저항 역할을 하게 만들었던 것처럼,
MOSFET이 Capacitor 역할을 하게 만들 수도 있다.
이것을 MOS Capacitor라 부른다.

MOS Capacitor는 Gate Polysilicon과 channel 사이의 capacitance를 활용하는 구조다.
NMOS capacitor: Poly-N+ capacitor
PMOS capacitor: Poly-P+ capacitor

MOSFET을 Capacitor로 쓸 때에는 Strong inversion region에 두고 쓴다.
Channel이 생겨야 Capacitance가 생기기 때문이다.
그래서 MOS Capacitor는 전압이 낮으면 capacitance가 없다가, 전압이 올라가면 생긴다.


Varactor:


Physical Parameters:

resistivity[Ohm*cm]
Cu: 1.7*10^-6
Al: 2.7*10^-6
N-type Si: 0.25
SiO2: ~10^14