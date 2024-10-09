---
layout: post
title:  "Digital - OSI model"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 5
---

1\. Physical Layer
전송 단위: 비트
대표 장치: 케이블, 안테나, 앰프, 네트워크 허브, 리피터 등
프로토콜: 이더넷, USB 등 케이블 , Bluetooth, Wi-Fi, LTE, 5G 등 안테나


2\. Data link layer
전송 단위: frame
대표 장치: L2 Switch, 모뎀, 기지국, AP
프로토콜: CSMA/CD, CSMA/CA, Slott Aloha, DAC/ADC, Multiplexer, Demultiplexer, MAC주소 관리 등


3\.  Network layer
전송 단위: Packet(패킷)
대표 장치: Router(라우터), L3 Switch
프로토콜: IP, ARP/NDP, RIP, RIP v2, OSPF, IGRP, EIGRP, BGP 등등의 Routing Protocol, AS번호, NAT 등


4\.  Transport layer
전송 단위: Segment(세그먼트)
대표 장치: L4 Switch
프로토콜: TCP, UDP


5\.  Session layer
대표 장치: L4 Switch
프로토콜: RPC, NetBIOS


6\.  Presentation layer
프로토콜: ASCII, 유니코드, MIME, EBCDIC, UTF-8, MBCS. EUC-KR, JPG, MP3, MPEG 등


7\.  Application layer
전송 단위: Message 또는 Data
대표 장치: L7 Switch, 방화벽
프로토콜: FTP, HTTP, HTTPS, XML, Telnet, SSH, SMTP, POP3, IMAP 등

