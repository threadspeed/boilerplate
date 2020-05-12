---
title: python script week 008 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 008'

Functions in program: 
* `def star_dialect(text):`
* `def reduce2(word):`
* `def find_vowels(text):`
* `def reduced(s1, s2):`
* `def desypher(text):`
* `def translate(text):`
* `def find_syll(text):  # ищем слоги, т.е. последовательные сочетания согласная + гласная`

Modules used in program: 
* `import random`
* `import re`

## python week 008

Python mysql example: week 008

```python
# 0

vowels = "auioe"
textik = '''aaaaeeeeeuuuuuuaaaaaaaiiiiiiiiiccccccvvvvvvvvvvvvvvvhhhhhhhhhhhhfffffffffbbbaaaaaaaaaauuueeeeeeeeeuuuuunnnnnnnnnntttttttthhhhhhhhhhhhhnnnnnaaaauuuuuuuuuuuuuuueeeeeeeeebbbbbnnnnnnnnnllllllllldddddddddddddddsssssnnnaaaaiiiiiiuuuuuuuuuuuuuuueeeeeeeeeeeooooooooiiiiiiiiiiooookkkkkkkkkkttttttttttttttt'''

### читерский способ с регулярными выражениями

import re

slogs = re.findall('[qwrtypsdfghkjlzxcvbnm][auioe]', textik)
word = "".join(slogs)
print(word)

### без регулярных выражений
  
def find_syll(text):  # ищем слоги, т.е. последовательные сочетания согласная + гласная
  n = len(text)
  result = ""
  for i in range(n - 1):
    if text[i] not in vowels and text[i+1] in vowels:
      result += text[i:i+2]
  return result
  
word = find_syll(textik)
print(word)

# 1

# bad?

alph_lowercase = range(ord('a'), ord('z') + 1)
alph_uppercase = range(ord('A'), ord('Z') + 1)

def translate(text):
  
  result = ""
  a_upp = ord('A')
  a_low = ord('a')
  
  for s in text:
    sym = ord(s) # запоминаем код символа в таблице юникода
    
    if ord(s) in alph_uppercase:
      s_num = max(a_upp, (sym + 1) % 91)
      s = chr(s_num)
    
    elif ord(s) in alph_lowercase:
      s_num = max(a_low, (sym + 1) % 123)
      s = chr(s_num)
    
    result += s
  return result

example = '''Sgd Ydm ne Oxsgnm, ax Shl Odsdqr

Adztshetk hr adssdq sgzm tfkx.
Dwokhbhs hr adssdq sgzm hlokhbhs.
Rhlokd hr adssdq sgzm bnlokdw.
Bnlokdw hr adssdq sgzm bnlokhbzsdc.
Ekzs hr adssdq sgzm mdrsdc.
Rozqrd hr adssdq sgzm cdmrd.
Qdzczahkhsx bntmsr.
Rodbhzk bzrdr zqdm's rodbhzk dmntfg sn aqdzj sgd qtkdr.
Zksgntfg oqzbshbzkhsx adzsr otqhsx.
Dqqnqr rgntkc mdudq ozrr rhkdmskx.
Tmkdrr dwokhbhskx rhkdmbdc.
Hm sgd ezbd ne zlahfthsx, qdetrd sgd sdloszshnm sn ftdrr.
Sgdqd rgntkc ad nmd-- zmc oqdedqzakx nmkx nmd --nauhntr vzx sn cn hs.
Zksgntfg sgzs vzx lzx mns ad nauhntr zs ehqrs tmkdrr xnt'qd Ctsbg.
Mnv hr adssdq sgzm mdudq.
Zksgntfg mdudq hr nesdm adssdq sgzm *qhfgs* mnv.
He sgd hlokdldmszshnm hr gzqc sn dwokzhm, hs'r z azc hcdz.
He sgd hlokdldmszshnm hr dzrx sn dwokzhm, hs lzx ad z fnnc hcdz.
Mzldrozbdr zqd nmd gnmjhmf fqdzs hcdz -- kds'r cn lnqd ne sgnrd!'''

print(translate(example))

# 2
# читабельный вид не получается

note = "ydybtlhsibqgkecosemabpflmeeoxzmwypsqmeylrfpcrk"
vowels = "aeiouy"
consonants = "bcdfghjklmnpqrstvwxz"

def desypher(text):
  text = text[-2::-3]
  print((text))
  result = ""
  
  for s in text:
    if s in consonants:
      real_s_index = consonants.index(s) - 2
      result += consonants[real_s_index]
    
    elif s in vowels:
      real_s_index = vowels.index(s) - 2
      result += vowels[real_s_index]
  return result  

print(desypher(note))

# 3

vowels = "ауеёоияэюы"

def reduced(s1, s2):
  return s1 + '-' + s2

#### import this from the other file ######

def find_vowels(text):
  n = len(text)
  result = []
  for i in range(n):
    if text[i] in vowels:
      result.append(i)
  return(result)


#########################################

def reduce2(word):
  n = len(word)
  v_pos = find_vowels(word)
  n_syll = len(v_pos)
  
  # количество оставляемых "слогов"  - соответствует количеству оставляемых гласных
  
  if n > 7:                                   # для длинных слов
    if n_syll > 5:                                # в которых много слогов
      p1 = v_pos[2]                                 # оставим первые два "слога" 
      p2 = v_pos[-1]                                # и последний
    elif n_syll > 2:                              # в которых немного слогов
      p1 = v_pos[1]                                 # оставим первый "слог"
      p2 = v_pos[-1]                                # и последний
    else:                                         # в которых мало слогов
      p1 = max(0, v_pos[0] - 1)                     # оставим начало слова (до первой гласной) или (если первая буква гласная, то только ее)
      p2 = min(v_pos[-1] + 1, n - 1)                 # оставим конец слова (после последней гласной) или (если она последняя, только ее)
  elif n > 5:                                 # для слов средней длины
    if n_syll > 2:                              # если в них 3 и более слогов
      p1 = v_pos[1]                               # оставим первый "слог"
    else:
      p1 = v_pos[0]                             # оставим все, до первой гласной
    p2 = min(v_pos[-1] + 1, n - 1)                # см. выше
  elif n > 3:                                 # для маленьких слов - берем первую и последнюю буквы
    p1 = 1
    p2 = n - 1
  else:                                       # самые маленькие слова оставляем без именений
    p1 = 0
  
  if p1 != 0:
    return reduced(word[:p1], word[p2:])
  else:
    return word

import random

go = True
while go:
  word_input = input()
  print(reduce2(word_input))
  if random.randint(1, 100) > 75:
    go = False

# 1 от Александры Белобородовой

vowels = "ауеёоияэюы"

def star_dialect(text):
  
  next = False    # индикатор для того, чтобы помнить, что после ж с гласными ничего не происходит
  n = len(text)
  result = ""     # в этой переменной будет записана измененная строка
  
  for i in range(n):
    s = text[i]
    add = ''
    if not next and s in vowels:
      if s in "яиеы":
        if text[max(i-1, 0)] not in vowels:   # если подряд идут две гласные, то добавлять мягкий знак не нужно
          add = "ь" 
        if s == "ы":  # замена ы на и
          s = "и"
      elif s == "э":  # замена э на е
        s = 'е'
    elif next:        # "забываем" о том, что предыдущая буква была "ж"
      next = False
    elif s == "ж":    # если встретилась буква ж, то необходимо запомнить это до следующей итерации
      next = True
    result += add + s   # добавляем к результату либо мягкий знак, либо пустую строку + видоизмененный (или нет) символ
  return result  
  
text = 'О владыка! Но разве это законно? А как быть с джедаями? Да, да, Владыка, как прикажете. Что это там происходит? Мы потеряли связь!'
print(star_dialect(text))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
