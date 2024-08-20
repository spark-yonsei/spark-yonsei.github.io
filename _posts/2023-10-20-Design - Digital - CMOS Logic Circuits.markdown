---
layout: post
title:  "Digital - CMOS Logic Circuits"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 5
---

옛날에는 Digital Logic을 하드웨어로 구현할때 BJT를 사용했지만,<br>
현대에 와서는 CMOS Transistor로 Digital Logic을 구현한다.<br>
CMOS transistor로 Digital Logic을 구현한 회로를 CMOS Logic 회로라고 부른다.<br>
<br>
<br>
CMOS Logic 회로에서는 MOSFET들의 Gate Capacitance가 Drain Current에 의해 충전/방전된다.<br>
Gate Capacitance의 충전/방전 여부로 1/0을 판단하게 된다.<br>
<br>
CMOS Logic 회로에 |Vth|가 작은 MOSFET을 쓴다면, 속도는 빠르지만 leakage current가 크다.<br>
전류가 많이 흘러 Gate Capacitance를 빠르게 충전/방전할 수 있지만, 꺼진 상태에서도 전류가 많이 새기 때문이다.<br>
반대로 |Vth|가 큰 MOSFET을 쓴다면, 속도는 느리지만 leakage current가 적은 회로가 된다.<br>
그래서 요구사항에 적합한 Vth를 갖는 트랜지스터를 사용하는 것이 중요하다.<br>
<br>
<br>
Logic 회로는 트랜지스터의 on/off characteristic을 이용해 만든거라,<br>
트랜지스터가 작아지든 새로운 물질로 만들어지든 on/off만 잘 되면 그대로 잘 동작한다.<br>
그래서 Moore's law에 의해 트랜지스터가 작아지면 그게 성능 증가와 직결됐다.<br>
트랜지스터가 작아져서 IC에 더 많은 트랜지스터를 넣을 수 있으면, 더 많은 연산을 할 수 있기 때문이다.<br>
<br>
더 작은 트랜지스터를 활용해 IC 하나에 더 많은 logic block들을 넣다보니 새로운 문제들이 발생하게 됐다.<br>
Delay 관련 문제와 Power 관련 문제다.<br>
<br>
<br>
Delay 관련 문제:<br>
Logic 회로에서 수행해야 하는 function이 복잡해지면서,
function 하나를 여러 block들로 쪼개고 


Sequential machine은 moore-type 또는 mealy-type state machine으로 구현되며, state-transition diagram으로 표현된다.
state transition은 보통 clock에 맞춰 발생한다.

Large-scale function을 combinational logic으로 만들어야 할 때가 있다.
이런 경우, 보통 function을 여러개 block으로 쪼개고 flipflop이나 latch같은 memory component들을 집어넣는다.

이 memory component들은 하나의 clock에 의해 모두 동작한다.
나눠진 block들이 모두 synchronous하게 동작하도록 하기 위해서다.

이렇게 쪼개고 memory component들을 집어넣으면, temporal parallelsim을 만들어 pipeline같은 성능 개선을 구현할 수 있다.

요즘 나오는 digital circuit들은 synchronous manner로 동작하게 되어 있다.
결국 clock based라는 거다.


IC 내에서 
flipflop은 data가 제때 도착하지 않으면 출력에 그 data를 반영하지 못한다. clock에 맞춰 동작하니까.
그래서, data가 clock보다 느리게 도착하면 전체 회로가 원래 설계와는 다르게 동작할 수 있다.
그러면 이 느린 data를 위해 clock을 느리게 바꿔줘야 하나? 그러면 또 전체 회로가 느려진다.

커다란 회로들에서는 flipflop들 사이의 delay, clock-skew 등이 문제를 만든다.
clock-skew는 clock 신호의 시간 차이를 말한다.

flipflop들 사이의 delay든 clock-skew든, 원인은 wiring delay다.
그래서 PnR할때 clock-skew에 신경써줘야 한다.

clock-skew를 줄이기 위해 'clock trees'라는 buffer tree들을 쓰기도 한다.
이걸로 clock branch들에 동일한 수의 flipflop들이 연결되어 있도록 한다.

equal-length wiring을 통해 wiring delay time이 모두 똑같도록 만들긴 하지만,
local supply voltage bounce나 local hot spot같은 문제로 delay가 변할 수 있다.

그래서 power consumption을 계산해 어디서 얼마나 supply voltage bounce가 발생할지 예측해야 하고,
온도 분포 또한 worst case까지 고려해서 timing verification을 해야 한다.







Power 관련 문제:

요즘 digital system들은 3D stacking, chiplet같은 상황에서 power consumption을 어떻게 줄여야 할지를 생각해야 한다.

Large-scale digital circuit들에서는 power consumption 줄이는게 아주 중요하다.
보통 flipflop과 clock distribution network가 소비하는 power의 비중이 크다.
그래서, data가 안바뀔때는 power 아끼기 위해 clock을 꺼버리는 clock-gating이라는 방법이 있다.
또는, 안쓰는 block은 꺼두는 것으로 dynamic power를 아낄 수 있다. 이건 power gating

근데, 이렇게 껐다 켜더라도 memory가 보존되어야 하는 block들이 있다.
이 경우에는 끄기 전에 어디 다른 곳에 미리 저장해두거나,
메모리에만 최소한의 전압을 걸어두거나,
껐다 켜도 데이터가 유지되는 nonvolatile memory를 써야 한다.

DVFS: Dynamic Voltage and Frequency Scaling
DVFS로 clock frequency, power supply voltage를 내려서 power consumption을 내릴 수 있다.

이거랑 조금 다른 이야기일 수는 있는데, CPU가 과열될 경우 clock, voltage를 강제로 내려서 발열 줄이는게 CPU throttling이다.
clock gating: 안쓰는 block은 clock마저 안들어가게 꺼버리는거. power 아끼려고 쓰는 기술이다.



Verification:
근데, 트랜지스터가 작아져서 커다란 digital system들이 한 IC에 들어가게 되자,
모든 process corner에서 chip이 잘 동작하도록 하는 design verification이 복잡해졌다.

























