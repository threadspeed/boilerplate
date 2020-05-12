---
title: python script hy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hy'

Functions in program: 
* `def echo(bot, trigger):`

Modules used in program: 
* `import os`

## python hy

Python example: hy

```python
from willie import module
import os
from subprocess import Popen, PIPE

@module.commands('hy')
def echo(bot, trigger):
    bot.reply(Popen(["hy", "-c", trigger.group(2)], stdout=PIPE).communicate()[0])
    #         Popen(["python", "-c", "print('echo'"], stdout=PIPE).communicate()[0])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
