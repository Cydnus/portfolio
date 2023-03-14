---
title: 딥러닝을 활용한 숫자 수화인식
author: Cydnus
date: 2019-11-24 18:00:00 +0900
categories: [안양대학교, 졸업논문/프로젝트]
tags: [Python, OpenCV, Tensorflow, Keras]
---

> 안양대학교 컴퓨터공학과 졸업 논문 / 프로젝트입니다.

> 소스는 [여기](https://github.com/Cydnus/Study_files/tree/main/Certificated_Programs/%EC%BB%B4%ED%93%A8%ED%84%B0%EA%B3%B5%ED%95%99%EA%B3%BC/%EC%88%AB%EC%9E%90%EC%88%98%ED%99%94%EC%9D%B8%EC%8B%9D)에서 확인 가능합니다.

### Summary

- 중국 발 미세먼지로 인하여 한국내 미세먼지 농도 안좋은 상황
- 자동차 매연으로 인하여 미세먼지 양 증가
- 겨울이 되어 감에 따라 화석연료 난방에 의한 미세먼지 양 증가

### Environment

- Hardware
  - CPU : intel i7-8550U
  - RAM : 8GB
  - GPU : Nvidia Geforce MX 150
- OS : Windows 10 Education x64
- Language : Python
  - Anaconda 1.7.2
  - Python 3.7.3
  - Ipython 7.6.1
  - Module
    - tensorflow-gpu 1.15.0
    - Ndivia Cuda v.10
    - Ndivia Cudnn v.10
- IDE : Jupyter notebook 6.0.0

### Construction

#### 1. 전처리 및 특징 추출

    1. 이미지 추출
      - 이미지 크기 조정
      - YCrCb를 이용하여 피부색 검출
    2. 이미지 증폭
      - 확보된 데이터셋을 ImageDataGenerator를 통하여 데이터 증폭
    3. 정규화
      - 100X100 사이즈의 이미지의 각 픽셀을 0 ~ 1 사이로 정규화
    4. 분류
      - K-Way 검증 방식(5-Way)를 위한 학습 데이터와 검증 데이터로 나눔

#### 2. 모델구성

- 모델 개요

  ![model image](/posts/191124_GP/model.png)

  - VGG 16 / 19 모델을 참고하여 작성

- Optimizer : RMSProp

#### 3. 학습 결과

![1-Way](/posts/191124_GP/index1.png)

![2-Way](/posts/191124_GP/index2.png)

![3-Way](/posts/191124_GP/index3.png)

![4-Way](/posts/191124_GP/index4.png)

![5-Way](/posts/191124_GP/index5.png)

#### 4. 테스트

- 테스트 방식

  1. 기존에 확보된 이미지 중 학습/검증에 사용하지 않은 이미지 추출
  2. 테스트 데이터 전처리
  3. 학습 완료된 모델의 가중치 불러오기
  4. 전처리한 데이터를 모델에 적용

- 테스트 결과

  - 정확도 : 60 ~ 80%

  ![test result](/posts/191124_GP/Test_Result.png)

### Result

![Run](/posts/191124_GP/run.gif)

### Improvements

- 인식률 높이기
  - 인식률이 낮은점 개선
  - 비슷한 이미지에서 다르게 판별하는 상황 개선
- 인식량 늘리기
  - 숫자만 인식하는 것에서 문자, 단어까지 인식하도록 개선
