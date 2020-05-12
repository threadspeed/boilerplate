---
title: python script m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 7 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'm4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 7'


## python m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 7

Python example: m4 %25D0%25B4%25D0%25BE%25D0%25BF.%25D0%25B7%25D0%25B0%25D0%25B4%25D0%25B0%25D0%25BD%25D0%25B8%25D0%25B5 7

```python
#7. Гуси и кролики. У гусе и кроликов 2n лап. Сколько может быть гусей и
#кроликов (вывести все возможные сочетания)?

print("Программа подсчета кол-ва гусей и кролей")

n = int(input("Введите число N: "))
print('Всего лап:', 2 * n);

g = (2*n % 4) / 2;
k = (2*n - 2*g) / 4;

print("%6s %16s" % ("Гуси", "Кролики"));

while k != 0:
    print("%5s %15s" % (int(g), int(k)));
    g += 2;
    k -= 1;

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
