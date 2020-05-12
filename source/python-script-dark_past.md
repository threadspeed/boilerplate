---
title: python script dark past (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dark past'

Functions in program: 
* `def comment(bot, trigger):`
* `def _word_picker(filename):`

Modules used in program: 
* `import random`
* `import willie`
* `import os`

## python dark past

Python example: dark past

```python
import os
import willie
from willie import module
import random

'''
An insult generator that works off the pricipal of
<adverb><adjective><expletive><concrete noun> = hilarity
You warmly forceful cunt-ghost!

This is not supposed to include aggressively homophobic or racial slurs,
however, the lists of words were copied en mass, so some inoffensive words
may be left with more offence than intended when in the sentence below.
For example, "pinto" has just been removed from the nouns because of its
racial slur connotations
'''


def _word_picker(filename):
    filepath = os.path.join(os.path.dirname(__file__), 'word_lists', filename)
    with open(filepath) as words_file:
        words = words_file.read().splitlines()
        return random.choice(words)


@module.rule('.*does jerkins.*')
@module.rule('.*can jerkins.*')
@module.rule('.*jerkins has a dark past.*')
def comment(bot, trigger):

    verb = _word_picker('verbs.txt')
    subject = _word_picker('consequences.txt')

    bot.say('I %s %s!' % (verb, subject))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
