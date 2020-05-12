---
title: python script multi queue (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multi queue'

Functions in program: 
* `def get_s():`
* `def worker(s_q, r_q):`

Modules used in program: 
* `import random`
* `import time`
* `import sys`

## python multi queue

Python example: multi queue

```python
from multiprocessing import Process, Queue
import sys
import time
import random


def worker(s_q, r_q):
	while True:
		s = s_q.get()
		if not s:
			break
		time.sleep(random.random())
		r_q.put("%s is a %s!" % (s, random.choice(['cat', 'dog', 'oter', 'hedgehog'])))


def get_s():
	return raw_input("Enter a name: ")

send_q = Queue()
receive_q = Queue()
p = Process(target=worker, args=[send_q, receive_q])
p.start()

s = get_s()
while s:
	send_q.put(s)

	while receive_q.empty():
		print('.',)
		sys.stdout.flush()
		time.sleep(.2)
	
	message = receive_q.get_nowait()
	if not message:
		raise RuntimeError("This is weird!")
	print('Message:', message)

	s = get_s()

send_q.put(None)

print("Finita!")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
