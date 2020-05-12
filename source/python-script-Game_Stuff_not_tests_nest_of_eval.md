---
title: python script Game Stuff not tests nest of eval (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Game Stuff not tests nest of eval'


## python Game Stuff not tests nest of eval

Python example: Game Stuff not tests nest of eval

```python
__author__ = 'Gregorio Manabat III'

nested = 'print("LOLOL")'

for i in range(6):
    nested = nested.replace('\\', '\\\\')
    nested = nested.replace('\"', '\\\"')
    nested = "\"eval(0)\"".replace('0', nested)

nested = "eval(0)".replace('0', nested)
print(nested)

eval(""
"eval(\""
"eval(\\\""
"eval(\\\\\\\""
"eval(\\\\\\\\\\\\\\\""
"eval(\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\""
"eval(\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\""
"eval(""print(\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\"LOLOL\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\")"
")\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\""
")\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\""
")\\\\\\\\\\\\\\\""
")\\\\\\\""
")\\\""
")\""
")"
)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
