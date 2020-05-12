---
title: python script score (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'score'

Functions in program: 
* `def score(a):`

Modules used in program: 
* `import sys`

## python score

Python example: score

```python
#!/usr/local/bin/python3.3 -tt

import sys


ONE_TO_NINE = tuple(range(1, 9+1))


def score(a):
    s = [0, 0, 0]

    h, w = len(a), len(a[0])

    # Horizontal Score Contribution
    for i in range(h):
        for j in range(w - 8):
            if tuple(sorted(a[i][j:j+9])) == ONE_TO_NINE:
                s[0] += 1

    # Vertical Score Contribution
    for j in range(w):
        for i in range(h - 8):
            t = []
            for k in range(9):
                t.append(a[i+k][j])
            if tuple(sorted(t)) == ONE_TO_NINE:
                s[1] += 1

    # 3x3 Block Score Contribution
    for i in range(0, h - 2):
        for j in range(0, w - 2):
            t = []
            for k in range(3):
                for l in range(3):
                    t.append(a[i+k][j+l])
            if tuple(sorted(t)) == ONE_TO_NINE:
                s[2] += 1

    return s

if __name__ == '__main__':
    a = []
    for l in sys.stdin:
        a.append([])
        for i in l.split():
            a[-1].append(int(i))
            
    h, w = len(a), len(a[0])

    s = score(a)

    t = [(w - 8) *  h,
         (h - 8) *  w,
         (h - 2) * (w - 2),
         ]

    print('vertical score  : %d / %d' % (s[1], t[1]))
    print('horizontal score: %d / %d' % (s[0], t[0]))
    print('3*3 block score : %d / %d' % (s[2], t[2]))
    print('total score     : %d / %d' % (sum(s), sum(t)))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
