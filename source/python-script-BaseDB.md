---
title: python script BaseDB (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'BaseDB'


## python BaseDB

Python mysql example: BaseDB

```python
class BaseDB:
  def __init__(self, path, name):
    self._path = path
    self._dbname = name

  @property
  def name(self):
    """
    prefix = ""
    if "pitts" in self._path:
      prefix = "pitts"
    if "t27" in self._path:
      prefix = "t27"
    if "ttm" in self._path:
      prefix = "ttm"
    """
    prefix = self._path[:-4]
    prefix = prefix.split("/")[-1]

    return prefix + "_" + self._dbname

  #length = property(get_length)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
