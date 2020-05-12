---
title: python script pkl xz (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pkl xz'

Functions in program: 
* `def pkl_to_pkl_xz(file_path):`
* `def save(data, output_path):`
* `def load(input_path):`

Modules used in program: 
* `import pickle as pkl`
* `import subprocess as proc`

## python pkl xz

Python mysql example: pkl xz

```python
# save and load "pkl.xz" pickle files compressed with xz

import subprocess as proc
import pickle as pkl

def load(input_path):
    with open(input_path, "rb") as f:
        result = proc.run(["xz", "--decompress"], stdin=f, stdout=proc.PIPE)
        if result.returncode != 0:
            raise ChildProcessError(result.returncode)
        return pkl.loads(result.stdout)

def save(data, output_path):
    with open(output_path, "wb") as datafile:
        pickle = pkl.dumps(data)
        result = proc.run(["xz"], input=pickle, stdout=datafile)
        if result.returncode != 0:
            raise ChildProcessError(result.returncode)

def pkl_to_pkl_xz(file_path):
    with open(file_path, "rb") as in_file:
        with open(str(file_path) + ".xz", "wb") as out_file:
            proc.run(["xz"], stdin=in_file, stdout=out_file)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
