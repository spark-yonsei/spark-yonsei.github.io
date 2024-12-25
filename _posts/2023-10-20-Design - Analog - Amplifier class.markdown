---
layout: post
title:  "Analog - Amplifier Class"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Amplifier는 동작 방식에 따라 'class'로 구분된다.<br>
<br>
Amplifier는 동작 방식에 따라 효율이 결정되는데,<br>
효율이 높은 amplifier는 linearity가 낮고,<br>
효율이 낮은 amplifier는 linearity가 높다는 특징이 있다.<br>
즉, amplifier의 class를 확인하면 동작 방식, 효율, linearity를 파악할 수 있다.<br>
<br>
<br>
Class A, B, AB, C:<br>
Output Stage 트랜지스터들이 gain을 만든다.<br>
Output Stage 트랜지스터들이 효율을 위해 잠시 꺼졌다 켜지기도 한다.<br>
효율이 낮지만 linearity가 높다.<br>
<br>
Class D, E, F, G, S, T:<br>
Gain이 전원 전압에 비례한다.<br>
Output stage TR들이 완전히 껐다 켜지며 PWM(Pulse Width Modulation) 동작을 한다.<br>
효율이 높지만 linearity가 낮다.<br>
<br>
<br>
Class A amplifier:<br>
Class A amplifier는 Output 트랜지스터 하나가 항상 켜져있는 구조다.<br>
트랜지스터가 계속 켜진 상태로 gain을 만들기 때문에, gain이 크고 linearity가 높다.<br>
대신, 항상 켜져있기 때문에 전류 소비도 계속 일어나 전력 효율이 나쁘다.<br>
<br>
그래서 high-fidelity audio amplifier 등 고성능 amplifier가 필요한 곳에 쓰이지만,<br>
효율이 나쁜 만큼 발열이 심해 고전력 회로에서는 사용하기 어렵다.<br>
<br>
<br>
Class B amplifier:<br>
Class B amplifier는 Output 트랜지스터 2개가 번갈아 켜지는 구조다.<br>
input signal이 positive일 때는 위쪽 트랜지스터만, negative일 때는 아래쪽 트랜지스터만 켜지는 구조다.<br>
이런 구조를 push-pull 구조라고 부른다.<br>
<br>


class A amplifier보다는 효율이 높은 구조지만, 새로운 문제가 또 생긴다.


입력 전압이 -0.7V~0.7V동안은 위아래 트랜지스터가 둘 다 꺼져서 출력이 안나온다.

이거때문에 zero-crossing distortion(Crossover distortion이라고도 한다)이 생겨서,
class B amplifier는 audio amplifier같은 곳에 못쓴다.





Class AB amplifier:
이름에서 보이듯, Class A랑 Class B를 합친 구조다.
audio power amplifier design에서 많이 쓰이는 구조다.

class B를 조금 변형한 구조인데, crossover point에서 두 트랜지스터가 꺼지지 않고 켜져있는 구조다.

여기 들어가는 트랜지스터들은 걸려있는 bias voltage가 아주 작다. cutoff point보다 아주 조금 높은 전압이다.
이렇게 되면 트랜지스터가 조금 더 오래 켜져있다. half cycle보다 조금 더 길게 켜져있다.

Class B는 half cycle보다 짧게, Class A는 항상 켜져있으니 그 사이에 있다는 의미로 class AB라 한다.
하여간, half cycle보다 길게 켜져있기에, crossover distortion이 일어나지 않는다.
efficiency는 50~60% 정도다.

Class C amplifier:
Class C amplifer는 효율이 꽤 높지만, linearity가 많이 떨어진다.
Class A, AB, B는 linear amplifier로 분류되지만, C는 그렇지 못한다.

Class C amplifier는 절반도 훨씬 안되게, 90도 정도만 켜진다.
그래서 효율은 80%정도 되긴 하는데, 엄청난 distortion이 생긴다.
Sine wave가 들어오면 머리만 참수해서 내보내는 수준이니까.

그래서, class C amplifier는 high frequency sine wave oscillator나 RF amplifier에 쓰인다.
고주파에서는 amplifier에 의해 발생한 current가 LC resonance circuit에 의해 특정 주파수의 sine wave로 바뀔 수 있기 때문이다.

class D~T는 switching operation을 한디.





Power Amplifiers(PA):

Transmitter의 마지막 stage가 PA다.
PA는 온갖 무선 시스템에 쓰인다.

PA design은 active circuit, passive network design으로 나뉜다.

active circuit: device performance에 대한 설계
Device gain, efficiency, linearity
Operation modes, classes
harmonics, waveform shaping
stability and reliability

passive network: impedance matching에 대한 설계
impedance transformation
power combining
harmonics, waveform shaping
bandwidth and filtering


PA performance metrics:

PA power gain: Gp=Pout/Pin

PA Drain Efficiency: DE 또는 eta = Pout/P_DC

Power Added Efficiency: PAE = (Pout - Pin)/P_DC


PA Efficiency Fundamental Limit:
PAPAE = eta_Device * eta_PAmode * eta_PAgain * eta_OutputLoss * eta_ThermalAging

eta_Device:
Device intrinsic eta.
Knee voltage, ~(1-Vknee/VDD)
Large signal output impedance ~Zout/(Zout+ZL)

eta_PAmode:
PA Classes and Harmonic
Shaping and termination
이게 PA Engineer들이 'Waveform Engineer'라고 불리는 이유다.

eta_PAgain
Input, Output loading을 고려한 Device gain
= (1-1/Gp)

eta_OutputLoss
PA output network
Loss = Pout/P_PA
Differential Load Balancing

eta_ThermalAging
device aging, reliability


Typical RF and mm-wave PA Power Levels:

PA의 output power, Pout을 제한하는 요소는 Regulation과 Link Budget이다.
-> Friis Transmission Equation?

Output power:
LTE: 23dBm, 26dBm

WLAN: 20~26dBm

NB IoT: 14dBm, 20dBm, 23dBm

Bluetooth:
Class 1: 20dBm,
Class 2: 4dBm,
Class 3: 0dBm,
Class 4: -3dBm

PA의 Pout은 Array 크기와 연관이 깊다.
작은 array는 높은 Pout을,
큰 array는 낮은 Pout을 보여준다.

EIRP? 무슨 Radiated Power

PA 설계시,
저주파에서는 가능한 power(Psat) 상방이 application, regulation에 의해 정해진다.
주파수가 올라가면, 상방이 device limitation에 의해 막힌다. -> Johnson limit

x축을 주파수, y축을 Psat으로 했을때, Johnson limit는 -20dB/dec 직선으로 나온다.
Johnson limit는 system level design에서 유용하다. 주어진 주파수에서 얻어낼 수 있는 power를 알려준다.

어쨌든, 높은 주파수에서는 큰 Power를 전달하기 어렵다는걸 보여준다.

위에서는 주파수와 Psat에 대한 이야기였고,
여기서는 Pout과 Efficiency에 대한 이야기를 하려고 한다.

