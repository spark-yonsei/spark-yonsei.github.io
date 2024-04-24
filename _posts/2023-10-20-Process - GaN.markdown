---
layout: post
title:  "GaN"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---


GaN은 high electric breakdown field, high electron saturation velocity, high mobility in 2DEG channel등 특성을 갖는다.

경쟁 기술: Si Superjunction MOSFET, SiC MOSFET

현재, GaN power electronic device들은 lateral heterojunction을 커다랗고 저렴한 silicon substrate 위에 만든걸 쓴다.
GaN on Si: 기존 Si fab에서도 만들 수 있어서 경제적이다.

저렴하다는 장점때문에 Si가 Substrate로 쓰인다.
단점은 GaN과 Si 사이의 thermal mismatch, lattice 문제?

GaN-on-Si 기술은 metal-organic CVD 기술과 실시간 stress/curvature monitoring 기술이 발전하면서 빠르게 발전했다.

GaN power devices: low Ron, low leakage, small dynamic Ron degradation.

EPI growth 기술이 발전하면서, GaN-on-Si 소자들이 많이 쓰이고 있다.

왜 Si를 쓰냐? 싸다. 모래잖아.

Epitaxial growth는 AlN neucleation layer(Si가 GaN epilayer로 diffusion되는걸 막는 역할)을 먼저 깔고,
transitin layer(stress balance, crystallinity)를 깐다. 이게 충분히 두꺼워야 crack이 안생긴다.
그 위에 GaN buffer를 깔고, barrier layer를 깐다.

transition layer에는 graded AlGaN layer, AlN/GaN super lattice, multiple AlN stress-release insertion layer 등이 쓰인다.

background impurity(Si, O 등)에 의해 lateral punchthrough가 일어날 수도 있는데,
이건 transition layer/buffer layer에 compenation doping(C 등)을 해서 방지한다.

근데, compensation을 할때 ron에 영향 안주게 조심해야 한다.
carbon dopant가 acceptor-like deep center들을 만들 수도 있기 때문이다.

Power switching device면, off 특성이 중요하다.
GaN device로 off를 만들려면, Enhancement GaN devcie를 쓰든가 Si FET을 같이 써야 한다.

Si FET을 같이 쓸 경우, Si MOSFET의 gate 전압으로 소자를 제어할 수 있다.

power electronics에서는, ringing noise를 줄이고 안전한 동작을 하기 위해 slew rate 조절이 중요하다.
slew rate 조절을 위해서는 GaN gate를 직접 제어하는게 도움이 된다.
gate driver에 의해 제어되는 GaN device들이 많이 쓰인다.

high breakdown voltage를 위해, multiple field plates가 사용된다.
gate와 drain 사이의 depletion region을 넓히는 역할을 한다.

GaN HEMT가 완성되면, Si MOSFET과 cascode로 연결된다.
MOSFET On -> 이때 보이는 Ron은 HEMT와 MOSFET의 ron 더한 값이다.
MOSFET off-> GaN HEMT의 pinchoff 전까지는 역전압 다 버틴다.

이 Cascode 구조는 normally off 상태다.
MOSFET의 threshold를 넘으면 켜지고,
blocking voltage는 HEMT의 gate-drain breakdown voltage를 따라간다.

HEMT에서, source와 drain의 ohmic contact는 gold-free, Al based metal layer로 만들어진다.
Si Foundry와의 compatibility를 위해서다.

GaN과 AlGaN의 interface의 piezoelectric, polarization effect로 2DEG가 생긴다.

dielectric은 low gate leakage를 위해 SiO2, Si3N4, high-k 등으로 얇은 dielectric layer를 쓴다.



GaN device는 dynamic Ron 문제를 겪는다.
GaN device 구조의 trap들과 large depletion length 때문이다.

수많은 channel electron들이 trapped되어 conduction에 기여하지 못하게 되는데,
이 trapped되는 시점이 HEMT가 켜지는 시점이다.

결국 dynamic Ron이 static Ron보다 큰 값을 갖게 되고, 이건 power loss로 이어진다.

근데, GaN device들은 high voltage에 쓰이는 소자라 large depletion length가 필요한건 어쩔 수가 없다.

그래서 소자 개발자들은 GaN buffer, interfaces, dielectric layers, field plate 구조 등을 잘 조절해서,
trap 현상을 최대한 줄이면서도 breakdown voltage는 높게 유지해야 한다.


HEMT개발에서, device reliability도 중요하다.
device는 쓰다보면 특성이 안좋아지니까, 600V rated device더라도 처음에는 1350V정도 버티도록 만들어준다.

Cascode MOSFET을 안쓰고, 그냥 enhancement GaN TR을 쓰기도 한다.
이때는 cost, size, slew rate, control 등 이유다.


normally off device에서 low Ron을 얻고 싶다면,
source-to-gate access region과 gate-to-drain access region에서 높은 2DEG 밀도를 유지해야 하며,
zero gate bias에서는 gate 제어 하에 있는 channel이 완전히 depleted되게 해야 한다.


Enhancement GaN에서 normally off + low Ron을 얻기 위한 2가지 방법을 소개한다.

p-GaN Gate FET:
AlGaN barrier layer와 gate electrode 사이에 p-type GaN layer를 끼우는 방식이다.
p-GaN layer의 doping level과 두께를 잘 조절한다면,
p-GaN layer에 충분히 많이 존재하는 negative charge들이 그 아래의 2DEG를 deplete시키게 된다.
이 방식의 예시가 GIT(Gate Injection Transistor)다. EPC(Efficient Power Conversion)에서 만들었다.




참고자료: 'GaN-on-Si Power Technology: Devices and Applications'