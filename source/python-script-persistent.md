---
title: python script persistent (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'persistent'


Modules used in program: 
* `import os`
* `import json`

## python persistent

Python example: persistent

```python
import json
import os

class PersistentContent(object):
    def __init__(self, filename):
        if os.path.isfile(filename):  # only load if it already exists
            with open(filename, 'r') as fh:
                data = json.load(fh)
                for (k, v) in data.items():
                    self.__dict__[k] = v
        self.__dict__['_file'] = filename  # direct assignment to bypass save

    def _save(self):
        with open(self._file, 'w') as fh:
            json.dump(self.__dict__, fh)

    def __setattr__(self, key, value):
        self.__dict__[key] = value
        self._save()

    def __getattr__(self, key):
        return self.__dict__.get(key, None)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
