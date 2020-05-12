---
title: python script prng example (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'prng example'


Modules used in program: 
* `import numpy as np`
* `import random`

## python prng example

Python example: prng example

```python
#!pip install Pycryptodome

import random
import numpy as np
from scipy import stats

# Key Generation with p-value < 0.0000000005 using K-S test
p_value = 1
while (p_value > 0.00000005):
  #getting systemRandom instance out of random class
  systemRandom = random.SystemRandom()
  #SystemRandom.randint()
  key = systemRandom.randint(0,pow(2,128)-1)
  tmp = '{0:0128b}'.format(key)

  key_l = list(tmp)
  key_li = [float(i) for i in key_l]
  key_list = np.array(key_li)

  p_value = stats.kstest(key_list, "uniform").pvalue

print(p_value)

# Generate CSRN using AES CTR mode
from Crypto.Cipher import AES
from Crypto.Util import Counter
from Crypto import Random

arr = []
input = 0
nonce = Random.get_random_bytes(4)
ctr = Counter.new(64, prefix=nonce, suffix=b'ABCD', little_endian=True, initial_value=10)
cipher = AES.new(key.to_bytes(16, 'little'), AES.MODE_CTR, counter=ctr)

for cnt in range(0,15):
  ciphertext = cipher.encrypt(input.to_bytes(16, 'little'))
  txt = int.from_bytes(ciphertext, 'little')
  bin_txt = '{0:0128b}'.format(txt)
  print(bin_txt)
  arr.append(txt)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
