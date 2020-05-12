---
title: python script Sorted sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Sorted sort'


Modules used in program: 
* `import time`
* `import random`
* `import time`

## python Sorted sort

Python mysql example: Sorted sort

```python
import time
import random
random_items100 = [random.randint(1,10001) for c in range(100)]
random_items500 = [random.randint(1,10001) for c in range(500)]
random_items1000 = [random.randint(1,10001) for c in range(1000)]

####sorted 성능 테스트(n=100)
startTime = time.clock()
sorted(random_items100)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for sorted_function is:', elapsedTime)

##sorted 성능 테스트(n=500)
import time
startTime = time.clock()
sorted(random_items500)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for sorted_function is:', elapsedTime)

##sorted 성능 테스트(n=1000)
startTime = time.clock()
sorted(random_items1000)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for sorted_function is:', elapsedTime)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
