---
title: python script locust dbapis (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'locust dbapis'


Modules used in program: 
* `import random, string`

## python locust dbapis

Python example: locust dbapis

```python
from locust import HttpLocust, TaskSet, between, task
import random, string


class ApiRequests(TaskSet):
    @task()
    def university(self):
        self.client.get("/api/university/")

    @task()
    def company(self):
        self.client.get("/api/company/")


class WebsiteUser(HttpLocust):
    task_set = ApiRequests
    wait_time = between(0.0, 2.0)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
