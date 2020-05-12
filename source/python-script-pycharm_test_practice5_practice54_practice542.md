---
title: python script pycharm test practice5 practice54 practice542 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pycharm test practice5 practice54 practice542'

Functions in program: 
* `def num_test():`

## python pycharm test practice5 practice54 practice542

Python mysql example: pycharm test practice5 practice54 practice542

```python
#coding = utf-8



"""
cn_mobile = [134,135,136,137,138,139,150,151,152,157,158,159,182,183,184,187,188,147,178,1705]
cn_union = [130,131,132,155,156,185,186,145,176,1709]
cn_tel=[133,153,180,181,189,177,1700]
"""

#答案
def num_test():
    cn_mobile = [134, 135, 136, 137, 138, 139, 150, 151, 152, 157, 158, 159, 182, 183, 184, 187, 188, 147, 178, 1705]
    cn_union = [130, 131, 132, 155, 156, 185, 186, 145, 176, 1709]
    cn_tel = [133, 153, 180, 181, 189, 177, 1700]
    you_num = input('Pleause input your number: ')
    first3 = int(you_num[0:3])
    first4 = int(you_num[0:4])
    if len(you_num) == 11:
        if first3 in cn_mobile or first4 in cn_mobile:
            print('operation: ChinaMobile')
            print('We \'re sending varification code via text to your phone:{}'.format(you_num))
        elif first3 in cn_union or first4 in cn_union:
            print('operation: ChinaUnion')
            print('We \'re sending msg via text to your phone:',you_num)
        elif first3  in cn_tel or first4 in cn_tel:
            print('operation: ChinaTelecom')
            print('We \'re sending msg via text to your phone: ',you_num)
        else: print('No such operator!')
    else:
        print('Invalid length, your number should be in 11 digits.')
        num_test()

num_test()




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
