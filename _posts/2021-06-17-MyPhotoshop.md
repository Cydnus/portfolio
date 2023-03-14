---
title: Simple Photo Editer
author: Cydnus
date: 2021-06-17 18:00:00 +0900
categories: [대한상공회의소 서울기술교육센터, Bigdata(python)]
tags: [Python, OpenCV, Numpy, MatPlotlib, Pandas]
---

> 대한상공회의소 서울기술교육센터에서 진행하였던 Bigdata과목 학습 내용입니다.

> 소스는 [여기](<https://github.com/Cydnus/Study_files/tree/main/Certificated_Programs/IoT%EA%B8%B0%EB%B0%98%20%EC%8A%A4%EB%A7%88%ED%8A%B8%ED%8C%A9%ED%86%A0%EB%A6%AC%20SW%EA%B0%9C%EB%B0%9C%20%EC%A0%84%EB%AC%B8%EA%B0%80%20%EA%B3%BC%EC%A0%95/BigData(python)/Day09>)에서 확인 가능합니다.

### Summary

OpenCV를 통한 이미지 처리 방식을 학습하는 것을 목표로 만든 프로그램이다.

### Environment

- OS : Windows 10
- Language : python 3.8 (ananconda)
- IDE : Jupyter Notebook

### Key Feautres

- 이미지 불러오기, 저장
- 회전, 확대/축소, 상하반전, 좌우반전
- 이미지 블러링, 엠보싱, 흑백이미지, 밝게/어둡게

### Key Source

- 이미지 출력

```python
def Display_Image():
    global  window ,openimg,canvas

    img = ImageTk.PhotoImage(openimg)
    print(openimg.size)
    window.geometry('%sx%s'%(openimg.size[0],openimg.size[1]))
    canvas.delete('all')
    canvas.width = openimg.size[0]
    canvas.height = openimg.size[1]
    canvas.create_image(0, 0,anchor='nw' ,image=img )
    canvas.image =img
    canvas.pack(expand=True, fill='both')

```

- 확대

```python
def Enlargement():
    global openimg
    if openimg == None :
        return

    scale = simpledialog.askinteger('확대','확대할 배율을 입력하세요(2~4)',minvalue = 2,maxvalue=10)
    width = openimg.size[0]
    height = openimg.size[1]
    img2 = cv2.resize(PILToNpArray(openimg),(int(scale*width), int(scale * height)),interpolation=cv2.INTER_CUBIC)
    openimg = None
    openimg = NpArrayToPIL(img2)
    Display_Image()
```

### Result

![출력](/posts/210617_myPhotoshop/myPhotoShop.gif)
