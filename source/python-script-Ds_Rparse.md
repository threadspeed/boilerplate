---
title: python script Ds Rparse (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ds Rparse'


## python Ds Rparse

Python mysql example: Ds Rparse

```python
firstline = True
out = ''

infile = open('data1416.csv')
for line in infile:
    # First line = Column names
    if firstline:
        line = line.replace('year,month,day', 'date')
        out += line
        firstline = False
    else:
        parsed = line.split(',')
        # R accepts Dates as "YYYY-MM-DD" format.
        parsed[0] = '-'.join(parsed[0:3])
        del parsed[1:3]
        out += ','.join(parsed)

outfile = open('data1416_R.csv', 'w')
outfile.write(out)

infile.close()
outfile.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
