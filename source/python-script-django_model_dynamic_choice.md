---
title: python script django model dynamic choice (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'django model dynamic choice'


## python django model dynamic choice

Python example: django model dynamic choice

```python
class DynamicChoice(object):
    """
    Trivial example of creating a dynamic choice
    """
    
    def __iter__(self):
        for choice in self.generate():
            if hasattr(choice,'__iter__'):
                yield (choice[0], choice[1])
            else:
                yield choice, choice
            
    def __init__(self):
        """
        If you do it here it is only initialized once. Then just return generated.
        """
        import random
        self.generated = [random.randint(1,100) for i in range(10)]            
            
    def generate(self):
        """
        If you do it here it is  initialized every time the iterator is used.
        """
        import random
        return [random.randint(1,100) for i in range(10)] 

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
