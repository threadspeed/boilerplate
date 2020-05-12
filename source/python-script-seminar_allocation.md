---
title: python script seminar allocation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'seminar allocation'


Modules used in program: 
* `import random`

## python seminar allocation

Python mysql example: seminar allocation

```python
"""
TOC: http://www.deeplearningbook.org/contents/TOC.html
"""
import random
random.seed(2525)

num_for_each_chapters = [2,12,14,5,11,6,14,7,11,12,6,5,5,9,6,7,5,7,5,15]
members = ['yuji', 'hirokazu', 'kazuya', 'nabe', 'mitsu', 'msrks']

for chapter, num_sections in enumerate(num_for_each_chapters):
    for section in range(num_sections):
        selected = random.choice(members)
        print(f'{chapter+1}-{section+1}: {selected}')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
