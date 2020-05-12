---
title: python script maketoken (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'maketoken'

Functions in program: 
* `def main():`
* `def get_desired_smart(IV, desired, junk):`
* `def get_desired_naive(IV, desired, junk):`

## python maketoken

Python mysql example: maketoken

```python
#!/usr/bin/env python
from __future__ import print_function
from base64 import b64encode
from submarine import validate_token
from Crypto import Random


def get_desired_naive(IV, desired, junk):
	result = ''
	for N in range(0, len(desired)):
		for M in range(0, 0xFF):
			head = result + chr(M)
			tail = IV[N+1:]
			notjunk = head + tail
			token = b64encode(notjunk + junk)
			found = validate_token(token)
			if found[N] == desired[N]:
				result = head
				break
	return token


def get_desired_smart(IV, desired, junk):
	result = ''
	intermediate = validate_token(b64encode(IV + junk))
	for N in range(0, len(desired)):
		result += chr(ord(intermediate[N]) ^ ord(IV[N]) ^ ord(desired[N]))
	return b64encode(result + IV[len(result):] + junk)


def main():
	desired = 'david'
	rand_source = IV = Random.new()
	iv = rand_source.read(15)
	junk = rand_source.read(16)
	for N in range(0, 0xFF):
		result = validate_token(b64encode(iv + chr(N) + junk))
		if len(result) != len(desired):
			continue
		print(get_desired_naive(iv + chr(N), desired, junk))
		print(get_desired_smart(iv + chr(N), desired, junk))


if __name__ == "__main__":
	main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
