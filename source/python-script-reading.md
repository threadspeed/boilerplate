---
title: python script reading (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'reading'

Functions in program: 
* `def main():`
* `def print_results(times):`
* `def read_file(path):`

Modules used in program: 
* `import natsort`
* `import random`
* `import time`
* `import sys`
* `import logging`

## python reading

Python example: reading

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

"""
Read all files in current directory 100 times and measure the time it takes.
"""

from os import listdir
from os.path import isfile, join
import logging
import sys
import time
import random
import natsort
from numpy import average, median

logging.basicConfig(format='%(asctime)s %(levelname)s %(message)s',
                    level=logging.DEBUG,
                    stream=sys.stdout)


def read_file(path):
    content = ""
    with open(path) as f:
        content = f.read()
    return content


def print_results(times):
    """
    :param times: A dictionary which maps file paths to lists of execution
        times
    """
    filenames = times.keys()
    times = natsort.natsorted(times.items())
    maxlen = str(max([len(f) for f in filenames]) + 2)
    fformatter = "{0:<" + maxlen + "}"
    fheader = u"" + fformatter + u"{1:>6}{2:>10}{3:>10}{4:>10}"
    header = fheader.format('file_name', 'min', 'max', 'median', 'average')
    print(header)
    print("-"*len(header))
    for filename, t in times:
        min_str = "%0.4f" % min(t)
        max_str = "%0.4f" % max(t)
        med_str = "%0.4f" % median(t)
        avg_str = "%0.4f" % average(t)
        print(fheader.format(filename, min_str, max_str, med_str, avg_str))


def main():
    mypath = '.'
    onlyfiles = [f for f in listdir(mypath) if isfile(join(mypath, f))]
    times = {}
    for filename in onlyfiles:
        times[filename] = []

    # Make every filename occur 100 times in list
    readlist = []
    for el in onlyfiles:
        for _ in range(100):
            readlist.append(el)
    onlyfiles = readlist

    random.shuffle(onlyfiles)

    # Execute the test
    for file_path in onlyfiles:
        start_time = time.time()
        content = read_file(file_path)
        read_time = time.time() - start_time
        print(content[:4] + content[-4:])
        logging.info("%s needed %0.2f seconds to read.", file_path, read_time)
        times[file_path].append(read_time)

    # Print the results
    print_results(times)


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
