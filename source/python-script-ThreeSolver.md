---
title: python script ThreeSolver (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ThreeSolver'

Functions in program: 
* `def ReadBoard(B):`
* `def canMerge(v1, v2):`
* `def mergeScore(v1, v2):`
* `def addPoints(s, d):`
* `def isValidLocation(s):`

Modules used in program: 
* `import string`
* `import sys`
* `import random`
* `import copy`
* `import numpy`

## python ThreeSolver

Python example: ThreeSolver

```python
#!/usr/bin/python

import numpy
import copy
import random
import sys
import string

BOARD_SIZE = 4

MOVE_UP = (-1, 0)
MOVE_DOWN = (1, 0)
MOVE_LEFT = (0, -1)
MOVE_RIGHT = (0, 1)

MOVES = (MOVE_UP, MOVE_DOWN, MOVE_LEFT, MOVE_RIGHT)
MOVES_STRING = ("UP", "DOWN", "LEFT", "RIGHT")
UP_DOWN_LEFT_RIGHT = ((MOVE_UP, MOVE_DOWN), (MOVE_LEFT, MOVE_RIGHT))


def isValidLocation(s):
    if (s[0] < 0 or s[1] < 0 or s[0] >= BOARD_SIZE or s[1] >= BOARD_SIZE):
        return False
    return True


def addPoints(s, d):
    return (s[0] + d[0], s[1] + d[1])


def mergeScore(v1, v2):
    if v1 > 2 and v2 > 2 and v1 == v2:
        return 2
    if v1 != 0 and v2 != 0 and v1 + v2 == 3:
        return 2
    return 0

def canMerge(v1, v2):
    if v1 > 2 and v2 > 2 and v1 == v2:
        return True
    if v1 != 0 and v2 != 0 and v1 + v2 == 3:
        return True
    return False


class Board(object):
    def __init__(self):
        self.board = numpy.zeros((BOARD_SIZE, BOARD_SIZE), dtype=numpy.uint16)
        self.wasMoved = False
        self.depth = 0

    def getScore(self):
        score = 0.0
        for i in range(BOARD_SIZE):
            for j in range(BOARD_SIZE):
                s = (i, j)
                if (self.board[s] == 0):
                    score += 4
                score += self.checkAllMerges(s)
                score += self.checkLock(s)
                #score += self.checkNextMerges(s)
        return score

    def checkAllMerges(self, s):
        score = 0
        for m in (MOVE_DOWN, MOVE_RIGHT):
            d = addPoints(s, m)
            if isValidLocation(d):
                score += mergeScore(self.board[s], self.board[d])
        return score

    def checkNextMerges(self, s):
        score = 0
        return 0
        for m in (MOVE_DOWN, MOVE_RIGHT):
            d = addPoints(s, m)
            if isValidLocation(d) and self.board[s] > 0:
                if self.board[s] * 2 == self.board[d]:
                    score += 1
                if self.board[s] == self.board[d] * 2:
                    score += 1
        return score

    def checkLock(self, s):
        return 0
        score = 0
        for (t1, t2) in UP_DOWN_LEFT_RIGHT:
            d1 = addPoints(s, t1)
            d2 = addPoints(s, t2)
            if isValidLocation(d1) and isValidLocation(d2):
                c = self.board[s]
                v1 = self.board[d1]
                v2 = self.board[d2]
                if (c + v1 != 3 and c + v2 != 3 and c < v1 and c < v2):
                    score += -1
        return score

    def doMove(self, m):
        self.wasMoved = False
        movedLocation = []
        for outer in range(BOARD_SIZE):
            wasMoved = False
            for inner in range(1, BOARD_SIZE):
                if (m == MOVE_UP or m == MOVE_DOWN):
                    j = outer
                    if m == MOVE_UP:
                        i = inner
                    else:
                        i = BOARD_SIZE - 1 - inner
                else:
                    i = outer
                    if m == MOVE_LEFT:
                        j = inner
                    else:
                        j = BOARD_SIZE - 1 - inner
                s = (i, j)
                d = addPoints(s, m)
                if (self.board[d] == 0 and self.board[s] > 0):
                    self.board[d] = self.board[s]
                    self.board[s] = 0
                    wasMoved = True
                elif canMerge(self.board[s], self.board[d]):
                    self.board[d] += self.board[s]
                    self.board[s] = 0
                    wasMoved = True
            movedLocation.append(wasMoved)
        nextIndex = -1
        t = []
        for nextIndex in range(4):
            if (movedLocation[nextIndex]):
                self.wasMoved = True
                ml = (-1, -1)
                if (m == MOVE_LEFT):
                    ml = (nextIndex, BOARD_SIZE - 1)
                elif (m == MOVE_RIGHT):
                    ml = (nextIndex, 0)
                elif (m == MOVE_DOWN):
                    ml = (0, nextIndex)
                elif (m == MOVE_UP):
                    ml = (BOARD_SIZE - 1, nextIndex)
                t.append(ml)
        return t

    def checkAllMoves(self, nV):
        allScores = []
        allBoards = []
        allDir = []
        mi = 0
        for m in MOVES:
            newBoard = copy.deepcopy(self)
            nextCardLocations = newBoard.doMove(m)
            if (newBoard.wasMoved):
                score = 0
                nscore = 0
                for ncl in nextCardLocations:
                    newBoard.board[ncl] = nV
                    score += newBoard.getScore()
                    nscore += 1
                    for mm in MOVES:
                        newBoardNew = copy.deepcopy(newBoard)
                        newBoardNew.doMove(mm)
                        if (newBoardNew.wasMoved):
                            score += newBoardNew.getScore()
                            nscore += 1
                    newBoard.board[ncl] = 0
                score = score / nscore
                allScores.append(score)
                allBoards.append(newBoard)
                allDir.append(MOVES_STRING[mi])

            mi += 1
        #print(allScores)
        #for b in allBoards:
        print(nV)
        print(self.board)
        print(allScores)
        i = allScores.index(max(allScores))
        return allDir[i]
        #return allBoards[i]


def ReadBoard(B):
    for i in range(BOARD_SIZE):
        print("Enter Line %d" % (i))
        line = sys.stdin.readline()
        sline = string.split(line, " ")
        for j in range(BOARD_SIZE):
            B.board[(i, j)] = int(sline[j])


if __name__ == "__main__":
    B = Board()
    ReadBoard(B)
    while (True):
        print(B.getScore())
        print("Enter next:")
        line = sys.stdin.readline()
        nV = int(line)
        B = B.checkAllMoves(nV)
        print(B.board)
        for xx in range(2):
            print("Fix Board i j v:")
            line = sys.stdin.readline()
            sline = string.split(line, " ")
            i = int(sline[0])
            j = int(sline[1])
            v = int(sline[2])
            B.board[(i, j)] = v


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
