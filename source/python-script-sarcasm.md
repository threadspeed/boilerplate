---
title: python script sarcasm (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sarcasm'

Functions in program: 
* `def comment_korean(bot, trigger):`
* `def comment_spanish(bot, trigger):`
* `def comment(bot, trigger):`

Modules used in program: 
* `import random`
* `import willie`

## python sarcasm

Python mysql example: sarcasm

```python
# -*- coding: utf-8 -*-
import willie
from willie import module
import random


@module.rule('eelface')
@module.rule('\s*lol\s*')
@module.rule('\s*haha\s*')
@module.rule('\s*hehe\s*')
@module.rule('\s*he he\s*')
@module.rule('\s*ha ha\s*')
@module.rule('\s*rofl\s*')
def comment(bot, trigger):
    responses = ['Very droll, Sir',
                 'Yes Sir, most amusing',
                 'Mm, Sir does enjoy his jokes',
                 'You are a veritable hoot, Sir',
                 'You are quite the card, Sir',
                 'Will that be all, Sir?',
                 'I feel honoured to be in the presence of such wit, Sir',
                 'Good one, Sir',
                 'I shall be telling that one to all my friends, Sir',
                 'A punchline for the ages, Sir',
                 'Another classic, Sir',
                 'Your razor wit has cut to the heart of the matter once again, Sir']
    bot.say(random.choice(responses))

@module.rule('\s*jeje\s*')
@module.rule('\s*je je\s*')
@module.rule('\s*jaja\s*')
@module.rule('\s*ja ja\s*')
def comment_spanish(bot, trigger):
    responses = ['Muy gracioso, Sir',
                 'Sí Señor, más divertida',
                 'Mm, Sir hace disfrutar de sus chistes',
                 '¿Eso es todo, Señor?',
                 'Me siento honrado de estar en presencia de tal ingenio, Sir',
                 'Muy buena, Sir',
                 'Debo estar diciendo que uno a todos mis amigos, Sir',
                 'Un remate de las edades, Sir',
                 'Otro clásico, Sir',
                 'Su ingenio de afeitar ha cortado al meollo de la cuestión, una vez más, Sir']
    bot.say(random.choice(responses))

@module.rule('\s*keke\s*')
@module.rule('\s*ke ke\s*')
def comment_korean(bot, trigger):
    bot.say(u'또한 한국어 이야기, ' + trigger.nick)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
