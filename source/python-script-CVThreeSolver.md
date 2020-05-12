---
title: python script CVThreeSolver (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'CVThreeSolver'

Functions in program: 
* `def sendMove(s, m):`
* `def randomMove(s):`
* `def getScreen(s):`
* `def ProssesGame():`
* `def cutBoard(I):`
* `def cutCards(I, nCard):`
* `def onMouseEvent(event, x, y, flags, param):`
* `def iview(I):`
* `def doModel(name):`

Modules used in program: 
* `import ThreesSolver`
* `import time`
* `import socket`
* `import random`
* `import numpy as np`
* `import cv2`

## python CVThreeSolver

Python example: CVThreeSolver

```python
#!/usr/bin/python

import cv2
import numpy as np
import random
import socket
import time
import ThreesSolver


CARD_H = 185
CARD_W = 135
CARD_H_SUB = 40
CARD_W_SUB = 20
CARD_NUM = 0
NUM = 0
SCALE = 0.2

SAMPLES_SIZE_CARD = 2001
SAMPLES_SIZE_NEXT = 288

MODEL = None
MODEL_NEXT = None

DEBUG = False
#DEBUG = True


def doModel(name):
    SAMPLES = np.loadtxt("train_samples%s.data" % (name), np.float32)
    RESPONSES = np.loadtxt("train_responses%s.data" % (name), np.int32)
    RESPONSES = RESPONSES.reshape((RESPONSES.size, 1))
    MODEL = cv2.KNearest()
    MODEL.train(SAMPLES, RESPONSES)
    return MODEL


def iview(I):
    global NUM
    s = "NUM%03d" % (NUM)
    cv2.imshow(s, I)
    NUM += 1
    return s


class GameCard(object):
    def __init__(self, I, debug=False):
        global CARD_NUM
        global SCALE
        self.I = I[20:-20, 10:-10]
        #self.G = cv2.cvtColor(self.I, cv2.COLOR_BGR2GRAY)
        self.s = cv2.resize(self.I, None, fx=SCALE, fy=SCALE)
        self.num = 0
        if debug:
            cv2.imwrite("cards/card_%03d.png" % (CARD_NUM), self.s)
            CARD_NUM += 1
        else:
            self.findNum()

    def findNum(self):
        global MODEL
        sample = self.s.reshape((1, SAMPLES_SIZE_CARD))
        sample = np.float32(sample)
        retval, results, neigh_resp, dists = MODEL.find_nearest(sample, k=1)
        self.num = int(results[0][0])


def onMouseEvent(event, x, y, flags, param):
    if (cv2.EVENT_LBUTTONDBLCLK == event):
        print("(%d, %d)" % (x, y))


def cutCards(I, nCard):
    global DEBUG
    H = CARD_H
    W = CARD_W
    b = ThreesSolver.Board()
    for i in range(4):
        for j in range(4):
            iT = I[i * H:(i + 1) * H, j * W:(j + 1) * W]
            c = GameCard(iT, DEBUG)
            b.board[i, j] = c.num

    if DEBUG:
        MOVES = ("LEFT", "RIGHT", "DOWN", "UP")
        return "SCREEN"
        return random.choice(MOVES)
    return b.checkAllMoves(nCard)


class NextCard(object):
    def __init__(self, I, debug):
        global SCALE
        self.I = I[125:185, 340:380]
        self.s = cv2.resize(self.I, None, fx=SCALE, fy=SCALE)
        self.num = 0
        if debug:
            self.saveImage()
        else:
            self.getNum()

    def saveImage(self):
        global CARD_NUM
        cv2.imwrite("next_card/card_%03d.png" % (CARD_NUM), self.s)
        CARD_NUM += 1

    def getNum(self):
        global MODEL_NEXT
        sample = self.s.reshape((1, SAMPLES_SIZE_NEXT))
        sample = np.float32(sample)
        retval, results, neigh_resp, dists = MODEL_NEXT.find_nearest(sample, k=1)
        self.num = int(results[0][0])


def cutBoard(I):
    B = I[340:1080, 90:630]
    return B


def ProssesGame():
    global DEBUG
    iSCR = cv2.imread("shot1.png")
    cv2.imshow('Screen', iSCR)
    nCard = NextCard(iSCR, DEBUG)
    iBRD = cutBoard(iSCR)
    #cv2.imshow('Board', iBRD)
    #cv2.setMouseCallback('Screen', onMouseEvent)
    nextMove = cutCards(iBRD, nCard.num)
    cv2.destroyAllWindows()
    return nextMove


def getScreen(s):
    time.sleep(1)
    s.send("SCREEN")
    time.sleep(0.3)
    s.recv(64)


def randomMove(s):
    s.send("MOVE")
    time.sleep(0.3)
    s.recv(64)


def sendMove(s, m):
    s.send(m)
    s.recv(64)

if __name__ == "__main__":
    global MODEL
    global MODEL_NEXT
    cSocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    cSocket.connect(("localhost", 4456))

    MODEL = doModel("")
    MODEL_NEXT = doModel("_next")
    while True:
        getScreen(cSocket)
        nextMove = ProssesGame()
        sendMove(cSocket, nextMove)
        #randomMove(cSocket)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
