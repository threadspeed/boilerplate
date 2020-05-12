---
title: python script step3 generic with abc (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'step3 generic with abc'

Functions in program: 
* `def write_test_files(tmpdir):`
* `def mapreduce(worker_class, input_class, config):`
* `def execute(workers):`

Modules used in program: 
* `import random`
* `import os`
* `import abc`

## python step3 generic with abc

Python example: step3 generic with abc

```python
import abc


class InputData(abc.ABC):
    """Abstraction base class"""
    @abc.abstractmethod
    def read(self):
        pass
        
    @classmethod
    @abc.abstractmethod
    def generate_inputs(cls, config):
        """generate inputs"""

        
import os

        
class PathInputData(InputData):
    """Concrete class"""
    def __init__(self, path):
        super().__init__()
        self.path = path
        
    def read(self):
        with open(self.path, 'rb') as handle:
            return handle.read()
        
    @classmethod
    def generate_inputs(cls, config):
        data_dir = config['data_dir']
        for name in os.listdir(data_dir):
            yield cls(os.path.join(data_dir, name))
            
            
class Worker(abc.ABC):
    """Abstraction base class"""
    def __init__(self, input_data):
        self.input_data = input_data
        self.result = None
    
    @abc.abstractmethod
    def map(self):
        pass

    @abc.abstractmethod
    def reduce(self, other):
        pass
        
    @classmethod
    def create_workers(cls, input_class, config):
        workers = []
        for input_data in input_class.generate_inputs(config):
            workers.append(cls(input_data))
        return workers
        

class LineCountWorker(Worker):
    """Concrete class"""
    def map(self):
        data = self.input_data.read()
        self.result = data.count(b'\n')
    
    def reduce(self, other):
        self.result += other.result


from threading import Thread


def execute(workers):
    threads = [Thread(target=w.map) for w in workers]
    for thread in threads: thread.start()
    for thread in threads: thread.join()
        
    first, rest = workers[0], workers[1:]
    for worker in rest:
        first.reduce(worker)
    return first.result

def mapreduce(worker_class, input_class, config):
    workers = worker_class.create_workers(input_class, config)
    return execute(workers)


import random


def write_test_files(tmpdir):
    for i in range(100):
        with open(os.path.join(tmpdir, str(i)), 'w') as handle:
            handle.write('\n' * random.randint(0, 100))

            
from tempfile import TemporaryDirectory


with TemporaryDirectory() as tmpdir:
    write_test_files(tmpdir)
    config = {'data_dir': tmpdir}
    result = mapreduce(LineCountWorker, PathInputData, config)
    print(result)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
