---
title: python script create base data (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'create base data'

Functions in program: 
* `def create_base_data(filename, outfile, add_line, limit):`

Modules used in program: 
* `import random`

## python create base data

Python example: create base data

```python
#coding:utf-8
import random

def create_base_data(filename, outfile, add_line, limit):
	file = open(filename,'r', encoding="utf-8")
	data = file.readlines()
	file.close()
	data = random.sample(data, limit)  # ランダムに何行か抜く
	# ファイルに書き出し
	file = open(outfile, 'w', encoding='utf-8')
	for line in data:
		file.write(line)
	file.write(add_line)
	file.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
