---
title: "[Algorithm]Sort Algorithm by Python"
categories: "Algorithm"
tags: "python"
toc_sticky: True
excerpt: "Sort Algorithm"
permalink: /Algorithm/Sort/
changefreq : day
use_math: true
---


## **O($n^2$)**

### 1. Bubble Sort

```python
def BS(list_):
    len_list = len(list_)
    for i in range(len_list-1):
        for j in range(len_list-i-1):
            if list_[j] > list_[j+1]:
                list_[j], list_[j+1] = list_[j+1], list_[j] # Swap list_[j], list_[j+1]
    return list_
```

- 인접한 값을 비교하여 자리를 바꾼다.(1부터 n-1까지)
- 이 과정을 n-1번 반복한다. 

### 2. Quick Sort

```python
def QS(list_):
    len_list = len(list_)
    if len_list <= 1:
        return list_
    pivot = list_[0]
    left = []
    right = []
    for i in list_[1:]:
        if i <= pivot:
            left.append(i)
        else:
            right.append(i)
    return QS(left) + [pivot] + QS(right)
```

- 리스트의 가장 앞인자를 Pivot으로 설정
- 피봇보다 큰 값은 right, 작은 값은 left 리스트에 append
- 재귀함수를 통해 반복(종결 조건 len_list <= 1)(숫자가 1개 또는 0개)

### 3.  Selection Sort

```python
def SS(list_):
    len_list = len(list_)
    for var in range(len_list-1):
        m = var
        for i in range(var+1,len_list):
            if list_[i] <= list_[m]:
                m = i
        list_[var], list_[m] = list_[m], list_[var] # Swap list_[m], list_[var]
    return list_
```

- 가장 작은 값을 찾아 첫번째 자리에 배치한다
- 두번째 작은 값을 찾아 두번째 자리에 배치한다
- 이 과정을 n-1번 반복한다

### 4. Insertion Sort

```python
def IS(list_):
    for i in range(1, len(list_)):
        j = i-1
        while(j>=0 and list_[i]<list_[j]):
            j-=1
        list_.insert(j+1,list_[i])
        del list_[i+1]
    return list_
```

- list[0]을 집합 U로 설정하고 집합 S(= list[1:] )에서 숫자를 1개씩 뽑아 U에서 배열한다

### 5. Shell Sort

```python

```

- 

## O(n log n)

### 1. Heap Sort

```python

```

- 



### 2. Merge Sort

```python

```

- 

## O(kn)

### 1. Radix Sort

```python

```

- 

------

## **공부하며 참고한 곳**

[**Blog**](https://medium.com/@joongwon/%EC%A0%95%EB%A0%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B8%B0%EC%B4%88-805391cb088e)

[**Blog**](https://www.daleseo.com/sort-selection/)

[**Blog**](https://leedakyeong.tistory.com/entry/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%9C%BC%EB%A1%9C-%EC%82%BD%EC%9E%85%EC%A0%95%EB%A0%AC-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-insertion-sort-in-python?category=842565)

------


## 