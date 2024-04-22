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








참고자료: 'GaN-on-Si Power Technology: Devices and Applications'