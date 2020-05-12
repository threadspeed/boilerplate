---
title: python script random.tweet%2520test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random.tweet%2520test'


Modules used in program: 
* `import random`
* `import tweepy`

## python random.tweet%2520test

Python mysql example: random.tweet%2520test

```python
import tweepy
import random

CONSUMER_KEY="xxxxxxx"
CONSUMER_SECRET="xxxxxxx"
auth = tweepy.OAuthHandler(CONSUMER_KEY, CONSUMER_SECRET)
ACCESS_TOKEN='xxxxxxxx'
ACCESS_SECRET='xxxxxxxx'
auth.set_access_token(ACCESS_TOKEN,ACCESS_SECRET)

api=tweepy.API(auth)

STATUS_DATA=["a","b","c","d","e"]
api.update_status(random.choice(STATUS_DATA))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
