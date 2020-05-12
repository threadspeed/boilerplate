---
title: python script tweet pic loop (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tweet pic loop'

Functions in program: 
* `def tweet(message):`

Modules used in program: 
* `import random`
* `import tweepy`
* `import time`

## python tweet pic loop

Python example: tweet pic loop

```python
import time
import tweepy
import random
from config import *

script_dir = os.path.dirname(__file__)
picture_path = os.path.join(script_dir, picture)

auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_key, access_secret)
api = tweepy.API(auth)

def tweet(message):
    try:
        api.update_with_media(picture_path, message)
    except tweepy.TweepError as e:
        print(e)
        time.sleep(5)

while True:
    try:
        print('Tweeting:', message)
        tweet(message)
        print('Sleeping for {} seconds'.format(timer))
        time.sleep(timer)
    except KeyboardInterrupt:
        print('\nExiting\n')
        break


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
