---
title: "LISP 7주차 - LISP의 리스트 자료구조(2)"
excerpt: "LISP의 리스트 자료구조를 알아보자."
categories:
  - lectures
tags:
  - lisp
last_modified_at:
---

## 구조
우리는 지금까지 구조적 프로그래밍 기법의 입장에서 시퀀스, 컨디션, 루프 세 가지 구성요소로 lisp 프로그래밍을 살펴봤다. 즉, 순차적 수행, 조건문, 반복문을 이용하였다. 

이번에는 Applicative Programming 의 프로그래밍 기법을 알아보자.

## Applicative Programming

Applicative Programming은 함수를 다른 함수의 입력으로 전달할 수 있는 프로그래밍 방법이다. 이 Applicative Programming은 LISP이 인터프리터이기 때문에 사용 가능한 프로그래밍 기법이다. 
이렇게 함수를 부를 수 있는 내장함수로는 funcall, mapcar이 있다. 


## funcall
funcall의 경우, function임을 나타내는 #'를 쓴 뒤 그 옆에 띄어쓰기 없이 함수명을 입력하며, 해당 함수명이 요구하는 인자를 입력한다.

```lisp
(funcall #'cons `a `b)

= (a . b)
```

mapcar는 함수를 주어진 각각의 원소에 대해서 해당 함수의 기능을 수행해준다. 

