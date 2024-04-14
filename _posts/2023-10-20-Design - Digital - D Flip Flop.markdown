---
layout: post
title:  "Digital - D flip flop"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 6
---


Positive edge triggered일 수도 있고 negative edge triggered일 수도 있는데,
하여간 매 edge마다 입력을 출력으로 보내는게 D flipflop이다.

D flipflop에는 Reset 신호 입력도 있는데, 이건 보통 asynchronous하다.
그래서 지금 clock이 어떤 상황이든지, 그냥 reset 신호 들어오면 reset된다.

register들을 initial condtion으로 보낼 때에도,
logic에 POR 신호가 들어오면 logic이 register들을 모두 initial condition으로 보낸다.

근데 D flipflop중에 TE(Test Enable), TI(Test Input)신호를 받게 되어 있는 것도 있다.
TE가 high면 TI에 들어오고 있는 값을 출력하는 방식이다.

왜 이런 기능을 달아놨나? scan test를 위해서다.

Logic회로를 만들면, 공정 과정의 문제로 fault가 생길 수 있다.
photoresist가 뭉쳐서 뿌려지는 바람에 도체가 옆 도체랑 붙어버리거나,
덜 뿌려져서 도체가 끊어진다거나 하는 문제가 생길 수 있다.
logic 회로들은 하도 도체 사이 거리가 좁다보니 이런 일들이 생길 수 있다.

그래서, logic 회로를 만든 후에는 fault가 있는지 확인해줘야 한다.

공정 문제로 생길 수 있는 fault는 3가지다.
stuck at 0, stuck at 1, open

도체가 VDD에 붙어버리면 stuck at 1,
도체가 GND에 붙어버리면 stuck at 0,
끊어지면 open

뭐 꼭 VDD, GND에 안붙더라도, 옆 도체가 1인데 여기랑 붙어버리면 1이 나올수도 있다.

그래서 이런 fault들이 있는지, 있다면 어디 있는지 어떻게 찾을 것인가?
이상적으로는, 발생할 수 있는 모든 입력 조합을 다 집어넣어보면 찾을 수 있을 것이다.

예를 들어, OR gate가 있을때, 이 안에 fault가 발생했는지 확인하고 싶다고 해보자.
이때 output이 stuck at 1이라면, 가능한 입력 조합 00 01 10 11중 00을 넣었을때에만 이 fault를 발견할 수 있다.
나머지 input 조합으로는 이 fault를 찾을 수 없다.

지금은 gate 하나였어서 어떤 input을 넣어야 어떤 fault를 확인할 수 있는 지 바로 확인했지만,
gate 갯수가 많아지면 무슨 조합을 넣어야 어디의 무슨 fault가 보일지 사람이 판단하기 아주 어렵다.

그럼 그냥 모든 input 조합 다 넣어보면 안되나? 그러기에는 가능한 조합이 너무 많다.

그래서 ATPG Tool이라는걸 쓴다.
ATPG Tool: Automatic Test Pattern Generation

이 회로에는 어떤 어떤 조합들을 넣어보면 fault를 모두 확인할 수 있을지 알려주는게 ATPG Tool이다

근데, 또 단순히 input 조합들만으로는 확인이 안되는 fault들이 있을 수도 있다.
flipflop 때문에 순차적으로 입력을 넣어줘야 하는데, 그 순차 입력 게획이 상당히 복잡하다거나 하는 경우다.
이런 문제를 해결하기 위해 scan test라는게 나왔다.

scan test는 testability를 위해 회로 내부를 바꾼다.
앞에서 언급한 TE, TI를 써서 바꾸는거다.
이러면 test pattern generation이 훨씬 쉬워질 수 있다.
뭐 이런 방법들로 stuck at 0, stuck at 1을 찾아낼 수 있다.

근데 open은 찾아내기가 좀 어렵다.
삼성전자는 scan test에서 측정하는 factor들 중 leakage current가 있는데,
아마 이게 open fault 때문인 것으로 보인다.

Fault coverage:
Logic을 잘 만들면 어디에서 fault가 발생하든 다 잡아낼 수 있다.
근데, 또 100%잡아낼 수 있게 만들면 logic이 너무 커진다.
그래서 한 95%정도 잡아낼 수 있게 만들고, 이 수치를 fault coverage라고 부른다.
이 맥락에서 DFT가 나오면, 그건 Design for Testability다.

