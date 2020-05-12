---
title: python script multi process (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multi process'

Functions in program: 
* `def list_append(count, id, conn):`

Modules used in program: 
* `import multiprocessing`
* `import random`

## python multi process

Python mysql example: multi process

```python
import random
import multiprocessing


def list_append(count, id, conn):
    output = []
    for i in range(count):
        output.append(random.random())
    conn.send(output)


if __name__ == "__main__":
    size = 10000000  # Number of random numbers to add
    procs = 2  # Number of processes to create

    # Create a list of jobs and then iterate through
    # the number of processes appending each process to
    # the job list
    jobs = []
    for i in range(0, procs):
        out_list = list()
        process = multiprocessing.Process(target=list_append,
                                          args=(size, i, child_conn))
        jobs.append(process)

        # Start the processes (i.e. calculate the random number lists)
    for j in jobs:
        j.start()

        # Ensure all of the processes have finished
    for j in jobs:
        j.join()

    print("List processing complete. {}".format(len(out_list)))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
