---
title: python script pycharm test practice5 loop-login-2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pycharm test practice5 loop-login-2'

Functions in program: 
* `def account_login():`

## python pycharm test practice5 loop-login-2

Python example: pycharm test practice5 loop-login-2

```python
# def account_login():
#     passwd = input('Password:')
#     if passwd == '123':
#         print('Login Success!')
#     else:
#         print('Wrong password or invalid input!')
#         account_login()
#
# account_login()

#######
passwd_list = ['reset','123']
#使用bool型
def account_login():
    tries = 3
    while tries > 0:
        passwd = input('Password:')
        passwd_correct = passwd == passwd_list[-1]
        passwd_reset = passwd == passwd_list[0]
        if passwd_correct:
            print('Login Success!')
            break
        elif passwd_reset:
            new_passwd = input('Enter your NEW password:')
            passwd_list.append(new_passwd)
            print('Your password has changed successfully!')
            account_login()
        else:
            print('Wrong password or invalid input! Please correct your input!')
            tries = tries -1
            print(tries,'times left')
    else:
        print('Your account has been suspended')
#调用函数
account_login()





```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
