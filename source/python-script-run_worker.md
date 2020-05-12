---
title: python script run worker (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'run worker'


## python run worker

Python mysql example: run worker

```python
from rq import Queue, Worker, Connection

if __name__ == '__main__':
	with Connection():
		q = Queue()
		Worker(q).work()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
