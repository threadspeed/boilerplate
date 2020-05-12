---
title: python script utils.unique slug generator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'utils.unique slug generator'

Functions in program: 
* `def unique_slug_generator(obj, new_slug = None):`
* `def random_string_generator(size = 10, chars = string.ascii_lowercase + string.digits + string.ascii_uppercase):`

Modules used in program: 
* `import string`
* `import random`

## python utils.unique slug generator

Python example: utils.unique slug generator

```python
############ random string generator ##################
import random
import string

def random_string_generator(size = 10, chars = string.ascii_lowercase + string.digits + string.ascii_uppercase):
    print(f"size is {size} and chars are: {chars}")
    generated_string = ''.join( random.choice(chars) for _ in range(size))
    return generated_string

# if __name__ == "__main__":
print(random_string_generator(size=12))



############ unique slug generator ##################
from django.utils.text import slugify
from .random_string_generator import random_string_generator

def unique_slug_generator(obj, new_slug = None):
    if new_slug is not None:
        slug = new_slug
    else:
        slug = slugify(obj.title)

    # if there already exists an object with that same slug, it would create a new slug as below
    Klass = obj.__class__
    qs = Klass.objects.filter(slug = slug)
    print(qs)
    qs_exists = qs.exists()
    if qs_exists:
        new_slug = "{slug}-{randstr}".format(
            slug = slug, 
            randstr = random_string_generator(size=6)
        )
        return unique_slug_generator(obj, new_slug=new_slug)

    return slug

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
