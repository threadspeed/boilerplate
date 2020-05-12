---
title: python script bewertung tests (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bewertung tests'


Modules used in program: 
* `import random`

## python bewertung tests

Python example: bewertung tests

```python
# -*- coding: utf-8 -*-
from __future__ import division

import random

from otree.common import Currency as c, currency_range

from . import views
from ._builtin import Bot
from .models import Constants


class PlayerBot(Bot):
    """Bot that plays one round"""

    def play_round(self):
        self.submit(views.MyPage)
        self.submit(views.Results)

    def validate_play(self):
        pass


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
