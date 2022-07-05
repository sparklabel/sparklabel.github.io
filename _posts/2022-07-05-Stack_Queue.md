---
title:  "[Data Structure] Stack, Queue and Deque"
excerpt: "YearDream offline group4"

toc: true                         # 목차
toc_sticky: true                  # 목차 사이드바 고정
  
published: true                   # 배포 여부

categories:
  - Python
tags:
  - Data Structure
  - Stack
  - Queue
last_modified_at: 2022-07-03T10:30:00+09:00
sitemap:
  changefreq: daily
  priority: 0.8
---

# Stack

<img src="https://hyeminnoh.github.io/Tech-Stack/assets/img/stack.5e20b63d.jpg" width='200'>

## 특징
+ LIFO(Last In First Out, 후입선출): 한 쪽 끝에서만 자료를 넣고 뺄 수 있는 구조. 스택에 데이터를 push하면 top 위치로 원소가 삽입되고, pop하면 top 위치의 데이터가 삭제된다. (쌓인 접시와 같은 구조)
+ Top 요소만 제한적으로 접근 가능
+ 시간 복잡도: O(1) ==> 탐색에 좋지 않음

## 장, 단점
+ 장점: 데이터 삽입/삭제 및 top 접근이 빠름, 히스토리 역추적에 좋음
+ 단점: 탐색 또는 중간 데이터 접근 어려움 (하나씩 빼내봐야 하니)

## 사용 예시
+ DFS(깊이 우선 탐색)
+ 재귀함수
+ 실행취소 같은 작업 역추적

## 구현 예시
- 별도의 파이썬 라이브러리 없어도 기본 리스트에서 append()와 pop() 메서드로 구현 가능.


```python
stack = []

stack.append(1)
stack.append(2)
stack.append(3)
stack.append(7)
stack.pop()
stack.append(9)
stack.append(5)
stack.pop()

print(stack)  # 가장 먼저 들어온(스택 최하단) 원소부터 출력 
print(stack[::-1]) # 가장 최근에 들어온(스택 최상단) 원소부터 출력
```

    [1, 2, 3, 9]
    [9, 3, 2, 1]
    

# Queue

<img src="https://hyeminnoh.github.io/Tech-Stack/assets/img/queue.e68e7a14.jpg" width='200'>

## 특징
+ FIFO(First In First Out, 선입선출): 먼저 넣은 데이터가 먼저 나옴 (줄서기와 같은 구조)
+ 시간 복잡도: O(1) ==> 탐색에 좋지 않음

## 장, 단점
+ 장점: 데이터 삽입/삭제 빠름. 입력 순서대로 처리 시 유리 
+ 단점: 탐색 또는 중간 데이터 접근 어려움

## 사용 예시
+ BFS(너비 우선 탐색)
+ 프린트 작업 대기열
+ ARS 고객센터

## 구현 예시
- queue 라이브러리 사용, FIFO/LIFO/Priority 가능


```python
import queue

fifo_queue = queue.Queue()  # FIFO

fifo_queue.put(3) # enqueue
fifo_queue.put(15)
fifo_queue.put(26)
fifo_queue.put(56)

print(fifo_queue.qsize()) # 크키
print(fifo_queue.queue)
```

    4
    deque([3, 15, 26, 56])
    


```python
print(fifo_queue.get())
print(fifo_queue.get())
print(fifo_queue.get())
```

    3
    15
    26
    


```python
lifo_queue = queue.LifoQueue()  # LIFO

lifo_queue.put(3) # enqueue
lifo_queue.put(15)
lifo_queue.put(26)
lifo_queue.put(56)

print(lifo_queue.queue)
print(lifo_queue.get())
print(lifo_queue.get())
print(lifo_queue.get())
```

    [3, 15, 26, 56]
    56
    26
    15
    


```python
pri_queue = queue.PriorityQueue()

pri_queue.put((34, 'a')) # 튜플 형태로 넣음 (우선순위, 데이터)
pri_queue.put((14, 'b'))
pri_queue.put((72, 'c'))
pri_queue.put((11, 'd'))
pri_queue.put((48, 'e'))

print(pri_queue.queue) # 숫자가 낮을 수록 우선순위가 높음 (i.e. 1순위, 2순위)
print(pri_queue.get())
print(pri_queue.get())
print(pri_queue.get())
print(pri_queue.get())
print(pri_queue.get())
```

    [(11, 'd'), (14, 'b'), (72, 'c'), (34, 'a'), (48, 'e')]
    (11, 'd')
    (14, 'b')
    (34, 'a')
    (48, 'e')
    (72, 'c')
    

# Deque ( = Double Ended Queue)  

<img src="https://hyeminnoh.github.io/Tech-Stack/assets/img/deque.6e1db229.jpg" width='200'>

## 특징
+ 양방향으로 삽입, 삭제 가능
+ 시간 복잡도: O(1)

## 장, 단점
+ 장점: 데이터 삽입/삭제 빠름, 인덱스 접근으로 탐색 가능
+ 단점: 메모리 공간이 큼, 큐나 스택에 비해 구현이 어려움

## 사용 예시
+ 데이터 편집이 잦은 경우
+ 데이터 개수가 가변적인 경우

## 구현 예시
- deque 라이브러리 사용


```python
from collections import deque

deque = deque('name')
print(deque)
deque[2] = 'M'
print(deque)
deque.insert(2,'A') 
print(deque)
deque.remove('a')
print(deque)
```

    deque(['n', 'a', 'm', 'e'])
    deque(['n', 'a', 'M', 'e'])
    deque(['n', 'a', 'A', 'M', 'e'])
    deque(['n', 'A', 'M', 'e'])