---
title: python script Jarvis jarvis (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Jarvis jarvis'

Functions in program: 
* `def approve():`
* `def code():`
* `def get_value():`

Modules used in program: 
* `import xlrd`
* `import json`
* `import random`
* `import os`
* `import requests`

## python Jarvis jarvis

Python example: Jarvis jarvis

```python
import requests
import os
import random
import json
import xlrd
from tools.random_tools import random_name, random_phone, random_QQ, random_WX, random_school, random_subject
from tools.redis_tools import redis_db
from tools.mysql_tools import mysql_db
from Computer.path import project_ptah


def get_value():
    """获取token"""
    with open(project_ptah() + '/md/jarvis.md', 'r')as f:
        return f.read()


def code():
    r = redis_db().get('liufeibiao@itcast.cn_cookie')
    return "liufeibiao=" + '95931'


url = 'http://jarvis.itcast.cn/api/v1/approve?'
cookie = {"oidc_id_token": get_value()}


def approve():
    data = {"page": 1, "pageSize": 10, "keyword": "", "queryType": "pending", "gid": 6, "startTime": 1556617080,
            "endTime": 1651311480}
    r = requests.get(url=url, params=data, cookies=cookie)
    print(r.json()["result"]["doc"]["approve_list"][0]["progress"])
    print(r.json()["result"]["doc"]["approve_list"][0]["result"])



approve()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
