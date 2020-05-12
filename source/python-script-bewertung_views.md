---
title: python script bewertung views (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bewertung views'


## python bewertung views

Python example: bewertung views

```python
# -*- coding: utf-8 -*-
from __future__ import division

from otree.common import Currency as c, currency_range, safe_json

from . import models
from ._builtin import Page, WaitPage
from .models import Constants


class MyPage(Page):
    pass

class ResultsWaitPage(WaitPage):

    def after_all_players_arrive(self):
        pass

class Results(Page):
    pass


page_sequence = [
    MyPage,
    ResultsWaitPage,
    Results
]


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
