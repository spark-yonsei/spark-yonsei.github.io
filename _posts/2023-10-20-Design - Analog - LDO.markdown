---
layout: post
title:  "Analog - LDO"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

LDO : Low Dropout Regulator<br>
<br>
<br>
회로가 제대로 동작하기 위해, 일정한 전압 입력이 필요한 경우가 많다.<br>
Op Amp input, MOSFET의 Gate 등은 전류를 소비하지 않기에 BGR(Bandgap Reference) 회로로 전압을 주면 된다.<br>
하지만 저항, logic cell 등 전류를 크게 소비하는 회로에 일정한 전압을 제공하기 위해서는 LDO 회로를 써야 한다.<br>
<br>
<br>
기본적인 LDO는 Op Amp, BGR, Feedback, Pass Transistor로 구성된다.<br>
<br>
Op Amp의 입력에는 BGR 전압, Feedback 전압이 들어온다.<br>
Op Amp의 출력에는 Pass Transistor의 Gate가 연결되어 있다.<br>
<br>
Pass Transistor는 출력 전류를 내보내는 역할을 한다.<br>
큰 전류를 내보내야 하기에 W/L이 큰 Transistor를 써야 한다.<br>
<br>
PMOS를 Pass Transistor로 쓰면 Common Source 구조가 되고,<br>
NMOS를 Pass Transistor로 쓰면 Source Follower 구조가 된다.<br>
<br>
<br>
Feedback 구조를 사용하는 이상, Frequency Compensation에 신경써야 한다.<br>
LDO의 Dominant Pole은 출력 node에서 만들어진다.<br>
<br>
$$p_0 = \dfrac{1}{R_{out}C_{load}}$$<br>
$$R_{out}=R_{load}||(R_{F_1}+R_{F_2})||1/gm$$<br>
<br>
Dominant pole 식에서 확인할 점은 2가지다.<br>
<br>
먼저 LDO 출력 전류를 늘리려고 Pass Transistor W/L를 무작정 늘리면,<br>
C_load가 지나치게 증가해 dominant pole이 저주파로 이동한다.<br>
따라서, feedback loop stability를 위해 W/L은 적절한 값으로 설정해줘야 한다.<br>
<br>
또한, gm이 증가하면 R_out이 감소함을 확인할 수 있다.<br>
따라서 Pass Transistor에 큰 전류가 흘러 gm이 증가하면, R_out이 감소해 dominant pole이 고주파로 이동한다.<br>
<br>
Feedback loop는 dominant pole이 고주파에 위치할수록 안정하다.<br>
LDO는 전류를 출력하면 feedback loop가 더 안정해지는 것이다.<br>
feedback loop가 더 안정해졌음은 phase margin 증가로 확인 가능하다.<br>
<br>
<br>
NMOS LDO의 장점:<br>
PMOS보다 NMOS의 $$\mu$$가 크기 때문에, gm이 크고 Rout이 작다.<br>
따라서 dominant pole이 상대적으로 더 높은 주파수에 있다.<br>
<br>
NMOS LDO의 단점:<br>
NMOS에 큰 Vgs를 확보해야 한다.<br>
큰 Vgs에 의해 LDO의 출력 전압이 제한된다.<br>
<br>
<br>
PMOS LDO의 장점:<br>
Source가 전원에 연결되어 있기 때문에,<br>
Vgs가 LDO 출력 전압에 영향을 주지 않는다.<br>
그래서 Low-Voltage Operation에서 쓰인다.<br>
<br>
PMOS LDO의 단점:<br>
NMOS보다 $$\mu$$가 작기 때문에, gm이 작고 Rout이 크다.<br>
따라서 dominant pole이 상대적으로 더 낮은 주파수에 있다.<br>
<br>
<br>
LDO 출력 node에는 Capacitor가 달려있는 경우가 많다.<br>
LDO 출력 전압이 살짝 흔들리더라도, 전하를 저장해둔 Capacitor가 일정한 전압을 유지해주기 때문이다.<br>
이 목적을 위해서는, LDO 출력에 있는 Capacitance가 클수록 좋다.<br>
<br>
그러나 LDO 내 feedback loop의 stability만 생각한다면,<br>
LDO 출력 node에 아예 Capacitance가 없는 편이 좋을 것이다.<br>
1/RoutCout인 dominant pole을 매우 높은 주파수로 보내기 위함이다.<br>
<br>
<br>
출력 node에 Capacitor를 달아놓지 않은 LDO를 Capless LDO라 부른다.<br>
<br>
Capless LDO의 장점:<br>
Feedback Loop가 Stable하다(Phase Margin이 크다).<br>
제조시 Capacitor 값을 아낄 수 있다.<br>
<br>
Capless LDO의 단점:<br>
출력 전압이 비교적 쉽게 흔들린다.<br>
따라서 설계에 주의를 요한다.<br>
<br>
<br>
LDO는 출력 node에 큰 전류가 흘러야 하는 경우에 쓰인다.<br>
따라서 전류가 흐르는 경로에도 신경을 써야 한다.<br>
<br>
먼저, Layout시 출력 node를 두꺼운 metal로 만들어야 한다.<br>
저항을 최소화해서, 큰 전류에 의한 전압 강하를 줄이기 위함이다.<br>
Metal은 저항이 가장 작은 top metal을 쓰는 것이 좋다.<br>
<br>
또한 출력 전압이 외부 회로에 전달되는 경로가 최대한 짧도록, IC 내 LDO 배치에 신경써야 한다.<br>
경로 최소화를 위해 IC 1개 안에 LDO 2개를 넣는 경우도 있는데,<br>
이때는 두 LDO 사이의 미세한 출력전압 차이가 문제가 되지 않도록 설계해야 한다.<br>
<br>
<br>
LDO에서 전압이 짧게라도 튀면, 그 짧은 시간동안 device에 stress가 들어간다.
그래서 튀는 전압은 최대한 줄이는게 좋다.

