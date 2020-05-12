---
title: python script create momme topics (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'create momme topics'

Functions in program: 
* `def create_topic(user, category):`

Modules used in program: 
* `import random`

## python create momme topics

Python mysql example: create momme topics

```python
import random

from django.contrib.auth.models import User

from ella.core.models import Category


def create_topic(user, category):
    " Helper method to create and return a Topic object. "
    from django.contrib.webdesign.lorem_ipsum import words
    from django.template.defaultfilters import slugify

    from scout.topics.models import Topic

    title = words(3)
    return Topic.objects.create(
        user=user,
        category=category,
        title=title,
        slug=slugify(title)
    )



lifestage = Category.objects.get(tree_path='lifestage')
children = lifestage.get_children()
users = User.objects.all()
user_cnt = users.count()
for i in range(0, 40):
    lifestage_category = children[random.randint(0, len(children)-1)]
    ls_children = lifestage_category.get_children()
    category = ls_children[random.randint(0, len(ls_children)-1)]
    
    
    user = users[random.randint(0, user_cnt-1)]
    create_topic(user, category)
    


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
