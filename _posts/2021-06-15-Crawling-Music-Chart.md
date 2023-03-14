---
title: Melon Chart Crawling
author: Cydnus
date: 2021-06-15 18:00:00 +0900
categories: [대한상공회의소 서울기술교육센터, Bigdata(python)]
tags: [Python, bs4(BeautifulSoup), Selenium, Pandas]
---

> 대한상공회의소 서울기술교육센터에서 진행하였던 Bigdata과목 학습 내용입니다.

> 소스는 [여기](<https://github.com/Cydnus/Study_files/tree/main/Certificated_Programs/IoT%EA%B8%B0%EB%B0%98%20%EC%8A%A4%EB%A7%88%ED%8A%B8%ED%8C%A9%ED%86%A0%EB%A6%AC%20SW%EA%B0%9C%EB%B0%9C%20%EC%A0%84%EB%AC%B8%EA%B0%80%20%EA%B3%BC%EC%A0%95/BigData(python)/NLP%2C%20%ED%81%AC%EB%A1%A4%EB%A7%81>)에서 확인 가능합니다.

### Summary

OpenCV를 통한 이미지 처리 방식을 학습하는 것을 목표로 만든 프로그램이다.

### Environment

- OS : Windows 10
- Language : python 3.8 (ananconda)
- IDE : Jupyter Notebook

### Key Feautres

- 온라인 뮤직 사이트(멜론) 의 인기 차트(HTML)를 읽어오기
- 상위 5개 출력
- Spread Sheet 로 저장

### Key Source

- 크롤링

```python
url = 'http://www.melon.com/chart/index.htm'
driver.get(url)

html = driver.page_source
soup = BeautifulSoup(html, 'html.parser')

```

- 파싱

```python
song_data = []
rank = 1

songs = soup.select('table > tbody > tr')
for song in songs:
    title = song.select('div.rank01 > span > a ')[0].text
    singer = song.select('div.rank02 > a')[0].text
    song_data.append(['Melon',rank,title,singer])
    rank+=1
```

### Result

![출력](/posts/210615_Crwaling-Music-Chart/result.png)
