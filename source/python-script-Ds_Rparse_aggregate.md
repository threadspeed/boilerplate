---
title: python script Ds Rparse aggregate (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ds Rparse aggregate'

Functions in program: 
* `def addlist(list1, list2):`
* `def mean(list_):`

## python Ds Rparse aggregate

Python example: Ds Rparse aggregate

```python
def mean(list_):
    return sum(list_)/len(list_)


def addlist(list1, list2):
    # addlist([1,2,3], [1,2,3]) -> [2,4,6]
    for i in range(len(list1)):
        list1[i] += list2[i]


firstline = True
out = ''
prevdate = ''
sumlist = []

infile = open('data1416.csv')
for line in infile:
    # First line = Column names
    if firstline:
        line = line.replace('year,month,day', 'date')
        out += line
        firstline = False
    else:
        parsed = list(map(float, line.split(',')))
        # R accepts Dates as "YYYY-MM-DD" format.
        parsed[0] = '-'.join(parsed[0:3])
        del parsed[1:3]
        if parsed[0] == prevdate:
            addlist(sumlist, parsed[1:])
        else:
            if sumlist:
                out += ','.join(parsed[0:1]+sumlist) + '\n'
            prevdate = parsed[0]
            sumlist = parsed[1:]


outfile = open('data1416_R_aggregate.csv', 'w')
outfile.write(out)

infile.close()
outfile.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
