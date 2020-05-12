---
title: python script pipLine (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pipLine'


Modules used in program: 
* `import threading`
* `import time`
* `import random`
* `import queue`

## python pipLine

Python mysql example: pipLine

```python
from threading import Thread
import queue
import random
import time
import threading



# 流水线
class Job(Thread):
    def __init__(self, q):
        Thread.__init__(self)
        self._q = q

    def run(self):
        while True:
            jobId = self._q.get()
            if jobId is None:
                continue

            try:
                print("Start Job: [%s] " % jobId)
                sleepTime = random.randint(1,10)
                time.sleep(sleepTime)
                print("Completed Job: [%s] sleep [%ds]" % (jobId,sleepTime))
            except Exception as e:
                print(e)
            finally:
                self._q.task_done()



if __name__ == "__main__":
    # 开启20份工作
    job_list = range(0,20)
    downloader_count = 10
    q = queue.Queue()

    for i in range(downloader_count):
        # 开了5条流水线
        downloader = Job(q)
        downloader.setDaemon(True)
        downloader.start()

    for jobId in job_list:
        q.put(jobId)

    q.join()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
