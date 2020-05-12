---
title: python script utils (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'utils'

Functions in program: 
* `def save_set_to_pkl(x, y, name_pkl):`
* `def open_pickle(path):`

Modules used in program: 
* `import os`
* `import pickle as pkl`
* `import easygui`
* `import numpy as np`
* `import matplotlib.pyplot as plt`

## python utils

Python example: utils

```python
# -*- coding: utf-8 -*
import matplotlib.pyplot as plt
import numpy as np
import easygui
import pickle as pkl
from keras.models import load_model
import os


def open_pickle(path):
    print(('открываем пикл файл ' + path))
    infile = open(path, 'rb')
    load_pkl = pkl.load(infile)
    infile.close()
    return load_pkl

def save_set_to_pkl(x, y, name_pkl):
    assert len(x) == len(y)
    dict = {'x': np.array(x), 'y': np.array(y)}
    outfile = open(name_pkl, 'wb')
    pkl.dump(dict, outfile)
    outfile.close()
    print("датасет сохранен в файл, количество записей = " + str(len(x)))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
