---
layout: post
title:  "Digital - ISA"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 5
---

CPU: Central Processing Unit<br>
ISA: Instruction Set Architecture<br>
<br>
ISA는 CPU에서 사용되는 명령어들의 집합을 말한다.<br>
정상적인 CPU 동작을 위해서는 그 CPU에 맞는 ISA를 사용해야 한다.<br>
<br>
ISA는 크게 RISC 계열과 CISC 계열이 있다.<br>
ARM CPU는 RISC, x86-64 CPU는 CISC 계열 ISA를 사용한다.<br>
<br>
RISC ISA는 명령어 수를 최소화하고, 명령어 크기를 고정한 ISA다.<br>
각 명령어들의 동작을 최적화해 효율을 높인다.<br>
<br>
CISC ISA는 여러 명령어들을 묶은 복합 명령어를 많이 갖고 있는 ISA다.<br>
그래서 한 개 명령어로 구현할 수 있는 동작이 많다.<br>
<br>
<br>
RISC CPU
명령어 수 적음
명령어 크기 고정
1개 명령어 처리속도 빠름
프로그래밍 코드 복잡


CISC CPU
명령어 수 많음
명령어 크기 명령어마다 다름
1개 명령어 처리속도 명령어마다 다름
프로그래밍코드 단순



왜 cisc는 명령어마다 길이가 다르냐?
여러 명령들을 묶어서 만든 복합 명령들이 많아서 그렇다

Risc는 명령 크기를 16비트, 32비트 이런식으로 고정해둔다

처리 속도:
Risc는 명령어마다 1클럭 또는 2클럭 안에 끝내게 되어 있다
Cisc는 명령어마다 다르다. 복합 명령들이 읶으니까

프로그래밍 편의:
Cisc에서 모든 명령을 다 숙지하고 있다면, 딱 적합한 명령어를 써서 프로그래밍을 단순하게 할 수 있다

근데 그렇게 되는거 자체거 힘든 일이라, 꼭 cisc가 risc보다 프로그래밍이 쉽다고는 할 수 없다