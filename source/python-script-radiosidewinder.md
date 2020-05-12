---
title: python script radiosidewinder (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'radiosidewinder'

Functions in program: 
* `def radiosidewinder(bot, trigger):`

## python radiosidewinder

Python mysql example: radiosidewinder

```python
from willie import module
from streamscrobbler import streamscrobbler

@module.commands('radiosidewinder')
def radiosidewinder(bot, trigger):
    SS = streamscrobbler()
    bot.reply("Currently playing: %s. Listen in here: %s" % (
        SS.getServerInfo('http://listen.radionomy.com/radio-sidewinder').get("metadata").get('song'),
        'http://www.radiosidewinder.com/listen-now/'
    ))
        


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
