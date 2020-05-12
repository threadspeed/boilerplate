---
title: python script Number Basic (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Number Basic'


Modules used in program: 
* `import random`
* `import math`
* `import math`
* `import math`

## python Number Basic

Python example: Number Basic

```python
##########
# Arithmetic operation

(5 + 2 * 3 + (3 - 1) / 2 + 9) % 2
Out[1]: 1

2**2  # power
Out[2]: 4

4**0.5  # square root
Out[3]:# 2

8**(1/3)  # qubic root
Out[4]: 2

8e3 # 8 * 10^3
Out[5]: 8000

8E3 # 8 * 10^3
Out[6]: 8000
##########



##########
# Assign value to variables and get the summation

var1 = 6
var2 = 2
var1 + var2
Out[7]: 8
##########



##########
# Delete a variable

var1 = 6
var2 = 2
var3 = 3

var1
Out[8]: 6

del var1
var1
Out[9]: NameError: name 'var1' is not defined

del var2, var3  # to delete multiple variables at a time
##########



##########
# NUmber type conversion


# To integer
int(5.32)
Out[10]: 5


# To float
float(320)
Out[11]: 320.0

float(21684315646321568)
Out[12]: 2.168431564632157e+16


# To complex
complex(5)
Out[13]: (5+0j)

complex(5,2)
Out[14]: (5+2j)

complex(5,-2)
Out[15]: (5-2j)


# Absolute value
abs(-5)
Out[16]: 5

abs(-5.32)
Out[17]: 5.32
##########



##########
# Constants
# First, import 'math' module
import math


math.pi
Out[18]: 3.141592653589793

math.e
Out[19]: 2.718281828459045
##########



##########
# Mathematical functions
# First, import 'math' module
import math


# ceil(x): y | y (smallest) >= x and y is an integer
math.ceil(5.001)
Out[20]: 6

math.ceil(-5.001)
Out[21]: 5


# cmp(x,y): -1 if x < y, 0 if x == y, or 1 if x > y
# NOTE: Python 3 does not have cmp(x,y) attribute anymore
# In Python 3, use (a > b) - (a < b) to for this case
a = 3
b = 4
(a > b) - (a < b)
Out[22]: -1

a = 3
b = 3
(a > b) - (a < b)
Out[23]: 0

a = 3
b = 2
(a > b) - (a < b)
Out[24]: 1


# exp(x): exponential of x | e^x
math.exp(2)
Out[25]: 7.38905609893065


# fabs(x): absolute value
math.fabs(-2.32)
Out[26]: 2.32


# floor(x): y | y (largest) <= x and y is an integer
math.floor(2.32)
Out[27]: 2

math.floor(-2.32)
Out[28]: -3


# log(x): Natural logarithm (base e) for x when x>0
math.log(3)
Out[29]: 1.0986122886681098


# log10(x): Logarithm (base 10)  for x when x>0
math.log10(3)
Out[30]: 0.47712125471966244


# log2(x): Logarithm (base 2)  for x when x>0
math.log2(3)
Out[31]: 1.584962500721156


# max(x1, x2, x3, ...): Maximum value from the arguments
max(2,5,100)
Out[32]: 100

max(-2,-5,-100)
Out[33]: -2


# min(x1, x2, x3, ...): Minimum value from the arguments
min(2,5,100)
Out[34]: 2

min(-2,-5,-100)
Out[35]: -100


# modf(x): (y, z) | y is the fractional part and z is the integer part
math.modf(-2.1)
Out[36]: (-0.10000000000000009, -2.0)

math.modf(2.123)
Out[37]: (0.12300000000000022, 2.0)

math.modf(2)
Out[38]: (0.0, 2.0)


# pow(x, y): x**y
math.pow(2, 3)
Out[39]: 8

math.pow(-2, 2)
Out[40]: 4


# round(x [,n]): x rounded to n digits from the decimal point
round(2.5)
Out[41]: 2

round(2.51)
Out[42]: 3

round(2.5, 0)
Out[43]: 2.0

round(2.51, 0)
Out[44]: 3.0

round(2.5, 1)
Out[45]: 2.5

round(2.549, 1)
Out[46]: 2.5

round(2.559, 1)
Out[47]: 2.6

round(-2.549, 1)
Out[48]: -2.5

round(-2.559, 1)
Out[49]: -2.6


# sqrt(x): Square root
math.sqrt(25)
Out[50]: 5.0
##########



##########
# Trigonometric functions
# Note: The number π cannot be represented exactly as a floating-point number
# So in some cases we won't get the exact value of a trigonometric function
# sin(π) will not be exactly 0 for an example.
# First, import 'math' module
import math


# sin(x): x in radian
math.sin(0)
Out[51]: 0.0

math.sin(math.pi/2)
Out[52]: 1.0

math.sin(math.pi/6)
Out[53]: 0.49999999999999994 # 0.5

math.sin(math.pi)
Out[54]: 1.2246467991473532e-16 # 0


# cos(x): x in radian
math.cos(0)
Out[55]: 1.0

math.cos(math.pi)
Out[56]: -1.0

math.cos(math.pi/6)
Out[57]: 0.8660254037844387


# tan(x): x in radian
math.tan(0)
Out[58]: 0.0

math.tan(math.pi/4)
Out[59]: 0.9999999999999999 # 1

math.tan(math.pi/2)
Out[60]: 1.633123935319537e+16  # ∞ (infinity)


# asin(x): arc sine of x in radian (get the angle in radian from value)
math.asin(0)
Out[61]: 0.0

math.asin(.5)
Out[62]: 0.5235987755982989 # π/4

math.asin(1)
Out[63]: 1.5707963267948966 # π/2


# acos(x): arc cosine of x in radian (get the angle in radian from value)
math.acos(0)
Out[64]: 1.5707963267948966 # π/2

math.acos(1)
Out[65]: 0.0


# atan(x): arc tangent of x in radian (get the angle in radian from value)
math.atan(0)
Out[66]: 0.0


# atan2(y,x): atan(y/x) in radians
math.atan2(0,1)
Out[67]: 0.0

math.atan2(1,0)
Out[68]: 1.5707963267948966


# hypot(x,y): Euclidean norm, sqrt(x*x + y*y)
math.hypot(4,3)
Out[69]: 5.0


# degrees(x): Converts angle x from radian to degree
math.degrees(math.pi)
Out[70]: 180.0


# radians(x): Converts angle x from degree to radian
math.radians(180)
Out[71]: 3.141592653589793 # π
##########



##########
# Random number functions
# First, import 'random' module
import random


# choice(sequence): Choose a random element from a non-empty sequence
# sequence - this could be a list, tuple, or string

random.choice([1, 2, 3, 4, 5, 6])
Out[72]: 1

random.choice([1, 2, 3, 4, 5, 6])
Out[73]: 6

random.choice([1, 2, 3, 4, 5, 6])
Out[74]: 3

random.choice([1, 2, 3, 4, 5, 6])
Out[75]: 6

random.choice([1, 2, [1,2,3], 3, 4, 5, 6])
Out[76]: 5

random.choice([1, 2, [1,2,3], 3, 4, 5, 6, 'string'])
Out[77]: 1

random.choice([1, 2, [1,2,3], 3, 4, 5, 6, 'string'])
Out[78]: [1, 2, 3]

random.choice([1, 2, [1,2,3], 3, 4, 5, 6, 'string'])
Out[79]: 'string'

random.choice('string')
Out[80]: 'n'

random.choice('string')
Out[81]: 's'

random.choice((1, 2, 3))
Out[82]: 3

random.choice((1, 2, 3))
Out[83]: 1


# randrange(start, stop=None, step=1, _int=int):
# Choose a random item from range(start, stop[, step])
# default range step is 1

random.randrange(2) # from 0 -> 2, except 2
Out[84]: 0

random.randrange(2) # from 0 -> 2, except 2
Out[85]: 1

random.randrange(2, 5)  # from 0 -> 5 , except 5, default step is 1
Out[86]: 3

random.randrange(2, 5)  # from 0 -> 5 , except 5, default step is 1
Out[87]: 4

random.randrange(2, 5, 2) # from 0 -> 5 , except 5, step is 2
Out[88]: 2

random.randrange(2, 5, 2) # from 0 -> 5 , except 5, step is 2
Out[89]: 4


# random(): x in the interval [0, 1)

random.random()
Out[90]: 0.8305635327570792

random.random()
Out[91]: 0.48515494046308605


# uniform(x,y): r | x <= r < y

random.uniform(5, 10)
Out[92]: 8.943616755677565

random.uniform(5, 10)
Out[93]: 5.469297933871174

random.uniform(5, -10)
Out[94]: 4.574787852169905

random.uniform(-5, -10)
Out[95]: -9.178825519599348
##########

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
