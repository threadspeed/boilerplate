---
title: python script test game script (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test game script'

Functions in program: 
* `def test_move_random_with_default_random_generator():`
* `def test_move_random_uses_random_choice():`
* `def test_get_move_command_north():`

Modules used in program: 
* `import random`

## python test game script

Python mysql example: test game script

```python
# shift-f10 to run tests
# ctrl-TAB to switch windows

# f2 to jump to error
# alt-enter to provide auto solution
# ctl-alt-"v" to pull out a variable
# shift-f6 to rename
# ctl-alt-"l" to clean up code

# import roman_to_number from project
#
import random

from game_script import Direction, get_move_command, move_random


def test_get_move_command_north():
    test_parts = [
        (Direction.NORTH, 'north'),
        (Direction.SOUTH, 'south'),
        (Direction.EAST, 'east'),
        (Direction.WEST, 'west')
    ]
    for direction, expected_direction in test_parts:
        result = get_move_command(direction)
        expected = {'action': 'move', 'direction': expected_direction}
        assert result == expected


def test_move_random_uses_random_choice():
    class TestRandom(random.Random):
        def __init__(self, *args, **kwargs):
            super(TestRandom, self).__init__(*args, **kwargs)
            self.direction_index = 0

        def choice(self, direction_list):
            return direction_list[self.direction_index]
    test_random = TestRandom()

    for index, direction in enumerate((direction for direction in Direction)):
        test_random.direction_index = index
        result = move_random(test_random)
        expected = get_move_command(direction)
        assert result == expected


def test_move_random_with_default_random_generator():
    expected = [get_move_command(direction) for direction in Direction]
    for _ in range(10):
        result = move_random()
        assert result in expected




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
