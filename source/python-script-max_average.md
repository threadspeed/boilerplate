---
title: python script max average (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'max average'

Functions in program: 
* `def highest_average(students):`

Modules used in program: 
* `import random`

## python max average

Python example: max average

```python
# zakładam input w formie listy list stringów i intów, gdzie każda podlista to ["imię", ocena, ocena, ocena, ocena]
import random
from collections import defaultdict
def highest_average(students):
    averages = defaultdict(int)
    for student in students:
        name = student[0]
        grades = student[1:]
        avg = sum(grades) // len(grades)
        averages[name] = avg
        print(f"{name} : {avg}")
    return max(averages, key=averages.get)

if __name__ == "__main__":
    test_case = []
    grade_length = random.randint(2, 20)
    test_count = int(input("Input test count: "))
    for i in range(test_count):
        builder = []
        builder.append(f"Student {i+1}")
        for i in range(grade_length):
            builder.append(random.randint(1, 100))
        test_case.append(builder)
    print(highest_average(test_case))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
