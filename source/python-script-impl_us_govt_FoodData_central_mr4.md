---
title: python script impl us govt FoodData central mr4 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'impl us govt FoodData central mr4'


Modules used in program: 
* `import random`
* `import json`
* `import random`
* `import json`

## python impl us govt FoodData central mr4

Python mysql example: impl us govt FoodData central mr4

```python
# FAILURE CAUSING
# MR4: subset relation based on ingredients
# MR4: subset relation based on ingredients
"""
import json
import random
from urllib.request import urlopen, Request

from us_govt.FoodData_central.reper import FOOD_TERMS

# query = random.choice(FOOD_TERMS)

query = "fast food"
data1 = {
    "generalSearchInput": query,
    "ingredients": "sugar, honey"

}
data_str = json.dumps(data1).encode("utf-8")
url = 'https://api.nal.usda.gov/fdc/v1/search?api_key=HgevTUI0JDgzi7Y9XcHR3a3o9SQP6LfblaH4tnMZ'
req = Request(url, data_str, {'Content-Type': 'application/json'})
f = urlopen(req)
for x in f:
    resp1 = json.loads(x)
f.close()

############################
data2 = {
    "generalSearchInput": query,
    "ingredients": "sugar, honey"
}
data_str2 = json.dumps(data2).encode("utf-8")
req = Request(url, data_str2, {'Content-Type': 'application/json'})
f = urlopen(req)
for x in f:
    resp2 = json.loads(x)
f.close()

########################
data3 = {
    "generalSearchInput": query,
    "ingredients": "sugar, honey, sugar and honey"
}
data_str3 = json.dumps(data2).encode("utf-8")
req = Request(url, data_str3, {'Content-Type': 'application/json'})
f = urlopen(req)
for x in f:
    resp3 = json.loads(x)
f.close()

if resp1['totalHits'] < resp2['totalHits'] < resp3['totalHits']:
    print('good')
else:
    print('bad')

"""


import json
import random
from urllib.request import urlopen, Request

from us_govt.FoodData_central.reper import FOOD_TERMS

for i in range(1):
    query = random.choice(FOOD_TERMS)
    data = {
        "generalSearchInput": query,
        "ingredients": "sugar"

    }
    data_str = json.dumps(data).encode("utf-8")
    url = 'https://api.nal.usda.gov/fdc/v1/search?api_key=HgevTUI0JDgzi7Y9XcHR3a3o9SQP6LfblaH4tnMZ'
    req = Request(url, data_str, {'Content-Type': 'application/json'})
    f = urlopen(req)
    for x in f:
        resp1 = json.loads(x)
    f.close()

    data2 = {
        "generalSearchInput": query,
        "ingredients": "sugar honey"
    }
    data_str2 = json.dumps(data2).encode("utf-8")
    req = Request(url, data_str2, {'Content-Type': 'application/json'})
    f = urlopen(req)
    for x in f:
        resp2 = json.loads(x)
    f.close()

    if resp1['totalHits'] > resp2['totalHits']:
        print('good, rerunning. . .', format(i))
        continue
    else:
        print('bad')
        break
else:
    print('unable to find fault')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
