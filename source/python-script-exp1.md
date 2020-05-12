---
title: python script exp1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exp1'


## python exp1

Python example: exp1

```python
d=['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z']

s= input("Enter message:\t")
k= input("Enter key:\t")

k=k.upper()
key=[]
for i in range (len(k)):
    key.append(d.index(k[i]))  

pt=""
for word in s:
	pt=pt+word
pt=pt.upper()
ct=[]
for i in range (len(pt)):
    ct.append((d.index(pt[i])))
et=[]   
for i in range (len(ct)):
    ct[i]=(ct[i]+key[i%len(key)])%26
    et.append(ct[i])
code=""
for i in range (len(et)):
    et[i]=d[et[i]]
    code=code+et[i]
print("Coded text is:\t")
print(code)


et=[]
for i in range(len(code)):
    et.append(code[i])
for i in range(len(et)):
    et[i]=d.index(et[i])                       
dt=[]
for i in range (len(et)):
    et[i]=(et[i]-key[i%len(key)])%26
    dt.append(et[i])
decode=""
for i in range (len(dt)):
    dt[i]=d[dt[i]]
    decode=decode+dt[i]
print("Decoded text is:\t")
print(decode)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
