---
title: python script CVCreateModelNextCard (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'CVCreateModelNextCard'

Functions in program: 
* `def readDir(num):`
* `def learnCard(I, num):`

Modules used in program: 
* `import glob`
* `import numpy as np`
* `import cv2`

## python CVCreateModelNextCard

Python example: CVCreateModelNextCard

```python
#!/usr/bin/python

import cv2
import numpy as np
import glob

SAMPLES_SIZE = 288
SAMPLES = np.empty((0, SAMPLES_SIZE))
RESPONSES = []


def learnCard(I, num):
    global SAMPLES
    global RESPONSES

    sample = I.reshape((1, SAMPLES_SIZE))
    SAMPLES = np.append(SAMPLES, sample, 0)
    RESPONSES.append(int(num))


def readDir(num):
    for fileName in glob.glob("./next_card/" + str(num) + "/*.png"):
        print(fileName)
        I = cv2.imread(fileName)
        learnCard(I, num)

if __name__ == "__main__":
    global SAMPLES
    global RESPONSES

    for num in (1, 2, 3, 6):
        readDir(num)

    RESPONSES = np.array(RESPONSES, np.int32)
    RESPONSES = RESPONSES.reshape((RESPONSES.size, 1))
    np.savetxt("train_samples_next.data", SAMPLES)
    np.savetxt("train_responses_next.data", RESPONSES)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
