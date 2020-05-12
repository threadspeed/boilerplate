---
title: python script tic tac toe (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tic tac toe'

Functions in program: 
* `def check_win(state):`
* `def check_tie(state):`
* `def make_move(state, action, player):`
* `def self_play(player1, player2, print_game, should_learn):`
* `def to_tuple(a):`
* `def main():`

Modules used in program: 
* `import random`
* `import numpy as np`

## python tic tac toe

Python example: tic tac toe

```python
import numpy as np
import random
from q_learning import QLearner

#This program trains two q_learners to play tic tac toe.
#They play each other over and over and then play againt a random player to test how well they learned

class RandomPlayer(object):
	def evaluate(self, state, final, reward, should_learn):
		#random doesn't care about your reward
		#random player only makes valid moves
		valid_moves = []
		for i in xrange(9):
			j = int(i / 3)
			k = i % 3
			if state[j][k] == 0:
				valid_moves.append(i)
		random.shuffle(valid_moves)
		if len(valid_moves) > 0:
			return valid_moves[0]
		else:
			return -1
	def reset(self):
		pass
		

def main():
	#tic tac toe

	#make the two computers play each other to learn the game
	player1 = QLearner(9)
	player2 = QLearner(9)
	random_player = RandomPlayer()
	for i in xrange(200000):
		self_play(player1, player2, False, True)
		#self_play(player2, player1, False, True)
		if i%1000 == 0:
			print(i)
			self_play(random_player,player2,True,False)

	self_play(player1,player2,True,False)
	
	#now test the program
	print("Random plays random")
	print("[Ties,Random Player 1 Wins, Random Player 2 Wins]")
	
	results = [0,0,0]
	for i in xrange(5000):
		j = self_play(random_player,random_player,False,False)
		results[j]+=1
	print(results)

	print("Player 2 plays random")
	print("[Ties,Random Player 1 Wins, QLearner Player 2 Wins]")
	results = [0,0,0]
	for i in xrange(5000):
		j = self_play(random_player,player2,False,False)
		results[j]+=1
	print(results)

	print("Player 1 plays random")
	print("[Ties, QLearner Player 1 Wins, Random Player 2 Wins]")
	results = [0,0,0]
	for i in xrange(5000):
		j = self_play(player1,random_player,False,False)
		results[j]+=1
	print(results)

def to_tuple(a):
	try:
		return tuple(to_tuple(i) for i in a)
	except TypeError:
		return a

#like wargames we will have the computer play itself
def self_play(player1, player2, print_game, should_learn):
	board = np.zeros((3,3))
	winner = 0
	rounds = 0
	while True:
		p1_action = player1.evaluate(to_tuple(board), False, 0,should_learn)
		if not make_move(board, p1_action, -1):
			player1.evaluate(to_tuple(board),True,-0.5, should_learn)
			if print_game:
				print("Player 1 made an invalid move")
				winner = 2
			break
		if print_game:
			print("Player 1's move")
			print(board)
			print("")
		if check_win(board):
			player1.evaluate(to_tuple(board),True, 0.2, should_learn)
			player2.evaluate(to_tuple(board),True, -0.1, should_learn)
			winner = 1
			if print_game:
				print("Player 1 wins")
			break
		if check_tie(board):
			break
		p2_action = player2.evaluate(to_tuple(board), False, 0, should_learn)
		if not make_move(board, p2_action, 1):
			player2.evaluate(to_tuple(board),True, -0.5, should_learn)
			winner = 1
			if print_game:
				print("Player 2 made an invalid move")
			break
		if print_game:
			print("Player 2's move")
			print(board)
			print("")
		if check_win(board):
			winner = 2
			#player2.evaluate(to_tuple(board),True, 5,should_learn)
			#player1.evaluate(to_tuple(board),True, -2,should_learn)
			player2.evaluate(to_tuple(board),True, 0.2, should_learn)
			player1.evaluate(to_tuple(board),True, -0.1, should_learn)
			if print_game:
				print("Player 2 wins")
			break
		if check_tie(board):
			player2.evaluate(to_tuple(board),True, -0.05, should_learn)
			player1.evaluate(to_tuple(board),True, -0.05, should_learn)
			break
		rounds += 1
	if print_game:
		print("Game Over")
	player1.reset()
	player2.reset()
	return winner

def make_move(state, action, player):
	i = int(action / 3)
	j = action % 3
	if not state[i,j] == 0:
		#invalid move
		state = np.zeros((3,3)).fill(-2)
		return False
	else:
		state[i,j] = player
		return True

def check_tie(state):
	if not np.any(state == 0):
		return True
	else:
		return False

def check_win(state):
	for row in xrange(0,3):
		test_vec = np.array([0,0,0])
		test_vec[row] = 1
		if abs(np.dot(state,test_vec).sum()) == 3:
			return True
		if abs(np.dot(np.transpose(state),test_vec).sum()) == 3:
			return True
	if abs(np.trace(state)) == 3 or abs(np.trace(np.rot90(state))) == 3:
		return True
	return False


if __name__ == "__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
