---
title: python script zukki (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'zukki'

Functions in program: 
* `def play():`
* `def getcards(num_of_player):`

Modules used in program: 
* `import random`

## python zukki

Python example: zukki

```python
#coding: utf-8
import random

class SampleAI:
    def __init__(self, cards):
        """
        [function]: initialize class AI
        input:
        - cards: (list)
        """
        self.pocket_cards = sorted(cards)
    
    def check(self, card):
        """
        [function]: check cards you can use now
        input:
        - card: card on the field
        output:
        - ret: cards you can use now
        """
        ret = [self.pocket_cards[0]]
        for c in self.pocket_cards:
            if c >= card:
                ret.append(c)
        return ret

    def turn(self, my_cards, card_on_the_field):
        """
        [function]: choice one from my cards
        input:
         - card_on_the_field
        output:
         - choiced card
        """
        if card_on_the_field == None:
            card_on_the_field = 5
        
        self.pocket_cards = my_cards

        cards = self.check(card_on_the_field)
        f = lambda x: abs(8-x)/10.0 - abs(x-1)*(7-len(self.pocket_cards))/30.0
        cards_and_probs = sorted([(c, f(c)) for c in cards], key=lambda x:x[1])
        #print(cards_and_probs)
        choice_card = cards_and_probs[0][0]
        for c, threthold in cards_and_probs:
            p = random.random()
            if threthold <= p:
                choice_card = c
                break
        self.pocket_cards.remove(choice_card)
        return self.pocket_cards, choice_card

def getcards(num_of_player):
    all_cards = range(1, 16) * 4
    #print(all_cards)
    players = []
    for i in xrange(num_of_player):
        player = []
        for j in xrange(7):
            draw = all_cards[random.randint(0, len(all_cards)-1)]
            all_cards.remove(draw)
            player.append(draw)
        players.append(sorted(player))
    return players

def play():
    a, b = getcards(2)
    
    ai = SampleAI(b)
    #print("you:{}, ai:{}".format(a, b))
    
    for i in xrange(6):
        print('your cards:{}'.format(a))
        xa = int(raw_input("it's your turn >>"))
        b, xb = ai.turn(b, xa)
        print('ai choice:', xb)
        a.remove(xa)

    print('you:{}, ai:{}'.format(a, b))
    print('you win' if a <= b else 'ai wins')

if __name__ == '__main__':
    play()
    


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
