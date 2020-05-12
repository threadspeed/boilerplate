---
title: python script createfile (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'createfile'

Functions in program: 
* `def main():`
* `def create_file(filename, size):`

Modules used in program: 
* `import sys`
* `import logging`
* `import string`
* `import random`

## python createfile

Python mysql example: createfile

```python
#!/usr/bin/env python

"""Create text files of different sizes with random content."""

import random
import string
import logging
import sys

logging.basicConfig(format='%(asctime)s %(levelname)s %(message)s',
                    level=logging.DEBUG,
                    stream=sys.stdout)


def create_file(filename, size):
    """
    Create files of a given size with random strings in them.
    Use values over 10,000,0000 with caution as it might render your PC useless
    for a couple of minutes.

    @param filename: The path to the filename
    @param size: Size in bytes
    """
    with open(filename, 'w') as f:
        symbols = string.letters + string.whitespace
        random_string = ''.join(random.choice(symbols) for _ in range(size))
        f.write(random_string)


def main():
    for el in [10, 100, 1024, 10*1024, 100*1024]:
        size = el*1024
        logging.info("Start creation of %i Byte file.", size)
        create_file("%i.txt" % size, size)


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
