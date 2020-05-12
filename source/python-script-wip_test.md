---
title: python script wip test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'wip test'

Functions in program: 
* `def _test1():`
* `def _test2():`
* `def drop_cache():`

Modules used in program: 
* `import sys`
* `import bisect`
* `import sys`
* `import io`
* `import zipfile`
* `import multiprocessing`
* `import six`
* `import numpy`
* `import os`

## python wip test

Python mysql example: wip test

```python
import os

import numpy
try:
    from PIL import Image
    available = True
except ImportError as e:
    available = False
    _import_error = e
import six
import multiprocessing
import zipfile
import io
import sys
import bisect


import sys
sys.path.insert(0, "../../")

from chainer.datasets.image_dataset import *
from chainer.dataset import dataset_mixin


def drop_cache():
    os.system("echo 3 | sudo tee /proc/sys/vm/drop_caches > /dev/null")
def _test2():
    import time
    import random
    import os
    from chainer.iterators import MultiprocessIterator
    IMGROOT="YOUR_PATH"
    zds = ZippedImageDataset(os.path.join(IMGROOT, "cropped-train256.zip")) # some zip

    for np in (1, 2, 4, 8, 16, 32):
        iterator = MultiprocessIterator(zds, 20, n_processes=np)
        drop_cache()
        t0 = time.time()
        for i in range(128):
            next(iterator)
        t1 = time.time()
        print("{}: {}".format(np, t1-t0))
    return
    
def _test1():
    import time
    import random
    import os
    IMGROOT="YOUR_PATH"
    zipfiles = [
        'cropped-train256/1.zip',
        'cropped-train256/2.zip'
    ]
    with open(os.path.join(IMGROOT, "train.txt"), 'r') as f:
        paths = [fn.strip() for fn in f.readlines()]
    ids = ImageDataset(paths, root=IMGROOT)
    zds = ZippedImageDataset(os.path.join(IMGROOT, "cropped-train256.zip"))
    mds = MultiZippedImageDataset([os.path.join(IMGROOT, zipfilepath) for zipfilepath in zipfiles])

    # random read test
    assert len(ids) == len(zds)
    idx = list(range(len(ids)))
    random.shuffle(idx)

    def random_read_test(ds, idx, repeat=10):
        results = []
        for r in range(repeat):
            drop_cache()
            t0 = time.time()
            for i in idx:
                d = ds[i]
            t1 = time.time()
            results.append(t1-t0)
        results = numpy.array(results)
        return numpy.min(results), numpy.sum(results)/len(results), numpy.max(results)

    repeat=1
    print("3")
    mds_result = random_read_test(mds, idx, repeat=repeat)
    print("2")
    zds_result = random_read_test(zds, idx, repeat=repeat)
    print("1")
    ids_result = random_read_test(ids, idx, repeat=repeat)

    print("--- min, avg, max")
    print(" image dataset: {}, {}, {}".format(*ids_result))
    print("zipped dataset: {}, {}, {}".format(*zds_result))
    print(" multi dataset: {}, {}, {}".format(*mds_result))

if __name__ == '__main__':
    _test1()
    _test2()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
