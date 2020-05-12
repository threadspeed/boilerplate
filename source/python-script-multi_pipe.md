---
title: python script multi pipe (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multi pipe'

Functions in program: 
* `def get_s():`
* `def worker(p):`

Modules used in program: 
* `import random`
* `import time`
* `import sys`

## python multi pipe

Python mysql example: multi pipe

```python
from multiprocessing import Process, Pipe
import sys
import time
import random

def worker(p):
	while True:
		s = p.recv()
		if not s:
			break
		time.sleep(random.random())
		p.send("%s is a %s!" % (s, random.choice(['cat', 'dog', 'oter', 'hedgehog'])))


def get_s():
	return raw_input("Enter a name: ")

parent_pipe, child_pipe = Pipe()
p = Process(target=worker, args=[child_pipe])
p.start()

s = get_s()
while s:
	parent_pipe.send(s)

	print('Thinking',)
	while not parent_pipe.poll():
		print('.',)
		sys.stdout.flush()
		time.sleep(.1)
	print

	message = parent_pipe.recv()
	if not message:
		raise RuntimeError("This is weird!")
	print('Message:', message)

	s = get_s()

parent_pipe.send(None)

print("Finita!")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
