---
title: python script dogs vs cats dataset (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dogs vs cats dataset'

Functions in program: 
* `def main():`
* `def write_dataset(paths, x, y=None):`
* `def write_image(path, x, y, i):`
* `def extract_label(path):`

Modules used in program: 
* `import numpy as np`
* `import h5py`
* `import threading`
* `import random`
* `import os`
* `import concurrent.futures`

## python dogs vs cats dataset

Python mysql example: dogs vs cats dataset

```python
import concurrent.futures
import os
from pathlib import Path
import random
import threading

import h5py
import numpy as np
from PIL import Image

DATASET_PATH = '/Users/kat/Documents/datasets/dogs-vs-cats'
IMAGE_SIZE = (32, 32)


def extract_label(path):
    name = Path(path).name
    if name.startswith('cat'):
        return 0
    if name.startswith('dog'):
        return 1
    raise ValueError(f'Could not determine label for {name}.')


def write_image(path, x, y, i):
    image = Image.open(path).convert('RGB').resize((IMAGE_SIZE[1], IMAGE_SIZE[0]), Image.LANCZOS)
    x[i] = np.float32(image).transpose((2, 0, 1)) / 255
    if y is not None:
        y[i] = extract_label(path)


def write_dataset(paths, x, y=None):
    done = 0
    lock = threading.Lock()

    def callback(fut):
        nonlocal done, lock
        with lock:
            done += 1
            if done % 100 == 99:
                print(f'{done+1}/{len(paths)} images processed.')

    futures = []
    with concurrent.futures.ThreadPoolExecutor(max_workers=os.cpu_count()) as e:
        for i, path in enumerate(paths):
            fut = e.submit(write_image, path, x, y, i)
            fut.add_done_callback(callback)
            futures.append(fut)
        concurrent.futures.wait(futures)


def main():
    train_paths = list((Path(DATASET_PATH) / 'train').iterdir())
    test_paths = list((Path(DATASET_PATH) / 'test1').iterdir())

    random.shuffle(train_paths)
    val_samples = round(len(train_paths) * 0.1)
    val_paths = train_paths[:val_samples]
    train_paths = train_paths[val_samples:]

    with h5py.File('dogs_vs_cats.h5', 'w') as f:
        x_train = f.create_dataset('x_train', (len(train_paths), 3) + IMAGE_SIZE, np.float32)
        y_train = f.create_dataset('y_train', (len(train_paths),), np.uint8)
        x_val = f.create_dataset('x_val', (len(val_paths), 3) + IMAGE_SIZE, np.float32)
        y_val = f.create_dataset('y_val', (len(val_paths),), np.uint8)
        x_test = f.create_dataset('x_test', (len(test_paths), 3) + IMAGE_SIZE, np.float32)

        write_dataset(train_paths, x_train, y_train)
        write_dataset(val_paths, x_val, y_val)
        write_dataset(test_paths, x_test)


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
