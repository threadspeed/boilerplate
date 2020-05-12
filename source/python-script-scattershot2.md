---
title: python script scattershot2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'scattershot2'


Modules used in program: 
* `import random`

## python scattershot2

Python mysql example: scattershot2

```python
# All command scripts have a context that contains a reference to
# the object that initiated the command, the target of the command,
# a string containing any parameters, and finally a dictionary containing
# information about the command.
#
# anh.context.object
# anh.context.target
# anh.context.command_string
# anh.context.command_info

import random

object = context['object']
target = context['target']
command = context['command_string']

#conceal shot
object.Conceal()

if combat.Hit(target):
	combat.RandomPoolDamage(random.randrange(35, 255))
	combat.RandomPoolDamage(random.randrange(35, 255))
	combat.RandomPoolDamage(random.randrange(35, 255))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
