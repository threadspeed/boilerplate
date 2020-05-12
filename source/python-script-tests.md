---
title: python script tests (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tests'


## python tests

Python mysql example: tests

```python
from unittest import TestCase

from main import BootcampSpot


class TestBootcampSpot(TestCase):
    def setUp(self) -> None:
        self.client = BootcampSpot()

    def test_login(self):
        self.client.login()
        self.assertEqual(type(self.client.auth_token), str)

    def test_get_assignments(self):
        self.assertEqual(type(self.client.get_assignments()), list)

    def test_generate_two_lists_of_ungraded_assignments(self):
        self.assertEqual(type(self.client.generate_two_lists_of_ungraded_assignments()), tuple)





```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
