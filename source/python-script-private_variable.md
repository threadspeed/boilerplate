---
title: python script private variable (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'private variable'


## python private variable

Python mysql example: private variable

```python
# -*- coding: utf-8 -*-


# 对象
class user:
    id = 0
    name = ""
    birthday = ""
    # 私有变量
    __phone = ""

    def __init__(self, id, name, birthday, phone):
        self.id = id
        self.name = name
        self.birthday = birthday
        self.__phone = phone

    def information(self):
        print("name: %s, birthday: %s" % (self.name, self.birthday))


if __name__ == '__main__':
    user = user(1, "honker", "2020-04-05", "17310011002")
    user.information()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
