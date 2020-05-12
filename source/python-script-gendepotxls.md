---
title: python script gendepotxls (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gendepotxls'

Functions in program: 
* `def main(sheetnum=10, urnnum=250):`

Modules used in program: 
* `import argparse`
* `import string`
* `import random`
* `import xlsxwriter`

## python gendepotxls

Python example: gendepotxls

```python
#!/usr/bin/env python
"""
Generates URN/codes and saves them to a single Excel file with each depot on a separate sheet.

URN Format: (\d{3})([A-Z])(\d{3})
Group 1: Random capital letter A-Z (technically unecessary)
Group 2: Depot number 01-67
Group 3: Sequence number 001-250 (never repeats)
"""

import xlsxwriter
import random
import string
import argparse

def main(sheetnum=10, urnnum=250):
    filename = "depot_codes.xls"
    workbook = xlsxwriter.Workbook(filename)
    for depot in range(1, sheetnum+1):
        worksheet = workbook.add_worksheet()
        for code in range(1, urnnum+1):
            urn = "%02d%s%03d" % (depot, random.choice(string.ascii_uppercase), code)
            worksheet.write(code-1, 0, urn)

if __name__ == '__main__':
    parser = argparse.ArgumentParser(
        description="Generates Excel file containing unique codes for a set number of depots with each depot's codes on a separate line"
    )
    parser.add_argument('depots', type=int, help="Number of depots from 0-99 (separate sheet in file created for each)")
    parser.add_argument('codes', type=int, help="Number of codes per depot")

    args = parser.parse_args()
    main(args.depots, args.codes)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
