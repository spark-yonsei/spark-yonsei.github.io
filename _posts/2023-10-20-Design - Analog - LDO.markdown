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


사실 LDO에 캐패시터 달면 동작상으로는 좋다.
PSRR 좋아지고, stability 좋아지고, noise 사라진다.
근데 캐패시터 때문에 면적이 커진다는게 문제다.

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
LDO PSRR:<br>
LDO가 디지털 회로에 연결될 경우에는 PSRR이 조금 낮아도 동작에 문제가 없다.<br>
<br>
이때는 전압이 짧은 시간동안 튀는 상황을 조심해야 한다.<br>
그 짧은 시간동안 소자들에 stress가 가해지고, stress가 쌓이면 소자 동작에 문제가 생길 수 있다.<br>
그래서 튀는 전압을 최대한 줄여야 한다.<br>
<br>
LDO가 아날로그 회로에 연결될 경우에는 PSRR이 중요한데,<br>
고주파에서는 capacitance의 영향으로 loop gain이 부족해 PSRR이 낮아진다.<br>
<br>
LDO 설계시 속도 개선을 위해 feed forward path를 만들어 두는 경우가 있는데,<br>
고주파에서 loop gain을 떨어뜨리기 때문에 PSRR에는 방해가 된다.<br>
<br>
<br>
LDO와 미세공정:<br>
소자가 높은 전압을 버티기 위해서는 크기가 커야 하는데,<br>
공정이 발전해서 미세한 소자를 사용하면 높은 전압에 견딜 수가 없다.<br>
따라서, 공정이 미세화되면 회로에 쓰이는 전원 전압이 낮아져야 한다.<br>
<br>
LDO 입장에서는 입력 전압은 낮아지고, 출력 전압은 유지해야 하는 상황이다.<br>
이때는 Pass transistor의 W/L을 늘려야 한다.<br>
Pass transistor W/L이 늘어나면 load current가 늘어나고, 보상이 어려워지고, 설계가 어려워진다.<br>
그래서 LDO 설계자 입장에서는 사실 피하고 싶은 상황이다.<br>
<br>
<br>
그래서 설계자들은 다른 방법을 찾게 됐다.<br>
예를 들어 1.8V 소자밖에 없더라도, 이 소자들을 조합해 3.3V 전압을 버틸 수 있는 회로를 만든다면 높은 전원 전압을 쓸 수 있을 것이다.<br>
<br>
발견된 해결책은 1.8V 소자들을 stack으로 쌓고, 전류로 bias를 잡아주는 방식이었다.<br>
이렇게 하면 1.8V 소자들로 3.3V 전원 전압에서 동작하는 회로를 만들 수 있다.<br>
단점은, biasing을 위해 전류가 계속 흘러야 해서 전류 소모가 계속 일어난다는 점이다.<br>
<br>
현재 첨단 공정인 GAAFET 공정에서는 아예 아날로그 트랜지스터를 만드는 것이 어려워 모든 설계를 이 방식으로 해야 한다.<br>
그래서 stack에서 지속적으로 전류가 소모되는 점이 문제가 되고 있고, 이 부분은 아직 연구 대상이다.<br>
<br>
<br>
이 방식은 미세공정이 아니어도, 단순히 마스크 값을 아끼기 위해 사용되기도 한다.<br>
3.3V 소자를 만들기 위해서는 lithography 과정에서 마스크를 더 써야 한다.<br>
마스크 비용을 아끼기 위해, 3.3V 소자 대신 1.8V 소자 stack과 전류 bias로 회로를 구성할 수도 있는 것이다.<br>
<br>
물론 이 경우에는 3.3V 소자를 사용하는 경우보다 소비전류가 많은 회로가 제작된다.<br>

ESR 저항:




LDO Cout에 달린 ESR저항이 zero를 만들어 PM을 개선하는 역할을 하는데,
이걸로 부족할 경우에는 LDO 출력에 저항이 보이도록 하면 된다.
ESR과 비슷하게, zero compensation 역할을 한다.

Display driver는 ITO(Indium-Tin-Oxide)가 연결되기 때문에 저항 수옴정도가 보인다.
그래서 딱히 저항을 달지 않아도 compensation이 된다.

LDO 출력에서 PAD를 통해 전압 출력이 나갈때, PAD까지 가는 배선에 의해 저항이 생긴다.
내부 Logic 회로 power는 LDO 출력이 PAD까지 가는 배선 위 어딘가에 연결될텐데,
LDO 출력에 가까운 곳에 해야 배선 저항이 온전히 zero를 만드는데에 쓰인다.
LDO 출력에서 먼 곳, 아예 PAD쪽에 logic power 배선을 연결하면 배선 저항이 frequency compensation에 도움이 안된다.


저항을 이용해 zero를 만들어 PM을 개선할 수 있지만,
저항이 너무 크거나 전류가 많이 흐를때는 전압강하가 커서 문제가 생긴다.


PAD는 옛날에는 stack 구조를 많이 썼지만, 요즘은 Cup 구조를 많이 쓴다.
PAD는 넓은 도체 판을 올려놓은거라, 저항이 아주 작다.

Pad 위에 Bump를 올리고, RDL을 놓는다.
RDL은 두꺼운 도체라서 저항이 작고, Bump도 도체 덩어리라서 저항이 작다.
즉, LDO 출력에 달린 저항 생각할때는 내부 배선 저항만 생각하면 된다.


Digital LDO: Pass TR의 Vgs가 아닌 size를 조정한다.
Digital LDO를 쓰면 headroom을 크게 개선할 수 있지만, ripple 등 단점이 많다.
사실 아날로그 LDO가 더 낫긴 하다.

NMOS LDO: 더 낮은 Dropout voltage를 갖는다.
더 낮은 전압에서도 동작할 수 있으니 power efficient하다는거다.

LDO PSRR 개선 방식:

Pre-regulated supply: Cascode TR 구조, Passive LPF 등을 supply와 LDO 사이에 연결한다.
power가 LDO에 들어오기 전에 noise를 줄여서 집어넣자는건데,
추가 회로들이 LDO power TR과 직렬로 연결되니, Dropout voltage가 너무 높아질 수 있다.
dropout voltage가 너무 높으면? 구현 가능한 최대 power efficieny가 낮아진다.


FFRC(Feedforward Ripple Cancellation):
power-LDO출력 사이 feedforward path를 만들어서 supply noise 전달을 줄인다?
이 방법에서는 전류가 변하면 gain이 비례해서 변해야 하는데, 이걸 넓은 전류 범위에서 만들기 어렵다.

NMOS LDO는 PMOS LDO보다 Rout(1/gm)이 더 작아서,
load current가 변할때 overshoot/undershoot가 더 작다.

NMOS LDO는 pass TR gate 전압이 LDO 입력 전압을 넘는 상황이 발생할 수도 있다.
dropout voltage가 낮으니, 낮은 전압 입력을 받을 가능성이 높으니까.
그러지 않도록, supply voltage를 충분히 높게 걸어줘야 한다.



Logic에 연결되면, load가 항상 달려있는 상태가 된다.
Logic에서 leakage가 계속 새고 있으니까.



LDO Stability 보상 방식중에, ESR을 쓰는 방식들이 많이 소개되어 있다.
하지만 요즘은 그런 보상방식을 쓰지 않는다.
옛날에 탄탈륨 캐패시터 쓸때는 ESR이 좀 돼서 가능했는데,
요즘은 MLCC를 쓰기 때문에 ESR이 없다.

LDO를 연결하는 도체때문에 인덕턴스가 생길수도 있다.
입력이든 출력이든 인덕턴스가 생길 수 있는건데,
이 인덕턴스 때문에 bode plot이 특정 구간에서 튈 수도 있으니 잘 확인해줘야 한다.