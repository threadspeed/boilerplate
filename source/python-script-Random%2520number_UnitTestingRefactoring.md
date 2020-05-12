---
title: python script Random%2520number UnitTestingRefactoring (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Random%2520number UnitTestingRefactoring'


Modules used in program: 
* `import unittest`

## python Random%2520number UnitTestingRefactoring

Python example: Random%2520number UnitTestingRefactoring

```python
#_*_Coding:utf-8_*_
import unittest
from RefactoringUnitTesting import compare

class TestRandom(unittest.TestCase):
    def test_guess1(self):         #testing less
        s=compare()
        self.assertEqual(s,1)
    def test_guess2(self):         #testing greater
        s = compare()
        self.assertEqual(s, 2)
    def test_guess3(self):          #testing same
        s = compare()
        self.assertEqual(s, 3)
    def test_guess4(self):          # testing quit
        s = compare()
        self.assertEqual(s, 4)
    def test_guess5(self):          # testing signal
        s = compare()
        self.assertEqual(s, 0)


if __name__ == '__main__':
    unittest.main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
