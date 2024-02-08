---
layout: post
title:  "Layout"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 10
---

일단 적을 수 있는거 몽땅 적어놓겠다.

-. 특정 기능을 수행하는 회로를 칩으로 제작할 수 있게 물리적으로 패턴으로 구현한 것

-. 반도체 설계 과정 중 하나
   ① 회로설계
   ② 레이아웃설계
-. 설계가 완료된 회로는 칩으로 만들기 위해 일정한 규칙을 갖는 물리적 패턴으로 변환시켜 주어야 하는 과정을 레이아웃 설계 또는 마스크 패턴(Pattern) 설계라고 함
   ① 패턴은 마스크로 제작 되어짐
   ② 실리콘 웨이퍼 위에 패턴을 형성하는 매개체 역할을 하게 됨-. 회로 설계된 결과를 실제 Wafer상에 구현하기 위한 Mask Data를 형상화 하는 작업
-. 회로 설계 관련 Spec을 이용하여 구현하고자 하는 논리 설계 및 회로 설계를 마친 이후, 회로와 동일한 전기적 접속 관계를 만족하는 Pattern 설계를 수행하는 것을 말함
-. Layout에는 Full-Custom(Cell, Block, I/O,...Shrink, Analog)인 Manual Layout 설계방식과
   Auto Layout 설계 방식이 있음


-. Normal Flow (Block, Full Chip Layout에 적용)
※ DRC검증 Rule을 Normal Design Rule 사용
① Pre-Meeting
② 1st sign-off
③ Feasibility Study ※ 상황에 따라 생략 가능
④ Layout Start
⑤ Customer Review & Layout Fix
⑥ Verification
⑦ Post-Layout Simulation⑧ DB 전달
⑨ 최종 Sign-off
⑩ Layout 종료

-. Standard Primitive Cell 제작 Flow (for P&R<D/K> STD-Prim Layout에 적용)
※ Standard Primitive는 해당 공정의 Design Kit로 사용되며 Full Chip P&R시 사용
※ Verification 단계가 2단계로 구성. DRC검증 Rule을 Special Design Rule 사용
① Pre-Meeting
② 1st sign-off
③ Feasibility Study ※ 상황에 따라 생략 가능
④ Layout Start
⑤ Customer Review & Layout Fix
⑥ 1st Verification w.i Via1 Cell
⑦ 1st Post-Sim w.i Via1 Cell
⑧ Customer Review w.o Via1 Cell
⑨ Final Verification w.o Via1 Cell
⑩ 2nd Post-Sim w.o Via1 Cell
⑪ DB 전달
⑫ 최종 Sign-off
⑬ Layout 종료


-. Standard IO Cell 제작 Flow (for P&R<D/K> STD-IO Layout에 적용)
※ DRC검증 Rule을 Special Design Rule 사용
① Pre-Meeting
② 1st sign-off
③ Feasibility Study ※ 상황에 따라 생략 가능
④ Layout Start
⑤ Customer Review & Layout Fix
⑥ Verification
⑦ Post-Layout Simulation
⑧ DB 전달
⑨ 최종 Sign-off
⑩ Layout 종료


-. Layout Design 사전준비
① System Library Set up for Layout Design
    * Design Directory 생성, ... 등 
② 공정 자료집 입수
    * Design Rule Spec
    * E/R Spec 입수
    * Layout Guide 및 주의사항, ... 등
③ 회로도 & Netlist 입수
④ 검증 (LVS, DRC, Antenna, LPE, ... 등) Rule 입수
⑤ Layout GRID 설정
⑥ 입수된 회로도를 이용한 Floor Plan (가배치 포함)
⑦ Estimate Layout TAT (Turn-Around Time) 산출


-. Layout Design 세부설계 진행방향
① 기본 소자 (저항, CAP, INDUCTOR, TR 등) 구조 이해
② Block Layout 진행 시 회로도와 Layout간의 Matching
③ 저항, CAP의 matching
④ Transistor의 matching
⑤ 공정 편차에 따른 Layout Methodology 고려
⑥ 수율 향상을 고려한 Layout Design
⑦ Latch up 및 Noise를 고려한 Layout
⑧ Block Guardring

Floor Plan이란?
-. IC 설계 공정에서의 레이아웃의 일부를 말하는 것
-. Transistor 배치가 아닌 Block 단위 배치를 말함
 
Chip floor plan을 할 때 고려해야 할 3가지
-. Noise의 영향
   The farer distance between analog and digital ckt, the lowernoise effect to analog from digital
   (1) Noise의 민감도는 Digital에서 Analog로 갈 수록 민감도가 커지지만,
        Noise는 Analog에서 Digital로 갈수록 커짐
   (2) Analog와 Digital의 Power는 반드시 분리하며, 특별히 주의가 필요한 Block의 경우 추가로 Power를 분리
-. 배선의 간소화
   The sensitive analog lines are as short as possible
-. Chip 면적의 최소화
   Considering the cost, we must care the smallest chip Area floor plane


-. Design Rule: Layout을 하기 전 반드시 필요한 File이며 공정 별로 Rule이 다름
-. Layout Notice
-. Critical / Dirty Path
-. Power / GND Path
-. Resistance / Capacitance of Path
-. Device Multi-place: 크기가 큰 Device의 경우 여러 개로 나누어 배치
-. Substrat Contact
-. ESD / Latch-up
-. PIN / PAN Assignment for Assembly
-. DRC / LVS (Clean)
-. Origin
-. Logo

https://blog.naver.com/kwon96812521/222676812185

