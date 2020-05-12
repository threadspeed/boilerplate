---
title: python script pycharm test practice5 practice51 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pycharm test practice5 practice51'

Functions in program: 
* `def create_file():`

## python pycharm test practice5 practice51

Python mysql example: pycharm test practice5 practice51

```python
# i = 0
# if i <= 10:
#     i = i + 1
# def create_file():
#     file_path = 'E:/MyCodes/python/tmp/practice5'
#     full_path = file_path + str(i) + '.txt'
#     file = open(full_path,'w')
#     file.write(str(i))
#     file.close()
#     print(str(i),' files created')
# #create_file()
# i = 1
# if i < 11:
#     create_file()
#     i = i + 1
# ==============================================

def create_file():
    path = 'E:/MyCodes/python/tmp/practice5/'
    for name in range(1,11):
        with open(path + str(name) + '.txt' , 'w' ) as text:
            text.write(str(name))
            text.close()
            print(str(name) + ' Done!')
create_file()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
