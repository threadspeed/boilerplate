---
title: python script concealshot (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'concealshot'


Modules used in program: 
* `import random`

## python concealshot

Python example: concealshot

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
	# Apply Random Dot So this can't be done AFK
	if random.randrange(1,99) == 99:
		combat.AddDot(target, random.randrange(25,50))

	combat.RandomPoolDamage(random.randrange(35, 255))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
