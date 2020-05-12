---
title: python script gendepotcodes (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gendepotcodes'

Functions in program: 
* `def main(csvnum=10, urnnum=250):`

Modules used in program: 
* `import argparse`
* `import string`
* `import random`
* `import csv`

## python gendepotcodes

Python mysql example: gendepotcodes

```python
#!/usr/bin/env python
"""
Generates URN/codes and saves them to separate CSV files - 1 for each depot.

URN Format: (\d{3})([A-Z])(\d{3})
Group 1: Random capital letter A-Z (technically unecessary)
Group 2: Depot number 01-67
Group 3: Sequence number 001-250 (never repeats)
"""

import csv
import random
import string
import argparse

def main(csvnum=10, urnnum=250):
    for depot in range(1, csvnum+1):
        filename = "depot-%d.csv" % depot
        with open(filename, 'wb') as f:
            fw = csv.writer(f, dialect='excel')
            for code in range(1, urnnum+1):
                urn = "%02d%s%03d" % (depot, random.choice(string.ascii_uppercase), code)
                fw.writerow([urn])

if __name__ == '__main__':
    parser = argparse.ArgumentParser(description="Generates separate CSV files containing unique codes for a set number of depots")
    parser.add_argument('depots', type=int, help="Number of depots from 0-99 (separate CSV file created for each)")
    parser.add_argument('codes', type=int, help="Number of codes per depot")

    args = parser.parse_args()
    main(args.depots, args.codes)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
