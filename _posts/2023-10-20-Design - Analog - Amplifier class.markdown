---
layout: post
title:  "Analog - Amplifier Class"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Amplifier는 동작 방식에 따라 'class'로 구분된다.<br>
<br>
Amplifier는 동작 방식에 따라 효율이 결정되는데,<br>
효율이 높은 amplifier는 linearity가 낮고,<br>
효율이 낮은 amplifier는 linearity가 높다는 특징이 있다.<br>
즉, amplifier의 class를 확인하면 동작 방식, 효율, linearity를 파악할 수 있다.<br>
<br>
<br>
Class A, B, AB, C:<br>
Output Stage 트랜지스터들이 gain을 만든다.<br>
Output Stage 트랜지스터들이 효율을 위해 잠시 꺼졌다 켜지기도 한다.<br>
효율이 낮지만 linearity가 높다.<br>
<br>
Class D, E, F, G, S, T:<br>
Gain이 전원 전압에 비례한다.<br>
Output stage TR들이 완전히 껐다 켜지며 PWM(Pulse Width Modulation) 동작을 한다.<br>
효율이 높지만 linearity가 낮다.<br>
<br>
<br>
Class A amplifier:<br>
Class A amplifier는 Output 트랜지스터 하나가 항상 켜져있는 구조다.<br>
트랜지스터가 계속 켜진 상태로 gain을 만들기 때문에, gain이 크고 linearity가 높다.<br>
대신, 항상 켜져있기 때문에 전류 소비도 계속 일어나 전력 효율이 나쁘다.<br>
<br>
그래서 high-fidelity audio amplifier 등 고성능 amplifier가 필요한 곳에 쓰이지만,<br>
효율이 나쁜 만큼 발열이 심해 고전력 회로에서는 사용하기 어렵다.<br>
<br>
<br>
Class B amplifier:<br>
Class B amplifier는 Output 트랜지스터 2개가 번갈아 켜지는 구조다.<br>
input signal이 positive일 때는 위쪽 트랜지스터만, negative일 때는 아래쪽 트랜지스터만 켜지는 구조다.<br>
이런 구조를 push-pull 구조라고 부른다.<br>
<br>


class A amplifier보다는 효율이 높은 구조지만, 새로운 문제가 또 생긴다.


입력 전압이 -0.7V~0.7V동안은 위아래 트랜지스터가 둘 다 꺼져서 출력이 안나온다.

이거때문에 zero-crossing distortion(Crossover distortion이라고도 한다)이 생겨서,
class B amplifier는 audio amplifier같은 곳에 못쓴다.





Class AB amplifier:
이름에서 보이듯, Class A랑 Class B를 합친 구조다.
audio power amplifier design에서 많이 쓰이는 구조다.

class B를 조금 변형한 구조인데, crossover point에서 두 트랜지스터가 꺼지지 않고 켜져있는 구조다.

여기 들어가는 트랜지스터들은 걸려있는 bias voltage가 아주 작다. cutoff point보다 아주 조금 높은 전압이다.
이렇게 되면 트랜지스터가 조금 더 오래 켜져있다. half cycle보다 조금 더 길게 켜져있다.

Class B는 half cycle보다 짧게, Class A는 항상 켜져있으니 그 사이에 있다는 의미로 class AB라 한다.
하여간, half cycle보다 길게 켜져있기에, crossover distortion이 일어나지 않는다.
efficiency는 50~60% 정도다.

Class C amplifier:
Class C amplifer는 효율이 꽤 높지만, linearity가 많이 떨어진다.
Class A, AB, B는 linear amplifier로 분류되지만, C는 그렇지 못한다.

Class C amplifier는 절반도 훨씬 안되게, 90도 정도만 켜진다.
그래서 효율은 80%정도 되긴 하는데, 엄청난 distortion이 생긴다.
Sine wave가 들어오면 머리만 참수해서 내보내는 수준이니까.

그래서, class C amplifier는 high frequency sine wave oscillator나 RF amplifier에 쓰인다.
고주파에서는 amplifier에 의해 발생한 current가 LC resonance circuit에 의해 특정 주파수의 sine wave로 바뀔 수 있기 때문이다.

class D~T는 switching operation을 한디.