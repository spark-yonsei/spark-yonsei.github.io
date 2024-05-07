---
layout: post
title:  "Microscopic Electromagnetics - Quantum Computers"
date:   2023-10-24 19:31:29 +0900
categories: Electromagnetics
order: 1
---

양자컴퓨터는 중첩, 얽힘, 간섭 등 양자역학적 특징을 이용하는 컴퓨터다.

1982년 리처드 파인만이 양자컴퓨터 개념을 제시했다.

쇼어 알고리즘, 그로버 알고리즘은 양자컴퓨터가 고전 컴퓨터보다 특정 연산에서 빠를 수 있다는걸 증명했다.

결국 양자컴퓨터에서 어려운 것은:
양자 오류 정정(Quantum Error Correction)을 활용한 Qubit 제어가 어려운 것이다.

양자컴퓨터 구조:
Physical Layer와 Logical Layer가 있다.

physical layer:
Lattice of superconducting qubits and resonators로 만들어진 physical quantum processor가 있고,
여기에 control을 위한 microwave pulses, readout을 위한 quantum-limited amplifiers가 있고
quantum error correction을 위한 부분이 있다.

Logical layer:
여기는 Shor, Grover의 quantum simulation들이 돌아간다.

쇼어 알고리즘:
양자 푸리에 변환을 사용한다.
빠른 소인수분해로 암호 해독을 빠르게 할 수 있다.

그로버 알고리즘:
찾으려는 값의 확률진폭을 키우는 과정을 반복해서, 고전 알고리즘 대비 복잡도를 최대 루트N배 낮출 수 있다.


큐비트를 구현하는 방법은 상당히 다양하다.

반도체 양자점, 초전도 등등

반도체 양자점 큐비트 방식은 양자점으로 양자정보처리를 한다.


X게이트, Z게이트: 단일 큐비트 게이트
CNOT 게이트: 다중 큐비트 게이트
X게이트는 NOT gate와 같은 역할을 한다.


양자점을 만들떄:
AlGaAs, GaAs를 붙여놓고 전압을 걸면, 접합면에서 전자가 전위 우물에 갇혀 양자점이 생긴다.


