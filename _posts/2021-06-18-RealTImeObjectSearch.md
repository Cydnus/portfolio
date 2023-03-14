---
title: 실시간 객체 탐지
author: Cydnus
date: 2021-06-18 18:00:00 +0900
categories: [대한상공회의소 서울기술교육센터, Bigdata(python)]
tags: [Python, OpenCV, Numpy, MatPlotlib, Pandas]
---

> 대한상공회의소 서울기술교육센터에서 진행하였던 Bigdata과목 학습 내용입니다.

> 소스는 [여기](https://github.com/Cydnus/Study_files/tree/main/Certificated_Programs/IoT%EA%B8%B0%EB%B0%98%20%EC%8A%A4%EB%A7%88%ED%8A%B8%ED%8C%A9%ED%86%A0%EB%A6%AC%20SW%EA%B0%9C%EB%B0%9C%20%EC%A0%84%EB%AC%B8%EA%B0%80%20%EA%B3%BC%EC%A0%95/BigData(python)/%EC%9B%B9%EC%BA%A0%20%26%20yolo)에서 확인 가능합니다.

### Summary

AI가 발전함에 따라서 학습 및 테스트 데이터의 전처리 및 실생활에 적용에 사용되는 영상처리의 기술의 중요성도 증가가 되고있다. 이 프로그램은 OpenCV와 학습된 데이터를 활용하는 영상처리의 예를 보여준다.

### Environment

- OS : Windows 10
- Language : python 3.8 (ananconda)
- IDE : Jupyter Notebook

### Key Feautres

- caffe로 학습된 가중치 불러오기
- 이미지에 존재하는 객체를 인식 및 구분
- 이미지에 존재하는 객체에 표시

### Key Source

```python
while done:
    ret, image = cap.read()
    if ret :
        (h,w) = image.shape[:2]
        blob = cv2.dnn.blobFromImage(cv2.resize(image,(300,300)),
                                     0.007843,
                                     (300,300),
                                     127.5)
        net.setInput(blob)
        detections = net.forward()

        for i in np.arange(0,detections.shape[2]):
            confidence = detections[0,0,i,2]
            if confidence > 0.2 :
                idx = int(detections[0,0,i,1])
                box = detections[0,0,i,3:7] *np.array([w,h,w,h])
                (sx,sy,ex,ey) = box.astype('int')

                label = '{} : {} %'.format(CLASSES[idx],confidence *100)
                cv2.rectangle(image,(sx,sy),(ex,ey), COLORS[idx],2)
                y = sy -15 if sy -15 > 15 else sy +15
                cv2.putText(image,
                            label,
                            (sx,y),
                            cv2.FONT_HERSHEY_SIMPLEX,
                            0.5,
                            COLORS[idx],
                            2)
        cv2.imshow('Detection',image)
        key = cv2.waitKey(delay)
        if key == ord('q'):
            break
```

### Result

![출력](/posts/210618_RTOS/result.gif)
