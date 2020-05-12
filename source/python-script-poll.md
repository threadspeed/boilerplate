---
title: python script poll (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'poll'

Functions in program: 
* `def link(data, rel):`

Modules used in program: 
* `import json`
* `import logging`
* `import requests`

## python poll

Python example: poll

```python
import requests
from requests.auth import HTTPBasicAuth
import logging
import json
from uuid import uuid4
from time import sleep

headers= { "Accept": "application/vnd.eventstore.events+json" }
auth=HTTPBasicAuth('changeit', 'changeit');

def link(data, rel):
    try:
        return [ l["uri"] for l in data["links"] if l["relation"] == rel][0]
    except:
        return None

uri = "http://127.0.0.1:2113/streams/verkaeufe?embed=body"

etag = ""
while(True):

    headers["If-None-Match"] = etag
    res = requests.get( uri, auth=auth, headers=headers)

    if res.status_code == 304:
        print("Nichts!")
        sleep(2)
        continue

    etag = res.headers.get("ETag")

    data = json.loads(res.text)

    print("Empfangen: ", len(data["entries"]))
    for e in data["entries"][::-1]:
        v = json.loads(e["data"])
        print('{}: {} {} zu je {} €'.format(e["title"],v['menge'],v['name'], v['preis']))

    previous = link(data, 'previous')
    if previous:
        uri = previous + "?embed=body"
        



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
