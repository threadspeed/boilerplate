---
title: python script doodle-crud-api (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'doodle-crud-api'


Modules used in program: 
* `import random`
* `import requests # https://requests.readthedocs.io/en/master/user/install/`

## python doodle-crud-api

Python mysql example: doodle-crud-api

```python
#! /usr/bin/env python3

# Script to get poll results and to post/update/delete a participant using Doodle CRUD API
# Note: an auth is needed to update registered user

import requests # https://requests.readthedocs.io/en/master/user/install/

poll_id = 'a5x4m4u83hhxkxd5' # ID of the poll

api_url = 'https://doodle.com/api/v2.0/polls/{}'.format(poll_id)

input('Get Data ...')
payload = {'adminKey':'', 'participantKey':''}
r = requests.get(api_url, params=payload)
assert(r.status_code == requests.codes.ok)
data = r.json()
print(data)

xhr_token = data['optionsHash']
participant_url = '{}/participants'.format(api_url)

input('Post participant ...')
payload = {
    'name': 'John Doe',
    'preferences': [1, 0], # choices
    'optionsHash': xhr_token, # required
    'participantKey': None,
}
r = requests.post(participant_url, json=payload)
assert(r.status_code == requests.codes.ok)
print(r.json())
# {'id': 511651895, 'name': 'John Doe', 'preferences': [1, 0]}
participant_id = r.json()['id']

update_url = '{}/{}'.format(participant_url, participant_id)

input('Update choice ...')
payload['id'] = participant_id
payload['preferences'] = [0, 1]
r = requests.put(update_url, json=payload)
assert(r.status_code == requests.codes.ok)
print(r.json())
# {'id': 587172925, 'name': 'John Doe', 'preferences': [0, 1]}

input('Delete participant ...')
r = requests.delete(update_url)
assert(r.status_code == requests.codes.ok)

# Change randomly the participant's choices
input('Spoil poll ...')
import random
participants = data['participants']
yes = 0
for participant in participants:
    # keys: id name preferences smallAvatarUrl largeAvatarUrl userId
    print(participant)
    if 'userId' in participant:
        continue # registered users cannot be updated
    # preferences = random.choice(([1, 0], [0, 1]))
    if random.random() < 0.5:
        preferences = [1, 0]
        yes += 1
    else:
        preferences = [0, 1]
    payload = {
        'id': participant['id'],
        'name': participant['name'],
        'preferences': preferences,
        'optionsHash': xhr_token, # required
        'participantKey': None,
    }
    print(payload)
    update_url = '{}/{}'.format(participant_url, participant['id'])
    #! Danger !# r = requests.put(update_url, json=payload)
    # assert(r.status_code == requests.codes.ok) # Fail for registered users
print('Number of yes {} / {} = {:.1f} %'.format(yes, len(participants), yes / len(participants) * 100))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
