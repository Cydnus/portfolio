---
title: 미세먼지 알림 어플
author: Cydnus
date: 2018-12-11 18:00:00 +0900
categories: [안양대학교, 소프트웨어공학]
tags: [Android, JAVA, OpenAPI]
---

> 안양대학교 컴퓨터공학과 소프트웨어 공학 과제 팀 프로젝트입니다.

> 소스는 [여기](https://github.com/Cydnus/Study_files/tree/main/Certificated_Programs/%EC%BB%B4%ED%93%A8%ED%84%B0%EA%B3%B5%ED%95%99%EA%B3%BC/%EB%AF%B8%EC%84%B8%EB%A8%BC%EC%A7%80%EC%96%B4%ED%94%8C)에서 확인 가능합니다.

### Summary

- 중국 발 미세먼지로 인하여 한국내 미세먼지 농도 안좋은 상황
- 자동차 매연으로 인하여 미세먼지 양 증가
- 겨울이 되어 감에 따라 화석연료 난방에 의한 미세먼지 양 증가

### Environment

- OS : Windows 10
- Language : JAVA
  - JRE : 1.8.0_152-release-1136-b06 amd64
  - JVM : OpenJDK 64-Bit Server VM by JetBrains s.r.o
- IDE : Android Studio 3.2.1 - build : #AI-181.5540.7.32.5056338, built on October 9, 2018
  -Target : Android 7.0.1 ( API 25 )

### Prerequisite

- 기상청, 환경부, 각 시 도 군청 등
  여러 곳에서 미세먼지에 대한 알림
- 한국 환경 공단에서
  미세먼지에 대한 측정소별 측정

### Research

- 국민안전처 미세먼지 경보 알림 존재
- 미리 제작되어 있는 어플리케이션 존재

### Target

- 사용자 지정 알림 서비스 제공
- GPS 기반 및 사용자의 지역 검색으로 미세먼지 상태 제공

### Data Flow Diagram

- 배경도

![배경도](/posts/181211_micro/back.png)

- 전체적인 흐름

![DFD1](/posts/181211_micro/dfd1.png)

![DFD2](/posts/181211_micro/dfd2.png)

![DFD3](/posts/181211_micro/dfd3.png)

### Structures design

![Structures design 1](/posts/181211_micro/sd1.png)

![Structures design 2](/posts/181211_micro/sd2.png)

![Structures design 3](/posts/181211_micro/sd3.png)

### NS-Chart

![NS-Chart](/posts/181211_micro/NS.png)

### Result

![running video](/posts/181211_micro/running.gif)
