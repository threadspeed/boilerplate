---
title: python script CVCreateModel (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'CVCreateModel'

Functions in program: 
* `def readDir(num):`
* `def learnCard(I, num):`

Modules used in program: 
* `import glob`
* `import numpy as np`
* `import cv2`

## python CVCreateModel

Python example: CVCreateModel

```python
#!/usr/bin/python

import cv2
import numpy as np
import glob

SAMPLES_SIZE = 2001
SAMPLES = np.empty((0, SAMPLES_SIZE))
RESPONSES = []


def learnCard(I, num):
    global SAMPLES
    global RESPONSES
    sample = I.reshape((1, SAMPLES_SIZE))
    SAMPLES = np.append(SAMPLES, sample, 0)
    RESPONSES.append(int(num))


def readDir(num):
    for fileName in glob.glob("./cards/" + str(num) + "/*.png"):
        print(fileName)
        I = cv2.imread(fileName)
        learnCard(I, num)

if __name__ == "__main__":
    global SAMPLES
    global RESPONSES

    for num in (0, 1, 2, 3, 6, 12, 24, 48, 96, 192, 384, 768):
        readDir(num)

    RESPONSES = np.array(RESPONSES, np.int32)
    RESPONSES = RESPONSES.reshape((RESPONSES.size, 1))
    np.savetxt("train_samples.data", SAMPLES)
    np.savetxt("train_responses.data", RESPONSES)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
