---
title: "Dell Power Edge R730 Rocky Linux 9 설치 기록"
last_modified_at: 2023-01-17 14:00:00 + 09:00
categories:
  - Server
tags:
  - Dell
  - Power Edge
  - R730
  - Firmware
---

Dell Power Edge R730 Rocky Linux 9 설치 기록
===


TCP 서버를 하나 만드려고 보니 설치할 곳이 없어서 방치된 서버 하나를 통째로 밀고 새로 설치하기로했다.

ESXi 설치를 제외하고는 모두 모니터와 키보드 마우스 연결해서 세팅했고 ESXi는 USB꽂아서 해보려다가 도저히 USB로 부팅이 안돼서 그냥 idrac 라는 dell 전용 콘솔 포트로 진행했다.


간단하게 대단위만 묶으면 아래와 같은 순서로 진행이 필요하다.

1. 펌웨어 업데이트

2. 레이드 설정

3. vmware 설치 - 라이선스 등록 방법 - https://lifegoesonme.tistory.com/399

4. Rocky Linux 설치


***









<!--

주석 위치

-->




