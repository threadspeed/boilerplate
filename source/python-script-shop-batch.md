---
title: python script shop-batch (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'shop-batch'


Modules used in program: 
* `import json`
* `import logging`
* `import requests`

## python shop-batch

Python example: shop-batch

```python
import requests
from requests.auth import HTTPBasicAuth
import logging
import json
from uuid import uuid4
from random import random, randint, choice

waren = [ 'Milch','Bananen','Äpfel','Birnen','Brot','Tomaten','Käse','Gurken','Zitrone']

auth=HTTPBasicAuth('changeit', 'changeit');
headers= { "Content-Type": "application/vnd.eventstore.events+json" }

for i in range(1,1000):
    events = []
    for j in range(1,1000):
        events.append({
            "eventId"    : str(uuid4()),
            "eventType"  : "Verkauf",
            "data"       : { 
                "name": choice(waren),
                "preis": round(random() * 10,2),
                "menge": randint(1,101),
            }
        })
    

    requests.post( 'http://127.0.0.1:2113/streams/verkaeufe', data=json.dumps(events), auth=auth, headers=headers)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
