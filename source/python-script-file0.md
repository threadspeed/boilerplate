---
title: python script file0 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'file0'

Functions in program: 
* `def zndkkys():`
* `def zd():`

Modules used in program: 
* `import random`

## python file0

Python example: file0

```python
# -*- coding: utf-8 -*-
from collections import deque
import random


z = u'ズン'
d = u'ドコ'
zzzzd = (z, z, z, z, d, )
kys = u'キ・ヨ・シ！'


# 無限ズンドコジェネレータ
def zd():
    while True:
        w = random.choice((z, d, ))
        print(w)
        yield w


def zndkkys():
    q = deque()
    # 絶対に一致しない4文字目まで読み飛ばす
    for i, w in enumerate(zd()):
        q.append(w)
        if i == 3:
            break

    # 5文字目以降は都度チェックしつつ不要な文字は捨てる
    for w in zd():
        q.append(w)
        if all((zzzzd[i] == p for i, p in enumerate(q))):
            print(kys)
            return
        q.popleft()


if __name__ == '__main__':
    zndkkys()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
