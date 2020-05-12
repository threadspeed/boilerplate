---
title: python script m4 1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 1'


## python m4 1

Python mysql example: m4 1

```python
# Задание 1
# Считайте с диска файл с именем m4_1.py. Содержащаяся в нем
# программа 15 раз печатает на экране слово «Халва...» (убедитесь в этом,
# запустив программу). Модифицируйте программу так, чтобы:
# а) слово печаталось не 15, а 10 раз;
# б) перед первым словом печаталось слово «Начало», а после последнего
# – слово «Конец»;
# в) каждое слово не только печаталось с новой строки, но между ними была
# пустая строка;
# г) перед каждым словом «Халва...» печатался его порядковый номер,
# начиная с 1;
# д) перед каждым словом «Халва...» печатались 10 первых нечетных чисел

rangeSize = 10 # размер последовательности
oddNumber = '['+','.join(str(x) for x in range(1, rangeSize*2, 2))+']' # список нечетных цифр
for element in range(rangeSize):
    if element == 0:
        print('Начало\n')
    print(oddNumber, ', Порядковый номер =', element + 1,"Халва...\n")
    if element == rangeSize -1:
        print('Конец')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
