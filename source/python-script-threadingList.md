---
title: python script threadingList (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'threadingList'

Functions in program: 
* `def job(jobId,q):`

Modules used in program: 
* `import threading`
* `import time`
* `import random`
* `import queue`

## python threadingList

Python example: threadingList

```python
from threading import Thread
import queue
import random
import time
import threading

# 消费者
def job(jobId,q):
    try:
        print("Start Job: [%s] " % jobId)
        sleepTime = random.randint(1,10)
        time.sleep(sleepTime)
        print("Completed Job: [%s] sleep [%ds]" % (jobId,sleepTime))
        q.put(jobId)
    except Exception as e:
        print(e)
    finally:
        q.task_done()


if __name__ == "__main__":
    job_list = range(0,20)
    q = queue.Queue()
    # 队列组
    threads = []
    for jobId in job_list:
        t = threading.Thread(target=job, args=(jobId, q)) # 定义多线程,把我们的url传给获取api数据的方法       
        t.start()
        threads.append(t)

    print("threads created")

    for thread in threads:
        thread.join() #阻塞,等待线程终止,那这样总时间不就是所有线程中最慢的?

    print("threads finish")


    for _ in job_list:
        result = q.get() # 线程结束后,再从队列里面把数据拿出来
        print(result)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
