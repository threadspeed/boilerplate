---
title: python script ALGORITHM LAB Weighted Interval Scheduling (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB Weighted Interval Scheduling'

Functions in program: 
* `def findMaxProfit(joblist,n):`
* `def latestNonConflict(joblist,n):`

## python ALGORITHM LAB Weighted Interval Scheduling

Python mysql example: ALGORITHM LAB Weighted Interval Scheduling

```python
# Weighted Interval Scheduling

def latestNonConflict(joblist,n):
	for j in range(n-1,-1,-1):
		if joblist[j][1]<=joblist[n][0]:
			return j
	return -1


def findMaxProfit(joblist,n):
	table=[]
	for i in range(n):
		table.append(joblist[i][2])
	for i in range(1,n):
		inclprofit=joblist[i][2]
		l=latestNonConflict(joblist,i)
		if l!=-1:
			inclprofit=inclprofit+table[l]
		table.append((max(inclprofit,table[i-1])))
	result=max(table)
	return result

n=int(input("No of jobs:"))
joblist=[]
for i in range(n):
	s=int(input("Enter the start time:"))
	f=int(input("Enter the finish time"))/
	w=int(input("Enter the weight of the job"))
	joblist.append([s,f,w])
print(joblist)
print("Sorted joblist:")
for i in range(n):
	for j in range(n-i-1):
		if joblist[j][1] >joblist[j+1][1]:
			temp=joblist[j]
			joblist[j]=joblist[j+1]
			joblist[j+1]=temp
print(joblist)

print("Optimal profit is:", findMaxProfit(joblist,n))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
