---
title: python script create comment data (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'create comment data'

Functions in program: 
* `def create_comment(obj, user):`

Modules used in program: 
* `import random`

## python create comment data

Python example: create comment data

```python
import random

from django.contrib.auth.models import User

from scout.topics.models import Topic


def create_comment(obj, user):
    from django.contrib import comments
    from django.contrib.comments.signals import comment_was_posted
    from django.contrib.sites.models import Site
    from django.contrib.contenttypes.models import ContentType
    from django.contrib.webdesign.lorem_ipsum import sentence


    comment = comments.get_model().objects.create(
        comment=sentence(),
        user=user,
        site=Site.objects.get_current(),
        content_type=ContentType.objects.get_for_model(obj),
        object_pk=obj.id
    )

    # Fire the comment_was_posted signal
    comment_was_posted.send(
        sender=comment.__class__,
        comment=comment,
        request=None
    )

    #  Return the comment
    return comment

# Loop over each topic and create comments on it
users = User.objects.all()
user_cnt = users.count()
for topic in Topic.objects.all():
    print(topic.id)
    for i in range(0, random.randint(0,5)):
        user = users[random.randint(0, user_cnt-1)]
        create_comment(topic, user)
        

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
