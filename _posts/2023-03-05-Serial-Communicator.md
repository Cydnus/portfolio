---
title: Serial Communicator
author: Cydnus
date: 2023-03-05 18:00:00 +0900
categories: [개인 프로젝트, Qt Framework]
tags: [C++, Qt Framework, Serial Communication]
---

> 자세한 소스는 [여기](https://github.com/Cydnus/Study_files/tree/main/QtFramework/SerialCommunicator)에서 확인이 가능합니다.

## Summary

유명 프로그램 Serial Com 프로그램을 따라서 제작. 해당 프로그램의 단점인 COM포트가 10이 최대인 점을 20까지 확장

## Environment

- OS : Windows 10
- Language : C++
- IDE : Qt Creator
- OneFile Build
  - OS : Ubuntu 22.04
  - mxe cross static compile

## Construction

1. 최근 실행 값 불러오기 (QSetting)
2. Serial Setting
3. 연결
4. 값 전송 및 읽기 대기

## Result

![결과](/posts/230305_SerialCom/result.gif)

## Improvements

- Add CR/LF
  : 제대로 작동하는지 의문(기존 프로그램도 마찬가지)
- Received Data 값들 저장
  : 메뉴바 구현
- 리눅스에서도 작동하기 위한 처리
