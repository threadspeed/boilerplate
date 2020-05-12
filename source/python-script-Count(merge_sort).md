---
title: python script Count(merge sort) (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Count(merge sort)'

Functions in program: 
* `def msort(list) :`
* `def merge(a, b):`

Modules used in program: 
* `import random`
* `import time`

## python Count(merge sort)

Python mysql example: Count(merge sort)

```python
#Mainidea : divide과정에서는 대소비교없이 반으로 쪼개는 과정이기때문에 comparison operation이 없다고 생각됨
#따라서, merge 과정에서 발생하는 대소비교의 갯수를 count하려함 Global선언을 통해 대소관계가 이루어질때마다 +1씩 카운트됨
import time
import random

random_items100 = [random.randint(1,10001) for c in range(100)]
random_items500 = [random.randint(1,10001) for c in range(500)]
random_items1000 = [random.randint(1,10001) for c in range(1000)]
#글로벌 변수
mergecount = 0

def merge(a, b):
    index_a = 0
    index_b = 0
    c = []
    global mergecount
    while index_a < len(a) and index_b< len(b): #index_a가 len(a)과 같거나 크다는 뜻은 모든 요소들을 훑었다는 뜻
        mergecount+=1
        if a[index_a] <= b[index_b]: # a list요소가 b list요소 보다 작을때
             c.append(a[index_a]) # 대소비교에서 작았던 a list요소를 c에 넣어준다
             index_a = index_a + 1
        else: #반대경우 : 원리는 작은것을 c에 넣어준다.
             c.append(b[index_b])
             index_b = index_b + 1
    # 대소비교 다 끝나고 남는 쪽은 c에 붙여준다.
    c.extend(a[index_a:])
    c.extend(b[index_b:])
    return c

def msort(list) :
    global mergecount
    if len(list) == 0 or len(list) == 1:
        return list[:len(list)] #리스트 길이가 0이거나 1이면 처음 넣어준 list가 return됨
    halfway = len(list) // 2
    list1 = list[0: halfway]
    list2 = list[halfway:len(list)]
    newlist1 = msort(list1)
    newlist2 = msort(list2)
    newlist = merge(newlist1, newlist2)
    return newlist

#msort(random_items100)
#msort(random_items500)
msort(random_items1000)
#msort([6,3,100,206,36,63,33,203,77,66])
print(mergecount)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
