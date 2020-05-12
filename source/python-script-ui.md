---
title: python script ui (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ui'


Modules used in program: 
* `import worker`
* `import tornado`
* `import tornado.web`
* `import tornado.ioloop`
* `import random`
* `import os`
* `import datetime`

## python ui

Python example: ui

```python
#!/usr/bin/python
# -*- coding= utf-8 -*-

import datetime
import os
import random
import tornado.ioloop
import tornado.web
import tornado
from rq import Queue, Connection
from rq.job import Job
import worker

class MainHandler(tornado.web.RequestHandler):
	def get(self):
		n = self.get_argument('n', '')
		if not n:
			n = random.randint(1, 100)
			self.write('<a href="/?n=%s">Try this</a>' % n)
			return
		n = int(n)
		with Connection():
			q = Queue()
			job = q.enqueue(worker.slow_pow, n)
			print(job.id)
			ret = {'job_id': job.id}
			self.write('Job added, check result at: <a href="/check/?job_id=%(job_id)s" target="_blank">%(job_id)s</a>' % ret)

class CheckHandler(tornado.web.RequestHandler):
	def get(self):
		job_id = self.get_argument('job_id', '')
		
		with Connection():
			job = Job().fetch(job_id)
			ret = job.return_value 
			status = False
			if ret is not None:
				status = True
			
			self.write({'status' : status, 'ret': ret})


app = tornado.web.Application([
	(r'/', MainHandler),
	(r'/check/', CheckHandler),
])

if __name__ == '__main__':
	app.debug = True
	app.listen(9527)
	tornado.ioloop.IOLoop.instance().start()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
