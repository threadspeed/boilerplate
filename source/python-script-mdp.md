---
title: python script mdp (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mdp'

Functions in program: 
* `def save(noise, name):`
* `def fromPPM(text):`
* `def toPPM(pixels):`
* `def smoothen(base):`
* `def create_noise(n):`
* `def mdp(base, r):`

Modules used in program: 
* `import json`
* `import random`

## python mdp

Python example: mdp

```python
import random

def mdp(base, r):
	# Calculate new dimensions
	n = len(base) * 2 - 1
	assert(n > 2)

	# Allocate
	copy = [[0 for _ in range(n)] for _ in range(n)]

	# Resize
	# 1 0 1
	# 0 0 0
	# 1 0 1
	for i in range(0, n, 2):
		for j in range(0, n, 2):
			copy[i][j] = base[i // 2][j // 2]

	# Diamond algorithm
	# 0 0 0
	# 0 1 0
	# 0 0 0
	for i in range(1, n, 2):
		for j in range(1, n, 2):
			# get surrounding values
			a = copy[i - 1][j - 1]
			b = copy[i - 1][j + 1]
			c = copy[i + 1][j - 1]
			d = copy[i + 1][j + 1]

			# average
			value = (a + b + c + d) // 4

			# random
			value += random.randint(-r, r)

			# clamp
			value = max(value, 0)
			value = min(value, 255)

			# store
			copy[i][j] = value

	# Square algorithm
	# 0 1 0
	# 1 0 1
	# 0 1 0
	for i in range(n):
		for j in range(i % 2 == 0, n, 2):
			a = 0
			b = 0
			c = 0
			d = 0

			# get surrounding values and account for edge cases
			if (i > 0): a = copy[i - 1][j]
			if (j > 0): b = copy[i][j - 1]
			if (i + 1 < n): c = copy[i + 1][j]
			if (j + 1 < n): d = copy[i][j + 1]

			# average
			value = a + b + c + d
			if (i == 0) or (j == 0) or (i + 1 == n) or (j + 1 == n):
				value //= 3
			else:
				value //= 4

			# random
			value += random.randint(-r, r)

			# clamp
			value = max(value, 0)
			value = min(value, 255)

			# store
			copy[i][j] = value

	return copy


def create_noise(n):
	return [[random.randint(0, 255) for _ in range(n)] for _ in range(n)]


def smoothen(base):
	n = len(base)
	for i in range(1, n - 1):
		for j in range(1, n - 1):
			base[i][j] = (
				base[i - 1][j - 1] + base[i - 1][j] + base[i - 1][j + 1] +
				base[i + 0][j - 1] + base[i + 0][j] + base[i + 0][j + 1] +
				base[i + 1][j + 1] + base[i + 1][j] + base[i + 1][j - 1]
			) // 9


def toPPM(pixels):
	height = len(pixels)
	width = len(pixels[0])

	buf = []
	buf.append("P3")
	buf.append("%i %i\n%i" % (width, height, 255))

	for row in pixels:
		for pixel in row:
			r = (pixel >> 16) & 0xFF
			g = (pixel >> 8) & 0xFF
			b = pixel & 0xFF

			buf.append("%i %i %i" % (r, g, b))

	return "\n".join(buf)


def fromPPM(text):
	lines = text.splitlines()
	
	width, height, _ = (int(x) for x in lines[1].split())
	pixels = [[0 for _ in range(width)] for _ in range(height)]
	
	lines = reverse(lines)
	for row in pixels:
		for i, pixel in enumerate(row)
			r, g, b = (int(x) for x in lines.pop().split())
			row[i] = (r << 16) & (g << 8) & b
	
	return pixels


import json

def save(noise, name):
	js = json.dumps(noise)

	with open(name + ".json", "w") as fh:
		fh.write(js)

	ppm = toPPM(noise)
	with open(name + ".ppm", "w") as fh:
		fh.write(ppm)


if (__name__ == "__main__"):
	noi = create_noise(32)
	save(noi, "0")

	for i in range(1, 6):
		onoi = noi
		noi = mdp(noi, 64 // i)
		save(noi, str(i))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
