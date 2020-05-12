---
title: python script Generator891 N (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Generator891 N'

Functions in program: 
* `def run():`
* `def createData(number):`
* `def writefiles(dirpath, filename, num):`
* `def ansfunc(N):`

Modules used in program: 
* `import random`
* `import time`
* `import os`

## python Generator891 N

Python mysql example: Generator891 N

```python
import os
import time
import random

def ansfunc(N):
    count = 0
    count += N // 2 + N // 3 + N // 5
    count -= N // 6 + N // 10 + N // 15
    count += N // 30
    return count

def writefiles(dirpath, filename, num):
    filepath = dirpath + "/" + filename
    filewriter = open(filepath, "w")
    filewriter.write(str(num) + "\n")
    filewriter.close()

def createData(number):
    nowtime = int(time.time())
    inputdirpath = str(nowtime) + "/input"
    outputdirpath = str(nowtime) + "/output"
    os.makedirs(inputdirpath)
    os.makedirs(outputdirpath)

    for i in range(1, number+1):
        questionN = int(random.randint(1, 10 ** 9 + 1) // abs(i - number - 1)) // abs(i - number - 1)
        answer = ansfunc(questionN if questionN > 1 else 1)

        inputfilename = "input" + str(i) + ".txt"
        writefiles(inputdirpath, inputfilename, questionN)

        outputfilename = "output" + str(i) + ".txt"
        writefiles(outputdirpath, outputfilename, answer)

def run():
    createData(10)

if __name__ == "__main__":
    print("start!")
    run()
    print("end!")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
