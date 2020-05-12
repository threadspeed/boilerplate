---
title: python script DDakji2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'DDakji2'

Functions in program: 
* `def ten_gacha(gacha_list):`
* `def s_gacha(gacha_list):`
* `def gacha(gacha_list):`

## python DDakji2

Python mysql example: DDakji2

```python
class Ddakji:
    def __init__(self, name, color, dance, vocal, visual):
        self.name = name
        self.color = color
        self.dance = dance
        self.vocal = vocal
        self.visual = visual
        self.appeal = dance + vocal + visual
    @property
    def who(self):
       return "{}는 {}타입의 {}등급이고 어필은 {}입니다.".format(self.name, self.color, self.rarity, self.appeal)

class Ssrare(Ddakji):
    rarity = 'Ssrare'


class Srare(Ddakji):
    rarity = 'Srare'


class Rare(Ddakji):
    rarity = 'Rare'


cards = [
    Ssrare('Sibuya Rin', 'Cool', 5000, 6000, 7000),
    Ssrare('Zzang Mio', 'Fashion', 6000, 5000, 6000),
    Ssrare('Fish Uzuki', 'Cute', 6000, 4000, 6000),
    Srare('Manekawa Miku', 'Fashion', 4000, 3000, 5000),
    Srare('Sick Ranko', 'Cool', 3000, 6000, 4000),
    Srare('Neet Anzu', 'Cute', 4000, 2000, 6000),
    Rare('Kirari', 'Fashion', 2000, 1000, 1000),
    Rare('Honda THE CAPTAIN Mio', 'Fashion', 1500, 1000, 1300),
    Rare('Kanade', 'Cool', 1200, 1300, 1500),
    Rare('Mayu', 'Cute', 1400, 1300, 1200)
]

def gacha(gacha_list):
    import random
    a = random.randint(1, 1000)
    rarelist = []
    srarelist = []
    ssrarelist = []
    for w_rarity in gacha_list:
        if isinstance(w_rarity, Ssrare):
            ssrarelist.append(w_rarity)
        elif isinstance(w_rarity, Srare):
            srarelist.append(w_rarity)
        else:
            rarelist.append(w_rarity)
    if a <= 15:
        n = random.randint(1, len(ssrarelist))
        return ssrarelist[n-1]
    elif a > 100 and a <= 200:
        n = random.randint(1, len(srarelist))
        return srarelist[n-1]
    else:
        n = random.randint(1, len(rarelist))
        return rarelist[n-1]

def s_gacha(gacha_list):
    import random
    srarelist = []
    ssrarelist = []
    num = random.randint(1,100)
    for w_rarity in gacha_list:
        if isinstance(w_rarity, Ssrare):
            ssrarelist.append(w_rarity)
        elif isinstance(w_rarity, Srare):
            srarelist.append(w_rarity)
    if num <= 2:
        n = random.randint(1, len(ssrarelist))
        return ssrarelist[n-1]
    else:
        n = random.randint(1, len(srarelist))
        return srarelist[n-1]

def ten_gacha(gacha_list):
    getlist = []
    for x in range(9):
        x = gacha(gacha_list)
        getlist.append(x)
    getlist.append(s_gacha(gacha_list))
    return getlist

a = ten_gacha(cards)

for x in a:
    print(x.who)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
