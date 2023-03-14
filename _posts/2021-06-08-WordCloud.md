---
title: NLP기반 WordCloud
author: Cydnus
date: 2021-06-15 18:00:00 +0900
categories: [대한상공회의소 서울기술교육센터, Bigdata(python)]
tags: [Python, NLP, WordCLoud, NLTK, MatPlotlib, Pandas]
---

> 대한상공회의소 서울기술교육센터에서 진행하였던 Bigdata과목 학습 내용입니다.

> 소스는 [여기](https://github.com/Cydnus/Study_files/tree/main/Certificated_Programs/IoT%EA%B8%B0%EB%B0%98%20%EC%8A%A4%EB%A7%88%ED%8A%B8%ED%8C%A9%ED%86%A0%EB%A6%AC%20SW%EA%B0%9C%EB%B0%9C%20%EC%A0%84%EB%AC%B8%EA%B0%80%20%EA%B3%BC%EC%A0%95/BigData(python)/NLP%2C%20%ED%81%AC%EB%A1%A4%EB%A7%81)에서 확인 가능합니다.

### Summary

많은 양의 데이터가 발생하는 요즘 데이터를 가공하고 처리하는 것 뿐만 아니라 그것을 보기 쉽게 보여주기 위한 방식이 중요해지고 있다. 이 프로그램은 Word Cloud를 통하여 해당 단어가 해외 논문에서 얼마나 많이 사용 되었는지에 대한 빈도수를 시각화 하는 프로그램이다.

### Environment

- OS : Windows 10
- Language : python 3.8 (ananconda)
- IDE : Jupyter Notebook

### Key Feautres

- Stop words를 제외한 나머지로 토큰화
- Word Cloud, Matplot을 통하여 이미지를 생성

### Key Source

- [RissData기반](https://github.com/CydNus/)으로 하여 동작

- 단어 전처리 (토큰화)

```python
words = []
for title in all_title:
    EnWords = re.sub(r"[^a-zA-Z]+",' ',str(title))
    EnWordsToken = word_tokenize(EnWords.lower())
    EnWordsTokenStop = [ w for w in EnWordsToken if w not in stopWords]
    EnWordsTokenStopLemma = [lemma.lemmatize(w) for w in EnWordsTokenStop]
    words.append(EnWordsTokenStopLemma)
print(words)
```

- Word Cloud & MatPlotlib 로 출력

```python
stopwords = set(STOPWORDS)
wc = WordCloud(background_color='ivory',stopwords=stopwords,width=800,height=600)
cloud = wc.generate_from_frequencies(word_count)
plt.figure(figsize=(8,8))
plt.imshow(cloud)
plt.axis('off')
plt.show()
```

### Result

![단어 분석](/posts/210608_wordcloud/graph.png)

![출력](/posts/210608_wordcloud/bigdata_word_cloud.jpg)
