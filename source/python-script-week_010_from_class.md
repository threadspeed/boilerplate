---
title: python script week 010 from class (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 010 from class'


## python week 010 from class

Python mysql example: week 010 from class

```python
# 0

group = s.split('\n')

# 1

ngroup = len(group) # number of people
print(ngroup)

# 2

n = int(input('Enter n:\n'))
print(group[n - 1]) # n-th person

# 3

nfirst = group[:n]
print(nfirst)

# 4

group_new = []
for i in group:
  group_new.append(i.split('. '))

print(group_new[0])

# 5

for i in group_new:
  if int(i[0]) % 10 == 2:
    print(i)
    
# 6
    
just_names = []
for i in group_new:
  just_names.append(i[1])
  
print(just_names[0])

# 7

### surname, name

group_names = []
for i in just_names:
  group_names.append(i.split())
  
print(group_names[0])
  
### name, surname
  
group_names_rev = []
for i in group_names:
  group_names_rev.append(i[::-1])

print(group_names_rev[0])

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
