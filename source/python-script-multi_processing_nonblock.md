---
title: python script multi processing nonblock (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multi processing nonblock'

Functions in program: 
* `def work(worker_id, queue):`
* `def check_queue(queue):`
* `def server(queue):`

Modules used in program: 
* `import time`
* `import random`

## python multi processing nonblock

Python mysql example: multi processing nonblock

```python
from multiprocessing import Process, Queue
from queue import Empty
import random
import time

WORKERS = 3  # Adjust according to CPU cores.


def server(queue):
    tasks = ["task_A", "task_B", "task_C", "task_D", "task_E", "task_F", "task_G", "task_H", "task_I", "task_J"]
    for i in range(WORKERS * 4):
        task = random.choice(tasks)
        print("Server: {0}".format(task))
        queue.put(task)
        time.sleep(1)


def check_queue(queue):
    try:
        task = queue.get_nowait()
        return task
    except Empty:
        return "empty"


def work(worker_id, queue):
    while True:
        task = check_queue(queue)
        if task is None:
            break
        if task == "empty":
            print("Worker {0}: Idling...".format(worker_id))
        else:
            print("Worker {0}: {1}".format(worker_id, task))
        time.sleep(0.5)
    queue.put(None)  # Propagate the the worker stop.


class Manager:

    def __init__(self):
        self.queue = Queue()
        self.server = None
        self.workers = []

    def start(self):
        for i in range(WORKERS):
            print("Starting worker {0}...".format(i))
            worker = Process(target=work, args=(i, self.queue))
            self.workers.append(worker)
            worker.start()
        print("Starting server...")
        self.server = Process(target=server, args=(self.queue,))
        self.server.start()

    def stop(self):
        print("Waiting for server to stop...")
        self.server.join()
        print("Server stopped, stopping workers...")
        self.queue.put(None)  # Trigger to stop the workers.
        for i in range(len(self.workers)):
            print("Stopping worker {0}.".format(i))
            self.workers[i].join()
        self.queue.close()


if __name__ == "__main__":
    manager = Manager()
    manager.start()
    manager.stop()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
