---
title: python script snake (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'snake'


Modules used in program: 
* `import random_ai as AI_2`
* `import random_ai as AI_1`
* `import threading`
* `import random`
* `import curses`
* `import time`

## python snake

Python example: snake

```python
import time
import curses
import random
import threading

import random_ai as AI_1
## import manual_ai as AI_2
import random_ai as AI_2

myscreen = curses.initscr()

class SnakeMap(object):
	# a 22*22 map, border is -1
	#   0 and 21 are border, 1--20 are avaiable
	SIZE = 22
	_map = []
	_snakemap = None

	def __init__(self, *args, **kwargs):
		_b = map(lambda x: -1, range(0, SnakeMap.SIZE))
		_c = map(lambda x: (x == 0 or x == SnakeMap.SIZE-1) and -1 or 0, range(0, SnakeMap.SIZE))
		self._map = map(lambda x: (x == 0 or x == SnakeMap.SIZE-1) and _b[:] or _c[:], range(0, SnakeMap.SIZE))

	@classmethod
	def get_instance(cls):
		if not cls._snakemap:
			cls._snakemap = cls()
		return cls._snakemap

	def row(self, y):
		return (y >= 0 and y < SnakeMap.SIZE) and self._map(y) or None

	def column(self, x):
		if x < 0 or x > SnakeMap.SIZE-1:
			return None
		return map(lambda c: c[x], self._map)

	def set_value(self, x, y, value):
		if x <= 0 or x >= SnakeMap.SIZE-1: return False
		if y <= 0 or y >= SnakeMap.SIZE-1: return False
		self._map[y][x] = value
		return True

	def get_value(self, x, y):
		if x < 0 or x > SnakeMap.SIZE-1: return None
		if y < 0 or y > SnakeMap.SIZE-1: return None
		return self._map[y][x]

	def get_map(self):
		return self._map

	def draw(self, line_offset=0):
		for y in range(0, SnakeMap.SIZE):
			_d = ""
			for c in self._map[y]:
				if c == -1:
					_d += "##" 
				elif c < 0:
					_d += "s%d" % -(c+1)
				elif c == 0:
					_d += "  "
				else:
					_d += ("%2d" % c)
			myscreen.addstr(y+line_offset, 0, _d)

class Snake(object):
	snake_name = "unknown"
	# -2, -3 ...
	snake_type = ""
	# a list of (x, y), 0 is the head
	snake = []
	# 1 - up, 2 - right, 3 - down, 4 - left
	direiction = 1
	next_direction = 1
	# length
	snakelen = 1

	_snakemap = None
	_forward_dict = {
		0: ( 0,  0),
		1: ( 0, -1),
		2: ( 1,  0),
		3: ( 0,  1),
		4: ( -1, 0),
	}
	_dead = False
	_ai = None

	def __init__(self, *args, **kwargs):
		self.snake_type = kwargs.get('type', "-2")
		self.snake = [(kwargs.get('x', 3), kwargs.get('y', 3)),]
		self.direction = kwargs.get('direction', 1)
		self._ai = kwargs.get('ai')()
		self.snake_name = kwargs.get('ai_name', 'unknown')
		self._ai.myscreen = myscreen
		self._snakemap = SnakeMap.get_instance()
		self.set_snake(0)
		self.snakelen = 3

	def set_snake(self, offset):
		if offset<0 or offset>=len(self.snake):
			return False
		(x, y) = self.snake[offset]
		self._snakemap.set_value(x, y, self.snake_type)
		return True

	def get_snake(self):
		return self.snake

	def clear_tail(self):
		(x, y) = self.snake[-1]
		self._snakemap.set_value(x, y, 0)
		self.snake = self.snake[:-1]
		return True

	def is_alive(self):
		if self._dead: 
			return False
		else:
			return True

	def check_dead(self, x = 0, y = 0):
		if not x and not y:
			(x, y) = self.snake[0]
		if self._snakemap.get_value(x, y) < 0:
			self._dead = True
			return True
		return False

	def get_forward_place(self, direction=None):
		if direction and (self.snakelen == 1 or direction + self.direction not in [4, 6]):
			# snake can not go back
			d = direction
		else:
			d = self.direction
		(ox, oy) = self._forward_dict[d]
		(x, y) = self.snake[0]
		# hack code
		if direction == 0: 	return (x, y, d)

		return (x+ox, y+oy, d)

	def forward(self, direction=None):
		(hx, hy, d) = self.get_forward_place(direction)

		if self.snakelen == len(self.snake):
			# remove the tail
			self.clear_tail()
		self.snake = [(hx, hy)] + self.snake
		self.set_snake(0)
		self.direction = d
		return True

	def increase(self, n):
		self.snakelen += n

	def set_next_direction(self, direction):
		if direction in [1, 2, 3, 4]:
			self.next_direction = direction
		else:
			self.next_direction = self.direction

class Egg(object):
	value = 0
	x = 0
	y = 0

	_snakemap = None
	def __init__(self, *args, **kwargs):
		self._snakemap = SnakeMap.get_instance()

	def new_egg(self):
		self.value += 1
		while True:
			x = random.randint(1, 20)
			y = random.randint(1, 20)
			if self._snakemap.get_value(x, y) == 0:
				self._snakemap.set_value(x, y, self.value)
				self.x = x
				self.y = y
				break

	def get_egg(self):
		return (self.x, self.y, self.value)

	def clear_egg(self):
		self._snakemap.set_value(self.x, self.y, 0)

class OneGame(object):
	MAX_STEP = 2000
	
	_snakemap = None
	egg = None

	steps = 0
	winner = 0

	_exit = False

	snakes = []
	snake_heads = ["[]", "()"]

	def __init__(self, *args, **kwargs):
		self._snakemap = SnakeMap.get_instance()
		s1 = Snake(type=-2, 
				x = 3, y = 3, direction = 3, 
				ai = AI_1.AI,
				ai_name = AI_1.AI_NAME)
		s2 = Snake(type=-3, 
				x = 18, y = 18, direction = 1, 
				ai = AI_2.AI,
				ai_name = AI_2.AI_NAME)

		self.snakes = [s1, s2]
		self.egg = Egg()
		self.egg.new_egg()

	def draw(self):
		y = 0
		for s in self.snakes:
			myscreen.addstr(y, 0, "Snake %d: %s len=%d, is_alive=%s" % (y+1, s.snake_name, s.snakelen, s.is_alive()))
			y += 1
		myscreen.addstr(y, 0, "Step: %d,  Winner: Snake %d" % (self.steps, self.winner))
		y += 1
		self._snakemap.draw(y)

		# beauty the snake
		for i in range(0, len(self.snakes)):
			s = self.snakes[i]
			(hx, hy) = s.get_snake()[0]
			myscreen.addstr(hy+y, hx*2, self.snake_heads[i])

		myscreen.addstr(y+22, 0, "")
		myscreen.refresh()

	def check_gameover(self):
		ai_alive = [s.is_alive() for s in self.snakes]
		if sum(ai_alive) <= 1:
			for i in range(0, len(ai_alive)):
				if ai_alive[i]:
					self.winner = i
			return True
		return False

	def run(self):
		while not self._exit and self.steps < self.MAX_STEP and self.egg.value<=20:
			# get the direction for the first snake
			snake_list = [
				{
					'snake': s.get_snake(),
					'direction': s.direction,
					'len': s.snakelen,
				} for s in self.snakes]

			threads = []
			for i in range(0, len(self.snakes)):
				s = self.snakes[i]
				t = threading.Thread(target=s._ai.one_step,
					args=(s,
						self._snakemap.get_map(),
						snake_list,
						i,
						self.egg.get_egg()
					))
				t.setDaemon(True)
				threads.append(t)

			# start all thread
			for t in threads: 
				t.start()
				# wait all thread for 0.5 seconds
				t.join(0.5)
			
			for i in range(0, len(threads)):
				t = threads[i]
				if t.isAlive():
					self.snakes[i]._dead = True

			if self.check_gameover():
				break

			# run snakes steps
			self.snake_step()
			self.steps += 1
			self.draw()

			if self.check_gameover():
				break
			time.sleep(0.1)

	def snake_step(self):
		(ex, ey, ev) = self.egg.get_egg()

		for i in range(0, len(self.snakes)):
			s = self.snakes[i]
			(x, y, d) = s.get_forward_place(s.next_direction)
			dead = s.check_dead(x, y) and 1 or 0
			# check eated egg
			if (x, y) == (ex, ey):
				s.increase(ev)
				self.egg.new_egg()
	
		if self.check_gameover():
			return

		# forward all snake at the same time
		for i in range(0, len(self.snakes)):
			s = self.snakes[i]
			s.forward(s.next_direction)

		all_heads = [s.get_snake()[0] for s in self.snakes]
		# check if they head-vs-head
		for i in range(0, len(self.snakes)):
			s = self.snakes[i]
			for j in range(0, len(all_heads)):
				if j == i:
					continue
				if s.get_snake()[0] == all_heads[j]:
					self.snakes[i]._dead = True
		return

try: 
	game = OneGame()
	game.draw()
	game.run()
finally:
	curses.endwin()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
