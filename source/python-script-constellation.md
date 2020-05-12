---
title: python script constellation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'constellation'

Functions in program: 
* `def read_constellation(filename):`

Modules used in program: 
* `import csv`

## python constellation

Python mysql example: constellation

```python
# -*- coding: utf-8 -*-
#星のデータの読み込み
import csv

def read_constellation(filename):
    with open(filename, 'r') as f:
        reader = csv.reader(f)
        result = []
        for row in reader:
            number = int(row[0])
            ra_hour = float(row[1])
            ra_min = float(row[2])
            ra_sec = float(row[3])
            sign = int(row[4])
            dec_deg = float(row[5])
            dec_min = float(row[6])
            dec_sec = float(row[7])
            mag = float(row[8])

            A = ra_hour*15 + ra_min/60*15 + (ra_sec/3600)*15
            B = dec_deg + dec_min/60 + dec_sec/3600
            if (sign == 0):
                B *= -1
            obj={}
            obj["hipid"] = number
            obj["mag"] = mag
            obj["ra"] = A
            obj["dec"] = B
            if mag < 4:
                result.append(obj)
    return result


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
