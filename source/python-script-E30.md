---
title: python script E30 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'E30'


Modules used in program: 
* `import random`

## python E30

Python example: E30

```python
import random
listt = []
with open('sowpods.txt', 'r') as f:
  listt = list (f)

leng = int(len(listt))
x = random.randint(0,leng)
print((listt[x]))
print("The entire file as been read!")
##
##
##import random
##listt = []
##with open('sowpods.txt', 'r') as f:
##  line = f.readline()
##  while line:
##    listt.append(line.strip())
##    line = f.readline()
##
##leng = int(len(listt))
##x = random.randint(0,leng)
##print((listt[x]))
##print("The entire file as been read!")



######with open('sowpods.txt', 'r') as f:
######    lines = f.readlines()
######print((random.choice(lines).strip()))


######print((random.choice(open('sowpods.txt','r').readlines()).strip()))

######
######import random
######import linecache
######
######count = 0
######with open('sowpods.txt', 'r') as f:
######    line = f.readline().strip()
######    while line:
######        line = f.readline().strip()
######        count +=1
######    x = random.randint(0,count)
######
######y = linecache.getline('sowpods.txt', x)
######print(y)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
