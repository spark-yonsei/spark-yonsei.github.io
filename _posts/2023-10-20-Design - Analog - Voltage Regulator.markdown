---
layout: post
title:  "Analog - Voltage Regulator"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 1
---

IC를 설계했으면, 여기에 전원을 공급해줘야 한다.
크게 두가지 방법이 있다.
PMIC라는 power 공급용 IC를 새로 가져와서 전원 공급에 사용할 수도 있고,
chip 내에 on-chip power management 회로를 넣을 수도 있다.


On-chip power management는 3가지가 있다.
Linear Regulator(LDO)
Switching Regulator(Buck Converter)
Switched-Capacitor Regulator(Charge Pump)

이런 방식들이 있다.
현업에서는 LDO가 가장 많이 쓰인다.



요즘은 PLL에도 LDO가 들어간다.

PMIC랑 on-chip power IC는 완전히 다르다.
PMIC는 power를 공급하는 IC를 따로 만들어둔거다.

PMIC에서는 capless LDO가 의미가 없다.
어차피 전압 받는 곳에서 캐패시터 붙여서 받는다.
그래서 굳이 capless로 만들지 않는다.

물론 PMIC 내부 구동을 위한 LDO라면 capless일 수도 있다.

근데 on-chip LDO는? 캐패시터 달 때도 있고 아닐때도 있다.
사실 LDO에 캐패시터 달면 동작상으로는 좋다.
PSRR 좋아지고, stability 좋아지고, noise 사라진다.
근데 캐패시터 때문에 면적이 커진다는게 문제다.

Switching regulator(buck)은 인덕터가 필요하다.
이 인덕터를 어떻게 작게 만들어서 집어넣을지가 문제다.

LDO에 캐패시터 달때, 조심해야 할 부분이 있다.
3.3v 출력에다가 ‘5v capacitor’를 쓰면, 그 캐패시터가 보여줘야 할 캐패시턴스가 안나온다. 좀 다른 캐패시턴스 값이 나온다.

캐패시턴스가 전압에 영향을 받아서 그렇다. 이거 다 맞춰서 넣어줘야 한다.

LDO Stability 보상 방식중에, ESR을 쓰는 방식들이 많이 소개되어 있다.
하지만 요즘은 그런 보상방식을 쓰지 않는다.
옛날에 탄탈륨 캐패시터 쓸때는 ESR이 좀 돼서 가능했는데,
요즘은 MLCC를 쓰기 때문에 ESR이 없다.

LDO를 연결하는 도체때문에 인덕턴스가 생길수도 있다.
입력이든 출력이든 인덕턴스가 생길 수 있는건데,
이 인덕턴스 때문에 bode plot이 특정 구간에서 튈 수도 있으니 잘 확인해줘야 한다.

LDO를 설계하다보면, 출력에 C가 얼마나 달리는지 모르고 만들어야 할 때가 있다.

출력 C가 너무 커지면 jitter는 줄어도 stability가 안좋아질 수 있다.
아니면 면적 부족해서 C를 더 줄여야 할 수도 있다.

High speed면 PSRR이 중요하다.
Logic에 연결된 LDO면 조금 덜 중요하다.
PLL은 jitter, PSRR 특성이 좋아야 한다.

근데 고주파에서는 PSRR 개선이 어렵다.
고주파에서는 loop이 잘 안보인다.

LDO 속도 개선하려고 feed forward path 붙일 수도 있는데, 이런게 다 나중에 PSRR에 방해가 된다.


LDO에는 다양한 load들이 연결된다.

Logic에 연결되면, load가 항상 달려있는 상태가 된다.
Logic에서 leakage가 계속 새고 있으니까.

하지만 no load, light load에 연결되는 경우들도 있다.

Automotive 분야에서는 -55도부터 150도까지 검증한다.

Power가 들어오면 자동으로 켜지는 self-startup LDO도 있고, startup 신호 받아서 켜지는 LDO도 있다.

LDO에 들어가는 bandgap reference?
Voltage mode BGR이 있고, current mode LDO가 있다.

사용하는 전압이 클때는 voltage mode BGR을 쓴다.
Voltage mode BGR은 동작점이 2개뿐이다.
아예 0v라서 꺼졌을때랑, 내가 설정한 전압 이렇게 2개뿐이다.
그래서, startup만 대충 시켜주면 알아서 동작점 잘 찾아간다.

근데, 삼성전자 공정 기준 5nm는 1.8v 소자가 최대고, 4nm은 1.2v 소자가 최대다.

근데도 1.8v 출력이 필요할 수도 있잖아?
이럴땐 current mode bgr을 써야 한다.

문제는, current mode bgr은 동작점이 되게 많다.
그래서 startup 시키기가 어려워진다.

그리고 삼성전자 3나노 공정부터는 FinFET이 아니라 GAAFET을 쓴다.

GAAFET은 두꺼운 트랜지스터를 만들기 어려워 높은 전압 소자를 만들기 어렵고,
Backside까지 써먹는 소자라서 backside를 깎아서 얇게 만든다. 그래서 vertical BJT를 만들기가 어렵다.
즉, 3나노에서는 BJT만드는거 자체가 어렵다는거다.

그래서, 공정이 미세화되면서 bandgap을 만들기가 점점 어려워지고 있다.




3nm 공정에서 웨이퍼 면적은 강남 땅이라고 생각하면 된다. 면적을 아주 조금이라도 줄여야 한다.

Switched capacitor도 가끔 쓰이긴 하는데, 큰 전류를 내기 어렵고 커다란 캐패시터가 들어갈 면적도 부족하다.

Buck converter도 인덕터때문에 면적이 넓어서, [A]단위에서나 쓰인다.

Digital LDO를 쓰면 headroom을 크게 개선할 수 있지만, ripple 등 단점이 많다.
사실 아날로그 LDO가 더 낫긴 하다.


Switching regulator:
효율이 좋다는 장점이 있다.
효율이 좋으니 열이 적게 나고,
그래서 열이 나면 안되는 경우 integrated buck 구조를 칩 안에 넣어 쓰기도 한다.
이 경우에는 인덕터 구현 방식이 중요하다.

인덕터를 따로 만들지 않고 wire inductor를 쓰겠다는 논문도 있었는데, 이 경우에는 인덕턴스 특성보장이 안된다. 즉 품질관리가 안되는거라 양산을 할 수 없다.

효율: buck이 높고 LDO가 낮다
소자: buck는 인덕터 하나 캐패시터 하나,
LDO는 캐패시터 하나면 된다
면적: buck이 넓고 LDO가 낮다

LDO with low supply:
공정이 미세화돼서 Supply voltage가 내려가면?
Headroom(VIN-VOUT)이 작아졌으니, power TR 크기를 키운다.

Power TR 크기가 커지면 load current가 늘어나고, 보상이 어려워지고, 설계가 어려워진다.

공정이 미세화되면 supply voltage 내려가는 이유가 뭔가?
높은 전압에 버티는 두꺼운 소자를 못만들어서 그렇다.

그러니까, 예를 들어 1.8V소자밖에 없어도, 이걸 어떻게든 조합해서 3.3v에서 동작하는 회로를 만들면 미세공정에서도 높은 supply voltage를 쓸 수 있다.

1.8v 소자들을 stack으로 쌓고 전류 흐르게 해서 biasing을 잡아주면 3.3v에서 동작하게 만들 수 있다.
근데 이 경우, 전류가 계속 흘러야 해서 전류 소모가 계속 일어난다.


사실 이런 방식은 사용되어온 역사가 있다.
3.3v 소자는 마스크를 더 써야 한다. 더 높은 전압에 버텨야 하니까.
근데, 고객이 마스크 비용 아끼려고 1.8v 소자만 쓰고싶을 수도 있다.
그러면 위에 말한대로 stack 쌓고 전류 bias 걸어서 1.8v 소자들이 3.3v에서 동작하게 만든다.

옛날에는 마스크비용 아끼려고 이런 선택을 하는거였는데,
GAAFET 공정에서는 아날로그 트랜지스터 만들기가 어렵기에 이제는 그냥 다 이렇게 해야 한다.
그러면 전류 계속 나가는거 어떡할거냐?
이건 연구할 부분이다.