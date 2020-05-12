---
title: python script exp Good one (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exp Good one'

Functions in program: 
* `def solve(x, y, c):`

## python exp Good one

Python example: exp Good one

```python
from Crypto.Util.number import *

enc = "5568805132927620915862961652915119205502564656170587178654125231161220625607540926896401096546698342568886941258210306584431194144941897964381622004367755249394250872087922576676409144449790059029381859185729426571175634174162864687636748588195830828723353334476423622404910269190260306288978339050977407035083644778247764945306764156900887854520481999652058760332985464811209439989757703438650513857873454169836287727668975248718567859201739917145994476350439430002816194907557441344087744129328521851711107645145482862861140859632619115308584677692"

length = len(enc)
sub_xy = enc[:length // 2]
sum_xy = enc[length // 2:]
num_sub_xy = int(sub_xy)
num_sum_xy = int(sum_xy)
assert num_sub_xy < num_sum_xy

x = (num_sum_xy + num_sub_xy) // 2
y = (num_sum_xy - num_sub_xy) // 2
# print("x:", x)
# print("y:", y)


def solve(x, y, c):
    if (y == 0):
        if (x == 1):
            print(c)
        return -1
    i = 9
    while x < y * i * i:
        i -= 1
    while i > 0:
        t = solve(y, x - y * i * i, c + [i])
        if (t != -1):
            return t
        i -= 1


# c = []
# solve(x, y, c)
c = [3, 2, 7, 5, 1, 7, 9, 4, 7, 5, 1, 7, 9, 1, 2, 8, 6, 8, 9, 3, 8, 2, 5, 8, 9, 2, 2, 1, 7, 5, 1, 7, 9, 6, 6, 4, 4, 7,
     5, 1, 7, 9, 7, 7, 7, 5, 1, 7, 9, 2, 8, 7, 1, 2, 7, 3, 1, 7, 6, 7, 8, 3, 8, 2, 1, 5, 4, 3, 4, 4, 5, 7, 3, 8, 4, 3,
     7, 5, 1, 7, 9, 6, 1, 3, 6, 6, 1, 7, 5, 1, 7, 9, 7, 5, 1, 7, 9, 2, 3, 7, 3, 2, 8, 2, 9, 6, 6, 6, 2, 2, 3, 2, 7, 5,
     1, 7, 9, 9, 7, 5, 1, 7, 9, 2, 7, 9, 9, 1, 6, 6, 9, 1, 5, 3, 6, 7, 5, 1, 7, 9, 7, 5, 1, 7, 9, 5, 1, 8, 2, 9, 2, 6,
     6, 9, 7, 5, 1, 7, 9, 5, 8, 5, 5, 8, 8, 7, 5, 1, 7, 9, 4, 6, 4, 2, 5, 7, 5, 1, 7, 9, 7, 5, 1, 7, 9, 2, 6, 5, 9, 7,
     5, 1, 7, 9, 8, 7, 7, 5, 1, 7, 9, 7, 9, 8, 2, 6, 2, 9, 2, 2, 5, 5, 9, 7]
cipher = "".join(str(x) for x in c)
print(cipher)

# find out the substring with the highest frequency
result_list = []
result_dict = {}
for i in range(2, len(cipher)):
    for j in range(len(cipher) - i + 1):
        result_list.append(cipher[j:j + i])
# print(result_list)
for i in range(len(result_list)):
    if result_list[i] in result_dict:
        result_dict[result_list[i]] += 1
    else:
        result_dict[result_list[i]] = 1
sorted_result = sorted(result_dict.items(), key=lambda x: x[1], reverse=True)
# print(sorted_result[:15])
msg = cipher.replace("75179", "0")
m = int(msg)
print(long_to_bytes(m))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
