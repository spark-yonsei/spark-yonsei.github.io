---
layout: post
title:  "Backend - Packaging"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 11
---

웨이퍼를 잘라서 나온 칩들을 포장하는 과정을 Packaging 공정이라 한다.<br>
<br>
Packaging 공정에서는 칩을 보호하기 위해 에폭시 수지로 포장하면서,<br>
동시에 외부와 전기신호를 주고받을 수 있도록 금속으로 길을 만들어놓아야 한다.<br>
<br>
<br>
먼저, 웨이퍼 뒷면을 갈아 웨이퍼를 얇게 만들어야 한다.<br>
<br>
원래 웨이퍼는 공정 도중 파손되는것을 막기 위해 600um~900um 정도로 두껍게 만든다.<br>
하지만 모든 공정이 끝난 후에는 칩이 얇은 것이 좋다.<br>
두께가 얇아야 열 방출도 잘 되고, 스마트폰 등 부피가 중요한 제품에 들어갈 수 있기 때문이다.<br>
<br>
그래서 웨이퍼 뒷면을 갈아 100um 정도로 얇게 만드는데, 이것이 backgrinding 공정이다.<br>
이때, 너무 얇게 갈면 칩이 휘어져 전기적 특성이 바뀔수도 있다. 그래서 적절히 얇게 갈아야 한다.<br>
<br>
<br>
Back grinding으로 웨이퍼를 얇게 만든 후에는,<br>
웨이퍼를 잘라 낱개의 칩들로 분리해야 한다.<br>
<br>
웨이퍼 위 칩들은 scribe line으로 구분되어 있는데,<br>
이 scribe line을 따라 다이아몬드 톱으로 웨이퍼를 절단한다.<br>
<br>
이 절단 작업을 wafer sawing 또는 dicing이라 부르며,<br>
잘라서 나온 낱개 칩을 bare chip 또는 die라 부른다.<br>
그러나, die 상태의 칩은 전기신호를 주고받을 수도 없고, 외부 충격에 의해 손상되기도 쉽다.<br>
<br>
<br>
절단된 칩들은 Lead frame 위로 옮겨진다.<br>
Lead frame은 칩을 지지해주는 골격 역할을 한다.<br>
<br>
그 후에는 칩과 Lead frame을 가느다란 금속 선으로 연결한다.<br>
이 금속 선들이 칩과 외부 회로 사이의 전기 신호를 전달하는 역할을 하게 된다.<br>
이 과정을 'wire bonding'이라 부른다.<br>
<br>
<br>
마지막으로, 탄소가루 섞은 에폭시 수지로 칩과 리드프레임을 포장한다.<br>
이 과정을 'encapsulation'이라 부른다.<br>
<br>
Encapsulation 후에는 에폭시 수지 포장이 칩을 열, 습기 등으로부터 보호하게 된다.<br>
탄소가루는 에폭시 수지를 검은색으로 만들어 빛을 차단하기 위해 쓰인다.<br>
<br>
에폭시 수지는 가격이 저렴하고 열을 잘 방출해 많이 쓰이는데,<br>
Si와 에폭시 수지의 열팽창계수가 같도록 에폭시 수지를 잘 만들어야 한다.<br>
그렇지 않으면 열에 의해 칩이 휘어진다.<br>
<br>
<br>
이후에는 에폭시 수지 포장 위에 칩 정보를 적어 완제품으로 만든다.<br>
이때 패키징에 제품 정보가 제대로 적히지 못해 제품 구별, 방향 구별 등이 안되는 경우가 있는데,<br>
이런 경우는 제품 불량으로 분류한다. 패키징도 백엔드 공정의 일부이기 때문이다.<br>
<br>
완제품은 다양한 전압, 온도, 습도 등에서 동작을 검증받고 제품으로 출하된다.<br>
이때, 완제품 상태에서 진행하는 테스트를 package test라 부른다.<br>
<br>
<br>
*Dicing<br>
원래는 backgrinding 후에 dicing을 했는데, 웨이퍼가 얇아서 칩이 손상되는 경우가 생겼다.<br>
그래서 dicing을 먼저 하고 backgrinding을 하기도 한다. 이것이 DBG(Dicing Before Grinding) 방식이다.<br>
이 경우에는 die 뒷면을 하나하나 다 갈아줘야 한다.<br>
<br>
다이아몬드 톱으로 scribe line을 따라 웨이퍼를 자르면 scribe line만큼의 면적 손실이 발생한다.<br>
이 손실을 Kerf loss(커프 손실)이라 부른다.<br>
<br>
커프 손실을 최대한 줄이기 위해 레이저로 웨이퍼를 자르는 stealth dicing,<br>
플라즈마로 웨이퍼를 자르는 plasma dicing 방식이 제시됐다.<br>
<br>
<br>
*Wire Bonding<br>
Wire bonding에 쓰이는 금속으로는 알루미늄, 구리, 금 등이 있는데, 대부분 금을 쓴다.<br>
<br>
알루미늄은 저항이 비교적 크기 때문에 두께가 두꺼워야 하며, 잘 끊어지는 특성이 있다.<br>
구리는 너무 단단해서 wire bonding에 사용하기에는 부적합하다.<br>
그래서 녹 안슬고, 적당히 단단하고, 잘 늘어나고, 저항이 낮은 금을 보통 쓴다.<br>
<br>
wire bonding에 쓰이는 금속 선은 매우 가늘기 떄문에, 상당히 큰 inductance를 가진다.<br>
그래서 회로 설계시에는 금속 선의 inductance를 반영한 설계를 위해, 금속선 1mm당 1nH 정도를 가정하고 설계한다.<br>
금속 선에 의해 inductance가 생길 경우, 신호 전달이 느려져 트랜지스터들이 더 느리게 켜지고 꺼지게 될 수 있다.<br>
<br>
<br>
*Wireless Bonding<br>
wire 없이 칩을 lead frame과 연결하는 방법으로 flip chip 방식이 있다.<br>
<br>
flip chip 방식은 칩 위에 bump를 만들고, 칩을 뒤집어 lead frame 위에 올리는 방식이다.<br>
이렇게 하면 칩과 lead frame이 wire 대신 bump로 연결되어, 전기 신호가 더 짧은 경로를 통해 전달된다.<br>
더 짧은 경로를 통하기 때문에 저항이 더 작고, 속도가 빠르며, 크기가 작다.<br>
<br>
<br>
TSV(Through Silicon Via) 방식은 여러개 칩을 하나의 패키지 안에 집어넣는 방식이다.<br>
TSV 방식에서는 칩들을 수직 관통하는 구멍을 뚫고, 칩들을 쌓은 후 구멍을 금속으로 채워넣는다.<br>
이렇게 하면 구멍에 채워진 금속들이 칩들을 연결하며 전기 신호를 전달한다.<br>
<br>
TSV 방식을 쓰면 기판 넓이를 줄일수 있고, 칩간 신호가 전달되는 속도도 빨라진다.<br>
그러나 칩을 관통하는 구멍을 뚫는게 상당한 기술력을 필요로 한다.<br>
<br>
<br>
*Encapsulation<br>
사실 탄소가루 섞은 에폭시 수지 말고, 세라믹이나 금속 소재로 칩을 포장하면 열 방출이 더 쉬워진다.<br>
이렇게 하지 않는 이유는 비용이 더 비싸기 때문이다.<br>
그래서, 열이 많이 발생하는 CPU에서만 열 방출 개선을 위해 금속 뚜껑을 쓴다.<br>

Metal can package:
비싸지면, epoxy가 stress를 다 흡수하기 때문에 die에 stress가 가해지지 않는다.
따라서 저항값이 압력에 영향받는걸 방지할 수 있다.

Plastic package:
플라스틱은 Si보다 열팽창계수가 10배정도 크다.

LGA:
BGA:
PGA:

Cpu pin이 메인보드에 달려있으면 LGA, CPU에 달려있으면 PGA, 납땜 형식이면 BGA

exposed pad: 패키지 하단에 있는 금속 패드
기판에 부착되니까 열 방출+기계적 안정성

반도체 패키지 종류:
Conventional Package: 웨이퍼를 칩 단위로 잘라서 패키징하는 방식
Wafer Level Package: 패키징 공정 일부 또는 전체를 웨이퍼 레벨에서 진행하고, 나중에 단품으로 자르는 방식

Conventional Package는 패키징하는 재료에 따라 Ceramic Package, Plastic Package로 구분할 수 있다.
Plastic Package는 잘라진 칩을 부착해 전기적으로 연결하는데,
칩을 어디에 붙이는지 따라 Leadframe type package, Substrate type package가 있다.

Wafer Level Package는:
Flip chip package: 칩 위에 RDL, Solder bump를 형성해 패키징하는 방식
WLCSP(Wafer Level Chip Scale Package): Substrate같은 곳에 붙이지 않고, 웨이퍼 위에 바로 배선, solder ball을 형성해 패키징하는 방식
TSV package: 쌓여있는 칩들을 TSV로 연결하는 방식

RDL: Re-Distribution Layer
칩이 외부와 전기적으로 연결되는 곳이 Pad인데, 이 pad를 재배열해주는 역할

Solder bump:
칩을 기판에 Flip chip 방식으로 연결하거나
BGA, CSP 등을 회로 기판에 직접 접촉시키기 위한 전도성 돌기

WLCSP는 다시 2가지로 분류된다.
Fan-in WLCSP: 웨이퍼 위에 바로 배선, 솔더볼을 부착
Fan-out WLCSP: 칩을 몰딩웨이퍼로 만들어, 웨이퍼레벨 공정으로 배선, 솔더볼 부착

Fan-in WLCSP를 하면 패키지 크기가 칩 크기와 같고,
Fan-out WLCSP를 하면 패키지가 칩보다 커진다



Conventional Package:

Plastic Pacakge는 칩을 둘러싸는 재료로 EMC 등의 플라스틱 재료를 사용하는 방식이다
이 중 리드프레임 타입 패키지는 칩이 리드프레임에 부착된다

패키지를 PCB에 연결하는 pin이 lead인데, lead를 프레임으로 잡아준 형태라 리드프레임이라 부른다.
리드프레임은 얇은 금속판에 에칭 등 방법으로 배선이 구현된 형태다.

여러가지 리드프레임 타입 패키지:
1970년대에는 DIP, ZIP같이 lead를 PCB 구멍에 집어넣는 through hole 형태가 많이 쓰였는데,
이후 pin 갯수가 많아지고 PCB 디자인이 복잡해지면서 구멍에 집어넣는 구조는 한계가 생겼다
그래서 TSOP, QFP, SOJ같이 리드가 표면에 붙는 형태가 개발됐다.
(Surface Mounting Type)

로직 칩 등 I/O pin이 많이 필요한 제품은 QFP처럼 4면에 lead가 있는 패키지가 적용됐다

얇은 패키지가 필요한 경우에는 TQFP, TSOP 등 패키지가 쓰였다

반도체 제품의 고속 동작이 요구되기 시작함에 따라,
패키지 배선 설계를 다층으로 할 수 있는 substrate type package가 주력 패키지 기술이 되었다.

하지만 TSOP 등 리드프레임 패키지도 아직 많이 쓴다. 왜냐면 저렴하기 때문이다.


리드프레임은 금속판에 스탬핑이나 에칭 방식으로 배선을 하기 때문에,
제조과정이 복잡한 substrate 방식보다 가격이 저렴하다

그래서, 그렇게까지 고속 동작이 필요하지 않은 제품에는 지금도 저렴한 리드프레임 패키지를 쓴다

DIP: Dual In-line Package
ZIP: Zig-zag In-line Package
QFP: Quad Flat Package
TQFP: Thin Quad Flat Package
TSOP: Thin Small Outline Package
SOJ: Small Outline J-leaded

Substrate type package:
Substrate를 사용한 패키징 방식이다.

Substrate는 제조할 때 여러 층의 필름을 써서 만들기도 하기에,
Laminated type package라고 부르기도 한다.

Laminate: 필름같은 얇은 재료들이 넓게 붙여진 것

Substrate package는 여러 층으로 배선을 만들기 때문에,
리드프레임 타입 패키지보다 전기적 특성이 우수하고 크기도 더 작게 만들 수 있다.

리드프레임으로는 1층밖에 못만든다.
substrate는 상황에 따라 적절한 층 수를 쓴다

리드프레임 패키지는 핀이 옆으로밖에 못나오는데,
substrate package는 아래 면 어디서든 나올 수 있어서 더 많은 수의 핀을 만들 수 있다
핀이 옆이 아니라 아래로 나오니 핀까지 포함한 면적은 substrate package가 더 작다.

그래서 지금은 substrate type package가 주로 쓰인다.

BGA: Ball Grid Array
FBGA: Fine pitch Ball Grid Array
얘네는 Package substrate에 Solder ball이 부착된 형태

LGA: Land Grid Array
이건 substrate 위에 solder ball이 없는 형태

substrate type package로는 일반적으로 BGA가 사용되지만,
최근에는 ball 없이 ball land만 갖는 LGA 형태 패키지도 사용되고 있다.

Ceramic Package:
Ceramic body를 사용하는 패키지다
열 방출, 신뢰성이 높다
하지만 세라믹 제조 공정이 비싸다

그래서 높은 신뢰성이 요구되는 로직 반도체에 사용되고,
CIS용 패키지에서는 검증용으로 사용된다.
CIS: CMOS Image Sensor


Wafer level package는 패키지 공정을 웨이퍼 레벨에서 진행한 패키지다.
패키지 공정 전체를 웨이퍼 레벨로 진행한 패키지는 WLCSP가 대표적이고,
일부를 웨이퍼 레벨로 진행하는 패키지는 RDL, TSV를 이용한 패키지들과 Flip chip package 등이 있다.

Fan in WLCSP:
웨이퍼 바로 위에 패키지용 배선, 절연층, 솔더 볼을 올려둔 패키징

이걸 conventional package랑 비교하면?

장점:
칩의 크기가 그대로 패키지 크기가 된다. 패키지 크기 최소화 가능
substrate같은 매개체 없이, 솔더 볼이 칩 위에 바로 붙기에 전류 경로가 짧다 그래서 전기적 특성이 향상된다
substrate, wire 등 패키징에 쓰이는 추가 재료들이 필요 없다

단점:
Si 칩이 그대로 패키지가 되기에, 패키지의 물리적,화학적 보호 기능이 약하다

Silicon과 PCB는 열팽창계수 차이가 크다.
그래서 솔더 연결부의 Solder Joint Reliability가 부족하다

메모리 칩을 개발할 경우, 용량이 같은 칩이더라도 새로운 기술로 칩을 개발하면 칩 크기가 달라진다. 그러면 기존 패키지 테스트 시스템을 사용하지 못하고 새로 다시 다 만들어야 한다

웨이퍼의 칩 수가 적고, 수율이 낮은 경우에는 conventional package보다 비용이 더 많이 든다




Fan-out WLCSP:


https://news.skhynix.co.kr/post/seominsuk-column-types-of-packages-1