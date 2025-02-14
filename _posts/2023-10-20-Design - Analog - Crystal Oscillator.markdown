---
layout: post
title:  "Analog - Oscillator"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Oscillator:

crystal: low frequency, excellent frequency stability, excellent phase noise.
대신, cannot be integrated on silicon

tuned oscillators: Clapp, Colpitts, Hartley oscillator
(LC oscillator)
Good phase noise, moderate frequency stability
대신, large chip area

Ring oscillator: Moderate phase noise, poor frequency stability
하지만! small area




Crystal Oscillator<br>
1912년에 발명됐는데, 그 뒤로 계속 쓰고 있다.
Crystal oscillator는 mechanical resonance에 의해 진동하고, 그걸 piezoelectric 효과로 전압으로 읽어온다.
진동이 계속될 수 있도록 전기 회로로 에너지를 넣어주고, 출력을 clock 신호로 사용한다.

quartz crystal은 mechanical, chemical stability가 높아 resonance frequency가 정확하고 안정적으로 나온다.

quartz crystal은 elastic hysteresis가 아주 작기 때문에 Q factor가 크다.
Q factor가 크다는건, 진동할때마다 날려먹는 에너지가 적다는거다.


Oscillator 종류:<br>
Rc 발진기<br>
크리스탈 발진기: 그냥 크리스탈<br>
크리스탈 오실레이터: 크리스탈 뿐 아니라 오실레이터 구조 전체를 하나의 패키지에 넣어둔것<br>
그냥 전원만 넣으면 클럭이 출력된다<br>
<br>
근데, 크리스탈만 있을때 전압출력은 사인파인데<br>
크리스탈오실레이터는 전압출력이 완전 네모네모라, pcb 설계시 간섭 노이즈, emi,emc에 주의해서 배선해야 한다<br>
<br>
<br>
Crystal oscillator는:<br>
항상 켜져있어야 하는 block이라, power 소비가 적어야 한다.<br>
항상 같은 주파수를 만들어야 하기 때문에, PVT variation에 적게 영향받아야 한다.<br>
오랫동안 켜둬도 주파수가 일정해야 한다. 즉, Allan Deviation이 작아야 한다.<br>
<br>
Allan Deviation:
예를 들어 t=1s에 측정한 10MHz clock의 Allan deviation이 10^{-9}였으면,
t=1s에 오차가 10MHz * 10^{-9} = 10mHz만큼 있다는 뜻이다.


Crystal은 항상 켜져있지만, power 많이 먹는 block들은 원래 꺼뒀다가 필요할때만 켠다.
근데 crystal의 long term stability가 부족하면, crystal만 믿었다가는 시간 측정 잘못해서 block이 필요할때 꺼져있을 수도 있다.
그래서, guard band를 넣어서 block을 조금 더 미리 켜줘야 한다. 그만큼 power가 더 나간다.

crystal의 long term stability가 높으면 guard band를 더 좁게 가져가도 될거다. 그러면 power을 아낄 수 있다.
그래서 Crystal의 long term stability가 부족하면, 결국 chip 전체의 power 소모가 늘어나게 된다.


외부에서 Crystal에 넣어줘야 하는 power:<br>
$$P_{Extr}$$: extract oscillation frequency and phase<br>
$$P_{Ener}$$: Inject energy into crystal to compensate loss<br>
$$P_{Timi}$$: Timing control of energy injection<br>
<br>
$$P_{XO} = P_{Extr} + P_{Ener} + P_{Timi}$$<br>
<br>
그리고 넣어주는 에너지가 소비하는 에너지보다 많아야 한다고 한다? 왜 부등호인지는 생각좀 해봐야겠다<br>
$$P_{XO} > P_{loss}$$<br>
<br>

<div style="float: left">
    <img src="/public/img/XO1.png" style="width: 50%; height: auto;" alt="my picture" />
</div>

<br>
Crystal의 등가회로는 이렇다.<br>
Co는 전극과 패키징에 의한 캐패시턴스를 표현한거고,<br>
RLC branch (Rs Ls Cs)는 crystal의 mechanical resonance를 표현한거다<br>
크리스탈을 패키징할때, 패키징이 작은 Crystal일 수록 ESR이 크고 motional inductance가 크다.
<br>
Q factor:<br>
$$Q=2\pi \dfrac{E_{Stored}}{E_{Loss,T}} = 2\pi \dfrac{0.5L_sI^2_{R_s}}{0.5I^2_{R_s}R_sT_{XO}} = \dfrac{\omega_{osc}L_s}{R_s}$$<br>





쓸때는 이렇게 밑에 shunt capacitance를 붙여서 쓴다.<br>
Cp가 작을때의 장점:
startup time이 Cp^2에 비례하기 때문에, Cp가 작으면 startup time이 짧다.
amplitude control loop의 반응 시간이 더 짧다.

Cp가 클 때의 장점:
RF phase noise가 작다.

<br>

<div style="float: left">
    <img src="/public/img/XO2.png" style="width: 50%; height: auto;" alt="my picture" />
</div>

<br>
당연히, 이렇게만 둔다고 동작하는건 아니다.<br>
밖에서 에너지를 넣어줘야 진동을 할거다.<br>
그 역할을 하는 회로를 붙여줘야 한다.<br>
<br>
Resonance mode가 2개 있는데,<br>
Parallel mode가 있고 series mode가 있다.<br>
<br>
Parallel mode 진동을 할때는 inverter를 붙여주면 되고,<br>
Series mode 진동을 할때는 buffer를 붙여주면 된다.<br>
<br>
$$f_{series} = \dfrac{1}{2\pi \sqrt{L_sC_s}}$$<br>
<br>
<br>
Parallel mode:<br>
Ls가 Cs뿐 아니라 Co, Cp의 영향도 받아 진동한다.<br>
$$f_{parallel}= \dfrac{1}{2\pi \sqrt{L_s\left(C_s||C_L \right)}}  = \dfrac{1}{2\pi \sqrt{L_sC_s}} \sqrt{1+\dfrac{C_s}{C_L}} = f_{series}\sqrt{1+\dfrac{C_s}{C_L}} \approx f_{series}\left(1+\dfrac{C_s}{2C_L} \right)$$<br>
<br>

$$f_{parallel}$$은 C_L에 대한함수라서 외부에 달아주는 C_p를 바꾸면 f_parallel도 바뀐다.<br>
근데 f_series는 crystal 내부 수치들에 의해서만 결정된다.<br>
<br>
이렇게도 표현할 수 있다:<br>
$$\dfrac{df_{parallel}}{dC_L}  = -f_{series} \dfrac{C_s}{2C^2_L}$$
이게 좀 중요해질 수도 있는게, SMD(Surface-Mount Device) 캐패시터는 C가 $$\pm1% ~ \pm5%$$정도의 variation을 갖는다.
이게 몇 Hz정도의 variation인지 알아야 한다면 이 수식을 쓰면 된다.

공진 주파수는 온도의 영향도 받는다. 대부분의 32kHz Crystal들은 XY cut인데, 이 경우 oscillation frequency는 온도에 대한 이차함수가 된다.

$$f_{parallel} = f_o\left(1 - \alpha\left(T-T_o \right)^2 \right)$$
$$T_o$$ : Turnover temperature
$$f_o$$ : Oscillation frequency at $$T_o$$
$$\alpha$$: temperature coefficient

Crystal을 직렬 RLC 하나 + C_o로 간단하게 모델링해놨지만, 사실은 f_{parallel}의 harmonic 주파수에 해당하는 진동들도 존재한다.
그런 진동들을 'overtone mode'라고 부른다.

예를 들어, 32kHz crystal에서는 fundamental frequency의 6배 주파수에 second overtne이 존재한다.

overtone의 영향을 줄이려면, 그 주파수에서의 drive level이나 loop gain이 낮게 나오게 하면 된다.

ESR: Equivalent Series Resistance
Series resonant frequency에서 crystal이 보여주는 resistance다.
$$ESR = R_s \left( 1+\dfrac{C_o}{C_p} \right)^2$$
Cp가 들어간걸 보면 Cp를 달아놓고 잰 것 같긴 한데, 정확히 어떻게 잰건지는 잘 모르겠다.
어쨌든, 보통 $$C_p>>C_o$$라서 $$ESR \approx R_s$$다.

Drive level은 crystal 내에서 소모된 전력을 말한다.
$$DL = 2ESR \left( \pi f \left( C_L+C_o \right)V_{pp} \right)^2
Vpp는 출력의 peak to peak 전압이다.

TCXO: Temperature Compensated Crystal 

고주파 Oscillator를 만들 경우, layout에서 작은 Capacitance만 생겨도 LPE해보면 출력주파수가 많이 떨어질 수 있다.

Oscillator 주파수는, 온도가 올라가면 주파수가 떨어지는게 좋다.
온도가 올라가면 소자들이 느려지니까, settling time이 늘어나기 때문이다.
주파수가 내려가줘야 문제 없이 잘 동작한다.

crystal같은 feedback 기반 oscillator는 Colpitts style이다.
이런건 고주파나 정교한 주파수 만드는데에 쓰인다.
충전 방전을 이용하는 oscillator는 relaxation oscillator라 부른다.