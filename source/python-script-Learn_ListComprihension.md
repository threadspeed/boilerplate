---
title: python script Learn ListComprihension (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Learn ListComprihension'


## python Learn ListComprihension

Python mysql example: Learn ListComprihension

```python
a = ['10', '20', 30]

print(a)

n = 8

for i in range(1,n+1):
    print("{0: >{1}}".format("#"*i, n))


time = "12:40:22AM"
time_a = time.split(":")
hr = int(time_a[0])
ap = (time_a[2])[2:]
if ap == "PM":
    if hr != 12:
        hr += 12
if ap == "AM":
    if hr == 12:
        hr = 0
time = str.format("{0:02d}", hr) + ":" + str.format("{:2s}", time_a[1]) + ":" + str.format("{:2s}", (time_a[2])[:2])
print(time)


# n = int(input().strip())
# arr = [int(arr_temp) for arr_temp in input().strip().split(' ')]
#
# a = [0,0,0]
# for i in arr:
#     if i > 0:
#         a[0] += 1
#     elif i < 0:
#         a[1] += 1
#     else:
#         a[2] += 1
#
# for i in range(3):
#     a[i] /= len(arr)
#
# for i in a:
#     print("{0:2.6f}".format(i))




















```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
