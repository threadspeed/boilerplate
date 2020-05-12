---
title: python script chromosome (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'chromosome'


Modules used in program: 
* `import random`

## python chromosome

Python example: chromosome

```python
import random

from allowed_blocks import *

class Nucleotide(object):
    def __init__(self, value = None):
        if value is None:
            self.value = random.choice(allowed_blocks)
        elif type(value) is list:
            self.value = random.choice(value)
        else:
            self.value = value

    def __str__(self):
        return "Nucleotide(" + self.value + ")"
    
    def flip(self, value = None):
        if value is None:
            self.value = random.choice(allowed_blocks)
        elif type(value) is list:
            self.value = random.choice(value)
        else:
            self.value = value

class Chromosome(object):
    def __init__(self, reactor_size = None, maximum_random = 9, allowed_blocks = None):
        if reactor_size is None:
            reactor_size = (
                random.randint(1,maximum_random),
                random.randint(1,maximum_random),
                random.randint(1,maximum_random))
        self.raw_data = [Nucleotide(allowed_blocks) for i in range(reactor_size[0] * reactor_size[1])]
        self.x, self.z, self.height = reactor_size
        self.allowed_blocks = allowed_blocks

    def __iter__(self):
        for n in self.raw_data:
            yield n

    def __str__(self):
        return str(self.x) + 'x' + str(self.z) + 'x' + str(self.height) + ': ' + self.encoded_data()

    def __getitem__(self, key):
        return self.raw_data[key]

    def encoded_data(self):
        cr_text = []
        for nucleotide in self.raw_data:
            cr_text.append(nucleotide.value)

        layout = "".join(cr_text)
        return layout
    
    @property
    def reactor_size(self):
        return (self.x, self.z, self.height)
        


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
