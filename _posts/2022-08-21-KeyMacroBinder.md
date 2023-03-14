---
title: 아두이노 키보드 매크로 바인더
author: Cydnus
date: 2022-08-21 18:00:00 +0900
categories: [개인 프로젝트, Qt Framework]
tags: [C++, Qt Framework, Arduino, Serial Communication]
---

> 자세한 소스는 [여기](https://github.com/cydnus/study_files/tree/main/QtFramework/KeyMacroBinder)에서 확인이 가능합니다.

## Summary

자주 사용하지만 한꺼번에 누르기 힘든 여러개의 키, 가끔 사용하지만 어떠한 키 조합인지 까먹게 되는 키들을 한번의 버튼을 누르는 것만으로 처리가 가능하게 하고자 제작한 아두이노 매크로 키보드의 키 맵핑을 쉽게 하기 위해 만든 프로그램

## Environment

- Arduino
  - Board : Arduino Pro Micro (Leonardo series)
  - Language : C/C++
  - IDE : arduino ide
- PC
  - OS : Windows 10
  - Language : C++
  - IDE : Qt Creator
  - OneFile Build
    - OS : Ubuntu 22.04
    - mxe cross static compile

## Construction

1. 아두이노 연결
2. 아두이노에서 값 읽어오기
3. 버튼에 키 추가/수정
4. confirm 시 값 전송

## Protocol

<table>
  <tr>
    <td>Frame Byte</td>
    <td>Op Code</td>
    <td >Data</td>
    <td >Frame Byte</td>
  </tr>
  <tr>
    <td>0xFC</td>
    <td>opcode</td>
    <td> Data bytes</td>
    <td>0xFC</td>
  </tr>
</table>
- PC to Arduino
<table>
  <tr>
    <td></td>
    <td>상위 4bit</td>
    <td>하위 4bit</td>
    <td>Data bit</td>
  </tr>
  <tr>
    <td>전체 키맵 조회</td>
    <td>A</td>
    <td>0</td>
    <td>0x80</td>
  </tr>
  <tr>
    <td>개별 키바인딩</td>
    <td>3</td>
    <td>키번호(0-F)</td>
    <td>키 코드(ASKII + @) + 0xff</td>
  </tr>
</table>

- Arduino to PC
<table>
  <tr>
    <td></td>
    <td>상위 4bit</td>
    <td>하위 4bit</td>
    <td colspan=3>Data bit</td>
  </tr>
  <tr>
    <td>전체 키 리스트</td>
    <td>A</td>
    <td>0</td>
    <td>키 번호</td>
    <td>키 코드</td>
    <td>0xFF(키 구분자)</td>
  </tr>
  <tr>
    <td>저장 완료</td>
    <td>4</td>
    <td>키번호</td>
    <td colspan=3></td>
  </tr>
</table>

## Result

![결과](/posts/220428_keybinder/result.gif)

## Improvements

- 아두이노 자동연결
  - 장치명등 변경하여 접근 필요
- 아두이노 자체 EEPROM 용량 및 쓰기 사이클 문제
  - 외부 EEPROM 장착하여 해결해야함 / 와이어링 다시 할 필요
