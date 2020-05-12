---
title: python script query (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'query'


Modules used in program: 
* `import sys`
* `import random`
* `import argparse`

## python query

Python mysql example: query

```python
#!/usr/bin/env python
import argparse
import random
import sys

parser = argparse.ArgumentParser(description="quering by item list",
                                 epilog="https://github.com/shenwei356/")
parser.add_argument('--query-file', type=str, default="query.txt", help='query file')
parser.add_argument('--subject-file', type=str, default="subject.txt", help='subject file')
parser.add_argument('--result-file', type=str, default="result.txt", help='result file')
parser.add_argument('-v', action='store_true', help='verbosely print(information'))
args = parser.parse_args()

sys.stderr.write('reading query list...\n')
query_data = set()
with open(args.query_file) as fh:
    for line in fh:
        query_data.add(line.strip())
sys.stderr.write('{} items loaded\n'.format(len(query_data)))

sys.stderr.write("start querying...\n")
with open(args.result_file, 'w') as fout:
    with open(args.subject_file) as fh:
        i, hit = 0, 0
        for line in fh:
            i += 1
            for item in line.strip().split('; '):
                if item in query_data:
                    fout.write(line)
                    hit+=1
                    if args.v:
                        sys.stderr.write('hit {} from {}\n'.format(hit, i))
                    break

        sys.stdout.write('hit {} from {}\n'.format(hit, i))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
