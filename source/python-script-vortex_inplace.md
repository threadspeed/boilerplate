---
title: python script vortex inplace (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'vortex inplace'

Functions in program: 
* `def vortex_sort(arr, start=0, end=None):`

## python vortex inplace

Python example: vortex inplace

```python
def vortex_sort(arr, start=0, end=None):
    """Swirl the array into order.
    Guaranteed to only use < for comparison, so use any objects you like.
    """
    if not arr[start:end]:
        return arr
    arlen = (end or len(arr)) - start
    rs = []
    mult = 1
    last = 0
    while last < arlen:
        number = mult * 4
        mult += 2
        rs.append((
            last, #start
            min(last + number, arlen) - last #length
        )) #start, length
        last += number
    rlen = len(rs)
    if rlen <= 1:
        #bubble sort
        sortedq = False
        srtd = 1
        while not sortedq:
            sortedq = True
            for i in range(arlen - srtd):
                if arr[i+1+start] < arr[i+start]:
                    arr[i+start], arr[i+1+start] = arr[i+1+start], arr[i+start]
                    sortedq = False
            srtd += 1
        return arr
    sortedq = False
    while not sortedq:
        sortedq = True
        for i in reversed(range(rlen - 1)):
            for _ in range(rs[i][1]):
                #swirl this ring to outer ring
                idx = 1 + -8 // rs[i][1] #2 = length
                olen = rs[i + 1][1]
                idx, min_val = min(
                    (idx % olen, arr[rs[i + 1][0] + idx % olen + start]),
                    ((idx + 1) % olen,
                     arr[rs[i + 1][0] + (idx + 1) % olen + start]),
                    ((idx + 2) % olen,
                     arr[rs[i + 1][0] + (idx + 2) % olen + start]),
                    key=lambda k: k[1]
                )
                if arr[rs[i+1][0] + idx + start] < arr[rs[i][0] + start]:
                    arr[rs[i][0] + start], arr[rs[i+1][0] + idx + start] \
                                   = arr[rs[i+1][0] + idx + start], \
                                   arr[rs[i][0] + start]
                    sortedq = False
                for r in rs:
                    arr.insert(r[0] + start, arr.pop(r[0] + r[1] - 1 + start))
    for r in rs:
        #recursively vortext sort ring
        vortex_sort(arr, r[0] + start, r[0] + r[1] + start)
    #merge rings together
    while rlen > 1:
        for i in range(0, rlen, 2):
            if i + 1 >= rlen:
                continue
            len1 = rs[i][1]
            len2 = rs[i + 1][1]
            tarlen = len1 + len2
            tmparr = []
            m, n = 0, 0
            while m < len1 and n < len2:
                if not arr[rs[i+1][0] + n + start] \
                   < arr[rs[i][0] + m + start]:
                    tmparr.append(arr[rs[i][0] + m + start])
                    m += 1
                else:
                    tmparr.append(arr[rs[i+1][0] + n + start])
                    n += 1
            if m < len1:
                tmparr.extend(arr[rs[i][0] + m + start
                                  :rs[i][0] + rs[i][1] + start])
            elif n < len2:
                tmparr.extend(arr[rs[i+1][0] + n + start
                                  :rs[i+1][0] + rs[i+1][1] + start])
            arr[rs[i][0] + start:rs[i][0] + tarlen + start] = tmparr
        rs = [(rs[i][0], rs[i][1] + rs[i+1][1])
              if i + 1 < rlen
              else rs[i]
              for i in range(0, rlen, 2)]
        rlen = len(rs)
    return arr

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
