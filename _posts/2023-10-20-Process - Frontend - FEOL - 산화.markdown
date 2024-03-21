---
layout: post
title:  "Frontend - FEOL - 산화(Oxidation)"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 2
---

웨이퍼 위에 SiO$$_{2}$$를 만드는 공정을 산화(Oxidation) 공정이라 부른다.<br>
산화 공정에서는 SiO$$_{2}$$로 MOSFET의 Gate Oxide를 만들기도 하고, 각 소자를 분리하는 절연체 벽을 만들기도 한다.
<br>
<br>
웨이퍼 표면에 SiO$$_{2}$$를 씌우는 데에는 3가지 방법이 있다.<br>
<br>
1\. 열산화(Thermal Oxidation)<br>
2\. 플라즈마 보강 화학적 기상 증착(Plasma-Enhanced Chemical Vapor Decomposition, PECVD)<br>
3\. 전기화학적 양극 처리(Anodizing)<br>
<br>
열산화에는 다시 2가지 종류가 있다.<br>
1\. 건식 산화(Dry Oxidation)<br>
2\. 습식 산화(Wet Oxidation)<br>
<br>
웨이퍼 주변을 진공으로 만들어놓고,<br>
뜨거운 상태에서 O2(g)를 넣어 산화시키면 건식 산화,<br>
H2O(g)를 넣어 산화시키면 습식 산화다.<br>
<br>
이때 건식산화는 습식산화에 비하면 느리지만 quality가 좋다.<br>
그래서 gate oxide가 될 부분은 무조건 건식산화로 산화막을 만든다.<br>
어차피 갈아버릴 곳들은 습식산화로 산화막 만들어도 상관 없다.<br>
<br>
동일한 온도와 시간을 가정하면, 습식산화로 얻은 산화막이 건식산화로 얻은 산화막보다 5~10배 두껍다.<br>
두께를 조절하려면, 그냥 더 오래 산화시키면 더 두꺼워진다.<br>
<br>
<br>
웨이퍼가 완성되면, 산화 공정을 통해 웨이퍼 표면에 SiO$$_{2}$$ 산화막을 생성하고 그 상태로 보관한다.<br>
불순물이 섞이는 것을 방지하기 위해서다.<br>
<br>
웨이퍼 위에 소자를 만들 때에는 원래 산화막을 갈아버리고, 새로 산화막을 씌운다.<br>
웨이퍼 전체가 아닌 특정 부분에만 산화막이 존재해야 하기 때문이다.<br>
<br>
<br>
소자가 생길 영역을 active region(또는 moat region)이라 부른다.<br>
소자가 생기지 않을 영역을 field region이라 부른다.<br>
<br>
active region에는 MOSFET의 Oxide 층을 구성할 SiO$$_{2}$$층이 필요하고,<br>
field region에는 웨이퍼 위 소자들을 분리할 SiO$$_{2}$$벽이 필요하다.<br>
<br>
<br>
SiO$$_{2}$$ in Active Region:<br>
미세공정을 하다보면 Gate Oxide가 점점 얇아질 필요가 있다.<br>
근데 이게 얇아지다보니 전류가 새는 문제가 점점 심해지게 되었다.<br>
<br>
그래서 물리적으로는 얇고, 전기적으로는 누설전류가 없는 절연막이 필요하게 됐다.<br>
그 결과, SiO$$_{2}$$보다 유전상수(dielectric constant, k)가 더 큰 high-k dielectric material이 Gate oxide로 쓰이게 됐다.<br>
<br>
지금은 HfO$$_{2}$$(산화하프늄)가 많이 쓰이고 있고, 란타넘(Lanthanum, La) 기반 산화물도 Gate Oxide 재료로 연구되고 있다.<br>
<br>
<br>
SiO$$_{2}$$ in Field Region:<br>
소자를 만들기 위해 웨이퍼에 n-well과 p-well을 만들다 보면 웨이퍼 안에 수많은 pn junction들이 생긴다.<br>
이 pn junction들에 의해 원하지 않는 전류가 흘러버릴 수 있기 때문에, 절연체를 pn junction들 사이에 끼워줘야 한다.<br>
이렇게 pn junction 사이에 절연체를 끼우는 것을 isolation이라 부른다.<br>
Isolation에 쓰이는 절연체는 SiO$$_{2}$$다.<br>
<br>
<br>
Isolation:<br>
Isolation 방식에는 LOCOS, STI, DTI가 있다.<br>
<br>
<br>
LOCOS(Local Oxidation of Silicon):<br>
Field region에 두꺼운 Oxide를 만들어 소자를 전기적으로 분리하는 공정이다.<br>
두꺼운 SiO2가 양 옆을 밀어내며 gate electrode 아래로 밀고 들어온다는 단점이 있다.<br>
이 현상을 bird's beak 현상이라 부른다. SiO2가 옆을 밀어내는 모양이 새 부리같이 생겨서 그렇다.<br>
<br>
Bird's beak 현상은 MOSFET의 channel에 영향을 주게 되는데, 공정이 미세화될수록 그 영향이 커진다.<br>
그래서 LOCOS 공정은 요즘 잘 안쓰인다.<br>
<br>
<br>
STI(Shallow Trench Isolation):<br>
그래서, LOCOS 대신 STI(Shallow Trench Isolation) 공정을 사용하기 시작했다.<br>
Field Region에 Trench를 파고, 그 안에 SiO2를 집어넣어 pn junction을 방지하는 방식이다.<br>
<br>
이렇게 만들면 SiO2가 gate electrode까지 들어가지 않는다.<br>
즉, bird's beak 현상이 일어나지 않는다.<br>
<br>
그리고 필요로 하는 넓이가 LOCOS보다 적기 때문에, STI 공정으로 회로의 집적도를 높이고 Chip 크기를 줄일 수 있다.
<br>
하지만, STI를 쓴다고 해서 SiO2가 양 옆을 아예 안밀어내는건 아니다.<br>
STI의 SiO2에 의해 반도체 영역이 stress를 받는걸 STI stress effect라 한다.<br>
STI stress에 의한 영향을 방지하려면, active region을 더미로라도 꽉 채워놓아야 한다.
STI stress effect는 모델링하는 파운드리 회사도 있고, 그렇지 않은 파운드리 회사도 있다.<br>
<br>
STI 공정을 쓰면 chip size를 작게 할 수 있다.<br>
원래 PN junction을 분리하려면 거리가 필요했는데, STI로 isolation을 하면 거리 없이도 isolation을 할 수 있다.<br>
결과적으로, 회로의 집적도를 높일 수 있다.<br>
<br>
STI Stress를 고려해서, layout시 바깥쪽에 source가 가도록 한다. 또는 양쪽 끝에 dummy transistor를 넣는다. Finger로 구성할 때 이야기고, N은 Vss 쪽으로, P는 VDD쪽으로 갈 가능성이 높아서 그렇다. 고 하는데 무슨 뜻인지는 알아봐야 한다.<br>
<br>
<br>
DTI(Deep Trench Isolation):<br>
DTI는 STI보다 훨씬 깊은 Trench를 파고, 거기에 SiO2를 집어넣는 방식이다.<br>
SNR 개선을 위해 옆 소자와 확실하게 분리되어야 하는 이미지 센서 등에 사용된다.<br>


이게 지금 소자를 분리하려는건지 pn junction 쪼개려는건지 확인 필요
아마 소자 분리가 맞을 것 같다. LOCOS로 pn junction못쪼개잖아

일단 웨이퍼 전체에 pad oxide를 깔고, moat region에만 nitride를 올린다.
그다음 Nitride가 없는 field region에만 SiO2를 넣는게


그다음에 다시 oxide를 키워서 nitride 없는 곳에만 SiO2를 만든다.