---
title: python script diceRoll (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'diceRoll'


Modules used in program: 
* `import unittest`
* `import random`

## python diceRoll

Python example: diceRoll

```python
import random
import unittest
from unittest.mock import patch


class Die():
    def __init__(self, sides=6):
        self._sides = sides

    def roll(self):
        return random.randint(1, self._sides)


class TestDice(unittest.TestCase):
    def _make_one(self, *args, **kw):
        return Die(*args, **kw)

    @patch('random.randint', return_value=3)
    def test_standard_size(self, randint):
        die = self._make_one()
        result = die.roll()
        randint.assert_called_with(1, 6)
        self.assertEqual(result, 3)

    @patch('random.randint', return_value=3)
    def test_custom_size(self, randint):
        die = self._make_one(sides=42)
        result = die.roll()
        randint.assert_called_with(1, 42)
        self.assertEqual(result, 3)


if __name__ == '__main__':
    unittest.main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
