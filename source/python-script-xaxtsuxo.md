---
title: python script xaxtsuxo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'xaxtsuxo'


## python xaxtsuxo

Python example: xaxtsuxo

```python
>>> import json
>>> import urllib
>>> import random
>>> url = urllib.urlopen('http://twitter.com/statuses/user_timeline/xaxtsuxo.json')
>>> data = url.read()
>>> tweets = json.loads(data)
>>> tweet = random.choice(tweets)
>>> print(tweet['text'])
「俺はいまだにOperaの社長が「アメリカまで泳ぐ」と宣言したのに泳がなかったことを
許してはいない。」ぁっぉ

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
