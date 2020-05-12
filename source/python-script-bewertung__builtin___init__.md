---
title: python script bewertung  builtin   init   (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bewertung  builtin   init  '


Modules used in program: 
* `import otree.test`
* `import otree.views`

## python bewertung  builtin   init  

Python example: bewertung  builtin   init  

```python
# This file is auto-generated. Don't change anything in this file.

import otree.views
import otree.test

from .. import models


class Page(otree.views.Page):
    z_models = models

    def z_autocomplete(self):
        self.subsession = models.Subsession()
        self.group = models.Group()
        self.player = models.Player()


class WaitPage(otree.views.WaitPage):

    z_models = models

    def z_autocomplete(self):
        self.subsession = models.Subsession()
        self.group = models.Group()


class Bot(otree.test.Bot):

    def z_autocomplete(self):
        self.subsession = models.Subsession()
        self.group = models.Group()
        self.player = models.Player()




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
