---
title: python script tweetbot (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tweetbot'


Modules used in program: 
* `import tweepy`
* `import random`
* `import time`
* `import composer`
* `import os`

## python tweetbot

Python mysql example: tweetbot

```python
import os
import composer
import time
import random
import tweepy

# Set up Twitter login
CONSUMER_KEY = 'xxx'
CONSUMER_SECRET = 'xxx'
ACCESS_KEY = 'xxx'
ACCESS_SECRET = 'xxx'
auth = tweepy.OAuthHandler(CONSUMER_KEY, CONSUMER_SECRET)
auth.set_access_token(ACCESS_KEY, ACCESS_SECRET)
api = tweepy.API(auth)

# Uncomment these to preview the tweets instead of actually tweeting them
#for x in range(0,20):
#	tweet = composer.compose()
#	print(tweet + " (%u)" % len(tweet))
#exit() 

while 1:

	tweet = composer.compose()
	print("Composing tweet: " + tweet)
	api.update_status(tweet)
	base_time = 75*60
	random_add = (random.randint(0,60))*60
	next_time = base_time + random_add
	print("Doing another one in %u minutes" % (next_time / 60))
	time.sleep(next_time)
	pass

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
