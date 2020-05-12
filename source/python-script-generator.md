---
title: python script generator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'generator'

Functions in program: 
* `def random_doc():`
* `def template_doc():`
* `def random_date():`
* `def random_stage():`
* `def several_random_words():`
* `def random_word():`
* `def random_name():`

Modules used in program: 
* `import uuid`
* `import pytz`
* `import random`
* `import json`

## python generator

Python mysql example: generator

```python
import json
import random
import pytz
import uuid

from datetime import datetime, timedelta

from random_words import RandomNicknames, RandomWords

from elasticsearch import Elasticsearch
es = Elasticsearch(hosts=['localhost'])
rn = RandomNicknames()
rw = RandomWords()


def random_name():
    return rn.random_nick() + ' ' + rn.random_nick()


def random_word():
    return rw.random_word()


def several_random_words():
    words = []
    for x in xrange(1, 5):
        words.append(random_word())
    return ' '.join(words)


def random_stage():
    return "{} {}".format(random.randint(1, 5),
                          several_random_words())


def random_date():
    now = datetime.utcnow().replace(tzinfo=pytz.UTC)
    date = now + timedelta(days=random.randint(-365, 365))
    return date.isoformat()



directions = ['inbound', 'outbound', 'screenshare', 'internal']


# index = "48a75041-75a4-43a8-a1ba-0ffa4ccbf420_v1"
account_id = '88a9769b-189f-487a-86c0-146da38562d1'
index = account_id + '_v1'
user_id = "062f38e9-1595-4d09-8b76-727144ee4baa"
team_id = "362e79b9-8cb6-4bd4-88cc-da828e9a9099"
department_id = "b1ff5bfe-16bb-477d-92e8-0c7dde72322f"
date = "2017-11-08T21:01:00+00:00"

def template_doc():
    return {
        'direction': 'screenshare',
        'user_id': user_id,
        "account_id": account_id,
        "title": "Sales Operations Manager",
        "company": "Honest Buildings",
        "caller": "Steve Richard",
        "contact": "Alex Brielmann",
        "call_stage": "1 - Qualification (Is there something to solve?)",
        "date": date,
        "team_id": team_id,
        "coach_me": False,
        "filter_words": [],
        "is_visible_to_others": True,
        "transcription_words": [],
        "id": None,
        "crm_link": "https://na33.salesforce.com/0063900000qT2Kv",
        "department_id": department_id,
        "outcome": "Unspecified",
        "transcription_text": "",
    }


def random_doc():
    copy_doc = template_doc()
    copy_doc['id'] = str(uuid.uuid4())
    copy_doc['date'] = random_date()
    copy_doc['direction'] = random.choice(directions)
    copy_doc['caller'] = random_name()
    copy_doc['contact'] = random_name()
    copy_doc['company'] = several_random_words()
    copy_doc['title'] = several_random_words()
    copy_doc['call_stage'] = random_stage()
    copy_doc['outcome'] = several_random_words()

    words = []
    maxrange = 1000 * 7  # This seems to work out to about 1MB, give or take.
    for x in xrange(1, random.randint(5, maxrange)):
        words.append(random_word())

    copy_doc['transcription_text'] = ' '.join(words)

    whole_counter = 1
    frac_counter = 0

    for word in words:
        start_frac = random.randint(0, 100)
        end_frac = random.randint(0, 100)
        start = '{}.{}'.format(whole_counter, str(start_frac).zfill(3))
        # Rolled over into next...whatever.
        if start_frac > end_frac:
            whole_counter += 1
        end = '{}.{}'.format(whole_counter, str(end_frac).zfill(3))
        copy_doc['transcription_words'].append({
            'start': start,
            'end': end,
            'word': word,
        })
        whole_counter += 1
        frac_counter += 1

    # Just put them all in. IDGAF.
    copy_doc['filter_words'] = copy_doc['transcription_words']
    return copy_doc


for x in xrange(1, 50):
    print(x)
    rdoc = random_doc()
    print(rdoc['id'])
    es.index(body=json.dumps(rdoc), doc_type='fileupload', index=index, timeout='120s')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
