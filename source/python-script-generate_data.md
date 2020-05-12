---
title: python script generate data (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'generate data'

Functions in program: 
* `def generate_item(s1, s2):`

Modules used in program: 
* `import random`
* `import argparse`

## python generate data

Python example: generate data

```python
#!/usr/bin/env python
import argparse
import random

parser = argparse.ArgumentParser(description="generate test data",
                                 epilog="https://github.com/shenwei356/")
parser.add_argument('-n',
                    type=int,
                    default=700000,
                    help='number of query list')
parser.add_argument('-m',
                    type=int,
                    default=3000000,
                    help='number of subject list')
parser.add_argument('-m2',
                    type=int,
                    default=4,
                    help='number of items of one line in subject list')
parser.add_argument('-s1', type=int, default=5, help='minimum size of item')
parser.add_argument('-s2', type=int, default=10, help='minimum size of item')
parser.add_argument('-fq', '--query-file', type=str, default="query.txt", help='query file')
parser.add_argument('-fs', '--subject-file', type=str, default="subject.txt", help='subject file')
args = parser.parse_args()

alphabet = 'abcdefghijklmnopqrstuvwxyz0123456789_-'
alphabet_size = len(alphabet)

random.seed = 1

def generate_item(s1, s2):
    return "".join([alphabet[random.randint(0, alphabet_size - 1)]
                    for i in range(s1+random.randint(0, s2-s1))])

query_data = set()
while(len(query_data)<args.n):
    query_data.add(generate_item(args.s1, args.s2))
with open(args.query_file, 'w') as fh:
    for item in query_data:
        fh.write('{}\n'.format(item))


subject_data = query_data
while(len(subject_data)<args.m):
    subject_data.add(generate_item(args.s1, args.s2))
with open(args.subject_file, 'w') as fh:
    for item in subject_data:
        items = [generate_item(args.s1, args.s2) for i in range(args.m2)]
        items.append(item)
        random.shuffle(items)
        fh.write('{}\n'.format('; '.join((items))))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
