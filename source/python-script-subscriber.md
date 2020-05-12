---
title: python script subscriber (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'subscriber'

Functions in program: 
* `def link(data, rel):`

Modules used in program: 
* `import json`
* `import requests`

## python subscriber

Python mysql example: subscriber

```python
import requests
from requests.auth import HTTPBasicAuth
import json
from time import sleep

def link(data, rel):
    try:
        return [ l["uri"] for l in data["links"] if l["relation"] == rel][0]
    except:
        return None

headers= { "Accept": "application/vnd.eventstore.competingatom+json" }
auth=HTTPBasicAuth('changeit', 'changeit')

while(True):
    res = requests.get( "http://127.0.0.1:2113/subscriptions/verkaeufe/lager?embed=body", auth=auth, headers=headers)

    entries = json.loads(res.text)["entries"]

    for e in entries:

        v = json.loads(e["data"])
        print('{}: {} {} zu je {} €'.format(e["title"],v['menge'],v['name'], v['preis']))

        requests.post( link(e,'ack'), auth=auth, headers={ "Accept": "application/json" })

    sleep(0.5)

  
        
        
   




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
