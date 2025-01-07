---
layout: post
title:  "Analog - Noise"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

IC 내 회로에는 다양한 이유로 noise가 발생한다.

주변 구조에 의한 noise:
Power supply noise
substrate coupling noise
EMI(Electromagnetic Interference)
Crosstalk

해결 방법:
differential circuit,
Guard ring, shielding 등 layout

소자에 의한 noise:
Thermal noise - 열에 의해 에너지를 받은 carrier들의 random한 움직임
Flicker noise - material defect
RTS noise - material defect
shot noise - semiconductor junction의 carrier들이 만드는 pulse

해결 방법:
적절한 회로 구조
더 많은 power



7번 data summation을 하는데, 매번 8code noise가 있다면:
summation한 data의 noise는 8sqrt7 = 21code. 8 7개를 rms한거다.
모두 양수였으면 그냥 평균냈겠지만, 음수 양수 섞이면 rms해야 한다.

물론, 각 noise에 correlation이 없다는걸 가정했기에 rms로 구한거다.

White noise 줄이려면 크기랑 전력이 필요하다. 그래서 크기 키우고 전류 높이면 white noise가 줄어든다.<br>


Kickback noise:<br>
Kickback noise는 Latch에서 발생하는 noise다. Latched comparator는 latch 구조를 포함하는 comparator인데, positive feedback 구조라서 analog signal을 digital signal로 바꾼다.<br>
<br>
예를 들어, input이 Vref보다 아주 조금 커도 그 차이가 positive feedback에 의해 증폭돼서 출력이 VDD가 되고, input이 Vref보다 아주 조금 작아도 Output은 VSS가 된다. Positive feedback은 차이가 커지는 방향으로 작용하기 때문이다.<br>
<br>
이 positive feedback 때문에, input 전압은 조금만 변해도 output 전압은 크게 변할 수 있다. 이 경우 latch 안 노드들의 dv/dt가 상당히 크다. 이 커다란 dv/dt가 parasitic capacitance에 Cdv/dt만큼 전류가 흐르게 만든다.<br>
<br>
Input 전압을 인가해주는 회로의 Rout이 0이라면 전류가 흘러들어와도 input 전압에 영향이 있지 않았겠지만, Rout이 0이 아니면 이 전류에 의해 input 전압이 달라진다. 이 현상이 kickback noise다.<br>
빠르고 전력 효율이 좋은 comparator일수록 kickback noise가 크게 생긴다.<br>
<br>
Kickback noise 해결방법:<br>
1\. Preamplifier를 comparator 앞에 붙인다.<br>
근데 이러면 preamplifier가 power를 먹어 전력효율이 떨어진다.<br>
2\. Differential pair의 drain들에 스위치를 달고, latch 전압이 바뀌는 동안 스위치를 열어서 전압 변화가 캐패시턴스에 전달 안되게 한다<br>.
이때는 스위치 열면 IDS=0이 되어 MOSFET들이 Triode region에 처박힌다. 그리고 Drain 전압이 어디에도 연결되지 않아서 맘대로 날뛸 수 있다.<br>
3\. Differential Pair의 gate들에 스위치를 달아서 input을 sampling해 넣ㄴ느다. 이러면 input에 의한 dV/dt가 전류를 만들 때 스위치가 열려있어 영향이 없다.<br>
하지만 스위치 닫히는게 어차피 input에 영향을 준다.<br>
<br>
몇가지 방법이 더 있다고는 하는데, 일단 kickback noise가 뭔지는 확인했으니 다음에 더 알아보자. 내용출처는 ‘Kickback noise reduction techniques for CMOS latched comparators’<br>

Layout때문에 kickback noise가 발생하는 경우도 있다.
이럴땐 Parasitic Capacitance 안생기게 주변을 다 치워버려야 한다.




noise는 플러스마이너스 모두로 움직이니까, 제곱으로 표현한다
noise의 spectral density는 단위가 [V^2/Hz]다


회로의 BW가 너무 넓으면, noise가 너무 많이 들어와서 SNR이 안좋아진다.

저항의 thermal noise:
진짜 저항에서도 발생하고, BJT parasitic resistance, MOSFET channel resistance 등에서도 발생한다.

vn^2 = 4kRT [V^2/Hz]

MOS thermal noise:
전류 기준: in^2 = 4kT\gamma gm
전압 기준: vn^2 = 4kT\gamma / gm

NMOS보다 PMOS의 noise가 더 작다.

gamma는 실험적으로 얻게 되는 값이다.

MOSFET을 만들어놓으면 Source, Drain, Gate쪽에 모두 저항 성분이 있는데,
W가 크다면 Source, Drain쪽 저항은 무시할 정도로 작아진다.

문제는 polysilicon때문에 생기는 gate쪽 저항인데,
이 저항이 또 noise를 만든다.
그래서 gate쪽 저항 성분을 layout을 잘 해서 최대한 줄여야 한다.

folding으로 gate 저항 줄이든가,
양쪽에 contact 꽂아서 gate 저항 줄이든가 해야 한다

substrate 저항에 의해서도 noise가 생긴다.
substrate 저항은 layout에 영향을 받고,
substrate contact를 커다란걸 써서 noise를 줄일 수 있다.

MOSFET Flicker noise:
gate oxide(SiO2)와 silicon substrate(Si) 사이 불안정한 결합을 dangling bond라고 부른다
이 결합들에 전자들이 갇혔다 풀려났다 하면서 noise가 생긴다
noise power density가 주파수에 반비례해서 1/f noise라고도 부른다

1/f noise를 줄이려면?
WL을 키워서 면적을 키우면 줄어든다.
1/f noise를 줄이는 회로 동작 방식으로는 LSE, chopping, CDS가 있다.

LSE(Large Scale Excitation):


chopping:

CDS(Correlated Double Sampling):


MOSFET이 amplifier로 쓰인다면,
gm, WL을 늘려야 한다.

MOSFET이 current source로 쓰인다면,
gm을 낮추고 WL을 늘려야 한다.

근데:
gm 늘리려고 전류 늘리면 전력 소모가 늘어난다
gm 늘리려고 W를 늘리면 MOSFET의 capacitance가 늘어난다

WL 늘리면 MOSFET의 capacitance가 늘어난다

cs amp에서는 R을 늘리면 thermal noise도 늘어나지만 gain 늘어나는 영향이 더 커서 noise가 줄어든다

current mirror에서는 MOSFET들이 current source로 쓰이니까, 둘다 gm이 작아야 noise가 적다
그래서 W/L이 작아야 gm이 작아 thermal noise가 작은데, 동시에 WL이 커야 1/f noise가 작다.

+Radiation Hardening


reference에 있는 flicker noise는 chopping으로 잡을 수가 없다.
flicker noise가 code dependent하게 들어오기 때문이다.


Offset cancel을 first stage에 넣을 수도 있고, second stage에 넣을 수도 있다.
second stage에 넣어야 noise가 second stage gain만 먹는다.
first stage에 들어가면 noise가 first, second stage gain을 모두 먹는다.


audio에서는 full range를 써서 reference noise가 없다?

Amplifier gain, noise:
총 gain은 그대로라고 할때, first stage gain이 클때 noise가 작다.
first stage의 noise에 대한 영향이 가장 큰 것이다.


Mirror된 current를 mirror할 경우에는 flicker noise가 많이 쌓인다.
이때는 DEM, chopping을 넣어서 flicker noise를 제거해주면 된다.