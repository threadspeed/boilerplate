---
title: python script TrainTestDataGenForPRNG Factoring9-8 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'TrainTestDataGenForPRNG Factoring9-8'

Functions in program: 
* `def int_to_onehotlist(int_var = 0):`
* `def int_to_binlist(int_var = 0):`
* `def gen_train_test_data(csprn_list):`
* `def gen_CSPRN_list(loop_limit = pow(2,8)): # Reduced to avoid multivalued function and long training time`
* `def gen_key(p_value_thre = 0.00000005):`

Modules used in program: 
* `import csv`
* `import functools as func`
* `import numpy as np`
* `import random`

## python TrainTestDataGenForPRNG Factoring9-8

Python example: TrainTestDataGenForPRNG Factoring9-8

```python
#!pip install Pycryptodome

import random
import numpy as np
from scipy import stats
from Crypto.Cipher import AES
from Crypto.Util import Counter
from Crypto import Random
import functools as func
#import pandas as pd
import csv

# Key Generation with p-value < 0.0000000005 under K-S test
def gen_key(p_value_thre = 0.00000005):
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
  return key, p_value

print(gen_key())

# Generate CSRN List using AES CTR mode
def gen_CSPRN_list(loop_limit = pow(2,8)): # Reduced to avoid multivalued function and long training time
  # pow(2,15) is for generating more than 2,000,000 train and test data, respectively
  arr = []
  input = 0
  nonce = Random.get_random_bytes(4)
  ctr = Counter.new(64, prefix=nonce, suffix=b'ABCD', little_endian=True, initial_value=10)
  key, p_value = gen_key()
  cipher = AES.new(key.to_bytes(16, 'little'), AES.MODE_CTR, counter=ctr)
  for cnt in range(0,loop_limit):
    ciphertext = cipher.encrypt(input.to_bytes(16, 'little'))
    txt = int.from_bytes(ciphertext, 'little')
    bin_txt = '{0:0128b}'.format(txt)
    arr.append(bin_txt)
  return(arr)

arr = gen_CSPRN_list()
print(type(arr))
print(arr[20])
print(arr[21])

# Generate train/test data
#   train/test input data: 
#     get every 9 bit by 1 bit rightshift from the begining of flattened 'arr'
#   train/test output data: 
#     get every 8 bit, where
#       - first 7 bit is from last part of the above 9 bit
#       - last  1 bit is from the next bit to the above 9 bit
def gen_train_test_data(csprn_list):
  train_in  = []
  train_out = []
  test_in   = []
  test_out  = []
  upper = len(csprn_list) - 1
  thre = upper/2
  for cnt in range(0,upper):
    k = cnt
    train_source0 = list(csprn_list[k])
    for i in range(0,118):
      i_t = train_source0[i:i+9]
      o_t = train_source0[i+2:i+10]
      train_i_num = func.reduce(lambda x,y:x*2+int(y), i_t, 0)
      train_o_num = func.reduce(lambda x,y:x*2+int(y), o_t, 0)
      if (cnt < thre):
        train_in.append(train_i_num)
        train_out.append(train_o_num)
      else :
        test_in.append(train_i_num)
        test_out.append(train_o_num)
      train_source1 = list(csprn_list[k+1])
    for i in range(118,127):
      i_j = 9 - (127 - i)
      i_t = train_source0[i:127] + train_source1[0:i_j]
      o_i = 0
      o_j = 8 - (127 - i - 2)
      if(i == 126) :
          o_j = 8
      if(i == 127) :
          o_i = 1
          o_j = 9
      o_t = train_source0[i+2:127] + train_source1[o_i:o_j]
      train_i_num = func.reduce(lambda x,y:x*2+int(y), i_t, 0)
      train_o_num = func.reduce(lambda x,y:x*2+int(y), o_t, 0)
      if (cnt < thre):
        train_in.append(train_i_num)
        train_out.append(train_o_num)
      else :
        test_in.append(train_i_num)
        test_out.append(train_o_num)
  return train_in, train_out, test_in, test_out

train_in, train_out, test_in, test_out = gen_train_test_data(arr)
#print(train_in)
print(len(train_in), len(test_in))
#print(train_out)
print(len(train_out), len(test_out))

# Each input data train_in/test_in is converted to a list of int32
def int_to_binlist(int_var = 0):
  tmp = '{0:09b}'.format(int_var)
  bin_l = list(tmp)
  #bin_list = [int(i) for i in bin_l]
  bin_list = [int(i) for i in bin_l]
  return bin_list

# This is obsoluted!
# Each output data train_out/test_out is converted to a onehot list of int32
def int_to_onehotlist(int_var = 0):
  onehot_list = []
  for i in range(0,256):
    #onehot_list.append(float(0))
    onehot_list.append(int(0))
  if(int_var != 0):
    #onehot_list[int_var - 1] = float(1)
    onehot_list[int_var - 1] = int(1)
  return onehot_list

for elm in train_in[120:129]:
  print(int_to_binlist(elm))
  
#for elm in train_out[120:129]:
#  onehot_list = int_to_onehotlist(elm)
#  print(elm, len(onehot_list), onehot_list[elm-1])
#  print(onehot_list)

list1 = []
for i in range(0,9):
    list1.append('in{}'.format(i))
list1.append('out')
print(list1)

# Training data csv file (DataFrame Format for Pandas)
# As input data space is pow(2,9) while output space is pow(2,8),
# too many training data set may contain more than one same 
# imputs data value with different output data value. This requires
# multivalued function which cannot be approximated by any neural
# network. Amount of training data must therefore be not too learge
# compared with pow(2,9).
with open('dataset_9-8_1.csv', 'w') as f:
    writer = csv.writer(f, lineterminator='\n') # 改行コード（\n）を指定しておく
    writer.writerow(list1)     # list（1次元配列）の場合
    i = 0
    for elm in train_in[0:2048]:
        list2 = int_to_binlist(elm)
        list2.append(train_out[i])
        writer.writerow(list2)
        i = i + 1

# Test data csv file (DataFrame Format for Pandas)
# As we will investigate asymptotics of next bit prediction probabilities,
# test data must be large enough.
with open('dataset_9-8_2.csv', 'w') as f:
    writer = csv.writer(f, lineterminator='\n') # 改行コード（\n）を指定しておく
    writer.writerow(list1)     # list（1次元配列）の場合
    j = i
    for elm in train_in[2048:]:
        list2 = int_to_binlist(elm)
        list2.append(train_out[j])
        writer.writerow(list2)
        j = j + 1
    i = 0
    for elm in test_in:
        list2 = int_to_binlist(elm)
        list2.append(test_out[i])
        writer.writerow(list2)
        i = i + 1

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
