---
title: python script exp Fast Speedy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exp Fast Speedy'

Functions in program: 
* `def drift(R, B):`
* `def get_data():`

## python exp Fast Speedy

Python example: exp Fast Speedy

```python
from Crypto.Util.number import *


def get_data():
    with open("flag.png.enc", "rb") as f:
        data = f.read()
    return bytes_to_long(data)


def drift(R, B):
    ans, ini = R[-1], 0
    for i in B:
        ini ^= R[i - 1]
    R = [ini] + R[:-1]
    return ans, R


cipher = get_data()
stream = "0" + bin(cipher)[2:]
# 89504E470D0A1A0A0000000D49484452
chunk = "89504E470D0A1A0A0000000D49484452"
png_head = int(chunk, 16)
png_head = bin(png_head)[2:]
z_start = []
for i in range(len(chunk) * 4):
    tmp1 = int(stream[i], 2)
    tmp2 = int(png_head[i], 2)
    res = tmp1 ^ tmp2
    z_start.append(res)
print(z_start)
l = []
# r in range(7, 100) -> enough samples to check
for r in range(7, 100):
    for s in range(2, r):
        cnt = 0
        B = [i for i in range(s)]
        R = z_start[:r][::-1]
        for i in range(128 - r):
            ans, R = drift(R, B)
            if R[0] == z_start[r + i]:
                cnt += 1
            else:
                break
        if cnt == (128 - r):
            l.append((r, s))

print(l)
for r, s in l:
    R = z_start[:r][::-1]
    B = [i for i in range(s)]
    A, plaintext = [], []
    for i in range(len(stream)):
        ans, R = drift(R, B)
        A = A + [ans]
        plaintext = plaintext + [int(stream[i]) ^ ans]
    raw = long_to_bytes(int(''.join([str(i) for i in plaintext]), 2))
    print(raw[:32], s)
    with open('test%d.png' % s, 'wb') as f:
        f.write(raw)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
