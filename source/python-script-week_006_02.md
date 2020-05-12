---
title: python script week 006 02 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 006 02'

Functions in program: 
* `def superhero():`
* `def fight(evil, count):`
* `def get_depressed():`
* `def dog_event(chance):`
* `def event(n):`
* `def pelmeshki():`
* `def event(n):`
* `def save_robot_Vasya(p):`
* `def ufo_arrives(p):`
* `def run_away():`

Modules used in program: 
* `import time`
* `import random`
* `import random`
* `import time`
* `import random`

## python week 006 02

Python mysql example: week 006 02

```python
# 6

import random
import time

def run_away():
    cat = not random.randint(0, 9)
    dog = random.randint(1, 100) <= 3
    if cat or dog:
        if cat:
            print("Кошка убежала!")
        if dog:
            print("Собака убежала!")
        print("Робот Вася спасен!")
    return (cat or dog)

def ufo_arrives(p):
    ufo = random.randint(1, 100) <= 7
    if ufo:
        p = min(p + 50, 100)
        print("Прилетело НЛО и подзарядило Васю на 50%!")
    return p
    
def save_robot_Vasya(p):
    p = round(p * 100) # Васин заряд
    t = 1
    while p > 0:
        print("тик-так... осталось {}%".format(p))
        time.sleep(0.2)
        if run_away():
            break
        if t % 5 == 0:
            p = ufo_arrives(p)
        t += 1 # счетчик времени
        p -= 2 # Васин заряд -2%
    else:
        print("Эх, Вася, Вася...")

# 7

import random

ask = "Может быть, они уже готовы? Съедим? (да/нет)\t"

urr = "Из твоего живота раздаётся долгое, тоскливое урчание..."
gluck = ["От дикого голода мысли в твоей голове как-то путаются...",
         "От голода у тебя начинаются галлюцинации...",
         "На тебя замахивается клюшкой для крокета Микки-Маус, заросший щетиной!",
         "Пол под твоими ногами превращается в лужайку кислотных цветов!"]

good = 'Ну, теперь-то они точно готовы. На пачке было написано "варить 12 минут".\nТвоё стоическое ожидание с лихвой вознаграждено восхитительным вкусом пельмешек. Победа!!'
bad = "Фу. Недоварились."

def event(n):
    return random.randint(1, 100) <= n
                                        '''
                                            # происходит ли некое событие с вероятностью n%
                                            # true/false на выходе
                                        '''

def pelmeshki():
    t = 0
    print("На плите варятся заветные пельмешки...")

    while t < 12:
        print("Прошла минута.")
        
        if event(50):
            print(urr)
        if event(5):
            print(gluck[random.randint(0,3)])

        answer = input(ask)
        t += 1

        if answer == 'да':
            print(bad)
            break
    else:
        print(good)

# 8

import random
import time



def event(n):
    return random.randint(1, 100) <= n
                                        '''
                                            # происходит ли некое событие с вероятностью n%
                                            # true/false на выходе
                                        '''

def dog_event(chance):
    dog = event(5)
    if dog:
        print("Внезапно на сцене появляется злая кусачая собака!")
        chance -= 15
    return chance
                                        '''
                                            # появляется ли собака, и если да, то изменяется вероятность (chance) победить злодея
                                            # возвращает вероятность победы (измененнную или оставшуюся прежней)
                                        '''

def get_depressed():
    result = event(5)
    if result:
        print("У героя депрессия... ( ;___;)")
    return result
                                        '''
                                            # впадает ли герой в депрессию
                                            # true/false на выходе       
                                        '''



    # сражение или серия сражений с одним злодеем
    # на входе: номер злодея и текущее число попыток
    # возвращает обновленное число попыток

def fight(evil, count):
    chance = 50     # битва с каждым новым злодеем начинается с вероятности победы 50%
    how = "отважно" # как сражаемся?
    sad_fights = 0  # для случая с депрессией: чтобы фиксировать, сколько битв осталось провести с уменьшенной на 10% вероятностью победы
    sad = False     # есть ли депрессия (в начале сражения с новым злодеем ее быть не может)
    won = False     # победил ли злодея? (переменная для цикла)
    
    while not won:
        time.sleep(0.2)
        print("Герой %s сражается со злодеем №%d" % (how, evil))

            # Если нам предстоит биться после того, как случилась депрессия, то количетво оставшихся боев в депрессивном состоянии надо уменьшить на один
            # Если таких боев не осталось, а мы на данный момент депрессивны, значит, пора выходить из депрессии => вернуть прежнюю вероятность победы
        
        if sad_fights != 0:
            sad_fights -= 1
        elif sad:
            chance = 50
            sad = False

            # Собственно, битва
            # Здесь же решается, появляется ли в этом раунде собака: если да, вероятность победы уменьшится
            
        if not event(dog_event(chance)):    # что делаем, если не побеждаем злодея в текующем раунде
            print("Герой проиграл... ( -_-)")

                # будет ли у героя депрессия?
                # если да, то запоминаем, что нам надо провести три следующих битвы с меньшей вероятностью победы,
                    #а также изменить настроение, с которым герой сражается со злодеями
                
            sad = get_depressed() 
            if sad:
                chance -= 10
                sad_fights = 3
                how = "отважно-депрессивно"
        else:   # победа
            won = True
            print("Герой победил! ( ^o^)")
        count += 1
    
    return count

def superhero():
    evil = 1    # номер злодея
    count = 0   # счетчик попыток

    while evil <= 13:
        count = fight(evil, count)  # Битва (серия битв) с данным злодеем
        evil += 1
    print("Число попыток, которое понадобилось герою, чтобы стать супергероем: %d" % count)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
