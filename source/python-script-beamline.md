---
title: python script beamline (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'beamline'

Functions in program: 
* `def save_to_database(img):`
* `def process_3(img_1, img_2):`
* `def process_2(img):`
* `def process_1(img):`
* `def get_image_from_detector():`

Modules used in program: 
* `import random`
* `import time`
* `import numpy as np`

## python beamline

Python mysql example: beamline

```python
from dask.distributed import Client, get_client, Variable, fire_and_forget
import numpy as np
import time
import random


def get_image_from_detector():
    """ Collect image from detector

    Actually this just produces a random image
    """
    # TODO: obtain used synchrotron from EBay
    return np.random.random((2000, 2000))

##########################################################
# Some image processing functions from our collaborators #
##########################################################

def process_1(img):
    time.sleep(random.random())
    return img


def process_2(img):
    time.sleep(random.random() / 2)
    return img / 10


def process_3(img_1, img_2):
    time.sleep(random.random() / 2)
    return img_1 + img_2


def save_to_database(img):
    time.sleep(0.5)

"""
Dear parallel programmer,

Please make the following happen on every image that we detect.

x = process_1(img)
y = process_2(img)
z = process_3(x, y)
save_to_database(img)
save_to_database(z)

Sincerely,
Beam Scientist
"""

# TODO: Please write parallel beamline code



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
