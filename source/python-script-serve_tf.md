---
title: python script serve tf (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'serve tf'


Modules used in program: 
* `import random`
* `import json`
* `import multiprocessing`
* `import os`
* `import logging`

## python serve tf

Python mysql example: serve tf

```python
import logging
import os
import multiprocessing
import json
import random


class TF_Process_Manager:
    def __init__(self, processes):
        self.procs = processes
        self.current_server = 0

    def process(self, data):
        self.current_server = (self.current_server + 1) % len(self.procs)
        print(self.current_server)
        process = self.procs[self.current_server]
        with process.lock:
            process.connection.send(data)
            return process.connection.recv()

    def start(self):
        for p in self.procs:
            logging.info("Starting process on gpu:{}".format(p.gpu))
            p.start()

    def wait_start(self):
        for p in self.procs:
            p.is_running.wait()

    def stop(self):
        for p in self.procs:
            p.should_stop.set()
        for p in self.procs:
            p.join()


class TF_Process(multiprocessing.Process):
    def __init__(self, gpu, models_dir, test_mode=False):
        multiprocessing.Process.__init__(self)
        self.lock = multiprocessing.Lock()
        self.test_mode = test_mode
        self.gpu = gpu
        self.models_dir = models_dir
        self.queue = multiprocessing.Queue()

        self.is_running = multiprocessing.Event()
        self.should_stop = None
        self.pipe = multiprocessing.Pipe()
        self.connection = self.pipe[0]

    def run(self):
        os.environ["CUDA_VISIBLE_DEVICES"] = str(self.gpu)
        #Some generic import functionality not actually implemented in gist
        self.model = generic_import_function(self.models_dir)

        self.is_running.set()
        self.should_stop = multiprocessing.Event()
        while not self.should_stop.is_set():
            input_data = self.recv()
            print("{} Data received".format(self.gpu))
            processed = self.process_input(input_data)
            print("{} Data processed".format(self.gpu))
            self.send(processed)

    def recv(self):
        return self.pipe[1].recv()

    def send(self, data):
        self.pipe[1].send(data)

    """
        Processing functions
    """

    def process_input(self, input_data):
        #Process input_data probably in json form and return some data to request.
        return self.model.sess.run(...)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
