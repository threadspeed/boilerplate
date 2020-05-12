---
title: python script find difference (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'find difference'

Functions in program: 
* `def naive_find_smallest_difference(hours):`
* `def parse_and_sanitize(hours):`
* `def map_differences(hours):`
* `def find_smallest_difference(hours):`

Modules used in program: 
* `import random`

## python find difference

Python example: find difference

```python
import random

def find_smallest_difference(hours):
    print(hours)
    hours = parse_and_sanitize(hours)
    differences = map_differences(hours)
    print(min(differences))
    return min(differences)

def map_differences(hours):
    sorted_hours = sorted(hours)
    differences = []
    for i in range(len(sorted_hours)-1):
        differences.append(sorted_hours[i+1] - sorted_hours[i])
    differences.append(abs(1440 - sorted_hours[-1] + sorted_hours[0]))
    return differences

def parse_and_sanitize(hours):
    parsed_hours = []
    for hour in hours:
        hour = hour.split(':')
        if 0 <= int(hour[0]) <= 24 and 0 <= int(hour[1]) <= 60:
            parsed_hours.append(int(hour[0])*60 + int(hour[1]))
        else:
            continue
    return parsed_hours

def naive_find_smallest_difference(hours):
    hours = parse_and_sanitize(hours)
    smallest = 1440
    hours = sorted(hours)
    for i in range(len(hours)-1):
        for y in range(i+1, len(hours)):
            diff = abs(hours[i] - hours[y])
            if diff < smallest:
                smallest = diff
    print(min(abs(hours[0] + abs(1440 - hours[-1])), smallest))
    return min(abs(hours[0] - abs(1440 - hours[-1])), smallest)


if __name__ == "__main__":
    test_times = input("How many times to tests? ")
    test_length = int(input("How many items to test on? "))
    for y in range(int(test_times)):
        random.seed(a=None)
        test_case = []
        for i in range(test_length):
            test_case.append(str(f"{random.randint(0, 23):02d}:{random.randint(0, 59):02d}"))
        if naive_find_smallest_difference(test_case) != find_smallest_difference(test_case):
            print(f"Error, naive returned {naive_find_smallest_difference(test_case)}, while normal returned {find_smallest_difference(test_case)}")
            print(f"Data set: {test_case}")
            break
        else:
            print("OK")
            
    edge_case = ["00:01", "12:12", "12:24", "17:28", "02:53", "19:19", "23:58"]
    print(find_smallest_difference(edge_case) == naive_find_smallest_difference(edge_case))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
