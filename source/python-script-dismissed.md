---
title: python script dismissed (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dismissed'

Functions in program: 
* `def comment(bot, trigger):`

Modules used in program: 
* `import time`
* `import random`
* `import willie`

## python dismissed

Python example: dismissed

```python
import willie
from willie import module
import random
import time


@module.rule('jerkins you are dismissed')
@module.rule('jerkins, you are dismissed')
@module.rule('jerkins go')
@module.rule('jerkins, go')
@module.rule('jerkins give us the room')
@module.rule('jerkins, give us the room')
@module.rule('jerkins leave')
@module.rule('jerkins, leave')
@module.rule('jerkins, just go')
@module.rule('jerkins just go')
def comment(bot, trigger):
    bot.reply('Very well sir, I shall retreat back below stairs')
    bot.part('#lobby')
    time.sleep(120)
    bot.join('#lobby')
    bot.say('I have returned Sir, should anyone have need of me')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
