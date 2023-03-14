---
title: AstLoner
author: Cydnus
date: 2021-06-08 18:00:00 +0900
categories: [대한상공회의소 서울기술교육센터, Bigdata(python)]
tags: [Python, Pygame]
---

> 대한상공회의소 서울기술교육센터에서 진행하였던 Bigdata과목 미니 프로젝트입니다.

> 소스는 [여기](https://github.com/Cydnus/Study_files/tree/main/Certificated_Programs/IoT%EA%B8%B0%EB%B0%98%20%EC%8A%A4%EB%A7%88%ED%8A%B8%ED%8C%A9%ED%86%A0%EB%A6%AC%20SW%EA%B0%9C%EB%B0%9C%20%EC%A0%84%EB%AC%B8%EA%B0%80%20%EA%B3%BC%EC%A0%95/BigData(python)/Day01)에서 확인 가능합니다.

### Summary

'백문불여일견' 이라는 말이 있듯이 흔히 프로그래밍 언어 공부법이라고 하면 '백문불여일타' 라 한다. 처음 python을 다루어 보는 사람들이 있는 만큼 pygame이라는 모듈 하나로 팀으로 게임을 만들어보자 는 프로젝트에서 시작되었다.

### Environment

- OS : Windows 10
- Language : python 3.8 (ananconda)
- IDE : Jupyter Notebook

### Key Feautres

- 시간에 따른 속도 증가
- 아이템 박스 획득
- 몬스터 피격

### Key Source

```python
def print_background(scr):
    global background1,background2,background1_x,background2_x, MOB, MOB_X, MOB_y, SCORE
    screen.fill((0,0,0))

    for i in range(0,len(background_x)):
        background_x[i] -= BACK_SPEED
        if background_x[i] <= -BACKGROUND_WIDTH:
            background_x[i] += (BACKGROUND_WIDTH*2)

    for i in range(0,len(bottom_x)):
        bottom_x[i] -= FORE_SPEED
        if bottom_x[i] <= WIDTH*-1 :
            bottom_x[i] += (WIDTH *2)
            SCORE += FPS * FORE_SPEED

    for i in range(0,MOB_LENGTH):
        MOB_X[i] -= FORE_SPEED
        if not(MOB_X[i] >  BOTTOM_WIDTH * -2):
            MOB.append(setMob())
            MOB.remove(MOB[0])
            MOB_X[0] += ( BOTTOM_WIDTH * MOB_LENGTH )
            MOB_X.append(MOB_X[0])
            MOB_X.remove(MOB_X[0])
            break

    for i in range(0,len(background)):
        scr.blit(background[i],(background_x[i], 0) )

    for i in range(0,len(bottom_x)):
        scr.blit( bottom[i], (bottom_x[i], HEIGHT*0.9) )

    for i in range(0,MOB_LENGTH):
        for j in range(0,SECTER_LENGTH):
            if not( MOB[i][j] == 80 or MOB[i][j] == 0 or MOB[i][j] == -1):
                color = (255,255,255)
                high = 50
                img = pyg.image.load(os.path.join(os.path.abspath('image'),'Box.png'))
                if MOB[i][j] == 50 :
                    color = (0,0,255)
                    high= MOB_TYPE[0]
                    img = pyg.image.load(os.path.join(os.path.abspath('image'),'small.png'))
                elif  MOB[i][j]== 60 :
                    color = (0,255,0)
                    high = MOB_TYPE[1]
                    img = pyg.image.load(os.path.join(os.path.abspath('image'),'mid.png'))
                elif MOB[i][j] == 70 :
                    color = (255,0,0)
                    high = MOB_TYPE[2]
                    img = pyg.image.load(os.path.join(os.path.abspath('image'),'Big.png'))
                scr.blit(img,[int(MOB_X[i]+BOTTOM_WIDTH/4),int(SECTER[j])])


    printScore = txtFont.render("Score : "+str(SCORE),True, (0,0,0) )
    scr.blit(printScore,[0,HEIGHT*0.05])

```

### Result

![시작 화면](/posts/210608_AstLoner/start.png)

![인게임 화면](/posts/210608_AstLoner/ingame.png)

![종료 화면](/posts/210608_AstLoner/endgame.png)
