---
 title: "[Algorithm]Binary Search by Python"
categories: "Algorithm"
tags: "python"
toc_sticky: True
excerpt: "Sort Algorithm"
permalink: /Algorithm/Binary/
changefreq : day
use_math: true
---

## **Binary Search**

대표적인 O(log n) 시간복잡도를 가지는 알고리즘이다

### by recursion(재귀)

```python
def search(num : list, target : int) -> int:
    def binary_search(left,right):
        if left <= right:
            mid = (left+right)//2
            if num[mid] < target:
                return binary_search(mid+1,right)
            elif num[mid] > target:
                return binary_search(left,mid+1)
            else:
                return mid
        else:
            return -1

    return binary_search(0,len(num)-1)

print(search([1,2,3,4,5,6,7,8,9],6)) # output : 5
```

### by Iterative(반복)

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

------

## **공부하며 참고한 곳**



------


## 