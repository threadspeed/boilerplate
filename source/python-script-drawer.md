---
title: python script drawer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'drawer'

Functions in program: 
* `def draw(code):`
* `def _bench(current=''):`

Modules used in program: 
* `import math`
* `import sys`
* `import time`

## python drawer

Python mysql example: drawer

```python
#!/usr/bin/env python
# -*- encoding: utf-8 -*-

from PIL import Image, ImageDraw, ImageFont, ImageFilter
# from utils import Config
from random import random as frand
from Crypto.Random import random
# import random
# from utils.URI import join
import time
import sys
import math

SCALE=3
WIDTH=120
HEIGHT=48
SHAPES=6
DISTORTION=2
DOTS=0.05
LINES=3
LINE_SEGS=3
NOISE=2
DEF_COLOR=(240, 240, 240, 255) # RGBA
BG_COLOR = (192, 224)
BG_TRANSPARENCY = (160, 192)
FONT_COLOR = (120, 168)
FONT_TRANSPARENCY = (224, 255)
FONT_NAME = 'SF_Arch_Rival.ttf'
FONT_ANG2 = (0, 900) # ang ** 2
# Debug only, since import settings requires whole project to be loaded.
FONT_PATH = '/home/eve/MCA2/Resources/Fonts/SF_Arch_Rival.ttf'
# FONT_PATH = join(settings.BASE_DIR, 'Resources', 'Fonts', FONT_NAME)
FONT_SIZE = 42
PERTURBATION = 0.85

_start_clock, _start_time = time.clock(), time.time()
_prev_clock, _prev_time = -1, -1

def _bench(current=''):
	global _prev_clock, _prev_time
	cur_clock, cur_time = time.clock(), time.time()
	if _prev_clock > 0:
		print('Benchmark for %s:' % current)
		print('CPU Time: %.6f seconds' % ( cur_clock - _prev_clock ))
		print('Real Time: %.6f seconds' % ( cur_time - _prev_time ))
		
	_prev_clock, _prev_time = cur_clock, cur_time

def draw(code):
	# TODO: Implements the draw method.
	
	# Create two image instance
	
	_bench()
	
	height, width = int(SCALE * HEIGHT), int(SCALE * WIDTH)
	
	img = Image.new('RGBA', (width, height), DEF_COLOR)
	empty = Image.new('RGBA', (width, height), (255, 255, 255, 0)) # Transparent
	
	_bench('create image')
	
	# First, fill some random quadrilateral to the background
	
	# draw = ImageDraw.Draw(img)
	
	ru, rb, rl, rr = (0, height * 3 / 8 - 1), (height * 3 / 8, height * 3 / 4 - 1), (0, width / 5 - 1), (width * 2 / 5, width * 4 / 5 - 1)
	
	for i in range(SHAPES):
	
		dh = height * i / 4 / ( SHAPES - 1 )
		dw = width * i / 5 / ( SHAPES - 1 )
	
		dot1 = random.randint(*rl) + dw, random.randint(*ru) + dh
		dot3 = random.randint(*rr) + dw, random.randint(*rb) + dh
		
		color = random.randint(*BG_COLOR), random.randint(*BG_COLOR), random.randint(*BG_COLOR), random.randint(*BG_TRANSPARENCY)
		# tr = random.randint(*RECTANGLE_TRANSPARENCY)
		
		tmp = empty.copy()
		draw = ImageDraw.Draw(tmp)
		
		if random.randint(0, 31) & 3 == 0:
			dot2 = random.randint(*rr) + dw, random.randint(*ru) + dh
			dot4 = random.randint(*rl) + dw, random.randint(*rb) + dh
			draw.polygon([dot1, dot2, dot3, dot4], outline=color, fill=color)
		else:
			draw.ellipse([dot1, dot3], outline=color, fill=color)
		
		img = Image.alpha_composite(img, tmp)
		
	_bench('draw polygon & ellipse')
		
	# Draw noise
	
	fnt = ImageFont.truetype(FONT_PATH, size=FONT_SIZE * SCALE)
	fnt_color = random.randint(*FONT_COLOR), random.randint(*FONT_COLOR), random.randint(*FONT_COLOR), random.randint(*FONT_TRANSPARENCY)
	
	tmp = empty.copy()
	draw = ImageDraw.Draw(tmp)
	
	if NOISE > 0:
		cnt = NOISE * 15 * SCALE
		edge_reserve = 10 * SCALE
		SIZE = int(1.2 * SCALE), int(2.4 * SCALE)
		while cnt:
			x, y, sz = random.randint(edge_reserve, width - edge_reserve), random.randint(edge_reserve, height - edge_reserve), random.randint(*SIZE)
			draw.arc((x - sz, y - sz, x + sz, y + sz), 0, 360, fill=fnt_color)
			# draw.arc((x - sz - 1, y - sz - 1, x + sz + 1, y + sz + 1), 0, 360, fill=fnt_color)
			cnt -= 1
			
	img = Image.alpha_composite(img, tmp)
	
	_bench('draw noise')
		
	# Next, draw the text.
	
	delta = width * 1 / 8
	tmp = empty.copy()
	
	for idx in range(len(code)):
		
		xpos = delta + width * 2 * idx / len(code) / 3

		# draw = ImageDraw.Draw(tmp)

		
		size = list(draw.textsize(code[idx], font=fnt))
		# Kind of shity
		size[1] += FONT_SIZE * SCALE / 5
		
		chimg = Image.new('RGBA', size)
		ImageDraw.Draw(chimg).text((0, -FONT_SIZE * SCALE / 8), code[idx], font=fnt, fill=fnt_color)
		ang = int(math.sqrt(random.randint(*FONT_ANG2)))
		if random.randint(0, 31) & 1:
			ang = -ang
		tmp.paste(chimg.rotate(ang, resample=Image.BICUBIC, expand=True), box=(xpos, 0))

		# draw.text((xpos, 0), code[idx], font=fnt, fill=fnt_color)
	
		img = Image.alpha_composite(img, tmp)
		
	_bench('draw font')
	R = [
			[
				random.randint(int(width * 0.3), int(width * 0.7)),
				random.randint(int(height * 0.3), int(height * 0.7)),
				random.randint(int(height * 0.3), int(height * 0.4)),
				(-frand() * 0.15) - 0.15,
			]
			for _ in range(DISTORTION)
	]
	
	for r in R:
		r.append(r[2] * r[2])
	
	# origimg = img.copy()
	# finalimg = img.resize((WIDTH, HEIGHT), resample=Image.ANTIALIAS)
	
	data = tuple(img.getdata())
	finaldata = list(data)
	
	iy = 0
	cnt = 0
	while iy < height:
		ix = 0
		while ix < width:
			cx, cy = ix, iy
			for r in R:
				dx, dy = ix - r[0], iy - r[1]
				r2 = dx * dx + dy * dy
				# if r2 >= r[2] * r[2]:
				if r2 >= r[4]:
					continue
				rscale = r[3] * math.sin(math.pi * math.sqrt(r2) / r[2])
				cx += dx * rscale
				cy += dy * rscale
			cx, cy = int(cx + 0.5), int(cy + 0.5)
			if 0 <= cy < height and 0 <= cx < width:
				# pix = origimg.getpixel((cx, cy))
				# pix = data[cy * width + cx]
				# img.putpixel((ix , iy), pix)
				# finaldata[iy * width + ix] = pix
				finaldata[cnt] = data[cy * width + cx]
			ix += 1
			cnt += 1
		iy += 1
		
	img.putdata(finaldata)
	
	_bench('distortion')
	img = img.filter(ImageFilter.GaussianBlur(int(1.5 * SCALE)))
	
	_bench('Gaussian blur')
				
	img.resize((WIDTH, HEIGHT), resample=Image.ANTIALIAS).save('/tmp/tmp.png')
	
	_bench('save')
	# finalimg.save('/tmp/tmp.png')


if __name__ == '__main__':
	valid_chars = 'ABCDEFGHIJKLMPQRSTUVWXYZ123456789'
	# start = time.time()
	code = ''.join([random.choice(valid_chars) for _ in range(4)])
	print('Code = ' + code)
	draw(code)
	print('Total CPU: %.6f seconds' % (_prev_clock - _start_clock))
	print('Total Time: %.6f seconds' % (_prev_time - _start_time))
	# stop = time.time()
	# print(stop - start)
	import os
	os.system(' ( xdg-open /tmp/tmp.png > /dev/null 2>&1 & ) & ')
	


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
