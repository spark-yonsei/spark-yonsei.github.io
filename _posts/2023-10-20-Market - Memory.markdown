---
layout: post
title:  "Memory"
date:   2023-10-04 19:31:29 +0900
categories: Market
order: 12
---

Seagate는 6월이 결산월이다.
2024년 10월에 발표하는 7~9월 실적은
2025년 1분기 실적(Q1FY25)이 된다.

클라우드, 기업에 많이 쓰이는 니어라인 HDD

Seagate 매출의 대부분은 HDD 제조에서 나온다.
Seagate의 HDD는 대용량 제품과 기존제품으로 구분된다

대용량 제품에는:
니어라인 HDD, VIA용 HDD, NAS용 HDD등이 포함
VIA: Video and Image Applications
NAS: Network Attatched Storage

Seagate 개발동향:
24TB: 종래기술
28TB: SMR기술
30TB: Mozaic 3+ 기술


반도체 배선공정에서 구리가 알루미늄보다 좋은 점:

저항이 낮다
열팽창계수가 낮다 -> Warpage가 낮다
열전도율이 높다 -> 열 방출이 잘된다

열전도율이 높은 EMC 소재?

구리의 단점:
소재 가격이 비싸고, etch가 어렵기 때문에
비싼 damascene 공정을 써야 한다

Alloy 공정:
금속에 열을 가해 grain boundry를 키워 저항을 낮추는 공정


왜 dry etch에 Ar plasma를 쓰나?
낮은 전압으로 만들 수 있어서 그렇다

HBM:
용량을 높인다
=처리할 수 있는 양을 키운다
=위로 쌓는다

속도를 높인다
=TSV 수를 늘린다

HBM3E 8단 양산은 하이닉스가 처음이다
HBM3E 12단 개발은 삼성전자가 처음이다
12단 양산은 아직 모른다


HBM 쌓는 방법:
TC-NCF : 삼성전자, 마이크론
MR-MUF: 하이닉스

TC-NCF:
Thermo Compressive - Non Conductive Film
열, 압력, 박막이 중요하다

Wafer 위에 chip을 열, 압력으로 쌓는 구조다.
그래서 Chip on Wafer, COW 구조다.
chip 사이사이에는 non conductive film을 깔아서 합선을 막는다.

TC-NCF는 하나씩 쌓는 방식이라 안전하지만 오래 걸린다.
또, film을 추가로 사용해야 해서 경제성이 떨어진다.

삼성전자는 TC-NCF로 12단을 먼저 개발한다.

HBM의 DRAM chip 하나당 3GB라서,
8단이면 24GB, 12단이면 36GB

MR-MUF:
MR: Mass Reflow - 대량으로 한번에 접합한다는 의미
chip을 다 쌓아올린 뒤에 한번에 붙이는 방식이다.

chip과 chip은 bump로 연결하는데, bump의 머리를 solder라고 부른다.
solder를 녹여 아래 chip과 붙이는 과정이 reflow다.

MUF: Molded Under Fill
chip간 빈 공간을 molding 소재인 EMC로 채운다.
EMC: Epoxy Molding Compound

삼성전자는 chip 사이를 NCF로 채우는데,
하이닉스는 molding 소재로 채우는 것이다.

molding 소재를 사용하면 한번에 underfill, molding을 할 수 있기 때문에
생산성과 경제성이 향상되는 장점이 있다.
molding 소재는 ncf보다 열 방출 능력도 좋다.

근데 삼성전자는 왜 MR-MUF를 안쓰냐?
MR-MUF는 mass reflow로 한번에 접합하기 때문에,
하나씩 쌓는 TC-NCF보다 Warpage에 취약하다.

특히나, 단 수를 높일수록 각 층의 chip 두께는 얇아진다.
JEDEC 기준이 총 두께 720um라서 그렇다.
chip이 얇아지면 warpage에 더 취약해진다.

그럼에도, 하이닉스는 warpage control에 자신이 있어 계속 MR-MUF를 쓴다고 한다.

한미반도체가 만드는 TC 본더가
chip들을 warpage 괜찮게 bonding하는 장비다.

Advanced MR-MUF:
하이닉스에서 Warpage를 개선한 방식

MR-MUF:
chip들을 상온에서 wafer에 붙어있을 정도로만 올려두고,
마지막에 한번에 reflow로 접합시킨다

Advanced MR-MUF:
chip들을 wafer에 올려둘때,
순간적으로 높은 열을 가해서 모두 임시접합을 해두는 방식이다.
그냥 올려두는것보다 더 잘 붙어있게 된다.
이걸로 warpage를 개선해서 12단 개발에 성공했다.

단순히 압력과 온도로 임시접합 시키는게 쉬운 일은 아닌데,
한미반도체가 bonding 잘하는 회사라 이걸 가능하게 했다

warpage control만 개선된게 아니라,
EMC 소재도 개선해서 Advanced EMC로 열방출을 개선했다.


GPU 구조:
Package substrate 위에 interposer,
interposer 위에 logic die와 CPU/GPU/SOC die,
Logic die 위에 HBM DRAM Die

즉, GPU와 HBM이 하나의 interposer 위에 2.5D packaging을 통해 만들어진다.

HBM 12단이라는건, Logic die 위에 DRAM Die 12장이 올라간다는 뜻이다.

Logic Die는 DRAM Die에 저장되어 있는 정보를 GPU에서 병렬계산 할 수 있도록 한다.
제어하는 역할만 하기 때문에 저장 기능은 필요 없다. 그래서 캐패시터가 없다.

DRAM은 저장을 해야 하니 캐패시터가 들어가는데,
캐패시터때문에 10나노 미만 DRAM을 만들기가 어려웠다.
근데 Logic die는 캐패시터가 없으니 FinFET 5nm 등 첨단공정을 쓸 수 있다.

하이닉스는 logic die는 TSMC에 맡긴다.

TSMC: FEOL -> TSV -> BEOL
하이닉스: EDS Test -> COW bonding



SK하이닉스는 16단 HBM3E를 생산하기 위해 12단 제품에서 양산 경쟁력이 입증된 '어드밴스드(Advanced) MR-MUF' 공정을 활용할 계획이다. HBM은 여러 개의 D랩을 쌓아 올린 뒤 칩과 칩 사이 회로를 보호하기 위해 공간을 메우는 공정을 거친다. SK하이닉스는 이 때 액체 형태의 보호재를 주입하고 굳히는 공정을 거친다.

칩을 하나씩 쌓을 때마다 필름형 소재를 깔아주는 삼성전자 방식 대비 공정이 효율적이고, 열 방출에도 효과적이라는 평가를 받는다. 특히, SK하이닉스의 어드밴스드 MR-MUF는 기존 공정보다 칩을 쌓을 때 가해지는 압력을 줄이고, 휨 현상 제어(Warpage control)도 우수해 안정적인 HBM 양산성을 확보할 수 있다.

SK하이닉스는 어드밴스드 MR-MUF 공정과 함께 하이브리드 본딩(Hybrid bonding) 기술도 백업 공정으로 함께 개발 중이다.




CXL: Compute Express Link 메모리 자원 공유를 위한 방안
PIM: memory 병목현상 해결을 위한 방안

HBM3E: 5세대
HBM4: 6세대
HBM5: 7세대

디본딩 기술: 붙인 칩을 떼어내는 기술
Mechanical: 힘으로 웨이퍼를 떼어내는 방식
Laser: 레이저로 떼어내는 방식

HBM은 단품 DRAM 칩 여러개를 수직으로 쌓아 대역과 용량을 늘린 메모리다
Base Die(Logic Die) 위에 Core Die(DRAM Die)를 쌓는 과정에서,
중간에 bump를 형성한 다음 웨이퍼 앞면에 캐리어 웨이퍼를 임시로 붙여야 한다.

그 후 웨이퍼 뒷면을 얇게 깎고, 후면 범프 형성 공정까지 한 뒤에는 이 캐리어 웨이퍼를 제거해야 한다.
여기에서 디본딩 기술이 필요하다.

Temporary bonding 후 공정을 거치고,
백사이드를 깎아내고 링프레임에 붙인 다음 디본딩을 한다

파티클 관리:
물리적인 방법과 화학적인 방법이 있다.

세정 장비는:
효율성: 파티클을 얼마나 빨리 떼어낼 수 있는지
효과성: 제거가 가능한지
친환경: 독성이 덜한 물질을 쓰는지

희귀가스는 제철소에서 만들어진다

저전력 DRAM: LPDDR

LPDDR5X의 성능을 높인 LPDDR5T

슈퍼컴퓨터 단위는 PF(PetaFlops)를 쓴다
초당 몇PF 연산이 가능한지가 지표다

HPSP: 고압수소어닐링(HPA), 고압산화공정(HPO) 장비를 만든다
HPA: 소자 계면 결함을 제거 -> 신뢰성, 성능 개선




SSD, DRAMless SSD

NAND, NOR memory

