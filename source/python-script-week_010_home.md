---
title: python script week 010 home (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 010 home'

Functions in program: 
* `def pf(text):`
* `def preprocess(text):`
* `def guess():`
* `def tr(m):`
* `def randomizer(t):`
* `def halver(lst):`
* `def splitter(text, s):`

Modules used in program: 
* `import random `

## python week 010 home

Python example: week 010 home

```python
# 1

def splitter(text, s):
  return text.split(s)
  
# 2 не поровну

def halver(lst):
  n = len(lst)
  h = (n + 1) // 2
  return lst[:h], lst[h:]
  
# 3

import random 

def randomizer(t):
  t2 = t[:]
  random.shuffle(t2)
  return t2[:5] + t2[-5:]
  
# 4

'''
гггг-ММ-дд (Канада, Польша, Швеция)
гггг.дд.ММ (Казахстан)
д/М/гггг (Бразилия, Греция, Тайланд) обратите внимание, что месяц и число могут записываться одной цифрой
М/д/гггг (США)
'''

def tr(m):
    return "%02d" % (int(m))

def guess():
  d = input("Введите дату")
  if d.find('/') != -1:
    s = "/"
  elif d.find('-') != -1:
    s = "-"
  elif d.find('.') != -1:
    s = "."
  else:
    print("SOmething is wrong")
    return
  
  dlst = d.split(s)
  
  if len(dlst[0]) == 4:
    year = dlst[0]
  else:
    year = dlst[2]
  
  if s == "-":
    month = dlst[1]
    day = dlst[2]
  elif s == ".":
    month = dlst[2]
    day = dlst[1]
  else:
    if int(dlst[1]) > 12:
      day = dlst[1]
      month = dlst[0]
    elif int(dlst[0]) > 12:
      day = dlst[0]
      month = dlst[1]
    else:
      print("We are not sure")
      day = dlst[1]
      month = dlst[0]
  
  print("%s.%s.%s" % (tr(day), tr(month), year))
  
# 5

def preprocess(text):
    syms = '.,:;-!?"'
    text = text.lower()
    for c in syms:
        text = text.replace(c, "")
    return text

def pf(text):
  text = preprocess(text)
  words = text.split()
  for word in words:
    if (len(word) > 1):
      rev_word = word[::-1]
      if word == rev_word:
        print(word)
    
text = '''В городе Н творятся странные вещи: поп не даёт Алле пойти на шабаш, его довод прост - это грешно, того и гляди будет новый всемирный потоп; 
бравый казак идёт в кабак, но у него невысок доход, поэтому он не спешит озвучивать заказ, а пересчитывает монеты, думает как дожить до получки;
слышится топот: начался тот самый шабаш; исповедующий буддизм дед, ругаясь, прячется в шалаш...
Око Луны следит за городом Н равнодушно или, может, слегка усмехаясь.'''

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
