---
layout: post
title:  "Scaling"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---

scale돼서 크기가 작아진 CMOS공정, 즉 scaled CMOS공정은:

크기가 작으니 input capacitance는 작아진다.
그렇다고 크기 줄인다고 RF performance가 계속 좋아지는 것은 아닌 것이,

interconnect parasitic때문에 또 악화된다.
실제로는 45nm, 28nm CMOS 정도가 성능이 최대치를 갖는 지점이다.
이거보다 작으면 소자들이 parasitic gate capacitance, resistance에 크게 영향받는다.
그래서 RF performance가 안좋아진다.
그래서 RF에서는 더 줄이는게 의미가 없다.

Si결정 격자 간격이 0.545nm다.
그래서 채널 길이 5nm 아래부터는 전자가 다양한 경로로 움직인다.


4GHz의 벽:
반도체공정이 미세화되면서, CPU 내 트랜지스터 집적도가 올라가게 되었다.
그 결과, 트랜지스터 방열면적이 줄어들었다.

근데, 전력소모는 크기가 작아졌다고 해서 작아지는게 아니다!
즉, 공정이 미세화될수록 방열면적은 줄어드는데 전력소모는 그대로라서 열 방출이 어려워진다.

그리고, CPU가 발전할수록 clock 주파수와 소비 전력 모두 계속해서 올라갔다.
그래서, 이대로는 열 방출이 안돼서 CPU clock이 4GHz를 넘을 수 없다는게 4GHz의 벽이다.
그래도 2010년대 이후로는 4GHz 넘는 CPU들이 많이 나오고 있다.

TDP: Thermal Design Power
CPU나 GPU 스펙을 보면 TDP가 적혀있는데, TDP 값 이상의 열 방출이 가능한 냉각 수단을 같이 쓰라는 뜻이다. TDP의 단위는 [W]다.

CPU에 공급되는 전력의 총량을 Pdynamic이라 하면 *수식 설명

Dark Silicon:
이것도 공정 미세화 때문에 생기는 문제다.
CPU에 넣어줄 수 있는 전력에는 한계가 있는데, 트랜지스터가 너무 많아서 일부 트랜지스터는 전력을 공급받지 못하는 현상이다.
이렇게 전력을 공급받지 못하는 구역을 ‘Dark Silicon’이라 한다.

다양한 short channel effect들

메모리 칩이나 로직 칩은 L을 무조건 작게 만들려고 하지만, 아날로그 칩은 그렇지 암ㅎ다. 당연히 L이 줄어들면 면적이 줄어드니까 경제적이긴 하지만,<br>
1\. Mismatch, 1/f noise를 줄이려면 L을 늘려야 한다.<br>
2\. L<3~4um부터는 L이 조금만 변해도 Vth가 엄청나게 변한다. 즉, process variation이 심해져서 chip간 variation이 심해진다. 그래서 보통 L을 4um 이상 어딘가 variation 적은 곳에 둔다.<br>
이런 이유로, 아날로그 회로에서는 L을 무작정 줄이지 않는다.<br>


트랜지스터가 작아질수록 Vth가 줄어들고 signal swing도 작아져서, analog 회로에서는 충분한 SNR을 만들기가 어렵다.
대신, 트랜지스터 delay가 줄어들어 timing resolution(sampling rate)은 좋아졌다.