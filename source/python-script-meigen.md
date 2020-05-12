---
title: python script meigen (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'meigen'


## python meigen

Python example: meigen

```python
>>> import json
>>> import urllib
>>> import random
>>> def meigen(name):
...     url = urllib.urlopen('http://twitter.com/statuses/user_timeline/%s.json' % name)
...     return random.choice(json.loads(url.read()))['text']
...
>>> print(meigen('atsuoishimoto'))
「妻に支えられてるふりをする技術」

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
