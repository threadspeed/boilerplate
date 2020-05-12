---
title: python script file1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'file1'

Functions in program: 
* `def zndkkys2():`

Modules used in program: 
* `import random`

## python file1

Python mysql example: file1

```python
# -*- coding: utf-8 -*-
from collections import deque
import random


z = u'ズン'
d = u'ドコ'
kys = u'キ・ヨ・シ！'

def zndkkys2():
    state = 0
    while True:
        num = random.choice((0, 1, ))
        # ズンならカウントアップ
        if num:
            yield z
            state += 1
        else:
            yield d
            # ドコの前に4回以上ズンが連続していたらキ・ヨ・シ！
            if state >= 4:
                yield kys
                return
            # ドコの前のズンが3回以下ならカウントを初期化
            else:
                state = 0

if __name__ == '__main__':
    print(''.join(zndkkys2()))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
