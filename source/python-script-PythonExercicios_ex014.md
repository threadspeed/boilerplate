---
title: python script PythonExercicios ex014 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex014'


## python PythonExercicios ex014

Python example: PythonExercicios ex014

```python
c = float(input('Informe a temperatura em °C: '))
f = (c / 5) * 9 + 32
# Também poderia ser feito da seguinte forma: f = ((9 * c) / 5) + 32
# OU f = 9 * c / 5 + 32
# Nesse último caso, foi tirado os parênteses pois foi aplicado a ordem de precedência. Levando em
# consideração que primeiro vai ser feito a multiplicação, após, o resultado vai ser dividido por 5
# e por último o resultado vai ser somado a 32.
k = c + 273
print('A temperatura de {}°C corresponde a {:.1f}°F e {:.1f}°K!'.format(c, f, k))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
