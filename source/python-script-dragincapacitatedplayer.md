---
title: python script dragincapacitatedplayer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dragincapacitatedplayer'


## python dragincapacitatedplayer

Python example: dragincapacitatedplayer

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

object = context['object']
target = context['target']
command = context['command_string']

if object.HasConsent(target):
	target.position = object.position
elif object.InGroup(target):
	target.position = object.position
else:
	SendConsentRequestMessage()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
