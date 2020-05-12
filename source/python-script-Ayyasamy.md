---
title: python script Ayyasamy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ayyasamy'

Functions in program: 
* `def write_xml(data, file_name):`
* `def write_csv(data, file_name):`
* `def write_json(data, file_name):`
* `def person():`

Modules used in program: 
* `import dicttoxml`
* `import csv`
* `import json`

## python Ayyasamy

Python example: Ayyasamy

```python
from faker import Factory
import json
import csv
import dicttoxml

myGenerator = Factory.create()
#Note: update the seed for reproduce the data
myGenerator.seed_instance(070)

def person():
	prof = myGenerator.profile(fields=['name', 'mail', 'address', 'website'], sex=None)
	phone = myGenerator.phone_number()
	ip = myGenerator.ipv4_private(network=False, address_class=None)

	return {
		'name': prof['name'],
		'mail': prof['mail'],
		'address': prof['address'],
		'website': prof['website'],
		'phone': phone,
		'ip_address': ip
	}

def write_json(data, file_name):

	with open(file_name + '.json','w') as file:
		json.dump(data, file, sort_keys=True, indent=4)	

def write_csv(data, file_name):
	write_mode = open(file_name + '.csv', 'w')
	csvwriter = csv.writer(write_mode)
	count = 0

	for datum in data:

	      if count == 0:
		     header = datum.keys()
		     csvwriter.writerow(header)
		     count += 1

	      csvwriter.writerow(datum.values())
	write_mode.close()

def write_xml(data, file_name):
	with open(file_name + '.xml', 'w') as f:
		f.write(dicttoxml.dicttoxml(data))

people = []
for i in range(100):	
	people.append(person())

write_json(people, 'people')
write_xml(people, 'people')
write_csv(people, 'people')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
