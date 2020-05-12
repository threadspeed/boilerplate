---
title: python script Ddakji4 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ddakji4'

Functions in program: 
* `def ten_gacha(gacha_list):`
* `def s_gacha(gacha_list):`
* `def gacha(gacha_list):`
* `def gacha_value(rarity_list):`
* `def make_rlist(gacha_list):`
* `def make_srlist(gacha_list):`
* `def make_ssrlist(gacha_list):`
* `def make_randint(num):`

## python Ddakji4

Python example: Ddakji4

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
       return "{}는 {}타입의 {}등급이고 레벨은 {}, 어필은 {}입니다.".format(self.name, self.color, self.rarity, self.level, self.appeal)
    def lesson(self, eat):
        exptable =[1, 11, 24, 40, 62, 87, 105, 140]
        for x in eat:
            eatexp = x.lessonexp
            self.exp = self.exp + eatexp
            if self.color == x.color:
                self.exp = self.exp + eatexp/2
        for x in range(self.maxlevel):
            if self.exp >= exptable[x]:
                self.level = x + 1
        self.dance = self.dance + (self.level-1) * 200
        self.vocal = self.vocal + (self.level-1) * 200
        self.visual = self.visual + (self.level-1) * 200
        self.appeal = self.dance + self.vocal + self.visual
        return self

class Ssrare(Ddakji):
    rarity = 'Ssrare'
    exp = 1
    level = 1
    maxlevel = 8
    lessonexp = level * 10

class Srare(Ddakji):
    rarity = 'Srare'
    exp = 1
    level = 1
    maxlevel = 6
    lessonex = level * 4

class Rare(Ddakji):
    rarity = 'Rare'
    exp = 1
    level = 1
    maxlevel = 4
    lessonexp = level * 2

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


def make_randint(num):
    import random
    n = random.randint(1, num)
    return n

def make_ssrlist(gacha_list):
    ssrlist = []
    for w_rarity in gacha_list:
        if isinstance(w_rarity, Ssrare):
            ssrlist.append(w_rarity)
    return ssrlist

def make_srlist(gacha_list):
    srlist = []
    for w_rarity in gacha_list:
        if isinstance (w_rarity, Srare):
            srlist.append(w_rarity)
    return srlist

def make_rlist(gacha_list):
    rlist = []
    for w_rarity in gacha_list:
        if isinstance(w_rarity, Rare):
            rlist.append(w_rarity)
    return rlist


def gacha_value(rarity_list):
    import random
    n = random.randint(1, len(rarity_list))
    return rarity_list[n-1]

def gacha(gacha_list):
    n = make_randint(1000)
    rarelist = make_rlist(gacha_list)
    srarelist = make_srlist(gacha_list)
    ssrarelist = make_ssrlist(gacha_list)
    if n <= 15:
        return gacha_value(ssrarelist)
    elif n > 100 and n <= 200:
        return gacha_value(srarelist)
    else:
        return gacha_value(rarelist)

def s_gacha(gacha_list):
    srarelist = make_srlist(gacha_list)
    ssrarelist = make_ssrlist(gacha_list)
    n = make_randint(100)
    if n <= 2:
        return gacha_value(ssrarelist)
    else:
        return gacha_value(srarelist)


def ten_gacha(gacha_list):
    getlist = []
    for x in range(9):
        x = gacha(gacha_list)
        getlist.append(x)
    getlist.append(s_gacha(gacha_list))
    return getlist

illjin = Ssrare('Sibuya Rin', 'Cool', 5000, 6000, 7000)
smr = Rare('Uzuki', 'Cute', 1000, 1000, 1000)

print(illjin.who)

illjin.lesson([smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr,smr])

print(illjin.level)
print(illjin.who)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
