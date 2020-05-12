---
title: python script week 008 cat (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 008 cat'

Functions in program: 
* `def game():`
* `def sylls(text):`
* `def _print_words(lst, text):`
* `def _reverse(lst, n): # создаем из списка с начальными индексами слогов список с индексами, обозначающими конец каждого слога # n - длина слова`
* `def find_vowels(text):  # находим позиции, на которых находятся гласные`
* `def _cat_translate(syll):  # переводим человеческий слог в кошачий`

## python week 008 cat

Python example: week 008 cat

```python
vowels = "ауеёоияэюы"
sonants = "йрлмн"
paired = "кгпбдтжшзсь"

'''
СГ >> мя
СГС >> мяв
Г >> я
'''

def _cat_translate(syll):  # переводим человеческий слог в кошачий
  n_syll = len(syll)
  last_not_vowel = syll[-1] not in vowels
  if last_not_vowel:
    result = "мяв"
  elif n_syll != 1:
    result = "мя"
  else:
    result = 'я'
  return result

def find_vowels(text):  # находим позиции, на которых находятся гласные
  n = len(text)
  result = []
  for i in range(n):
    if text[i] in vowels:
      result.append(i)
  return result #   возвращаем список позиций (индексов), на которых находятся гласные в данном слове

def _reverse(lst, n): # создаем из списка с начальными индексами слогов список с индексами, обозначающими конец каждого слога # n - длина слова
  result = []
  for i in lst[1:]:
    result.append(i - 1)
  result.append(n)
  return result

def _print_words(lst, text):
  prev_end = 0
  result = ""
  cat_result = ""
  for i in lst:
    syll = text[prev_end:(i + 1)]
    result += syll + "-"
    cat_result += _cat_translate(syll) + '-'
    prev_end = i + 1
  result = result[:-1]
  cat_result = cat_result[:-1]
  print(result)
  print(cat_result)

def sylls(text):
  v_pos = find_vowels(text)
  n = len(text)
  true_sylls = []   # сюда будем запоминать измененные границы слогораздела
  prev_end = 0  # переменная, чтобы помнить, где заканчивается предыдущий слог
  for i in v_pos:             # для каждой гласной
    syll = text[prev_end:(i + 1)]   # выделим соответствующий ей "слог" (в данный момент он может не быть слогом с действительно)
    n_syll = len(syll)        # запомним его длину

    if n_syll > 2:            # если в "слоге" три и более букв, может быть необходимость поменять границу слогораздела
      if syll[0] in sonants and syll[1] in paired:
        if syll[1] != "ь":
          prev_end = prev_end + 1
        else:
          prev_end = prev_end + 2
    true_sylls.append(prev_end)
    prev_end = i + 1
  # print(true_sylls) # список индексов, соответствующих началу каждого слога
  true_sylls = _reverse(true_sylls, n)
  return true_sylls
  
def game():
  ask = input("Повтори за мной: ")
  if ask != "":
    _print_words(sylls(ask), ask)
    game()
  else:
    print("Вы ничего не спросили. Котик устал, урок окончен!")

game()  
    
'''
sylls('корова')
sylls('койка')
sylls('кот')
sylls('он')
sylls('программирование')
sylls('ария')
sylls('стелька')
sylls('уезжать')
sylls('привет')
sylls('ободок')
sylls('ночник')
sylls('изжить')
sylls('соломка')
sylls('бульон')
sylls('почтальон')
'''



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
