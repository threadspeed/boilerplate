---
title: python script mosaic (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mosaic'

Functions in program: 
* `def toPPM(pixels):`
* `def createColoredGrid(width, height, padding, nboxes, padding_color, colors):`

Modules used in program: 
* `import random`

## python mosaic

Python example: mosaic

```python
import random

def createColoredGrid(width, height, padding, nboxes, padding_color, colors):
	box_len = width // nboxes
	columns = (width // box_len) + 1

	row_colors = [colors[x % len(colors)] for x in range(columns)]

	pixels = []
	for y in range(height):
		if (y % box_len == 0):
			random.shuffle(row_colors)

		row = [padding_color] * width

		y_offset = y % box_len
		if (y_offset >= padding and y_offset <= box_len):
			for x in range(len(row)):
				x_offset = x % box_len
				if (x_offset < padding or x_offset > box_len):
					continue

				row[x] = row_colors[x // box_len]

		pixels.append(row)

	return pixels


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


if (__name__ == "__main__"):
	colors = [0xffa70f, 0xff4948, 0x700090, 0x878787, 0x8f3900]
	filler = 0x000000

	pixels = createColoredGrid(1600, 1000, 5, 50, filler, colors)

	ppm = toPPM(pixels)

	with open("output.ppm", "w") as fh:
		fh.write(ppm)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
