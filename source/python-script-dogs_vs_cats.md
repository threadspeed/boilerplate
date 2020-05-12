---
title: python script dogs vs cats (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dogs vs cats'

Functions in program: 
* `def main():`
* `def seq(*layers):`

Modules used in program: 
* `import numpy as np`
* `import random`
* `import math`
* `import argparse`

## python dogs vs cats

Python mysql example: dogs vs cats

```python
import argparse

from functools import partial, reduce
import math
from pathlib import Path
import random

from keras.layers import *
from keras.models import Model
from keras.utils import io_utils
import numpy as np
from PIL import Image


def seq(*layers):
    return reduce(lambda f, g: lambda x: g(f(x)), layers, lambda x: x)


def main():
    parser = argparse.ArgumentParser()
    parser.add_argument('--dataset', default='dogs_vs_cats.h5',
                        help='the path to the HDF5 format dataset')
    args = parser.parse_args()

    x_train = io_utils.HDF5Matrix(args.dataset, 'x_train')
    y_train = io_utils.HDF5Matrix(args.dataset, 'y_train')
    x_val = io_utils.HDF5Matrix(args.dataset, 'x_val')
    y_val = io_utils.HDF5Matrix(args.dataset, 'y_val')

    input_layer = Input(shape=x_train.shape[1:])
    layers = seq(
        Conv2D(8, 3, 3, activation='relu', border_mode='same'),
        Conv2D(8, 3, 3, activation='relu', border_mode='same'),
        MaxPooling2D((2, 2)),
        Conv2D(16, 3, 3, activation='relu', border_mode='same'),
        Conv2D(16, 3, 3, activation='relu', border_mode='same'),
        MaxPooling2D((2, 2)),
        Conv2D(32, 3, 3, activation='relu', border_mode='same'),
        Conv2D(32, 3, 3, activation='relu', border_mode='same'),
        GlobalAveragePooling2D(),
        Dense(1, activation='sigmoid'),
    )
    model = Model(input_layer, layers(input_layer))
    model.summary()

    model.compile('adam', 'binary_crossentropy', metrics=['accuracy'])
    print('Building model...')
    try:
        model.fit(x_train, y_train, validation_data=(x_val, y_val), shuffle='batch', nb_epoch=100)
    except KeyboardInterrupt:
        pass


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
