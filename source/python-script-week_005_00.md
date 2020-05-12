---
title: python script week 005 00 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 005 00'

Functions in program: 
* `def masha_and_money():`
* `def gift():`
* `def print_result(dict):`
* `def vika_decides():`

## python week 005 00

Python mysql example: week 005 00

```python
# 0

week = "monday tuesday wednesday thursday friday saturday sunday"
weekend = "saturday sunday"
english = "monday thursday"

   #  0 - 15 будн - не может
   #  18 - 24 будн - не может
    # 19 - 24 выходные - не может
    # 17 - 18 пн чт - не может
    # 15 - 17 вт - не может
    # 0 - 24 суббота - не может

def vika_decides():
    day = input("В какой день недели кружок по проге?\nВведите день недели на английском.\n")
    day = day.lower()
    time = int(input("В какое время?\n"))
    no = "не "
    yes = ""

    if day in week and 0 <= time <= 24: 
        if day not in weekend:
            if (0 <= time < 15 or 18 <= time <= 24):
                result = no
            elif time < 17:
                if day != "tuesday":
                    result = yes
                else:
                    result = no
            elif day not in english:
                result = yes
            else:
                result = no
        elif time >= 19 or day == "saturday":
            result = no
        elif day == "sunday":
            result = yes
        print("Вика %sсможет посещать кружок." % result)
    else:
        print("Вы неправильно ввели данные.")

# 1

# мармелад + пирожные < 10 => Карлсон берет шоколадку, все ост - Малышу
# иначе:
    # 1/5 марм - Малышу, ост - Карлсону
    # пирожные
        # 2:3 (М:К) если кратно 5,
            # пополам если четно,
            # пополам + ост - К, если нечетно
    # шок пополам

def print_result(dict):

    # правильная форма для вывода числа мармеладок:
    if dict['Jelly'] != 0:
        j = "мармеладки (%d шт.)" % dict['Jelly']
    else:
        j = ""

    # правильная форма для вывода числа пирожных:
    if dict['Cake'] != 0:
        c = "пирожные (%d шт.)" % dict['Cake']
    else:
        c = ""

    # правильное объединение этих двух строк:
    if j != "" and c != "":
        sep = ", "
    else:
        sep = ""

    jc = j + sep + c

    # правильная форма для вывода информации о шоколадке
    if dict['Choco'] == 0.5:
        choco = " и половину шоколадки"
    elif dict['Choco'] == 1:
        choco = "целую шоколадку"
    elif dict['Choco'] == 0:
        if jc != "":
            choco = " и больше ничего"
        else:
            choco = "одни лишь поздравления, и ничего сладкого"
    print("%s получил %s%s." % (dict['Name'], jc, choco))

def gift():
    jelly = int(input("Количество мармеладок в подарке? "))
    cake = int(input("Количество пирожных в подарке? "))

    m = {'Name' : 'Малыш', 'Jelly' : 0, 'Cake' : 0, 'Choco' : 0}
    k = {'Name' : 'Карлсон', 'Jelly' : 0, 'Cake' : 0, 'Choco' : 0}

    if jelly + cake >= 10:
        m['Jelly'] = jelly // 5
        k['Jelly'] = jelly - m['Jelly']

        m['Choco'] = 0.5
        k['Choco'] = 0.5

        if cake % 5 == 0:
            part = cake // 5
            m['Cake'] = 2 * part
            k['Cake'] = 3 * part
        else:
            m['Cake'] = cake // 2
            k['Cake'] = m['Cake'] + cake % 2        
    else:
        k['Choco'] = 1
        m['Jelly'] = jelly
        m['Cake'] = cake

    print_result(m)
    print_result(k)


# 2

def masha_and_money():
    money = int(input("Сколько у Маши денег? "))
    days = int(input("Сколько дней ей надо прожить? "))
    hbs = int(input("Сколько дней рождений приходится на этот период? "))

    times = 3 # сколько раз в день ест
    hb_spent = 300 # сколько нужно денег на один день рождения
    home_food = 100 # сколько стоит домашняя еда
    diner_food = 150 # сколько стоит поесть в столовой
    salary = 400 # деньги за подработку
    
    meals = days * times # сколько всего раз ей надо поесть за данное количество дней
    hbs_money = hbs * hb_spent # сколько денег потратит на дни рождения
    normal_life = hbs_money + meals * home_food # сколько денег Маше нужно, чтобы сходить на все дни рождения и питаться только домашней едой  

    if money >= normal_life:
        
        diner = (money - normal_life) // (diner_food - home_food) # количество раз, когда мы можем заменить еду домашнюю на еду в столовой
        
        print("Маша сможет выжить и поесть в столовой %d раз" % diner)
        
    else:

        work = max(days // 7, 1) # сколько раз за этот период Маша может подработать
        work_money = work * salary # максимум, который Маша может заработать
        
        if money + work_money >= normal_life:
            money_needed = normal_life - money
            work_required = money_needed // salary + min(1, money_needed % salary) # сколько раз ей реально нужно поработать
            print("Маша сможет выжить. Для этого ей нужно подработать %d раз(а)" % work_required)
            
        else:
            
            ask = normal_life - (money + work_money)
            
            print("Чтобы выжить, Маше придется %d раз(а) подработать и попросить у родителей %d рублей." % (work, ask))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
