---
title: python script SimpleChatBot (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'SimpleChatBot'

Functions in program: 
* `def main(n):`

## python SimpleChatBot

Python mysql example: SimpleChatBot

```python
class Chat:
    vocabs = [
            "ああ、そうなんだー",
            "へー",
            "すごいねー"
            ]
    negative = "いや、それは違うんじゃないかなーｗ"
    farewell = ["またねー", "じゃあねー"]

    def response(self):
        """return response from self.vocabs at random.
        if self.count becomes larger than threshold given initially,
        return soft-negative response."""

        import random

        r = random.choice(self.rindex)

        if self.count > self.threshold:
            self.count = 0
            return self.negative
        else:
            self.count += 1
            return self.vocabs[r]

    def bye(self):
        """return farewell from self.farewell at random."""

        import random

        r = random.choice(self.findex)
        return self.farewell[r]

    def __init__(self, n):
        """initialize class Chat.
        set parameters in Chat."""

        self.count = 0
        self.threshold = n
        self.rindex = [i for i in range(len(self.vocabs))]
        self.findex = [i for i in range(len(self.farewell))]

def main(n):
    C = Chat(n)
    ibuf = obuf = ""
    byebye = False

    print("press 'Q' to quit")
    while True:
        ibuf = input('>')
        if ibuf == "q" or ibuf == "Q":
            byebye = True
            obuf = C.bye()
        else:
            obuf = C.response()
        print("Res. >> " + obuf)
        if byebye:
            sys.exit()

    return


if __name__ == '__main__':
    import sys

    if len(sys.argv) < 2:
        print("give me threshold", file = sys.stderr)
        sys.exit()

    main(int(sys.argv[1]))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
