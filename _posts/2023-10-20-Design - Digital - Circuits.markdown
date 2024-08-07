---
layout: post
title:  "Digital - Circuits"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 5
---


RTL: Register Transfer Language
DTL: Diode-Transistor Logic
TTL: Transistor-Transistor Logic

RTL은 1961년에 fairchild에서 출시됐다.
RTL의 input parallel register들에서 발생할 수 있는 short current를 방지하기 위해 parallel diode들을 쓴게 DTL이고,
그걸 다시 BJT로 대체한게 TTL이다.

처음에는 PMOS, 그 다음에는 NMOS processor들이 따로 출시됐는데,
1975년에 CMOS processor가 나온 뒤로는 모두 CMOS로 processor를 만들게 됐다.

Digital 회로가 CMOS로 구현될 경우, gate capacitance가 drain current에 의해 충전됐다가 방전됐다가 한다.
gate capacitance의 충전/방전에 의해 보이는 high/low 전압으로 1 또는 0 정보를 표현하게 되고,
high와 low를 구분하는 전압 기준을 'logical threshold'라고 부른다.

그리고 logical threshold와 high/low voltage의 차이를 'noise margin'이라 부른다.
보통 digital 회로들에서 noise margin은 충분히 크기 때문에,
supply voltage bounce같은 환경 변화에 크게 신경 안써도 된다.
analog에서는 신경 많이 써야 한다.

digital 회로는 트랜지스터의 on/off characteristic을 이용해 만든거라,
트랜지스터가 작아지든 새로운 물질로 만들어지든 on/off만 잘 되면 그대로 잘 동작한다.
그래서 Moore's law에 의해 트랜지스터가 작아지면 그게 성능 증가랑 직결됐다.

근데, 트랜지스터가 작아져서 커다란 digital system들이 한 IC에 들어가게 되자,
모든 corner에서 chip이 잘 동작하도록 하는 design verification이 복잡해졌다.

요즘 digital system들은 3D stacking, chiplet같은 상황에서 power consumption을 어떻게 줄여야 할지를 생각해야 한다.

Digital Circuit은 combinational circuit들과 sequential machine들로 이루어진다.

combinational circuit은 memory 없이, logic expression으로만 표현된다.
뭐 f(a,b,c) = \bar{a}bc + a\bar{b}c 이런 식이다.

Sequential machine은 moore-type 또는 mealy-type state machine으로 구현되며, state-transition diagram으로 표현된다.
state transition은 보통 clock에 맞춰 발생한다.

Large-scale function을 combinational logic으로 만들어야 할 때가 있다.
이런 경우, 보통 function을 여러개 block으로 쪼개고 flipflop이나 latch같은 memory component들을 집어넣는다.

이 memory component들은 하나의 clock에 의해 모두 동작한다.
나눠진 block들이 모두 synchronous하게 동작하도록 하기 위해서다.

이렇게 쪼개고 memory component들을 집어넣으면, temporal parallelsim을 만들어 pipeline같은 성능 개선을 구현할 수 있다.

요즘 나오는 digital circuit들은 synchronous manner로 동작하게 되어 있다.
결국 clock based라는 거다.

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

Time-Domain Signal Processing:
트랜지스터가 작아질수록 Vth가 줄어들고 signal swing도 작아져서, analog 회로에서는 충분한 SNR을 만들기가 어렵다.
대신, 트랜지스터 delay가 줄어들어 timing resolution(sampling rate)은 좋아졌다.

TDC: time-to-digital converter
Timing resolution이 개선돼서 time-domain signal circuit들이 많이 연구되기 시작했다는데,
time-domain signal circuit이 뭔지는 안나와있다.

ADC는 analog voltage signal을 digital 신호로 바꾸는건데,
TDC는 timing information을 digital information으로 바꾼다.

TDC는 PLL, CDR(Clock Data Recovery)회로 등 high-speed signal processing이 필요한 곳에 쓰인다.

time-domain signal processing은 CAM(Context Accessible Memory)에서도 exact data matching, nearest neighbor detection process에 쓰이고,
최근에는 CIM(Compute in Memory)의 Add operation에도 쓰인다.

AES: Advanced Encryption Standard, 암호화 방법

참고자료:
Reflections on Progress in Digital Circuits, Makoto Ikeda

Logic cell에 쓰이는 라이브러리들:<br>
RVT: Regular Voltage Threshold<br>
HVT: High Voltage Threshold<br>
LVT: Low Voltage Threshold<br>
SLVT: Super Lowe Voltage Threshold<br>
<br>
Threshold가 높으면 속도가 느리지만 leakage가 적고,<br>
Threshold가 낮으면 속도가 빠르지만 leakage가 많다.<br>
<br>
그래서 어디는 HVT, 어디는 LVT로 만들어 최적화할 수 있을 것이다.<br>
<br>
그런걸 ‘Multi Threshold Voltage Design’이라 부른다.<br>


LDO에서 전압이 짧게라도 튀면, 그 짧은 시간동안 device에 stress가 들어간다.
그래서 튀는 전압은 최대한 줄이는게 좋다.

MA: Direct Memory Access
CPU를 통하지 않고도 메모리에 접근할 수 있게 하는 기능.
이게 있으면, 다른 block이 memory에 접근해야 할때 CPU는 데이터 전송하라고만 해놓고
다른거 하다가 DMAC(DMA Controller)한테 interrupt 신호 받으면 아 전송 다 끝났구나 한다.

WDT: Watchdog Timer
비정상 상태, 무한루프 등 이상한 상태에 빠지면 System을 리셋하는 장치

ECC Memory: Error Correction Code Memory
데이터 손상을 복구하는 메모리.
우주선 중성자 방사능 때문에 cell에 저장된 정보가 바뀔 수 있어 필요하다.
이런 에러는 고도가 증가하면 엄청나게 늘어난다.
ECC Memory가 정보를 복구하는 알고리즘을 ECC logic이라 부른다.

SCU: System Controller Unit
각 peripheral들이 clock, memory 등 resource를 사용할때, 그걸 관리해준다.
SCFW(System Controller Firmware)에 의해 동작한다.
그래서 온갖 subsystem들을 SCU에서 관리한다.

PMU: Power Management Unit

RTC: Real Time Clock
그냥 시간 재는 회로다.

Boot sequence:
Power on -> POR/BOR 동작 ->
HIS OSC켜짐 -> PLL 켜짐 -> PLL Lock까지 대기 -> flash clock 켜짐 ->(Always on Block들)
flash에서 analog block 읽기(Flash Controller)
-> AHB prescaler, APB prescaler, Timer prescaler, clock gating 켜짐(clock generatro)