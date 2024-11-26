---
layout: post
title:  "Digital - OSI model"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 5
---

1\. Physical Layer
전기적 신호, 물리적 계층
RS232, RS485, 이더넷 등 전기적 특성 규정

Media, signal, and binary transmission
RS-232, RJ45, V.34, 100BASE-TX, SDH, DSL, 802.11

전송 단위: 비트
대표 장치: 케이블, 안테나, 앰프, 네트워크 허브, 리피터 등
프로토콜: 이더넷, USB 등 케이블 , Bluetooth, Wi-Fi, LTE, 5G 등 안테나


2\. Data link layer
1계층의 전기적 신호에 대한 포맷과 오류 수정 처리
예를 들어 START BIT - DATA - PARITY - STOP BIT, CRC 등

Physical Addressing
Ethernet, 802.11, MAC/LLC, VALN, ATM, HDP, Fibre channel,
Frame Relay, HDLC, PPP, Q.921, Token Ring

전송 단위: frame
대표 장치: L2 Switch, 모뎀, 기지국, AP
프로토콜: CSMA/CD, CSMA/CA, Slott Aloha, DAC/ADC, Multiplexer, Demultiplexer, MAC주소 관리 등


3\.  Network layer
통신하는 장치에 대한 통신 경로 및 논리주소 결정
IP주소, 라우터 기능

Path Determination and Logical Addressing
IP, ARP, IPsec, ICMP, IGMP, OSPF

전송 단위: Packet(패킷)
대표 장치: Router(라우터), L3 Switch
프로토콜: IP, ARP/NDP, RIP, RIP v2, OSPF, IGRP, EIGRP, BGP 등등의 Routing Protocol, AS번호, NAT 등


4\.  Transport layer
어떤 프로토콜로 데이터를 주고받을 것인가 결정
TCP 포트 번호(FTP, HTTP, TELNET 등)

End to end connections and Reliability
TCP, UDP, SCTP, SSL, TLS

전송 단위: Segment(세그먼트)
대표 장치: L4 Switch
프로토콜: TCP, UDP


5\.  Session layer
통신 중 상태를 점검하고 유지, 제어하는 역할

Interhost communication
Session Establishment in TCP, SIP, RTP, RPC-named pipes

대표 장치: L4 Switch
프로토콜: RPC, NetBIOS


6\.  Presentation layer
통신해서 얻은 데이터 처리
Encoding(암호화), Decoding(복호화), 압축 등

Data representation and Encryption
Recognizing Data: HTML, DOC, JPEG, MP3, AVI, Sockets

프로토콜: ASCII, 유니코드, MIME, EBCDIC, UTF-8, MBCS. EUC-KR, JPG, MP3, MPEG 등


7\.  Application layer
사용자 인터페이스 제공
이메일, 웹브라우저, FTP 등

Network process to application
DNS, WWW/HTTP, P2P, EMAIL/POP, SMTP, Telnet, FTP

전송 단위: Message 또는 Data
대표 장치: L7 Switch, 방화벽
프로토콜: FTP, HTTP, HTTPS, XML, Telnet, SSH, SMTP, POP3, IMAP 등

