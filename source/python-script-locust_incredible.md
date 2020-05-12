---
title: python script locust incredible (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'locust incredible'


Modules used in program: 
* `import random, string`

## python locust incredible

Python mysql example: locust incredible

```python
from locust import HttpLocust, TaskSet, between, task
import random, string


class IncredibleRequest(TaskSet):
    @task()
    def incredible(self):
        random_string = "".join(random.choices(string.ascii_lowercase[:5], k=2))
        self.client.get("/api/incredible/?model_input="+random_string)


class WebsiteUser(HttpLocust):
    task_set = IncredibleRequest
    wait_time = between(0.0, 2.0)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
