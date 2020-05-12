---
title: python script ZombieMarch (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ZombieMarch'

Functions in program: 
* `def main():`

Modules used in program: 
* `import time`
* `import random`
* `import sys`

## python ZombieMarch

Python mysql example: ZombieMarch

```python
#!/usr/bin/python

"""
 https://www.interviewstreet.com/challenges/dashboard/#problem/4ff1484963063 Zombie March
 http://www.17sotv.com/ 17sotv电影天堂
"""

import sys
import random
import time

page_rank_iteration_round = 50

def main():
    # read t
    line = sys.stdin.readline().strip()
    t = int(line)
    while t > 0:
        t = t - 1
        # test time
        # print("start: %d" % time.time())
        # read n, m, k
        line = sys.stdin.readline().strip()
        (n, m, k) = (int(i) for i in line.split())
        # define node degree, and edges
        degree = [0] * n
        edges = [[] for i in xrange(0, n)]
        # read edges
        for i in xrange(0, m):
            line = sys.stdin.readline().strip()
            (p, q) = (int(x) for x in line.split())
            degree[p] = degree[p] + 1
            degree[q] = degree[q] + 1
            edges[p].append(q)
            edges[q].append(p)
        # define zombie number
        num = [[0.0] * n for i in xrange(0, 2)]
        # read initial zombie number
        for i in xrange(0, n):
            line = sys.stdin.readline().strip()
            num[0][i] = float(line)
        # end input time
        # print("end input: %d" % time.time())
        # enumarate the process
        k = min(k, page_rank_iteration_round)
        (now, next) = (0, 1)
        while k > 0:
            k = k - 1
            for i in xrange(0, n):
                num[next][i] = 0
                for j in edges[i]:
                    num[next][i] = num[next][i] + num[now][j] / degree[j]
            (now, next) = (1 - now, 1 - next)
        # sort the result
        num[now].sort(reverse = True)
        # end compute time
        # print("end compute: %d" % time.time())
        # output the result
        for i in num[now][0:5]:
            print(int(round(i)),)
        print

if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
