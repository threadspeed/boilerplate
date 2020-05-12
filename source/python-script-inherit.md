---
title: python script inherit (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'inherit'


## python inherit

Python mysql example: inherit

```python
# -*- coding: utf-8 -*-


# 对象
class User:
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


# 继承
class SubUser(User):
    wechat = ""

    def __init__(self, id, name, birthday, phone, wechat):
        User.__init__(self, id, name, birthday, phone)
        self.wechat = wechat

    # 方法重写
    def information(self):
        print("name: %s, birthday: %s, wechat: %s" % (self.name, self.birthday, self.wechat))


if __name__ == '__main__':
    user = User(1, "honker", "2020-04-05", "17310011002")
    user.information()
    sub_user = SubUser(2, "honker", "2020-04-05", "17310011002", "17310011002")
    sub_user.information()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
