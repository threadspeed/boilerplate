---
title: python script machine-learning   main   (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'machine-learning   main  '


## python machine-learning   main  

Python mysql example: machine-learning   main  

```python
from optparse import OptionParser
from linear_regression import model as linear

parser = OptionParser()
parser.add_option('-t', '--train', dest='train')
parser.add_option('-p', '--passes', type='int', default=10, dest='passes')
parser.add_option('-l', '--learn_rate', type='float', default=0.1, dest='learn_rate')
parser.add_option('--l1', type='float', default=0, dest='lreg1')
parser.add_option('--l2', type='float', default=0, dest='lreg2')
(options, args) = parser.parse_args()

linear_model = linear.model()
linear_model.train(options)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
