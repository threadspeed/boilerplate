---
title: python script doodle-spoiler (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'doodle-spoiler'


Modules used in program: 
* `import requests # https://requests.readthedocs.io/en/master/user/install/`
* `import random`

## python doodle-spoiler

Python example: doodle-spoiler

```python
#! /usr/bin/env python3

# Script to randomize a Doodle poll

import random
import requests # https://requests.readthedocs.io/en/master/user/install/

poll_id = 'a5x4m4u83hhxkxd5'

api_url = 'https://doodle.com/api/v2.0/polls/{}'.format(poll_id)

r = requests.get(api_url, params={'adminKey':'', 'participantKey':''})
data = r.json()

participant_url = '{}/participants'.format(api_url)
for participant in data['participants']:
    if 'userId' in participant:
        continue # registered users cannot be updated
    update_url = '{}/{}'.format(participant_url, participant['id'])
    payload = {
        'id': participant['id'],
        'name': participant['name'],
        'preferences': random.choice(([1, 0], [0, 1])),
        'optionsHash': data['optionsHash'],
        'participantKey': None,
    }
    #! Danger !# requests.put(update_url, json=payload)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
