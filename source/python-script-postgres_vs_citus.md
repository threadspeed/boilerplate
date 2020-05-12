---
title: python script postgres vs citus (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'postgres vs citus'

Functions in program: 
* `def send_query_to_host(hostname, port, database, query, resultQueue):`

Modules used in program: 
* `import random`
* `import Queue`
* `import time`
* `import signal`
* `import atexit`
* `import random`
* `import os`
* `import sys`

## python postgres vs citus

Python example: postgres vs citus

```python
import sys
import os
import random
import atexit
import signal
from subprocess import Popen, PIPE

from os.path import expanduser
from threading import Thread
from time import sleep
import time
import Queue
import random

def send_query_to_host(hostname, port, database, query, resultQueue):
	pg = ['psql', '-X', '-e' , '-P','pager=off', '-v', 'ON_ERROR_STOP=1', '-h', hostname, '-p', str(port) , '-c', query, database]

	p = Popen(pg, stdin=PIPE, stdout=PIPE, stderr=PIPE)
	output, err = p.communicate()
	rc = p.returncode

	resultQueue.put(output)


if __name__ == "__main__":
	query_file = open("queries.sql", "r")
	lines = query_file.readlines()

	random.shuffle(lines)

	citus_host, citus_port = "localhost", 5432
	postgres_host, postgres_port = "localhost", 9703

	resultQueue = Queue.Queue()

	lineNumber = 1

	for line in lines:
		jobs = []
		print(line)
		postgres_thread = Thread(target = send_query_to_host, args=(postgres_host, postgres_port, "postgres" , line, resultQueue))
		postgres_thread.start()
		postgres_thread.join()
		postgres_result = resultQueue.get()

		if "CREATE TABLE" in line:
			line = line + "SELECT create_distributed_table('test', 'a')"

		citus_thread = Thread(target = send_query_to_host, args=(citus_host, citus_port, "postgres" , line, resultQueue))
		citus_thread.start()
		citus_result = resultQueue.get()
		citus_thread.join()

		if citus_result != postgres_result and "CREATE TABLE" not in line:
			print("Postgres and Citus returned different results for command:")
			print("------------------------")
			print(line)
			print("------------------------")
			
			print("Postgres result:")
			print("------------------------")
			print(postgres_result)
			print("------------------------")

			print("Citus result:")
			print("------------------------")
			print(citus_result)
			print("------------------------")

			exit(-1)
		else:
			print("Command ", lineNumber, " finished, the results are the same...")

		lineNumber = lineNumber + 1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
