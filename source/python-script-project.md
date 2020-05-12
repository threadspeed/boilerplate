---
title: python script project (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'project'

Functions in program: 
* `def play_turn(action_json=None):`

Modules used in program: 
* `import requests`
* `import json`
* `import random`

## python project

Python example: project

```python
# shift-f10 to run tests
# ctrl-TAB to switch screen

# f2 to jump to error
# alt-enter to provide auto solution
# ctl-alt-"v" to pull out a variable
# shift-f6 to rename
# ctl-alt-"l" to clean up code
import random
from pprint(import pprint)
import json
import requests

from game_script import Direction, get_move_command, move_random

ACCOUNT = {
    'name': 'Chinese Dragon',
    'uri': '/api/account/d8808608-64d0-4f30-aaed-6b51324410e9',
    'uuid': 'd8808608-64d0-4f30-aaed-6b51324410e9'
}

ADDRESS = 'http://54.85.100.225:8000'
TEAM_NAME = 'Chinese Dragon'


def play_turn(action_json=None):
    if action_json is None:
        action_json = {}
    game_address = ADDRESS + '/api/game'
    id_info_json = {
        'account_uuid': 'd8808608-64d0-4f30-aaed-6b51324410e9'
    }
    action_json.update(id_info_json)
    response = requests.post(game_address, json=action_json)
    return response

go_north = get_move_command(Direction.NORTH)
go_random = move_random(random)
game_response = play_turn(go_random)
print(game_response.json())
pprint(game_response.json())


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
