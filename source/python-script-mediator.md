---
title: python script mediator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mediator'


Modules used in program: 
* `import time`
* `import random`

## python mediator

Python example: mediator

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import random
import time

class TC:
	def __init__(self):
		self._tm = None
		self._bProblem = 0

	def setup(self):
		print("Setting up the Test")
		time.sleep(1)
		self._tm.prepareReporting()

	def execute(self):
		if not self._bProblem:
			print("Executing the test")
			time.sleep(1)
		else:
			print("Problem in setup. Test not executed.")

	def tearDown(self):
		if not self._bProblem:
			print("Tearing down")
			time.sleep(1)
			self._tm.publishReport()
		else:
			print("Test not executed. No tear down required.")

	def setTM(self, tm):
		self._tm = tm

	def setProblem(self, value):
		self._bProblem = value


class Reporter:
	def __init__(self):
		self._tm = None

	def prepare(self):
		print("Reporter Class is preparing to report the results")
		time.sleep(1)

	def report(self):
		print("Reporting the results of Test")
		time.sleep(1)

	def setTM(self, tm):
		self._tm = tm


class DB:
	def __init__(self):
		self._tm = None

	def insert(self):
		print("Inseting the execution begin status in the Database")
		time.sleep(1)
		import random
		if random.randrange(1, 4) == 3:
			return -1

	def update(self):
		print("Updating the test results in Database")
		time.sleep(1)

	def setTM(self, tm):
		self._tm = tm


class TestManager:
	def __init__(self):
		self._reporter = None
		self._db = None
		self._tc = None

	def prepareReporting(self):
		rvalue = self._db.insert()
		if rvalue == -1:
			self._tc.setProblem(1)
			self._reporter.prepare()

	def setReporter(self, reporter):
		self._reporter = reporter

	def setDB(self, db):
		self._db = db

	def publishReport(self):
		self._db.update()
		self._reporter.report()

	def setTC(self, tc):
		self._tc = tc

if __name__ == '__main__':
	reporter = Reporter()
	db = DB()
	tm = TestManager()
	tm.setReporter(reporter)
	tm.setDB(db)
	reporter.setTM(tm)
	db.setTM(tm)

	while True:
		tc = TC()
		tc.setTM(tm)
		tm.setTC(tc)
		tc.setup()
		tc.execute()
		tc.tearDown()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
