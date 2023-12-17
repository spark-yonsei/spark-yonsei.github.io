---
layout: post
title:  "KETI 세미나 내용"
date:   2023-10-04 19:31:29 +0900
categories: Miscellaneous
order: 9
---

KETI 세미나 내용:<br>
KETI에는 부서가 4개 있다. 센서, 디스플레이, 반도체2개인데, 강연해주신 분은 반도체 부서에서 오신 분이다. 부서 이름에 ‘융합신호’가 들어가는데, 아날로그, 디지털, RF 등 다양한 신호 관련인 듯 하다. 융합신호SoC어쩌구 부서다.<br>
<br>
거기서 RFIC를 하신다고 한다. 무선통신, 레이더센서, 고주파증폭기 등을 한다. mmWave, ARM기반 신호처리 SoC도 한다고 한다.<br>
<br>
고속 ADC, DAC 기반 재밍 신호처리 SoC 기술을 만들어 LIG넥스원에 납품했고, 전류측정 SoC를 IEEE Sensors에 냈고, 칩끼리 통신을 위한 고속 인터페이스 기술을 만들어 IEEE JSSC에 냈다.<br>
<br>
원래 이런 고속 인터페이스 기술 하던 곳이 퀄리타스반도체다. 삼성전자랑 TSMC에 납품한다는데, TSMC에는 왜 파는거지?<br>
<br>
요즘 센서들은 ADC, DAC, DSP, AI까지 들어가며 점점 더 복잡해지고 있다. 그래서 발전 방향이 2가지다.<br>
1\. 데이터가 너무 많으니까, 데이터 전송을 강화해서 다 슈퍼컴퓨터로 보내버리자.<br>
2\. 그 많은 데이터를 각 node에서 처리할 수 있도록 node 안 프로세스를 강화하자.<br>
<br>
전기차에서는 1번 방식을 많이 쓰고, 쏘카같이 운전하는 사람을 못믿는 경우에도 1번 방식으로 모니터링한다.<br>
<br>
신호처리에 FFT, CWT, MFCC, Reconfigurable filter등이 쓰인다. MFCC는 음성신호, 마이크 등에 많이 쓰이는 방식이다.<br>
<br>
ROIC: Readout Integrated Circuit<br>
FIB(Focused Ion Beam) 장비를 KETI가 갖고 있는데, 100억짜리다.<br>
이 부서에서 하려고 하는건 경량 인공지능 NVM 기반 센서보정기술, SoC수준 센서 시스템 등이다. 여기서 말하는 NVM은 Non-volatile memory 맞나<br>
<br>
CIS(CMOS Image Sensor인지 Contact Image Sensor인지 확인해야된다?)는 Clock이 너무 좁아서 SAR을 못쓴다. 지금은 Single Slope를 쓴다.<br>
<br>
Self Capacitance sensor, mutual capacitance sensor가 있다.<br>
<br>
요즘은 그냥 광센서보다도 라이다 관련을 많이 한다.<br>
<br>
쓰는 공정은 삼성전자 LF6S, TSMC 40nm, 180nm다.<br>
<br>
레이더에는 STFT가 쓰인다.<br>
<br>
요즘에는 인공지능이 MCU에서도 돌아가도록, 가벼운 모델들이 나온다.<br>
<br>
현대차는 딥러닝을 불신하지만, 그래도 머신러닝은 한다.<br>
Semi-Superimposed Learning 기반 SVM을 쓴다. SVM: Support Vector Machine<br>
<br>
PIM(Processing In Memory)는 AI 연산량을 줄이려고 쓴다.<br>
PHM: Prognostics and Health Management. 사고가 일어나기 전에 잡으려고 하는거다. 얘도 SVM을 쓴다.<br>
<br>
UAM: Urban Air Mobility, 약간 대중교통 비행기 같은 것 같다.<br>
<br>
KETI에서는 레이더를 계속 한다. 자율주행에는 레이더 라이다 카메라 다 있는게 좋기도 하고, 레이더는 아무나 쉽게 진입할 수 있는 분야가 아니다.<br>
<br>
옛날에는 24GHz 레이더 많이 썼는데, 요즘은 77, 79GHz가 많이 나온다.<br>
<br>
현재 KETI에서는 FMCW레이더와 Radar Signal Processing Block을 따로 개발중인데, 나중에는 같이 하려고 한다.<br>
<br>
구글이 옛날에 인피니온과 함께 ‘Soli’라는 프로젝트로 레이더 만든 적이 있다고 한다.<br>
<br>
전파연구원은 아직 100GHz 위 주파수를 할당한 적 없다. 일부러 막은건 아니고, 이 주파수도 쓸 수 있는 사람이 나타나면 할당해줄 의향 있다고 한다.<br>
<br>
근데 주파수가 100GHz쯤 되면 감도는 좋지만 직진성이 너무 강하다. 거의 빛이다.<br>
유럽의 실리콘밴드라는 회사가 이 대역을 쓰는 제품을 만들었다고는 하는데, 검색해도 잘 안나온다.<br>
<br>
레이더는 라이다만큼 정확한 형태를 볼 수는 없다. 하지만 비나 눈이 오면 라이다가 아무것도 못한다. 또, 라이다는 렌즈도 있어야 한다. 물론 라이다는 resolution이 좋긴 하다.<br>
<br>
사실 60GHz만 해도 직진성이 엄청 강하지만, Phase Shifter를 써서 120도 정도를 본다.<br>
<br>
차 밖을 보는 데에 77GHz 레이더를 많이 쓴다.<br>
<br>
통신에서 FDD, TDD, 레이더/안테나에서 2T2R, 2T4R이 뭔지 확인해보자.<br>
<br>
우리나라 팹리스업체 중 레이더 하는 회사는 없다 아마 너무 어려워서 같다.<br>
최근에는 TI, 인피니온이 레이더 많이 한다.<br>
작년 사이언스 표지가 Radar Revolution이었다.<br>
<br>
KETI도 FFT에서 STFT, CWT로 가려고 한다고 한다. 그래서 이게 머신러닝에서 도움받기 위해서냐고 질문했는데, 그건 아니라고 한다. 그냥 시간 주파수 같이 보려고 한건가? 하여간 내 입장에서는 시간-주파수가 머신러닝에 도움 될 부분이 있는지 생각해보자.<br>
<br>
CNN은 너무 무거워서, 여기서는 binarized CNN을 쓴다.<br>
<br>
삼성전자는 RF공정 지원 안해준다.<br>
