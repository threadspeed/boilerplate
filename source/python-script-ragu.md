---
title: python script ragu (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ragu'

Functions in program: 
* `def create_rows(num=count):`
* `def ph_num():`

Modules used in program: 
* `import csv, json, sys`
* `import random`
* `import pandas as pd`

## python ragu

Python mysql example: ragu

```python
from faker import Faker
import pandas as pd
import random
import csv, json, sys
from dicttoxml import dicttoxml

fake = Faker()
count = 100

def ph_num():
    n = '0000000000'
    while '9' in n[3:6] or n[3:6]=='000' or n[6]==n[7]==n[8]==n[9]:
        n = str(random.randint(10**9, 10**10-1))
    return n[:3] + '-' + n[3:6] + '-' + n[6:]

def create_rows(num=count):
	data = [{               
	           "name":fake.name(),
	           "email":fake.email(),
	           "address":fake.address(),
	           "website":fake.url(),
	           "phone_number":ph_num(),
	           "serial":x,
	           "ip_address":'.'.join('%s'%random.randint(0, 255) for i in range(4))
	        } for x in range(num)]
	print('Output files generated!! Generated people.json, people.csv and people.xml files')

	# Write CSV File
	f = open("people.csv", "w")
	w = csv.DictWriter(f, data[0].keys())
	w.writeheader()
	for row in data:
	 	w.writerow(row)

	# Write Json File	
	with open('people.json', 'w') as outfile:            
		json.dump(data, outfile, indent=4)

	# Write XML File
	dataval = dicttoxml(data)
	from xml.dom import minidom
	from xml.etree import ElementTree as ET
	root = ET.fromstring(dataval)
	tree = ET.ElementTree(root)
	data = minidom.parseString(ET.tostring(root)).toprettyxml(indent="   ")
	with open('people.xml', "w") as f:
		f.write(data)

create_rows()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
