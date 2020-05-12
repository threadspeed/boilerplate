---
title: python script practice python ex.16 password generator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'practice python ex.16 password generator'

Functions in program: 
* `def pw_gen(size = 8, chars=string.ascii_letters + string.digits + string.punctuation):`
* `def gen_psw():`

Modules used in program: 
* `import random`
* `import string`

## python practice python ex.16 password generator

Python example: practice python ex.16 password generator

```python
#http://www.practicepython.org/exercise/2014/05/28/16-password-generator.html



def gen_psw():
  import random
  
  origin_weak = "abcdefghijklmnop1234567890"
  origin_average = "abcdefghijklmnop1234567890ABCDEFGHIJKLMNOP*"
  origin_strong = "abcdefghijklmnop1234567890ABCDEFGHIJKLMNOP!@#$%^&*"
  len_pw_weak = 8 
  len_pw_average = 16 
  len_pw_strong = 32 
  
  pswd_ans = input("What strength password do you want?  Weak, Average or Strong \n")
  pswd_ans = pswd_ans.lower()

  if pswd_ans == "weak":
    pswd =  "".join(random.sample(origin_weak,len_pw_weak ))
    print((pswd))
  elif pswd_ans == "average":
    pswd =  "".join(random.sample(origin_average,len_pw_average ))
    print((pswd))
  elif pswd_ans == "strong":
    pswd =  "".join(random.sample(origin_strong,len_pw_strong ))
    print((pswd))
  
  
gen_psw()


"""Another Solution from the site: 

import string
import random

def pw_gen(size = 8, chars=string.ascii_letters + string.digits + string.punctuation):
	return ''.join(random.choice(chars) for _ in range(size))

print(pw_gen(int(input('How many characters in your password?'))))

"""

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
