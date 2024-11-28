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
Resistivity가 높은 박막으로 저항을 구현한다.<br>
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

resistivity[Ohm*cm]
Cu: 1.7*10^-6
Al: 2.7*10^-6
N-type Si: 0.25
SiO2: ~10^14



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


Capacitor:

Capacitor를 IC 안에 집어넣을때는:
Parallel capacitor(Linear)
Junction capacitor(Nonlinear) 이렇게 2가지 구조 중 하나를 쓴다.

Poly 2장 사이에 oxide를 끼워서 만들면 Poly-Poly Capacitor
Metal 2장 사이에 oxide를 끼워서 만들면 Metal-Metal Capacitor

metal을 쓰면 더 linear해지지만 capacitance 밀도는 떨어진다.

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

MOS Capacitor:
Poly-N+ capacitor: NMOS capacitor
Poly-P+ capacitor: PMOS capacitor

Capacitor로 쓸 때는 strong inversion region에 두고 쓴다.
capacitance density가 높다.

capacitance가 생기려면 밑에 channel이 생겨야 해서 그렇다.
그래서 전압이 낮으면 capacitance가 없다가 전압이 올라가면 생긴다.



MIM capacitors: similar to plate capacitors, the capacitance value is more accurate, and the capacitance value does not change with the bias voltage. Generally, mTOP l & mTOP -1 are used in the manufacturing process. The capacitance value can be estimated by the upper board area * unit capacitance value. The upper and lower plate connections are not interchangeable, and are generally used in analog and RF processes.

MOM capacitor: Interdigital capacitor, which uses C between the edges of the same layer of metal. In order to save the area, multiple layers of metal can be stacked, and the number of metal layers in PDK can be selected.

MOM capacitors are generally only used in advanced manufacturing processes of multilayer metals. Because it is realized through the layout of multilayer wiring, the determinism and stability of the capacitance value obtained are not as good as MIM. Generally, it may be used in applications that do not require high capacitance values.

MOS capacitor: MOS transistor with two ends structure, the capacitance value is not accurate. It can realize the capacitance value that changes with the change of the control voltage, and the connection of the upper and lower plates is not interchangeable.

Comparison of the capacitance values of three capacitors with the same area: MIM<MOM, MIM is about 1/3 MOS capacitance value.

The advantage of the MOM capacitor is that no additional mask is required, and MIM requires an additional mask and process to be realized.