---
title: python script eight puzzle v0.6 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'eight puzzle v0.6'

Functions in program: 
* `def index2loc(index):`
* `def shuffle():`
* `def show_leaderboard(sender):`
* `def button_pressed(sender):`
* `def move_piece(button, x, y):`
* `def isAdjacent(row1, col1, row2, col2):`
* `def update_score(player_name, score):`
* `def get_sorted_players():`
* `def add_player(player_name):`

Modules used in program: 
* `import urllib`
* `import random`
* `import json`
* `import requests`
* `import random, time`
* `import speech`
* `import ui`

## python eight puzzle v0.6

Python example: eight puzzle v0.6

```python
import ui
import speech
import random, time
import requests
import json
import random
import urllib

END_POINT = 'http://192.168.1.8:5000/puzzlescores'

def add_player(player_name):
    headers = {'Content-Type': 'application/json'}
    data = json.dumps({"name": player_name})
    response = requests.post(END_POINT, data, headers=headers)
    return response.json()


def get_sorted_players():
    headers = {'Content-Type': 'application/json'}
    url = END_POINT + '?' + urllib.quote('where={"moves": {"$gt": 1}}&sort=moves,name', safe = '/=&')
    r = requests.get(url, headers=headers)
    response = r.json()
    results = []
    for item in response['_items']:
        results.append({k:v for k,v in item.iteritems() if k in ['_updated', 'name', 'moves']})
    return results


# only update score if the new score is better
def update_score(player_name, score):
    headers = {'Content-Type': 'application/json'}
    url = END_POINT + '?where=name=="' + urllib.quote(player_name) + '"'
    r = requests.get(url, headers=headers)
    response = r.json()
    if len(response.get('_items', [])) == 1:
        player_dict = response['_items'][0]
        if 'moves' not in player_dict or player_dict['moves'] > score:
            headers['If-Match'] = player_dict['_etag']
            data = json.dumps({'moves': score})
            r2 = requests.patch(END_POINT + '/' + player_dict['_id'], data, headers=headers)
            return r2.json()
        else:
            return {'_status': 'OK2',
                    'reason': 'score not updated because it is not better'}
    else:
        return {'_status': 'ERR',
                'reason': 'player ' + player_name + ' not found'}
        





border_color = (1.00, 0.50, 0.00)
moves = 0
buttons_by_number = {}

def isAdjacent(row1, col1, row2, col2):
  if abs(row1-row2) + abs(col1-col2) == 1:
    return True 
  else:
    return False 


def move_piece(button, x, y):
  def animation():
    button.x = x
    button.y = y
  ui.animate(animation, duration=0.2)


def button_pressed(sender):
  global moves
  number = sender.title
  index = pieces.index(number)
  (row, col) = index2loc(index)
  empty_space_index = pieces.index('')
  (empty_space_row, empty_space_col) = index2loc(empty_space_index)
  if isAdjacent(row, col, empty_space_row, empty_space_col):
    move_piece(sender, empty_space_col*sender.width, empty_space_row*sender.width)
    moves += 1
    steps_label.text = 'Steps: ' + str(moves)
    pieces[index] = ''
    pieces[empty_space_index] = number
    if pieces == win_state:
      speech.say('you win', 'en-US', 0.3)
      update_score('Yuhang', moves)

def show_leaderboard(sender):
  print(get_sorted_players())

def shuffle():
  #find what pieces can move
  movable_pieces = []
  empty_space_index = pieces.index('')
  (empty_space_row, empty_space_col) = index2loc(empty_space_index)

  for number in pieces:
    index = pieces.index(number)
    (row, col) = index2loc(index)
    if isAdjacent(row, col, empty_space_row, empty_space_col):
      movable_pieces.append(number)
      
  random.shuffle(movable_pieces)
  to_move = movable_pieces[0]
  
  to_move_button = buttons_by_number[to_move]
  move_piece(to_move_button, empty_space_col*to_move_button.width, empty_space_row*to_move_button.width)
  pieces[pieces.index(to_move)] = ''
  pieces[empty_space_index] = to_move
  
pieces = ['1', '2', '3', '4', '5', '6', '7', '8', '']
win_state = ['1', '2', '3', '4', '5', '6', '7', '8', '']

v = ui.View(background_color=(0.40, 0.80, 1.00))
board = ui.View()
v.add_subview(board)
v.present('full_screen', hide_title_bar=False , orientations=['landscape'])
steps_label = ui.Label()
steps_label.frame = (30, 30, 250, 70)
#steps_label.background_color = (1.00, 0.00, 0.50)
steps_label.font =  ('Futura-CondensedExtraBold', 40)
steps_label.text = ' Steps: 0'
v.add_subview(steps_label)
board.frame = (v.width-v.height, 0, v.height, v.height)
board.border_width = 3
board.border_color = border_color
board.background_color = (1,1,1)


# convert index of button to row number and column number
def index2loc(index):
  row = index / 3
  column = index % 3
  return (row, column)


for i in range(9):
  button_text = pieces[i]
  if button_text != '':
    button = ui.Button(title=button_text)
    button.background_color = (1,1,1)
    button.font = ('Futura-CondensedExtraBold', 200)
    button.width = v.height/3
    button.height = button.width
    button.border_color = border_color
    button.border_width = 2
    (r, c) = index2loc(i)
    button.x = button.width*c
    button.y = button.height*r
    button.action = button_pressed
    board.add_subview(button)
    buttons_by_number[button_text] = button
  
leader_button = ui.Button(title='Leaderboard')
leader_button.background_color = (1,1,1)
leader_button.frame = (30, 200, 250, 70)
leader_button.corner_radius = 5
leader_button.font = ('Futura-CondensedExtraBold', 40)
leader_button.border_color = (0,0,0)
leader_button.border_width = 1
leader_button.action = show_leaderboard
v.add_subview(leader_button)

for i in range(50):
  shuffle()
  time.sleep(0.2)
speech.say('shuffling is done')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
