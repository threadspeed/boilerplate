---
title: python script flask large dict (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'flask large dict'

Functions in program: 
* `def main():`
* `def after(response):`
* `def hello_world():`

Modules used in program: 
* `import gc`
* `import optparse`
* `import random`

## python flask large dict

Python mysql example: flask large dict

```python
import random
import optparse
import gc

from flask import redirect, Flask
from memory_profiler import memory_usage

# Create flask app
app = Flask(__name__)
app.debug = True

@app.route('/')
def hello_world():
	###
	# The test:
	# Generate a 2440 mb dictionary and return a blank page.
	###
	large_dict = {}
	for x in xrange(125000):
		large_row = {}
		for y in xrange(125):
			large_row[random.randint(1, 10000000000)] = random.randint(1, 10000000000)
		large_dict[random.randint(1, 10000000000)] = large_row

	large_dict = {}
	gc.collect()
	return ''

@app.after_request
def after(response):
	print(memory_usage(-1, interval=.2, timeout=1), "after request")
	return response
	
def main():
	app.config['SECRET_KEY'] = "BLAH"
	
	parser = optparse.OptionParser()
	parser.add_option("--host", default="0.0.0.0") # can't use -h, it's already taken by help
	parser.add_option("-p", "--port", default="5123")
	options, args = parser.parse_args()

	if len(args) > 0:
		parser.error("Unexpected arguments: %s" % args)

	app.run(host=options.host, port=int(options.port))

if __name__ == '__main__':
	# Start app
	main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
