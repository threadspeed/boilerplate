---
title: python script serve (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'serve'

Functions in program: 
* `def process():`
* `def files(path):`
* `def hello():`

Modules used in program: 
* `import argparse`
* `import random`
* `import json`
* `import os`
* `import logging`

## python serve

Python mysql example: serve

```python
from flask import Flask, send_from_directory, request, redirect, Response
import logging
import os
import json
import random
from serve_tf import TF_Process, TF_Process_Manager
import argparse


parser = argparse.ArgumentParser()
parser.add_argument("--addr", default="127.0.0.1", help="address to listen on")
parser.add_argument("--port", default=8000, type=int, help="port to listen on")
parser.add_argument("--gpus", default="0,0", type=str, help="GPUs to load models onto.")
parser.add_argument("--test_mode", default=False, help="run with local images that are in the git repo")
a = parser.parse_args()

app = Flask(__name__)
logging.basicConfig(level=logging.DEBUG)

tf_manager = None

@app.route("/")
def hello():
    return send_from_directory('static', 'index.html')


@app.route("/<path:path>", methods=['GET'])
def files(path):
    return send_from_directory('static', path)


@app.route("/process", methods=['POST'])
def process():
    logging.debug("Calling tf_server")
    logging.debug(request.json)
    res = tf_manager.process(request.json)
    return res

  
if __name__ == '__main__':
    tf_manager = TF_Process_Manager([TF_Process(i, './models/', test_mode=a.test_mode) for i in a.gpus.split(',')])
    tf_manager.start()
    tf_manager.wait_start()
    app.run(host=a.addr, port=a.port, threaded=True)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
