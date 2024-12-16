---
layout: post
title:  "Analog - PLL"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

PLL : Phase Locked Loop<br>
<br>
<br>
PLL은 생성된 신호가 Reference signal에 'frequency and phase locked'되도록 만드는 negative feedback system이다.

PLL Applications:

Zero Delay buffer:
Main Clock이 subblock들에 전달되는데, 이때 block까지의 거리가 모두 제각각이라 도착하는 clock들의 phase도 제각각이다.
근데, data는 clock이랑 다른 경로로 들어오니까, 도착하면 clock과 data의 phase가 안맞는다. 즉, skew가 안맞는다.
이때 phase를 맞춰주기 위해 PLL을 쓸 수 있다.

Low-Jitter Sampling Clock:
PLL로 입력 clock의 low frequency jitter를 없앨 수 있다.
jitter를 없앤 clock을 sampling 등에 활용할 수 있다.

for N bit resolution,
Jitter < 1/(2^N pi f_in)

PLL은 대부분 CP-PLL 형태로 구현된다.
PFD, CP는 Digital phase error signal을 analog current로 바꾼다
Loop filter가 전류를 전압으로 바꾸고, 그 전압이 VCO에 들어간다.


PLL은 Clock 신호를 입력받아, 다른 주파수의 Clock 신호를 출력한다.<br>
Oscillator 회로로는 만들기 어려운 수백MHz, GHz 대역의 Clock 신호를 만드는 데에 쓰인다.<br>
고주파 Clock이 아니더라도, Clock의 Jitter를 없애기 위해 사용되기도 한다.<br>
<br>
<br>
PLL은 4개 회로를 기본으로 한다.
PD: Phase Detector
CP: Charge Pump
LF: Loop Filter
VCO: Voltage Controlled Oscillator


PD:
PLL은 출력 신호의 phase와 입력 신호의 phase를 비교하는 feedback system이다.
비교는 PLL 안의 phase detector에서 진행된다.
PD는 입력 Clock 신호와 출력 Clock 신호의 


LF:
PLL은 layout해놓으면 캐패시터가 엄청나게 커다랗다.
Loop filter에 엄청나게 커다란 캐패시터가 들어가기 때문이다.

passive filter: noise가 적고 PSRR이 좋다. 근데 lock acquisition range가 제한된다.
active filter: active element들에 의한 noise가 성능을 다 깎아먹는다. 대신 lock acquisition range를 늘릴 수 있다.


VCO:
free run에서 출력주파수 0이면 소비전류가 크다?
우리는 전류 아끼려고 free run에서 출력주파수가 0이 아니게 만들었다?
VCO는 온도가 올라가면 인버터 동작이 느려지고 소비전류가 떨어진다.


PLL Jitter:
Input Clock에 섞인 noise에 의한 Jitter
VCO 출력에 섞인 noise에 의한 Jitter

Input Clock에 noise가 없으면 넓은 Bandwidth,
noise가 상대적으로 많으면 좁은 Bandwidth로 LF를 만들면 된다.


Noise in PLL:
Reference clock noise,
PFD+CP noise(CP noise가 대부분)
Loop Filter 저항에 의한 noise
VCO phase noise
Divider Noise

phase noise에 루트씌우면 그게 [rad]로 jitter가 된다.

charge pump의 noise: NMOS, PMOS에 의한 noise

VCO에서는 edge transition이 많을수록 jitter가 많이 생긴다
한바퀴 안에 인버터 구조를 많이 만날수록 많이 생기는거다


Type: loop 내 integrator의 수
Order: loop 내 pole의 수

언제나 order > type,
언제나 PLL은 type 1 이상


요즘은 PLL에도 LDO가 들어간다.




Spur:
PD를 만들때, 2-state PD로 만들었을때와 XOR PD를 만들었을때 spur를 비교하려고 한다.
2-state PD는 입력 주파수의 홀수배에서 spur,
XOR PD는 입력 주파수의 홀수배 의 두배 주파수에서 spur

2-state PD가 더 낮은 주파수에도 spur를 만들고 있으니,
XOR PD가 더 나은 'ripple spur suppression'을 하고 있다고 할 수 있다.

RF PLL에서는 Spur 없애는게 가장 중요하다.





Phase Detector Range Extension:
Frequency divider를 통해 PD range를 넓힐 수 있다.

phase error가 정의되는건 원래 input에서,
phase error가 측정되는건 divided input에서기 때문이다.

예를 들어, 5ns delay면 