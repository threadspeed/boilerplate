---
title: python script step1 nongeneric (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'step1 nongeneric'

Functions in program: 
* `def write_test_files(tmpdir):`
* `def mapreduce(data_dir):`
* `def execute(workers):`
* `def create_workers(input_list):`
* `def generate_inputs(data_dir):`

Modules used in program: 
* `import random`
* `import os`

## python step1 nongeneric

Python mysql example: step1 nongeneric

```python
class InputData(object):
    """Abstraction base class"""
    def read(self):
        raise NotImplementedError
        
        
class PathInputData(InputData):
    """Concrete class"""
    def __init__(self, path):
        super().__init__()
        self.path = path
        
    def read(self):
        with open(self.path, 'rb') as handle:
            return handle.read()

        
class Worker(object):
    """Abstraction base class"""
    def __init__(self, input_data):
        self.input_data = input_data
        self.result = None
        
    def map(self):
        raise NotImplementedError
        
    def reduce(self, other):
        raise NotImplementedError
        

class LineCountWorker(Worker):
    """Concrete class"""
    def map(self):
        data = self.input_data.read()
        self.result = data.count(b'\n')
    
    def reduce(self, other):
        self.result += other.result
        
        
# Orchastration by helper functions

import os


def generate_inputs(data_dir):
    for name in os.listdir(data_dir):
        yield PathInputData(os.path.join(data_dir, name))
        

def create_workers(input_list):
    workers = []
    for input_data in input_list:
        workers.append(LineCountWorker(input_data))
    return workers


from threading import Thread


def execute(workers):
    threads = [Thread(target=w.map) for w in workers]
    for thread in threads: thread.start()
    for thread in threads: thread.join()
        
    first, rest = workers[0], workers[1:]
    for worker in rest:
        first.reduce(worker)
    return first.result

def mapreduce(data_dir):
    inputs = generate_inputs(data_dir)
    workers = create_workers(inputs)
    return execute(workers)


import random


def write_test_files(tmpdir):
    for i in range(100):
        with open(os.path.join(tmpdir, str(i)), 'w') as handle:
            handle.write('\n' * random.randint(0, 100))

            
from tempfile import TemporaryDirectory


with TemporaryDirectory() as tmpdir:
    write_test_files(tmpdir)
    result = mapreduce(tmpdir)
    print(result)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
