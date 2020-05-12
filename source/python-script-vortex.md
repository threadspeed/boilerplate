---
title: python script vortex (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'vortex'

Functions in program: 
* `def vortex_sort(arr):`

## python vortex

Python mysql example: vortex

```python
def vortex_sort(arr):
    """Swirl the array into order.
    Guaranteed to only use < for comparison, so use any objects you like.
    """
    arlen = len(arr)
    rs = []
    mult = 1
    last = 0
    while last < arlen:
        number = mult * 4
        mult += 2
        rs.append(arr[last:last + number])
        last += number
    if len(rs) <= 1:
        #bubble sort
        arr = rs[0]
        arlen = len(arr)
        sortedq = False
        srtd = 1
        while not sortedq:
            sortedq = True
            for i in range(arlen - srtd):
                if arr[i+1] < arr[i]:
                    arr[i], arr[i+1] = arr[i+1], arr[i]
                    sortedq = False
            srtd += 1
        return arr
    sortedq = False
    while not sortedq:
        sortedq = True
        for i in reversed(range(len(rs) - 1)):
            for _ in range(len(rs[i])):
                #swirl this ring to outer ring
                idx = 1 + -8 // len(rs[i])
                olen = len(rs[i + 1])
                idx, min_val = min(
                    (idx, rs[i + 1][idx % olen]),
                    (idx + 1, rs[i + 1][(idx + 1) % olen]),
                    (idx + 2, rs[i + 1][(idx + 2) % olen]),
                    key=lambda k: k[1]
                )
                if rs[i+1][idx] < rs[i][0]:
                    rs[i][0], rs[i+1][idx] = rs[i+1][idx], rs[i][0]
                    sortedq = False
                for r in rs:
                    r.insert(0, r.pop(-1))
    for i in range(len(rs)):
        #recursively vortext sort ring
        rs[i] = vortex_sort(rs[i])
    #merge rings together
    rlen = len(rs)
    while rlen > 1:
        for i in range(0, rlen, 2):
            j = i + 1
            if j >= rlen:
                continue
            _i = i
            i, j = rs[i], rs[j]
            len1 = len(i)
            len2 = len(j)
            tarlen = len(i) + len(j)
            tmparr = [0] * tarlen
            m, n, p = 0, 0, 0
            while m < len1 and n < len2 and p < tarlen:
                if not j[n] < i[m]:
                    tmparr[p] = i[m]
                    m += 1
                else:
                    tmparr[p] = j[n]
                    n += 1
                p += 1
            if m < len1:
                tmparr = tmparr[:p]
                tmparr.extend(i[m:])
            elif n < len2:
                tmparr = tmparr[:p]
                tmparr.extend(j[n:])
            rs[_i] = tmparr
        rs = [rs[i] for i in range(0, rlen, 2)]
        rlen = len(rs)
    return rs[0]

if __name__ == '__main__':
    import random
    a = list(range(int(input('How many elements? '))))
    random.shuffle(a)
    print('start:', a)
    b = vortex_sort(a)
    print('\nend:', b)
    print('\nsorted?', list(sorted(a)) == b)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
