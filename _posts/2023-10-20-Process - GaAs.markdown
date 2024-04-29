---
layout: post
title:  "GaAs"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---


GaAs HBT는 90년대 말부터 Cellular Power Amplifier들에 쓰이기 시작했다.
GaAs 산업 자체가 핸드폰과 함께 많이 발전했다.


처음에는 commercial wireless communication에 MESFET이 쓰였다.

MESFET을 만들 때에는, 일단 implant를 하든 epitaxially grow를 하든 해서 n-type GaAs channel을 먼저 만든다.
이 n-type GaAs channel에 Schottky gate를 만들어서 MESFET을 만든다.

GaAs MESFET은 Si MOSFET과 비슷한 구조를 갖는다.
웨이퍼 표면을 통해 Source와 Drain 사이에 전류가 흐른다.
구조상 전류는 가로로 흐른다.

HBT는 Emitter와 Collector 사이에 전류가 흐르는데, 구조상 전류가 세로로 흐른다.
그래서 higher power density가 가능하다고 한다.

HBT는 MESFET에 비해 더 낮은 saturation voltage를 갖는다.
게다가 bias, 온도가 변해도 linear해서 better linear performance를 갖는다.
그래서 많이 쓰이게 되었다.


GSM, EDGE에서는 Power Amplifier가 Saturated mode에서 동작해야 한다.
그래서 ruggedness, efficiency, gain 개선이 필요하다.

CDMA, WCDMA에서는 Power Amplifier가 linear mode에서 동작해야 한다.
그래서 linearity, efficiency 개선이 필요하다.

어느 쪽이든, RF performance와 ruggedness/breakdown voltage 사이의 best tradeoff를 달성하기 위해 emitter layer와 collector layer에 집중했다.

높은 bias 또는 mismatch 상황에서 not-rugged device들이 발생할 수 있다.
이 경우 device들은 회복하지 못한다.


미래 시스템들은 power amplifier를 하나만 요구한다.
즉, HBT가 2가지 mode에서 모두 동작해야 한다.

요즘은 ruggedness를 한계까지 끌어올릴 필요는 없지만,
efficiency와 linearity는 언제나 높을수록 좋다.


HBT가 많이 쓰이게 된 뒤, HBT와 FET, pHEMT를 한번에 integrate하는 BiFET 공정이 연구되기 시작했다.

Si 기술의 RF application에서 쓰이는 through-substrate via는 GaAs HBT에서는 처음부터 쓰였다.


1세대 BiFET integration:
HBT layer를 활용해서 FET을 만들었다. 그래서 비용이 더 들지는 않았다.
근데 FET 성능이 좀 애매했다.

2세대 BiFET integration:
추가 epi layer들과 process들을 감수하고, high performance FET (pHEMT)를 넣는다.
이 pHEMT 덕분에 high-performance RF switching 구조나 low noise amplifier, high power antenna switch branch를 만들 수 있다.

이런 공정 발전으로, Power amplifier의 linearity, efficiency가 개선될 수 있었다.

HBT는 Passive device로는 MIMCAP, thin film resistor 쓴다.


가격 절감:
비싼 금속을 덜 써야 하고, die 면적을 줄여 한 웨이퍼당 생산되는 die수를 늘려야 한다.

GaAs process들은 contact, wiring에 금을 쓰고 있다.

GaAs MMIC는 gold based contact, wiring 뿐 아니라 through-substrate via와 함께 back side metal에도 gold를 쓴다.
backside metal을 구리나 은으로 대체하면 가격이 절감될거다.

근데, frontside metal은 backside보다 훨씬 복잡하다. 배선이 있으니까.
그래서 금 말고 다른걸로 대체할때는 reliability를 잘 따져줘야 한다.

frontside에는:
gold-based ohmics(HBT emitter, base, collector and FET source, drain),
Schottky contacts(diode, pHEMT gate),
multiple wiring layers
가 있다.

이 중에서 금을 가장 많이 쓰는건 wiring이다.
그래서 이걸 Al, Cu, AlCu 등으로 대체하려는 연구를 하고 있다.


금, 백금을 없애야 싸지는데 이게 쉽지가 않다.
ohmic contact를 손대기 시작하면 risk가 늘어난다.


Die Size:
더 큰 HBT를 쓰면 cell이 더 적게 필요하다. -> footprint가 줄어든다.
challenges: self-heating, proximity heating에 의한 junction temp 증가,
늘어난 parasitic에 의한 performance degradation

Bond pad는 die에서 상당한 면적을 차지한다.
근데 bond pad 면적을 줄이면 wire bond probe 하기가 어려워져서,
wafer level die test가 어려워진다.

-> test capability가 발전하면서, bond pad가 더 작아질 수 있었다.

capacitor가 bond pad 다음으로 면적을 많이 먹는다.
더 얇은 dielectric들이 나오면서 MIM, Stacked capacitor의 밀도가 올라갔다.

면적 아끼려고 bond pad 밑에 capacitor를 넣기 시작했는데,
이때는 yield, reliability에 신경써줘야 한다.

capacitor 말고 다른것들도 bond pad 밑에 넣으려고 하고 있다. 면적 더 줄일 수 있으니까.