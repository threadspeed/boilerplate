---
title: python script Ruido (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ruido'

Functions in program: 
* `def filtroPromedio(imagen):`
* `def filtroGrisesPromedio(imagen):`
* `def bordesPorResta(im, imagen2):`
* `def quitarRuidoPorVecindad(imagen):`
* `def generarRuido(m, porcentaje):`
* `def filtroPromedio(imagen):`
* `def filtroGrisesPromedio(imagen):`
* `def bordesPorResta(im, imagen2):`
* `def quitarRuidoPorVecindad(imagen):`
* `def generarRuido(m, porcentaje):`

Modules used in program: 
* `import random as R`
* `import random as R`

## python Ruido

Python mysql example: Ruido

```python
from sys import argv
from PIL import Image as I
import random as R


def generarRuido(m, porcentaje):
	imagenConRuido = m
	p = m.load()
	x,y = m.size
	totalPixeles = x * y
	pixelesMarcados = totalPixeles * porcentaje
	pixelesMarcados = pixelesMarcados / 100
	print(pixelesMarcados)
	for i in range(int(pixelesMarcados)):
		pxx = R.randrange(0,x)
		pxy = R.randrange(0,y)
		sop = R.uniform(0,1)
		pixel = ''
		if(sop > .5):
			pixel = (255,255,255)
		else:
			pixel = (0,0,0)
		imagenConRuido.putpixel((pxx,pxy),pixel)
	imagenConRuido.show()
	quitarRuidoPorVecindad(imagenConRuido)

def quitarRuidoPorVecindad(imagen):
	m = []
	imagen = imagen.convert('RGB')
	x,y = imagen.size
	pixeles = imagen.load()
	c = 1
	for i in range(x):
		for j in range(y):
			px = pixeles[i,j]
			b = px[0]
			if(b == 255 or b == 0):
				m.append((i,j))
				c = 0
				try:
					p1 = pixeles[i+1,j]
					c += 1
				except:
					p1 = (0,0,0)
				try:
					p2 = pixeles[i-1,j]
					c += 1
				except:
					p2 = (0,0,0)
				try:
					p3 = pixeles[i,j+1]
					c += 1
				except:
					p3 = (0,0,0)
				try:
					p4 = pixeles[i,j-1]
					c += 1
				except:
					p4 = (0,0,0)
			
				if(c > 4): 
					c = 4
				r = (p1[0] + p2[0] + p3[0] + p4[0])
				g = (p1[0] + p2[0] + p3[0] + p4[0]) 
				b = (p1[0] + p2[0] + p3[0] + p4[0])
				pxnvo = (r/c,g/c,b/c)
				imagen.putpixel((i,j),pxnvo)
				c = 0
	#SEGUNdA PASADA
	fi = imagen.load()
	for e in m:
		c = 0
		pixel = fi[e]
		i,j = e
		try:
			p1 = fi[i+1,j]
			c += 1
		except:
			p1 = (0,0,0)
		try:
			p2 = fi[i-1,j]
			c += 1
		except:
			p2 = (0,0,0)
		try:
			p3 = fi[i,j+1]
			c += 1
		except:
			p3 = (0,0,0)
		try:
			p4 = fi[i,j-1]
			c += 1
		except:
			p4 = (0,0,0)			
		r = (p1[0] + p2[0] + p3[0] + p4[0])
		g = (p1[0] + p2[0] + p3[0] + p4[0]) 
		b = (p1[0] + p2[0] + p3[0] + p4[0])
		pxnvo = (r/c,g/c,b/c)
		imagen.putpixel((i,j),pxnvo)
		c = 0
	imagen.show()
	return imagen

def bordesPorResta(im, imagen2):
	x,y = im.size
	m1 = im.load()
	m2 = imagen2.load()
	imb = I.new('RGB',(x,y))
	for i in range(x):
		for j in range(y):
			r = m1[i,j][0] - m2[i,j][0]
			g = m1[i,j][1] - m2[i,j][1]
 			b = m1[i,j][2] - m2[i,j][2]
			pixel = (r,g,b)
			imb.putpixel((i,j),pixel)
	imb.show()

def filtroGrisesPromedio(imagen):
	x, y = imagen.size
	px = imagen.load()
	imagenGrises = I.new('RGB',(x,y))
	for i in range(x):
		for j in range(y):
			pixeles = px[i,j]
			prom = sum(pixeles) / 3
			imagenGrises.putpixel((i,j),(prom,prom,prom))
	return imagenGrises

def filtroPromedio(imagen):
	x,y = imagen.size
	pixeles = imagen.load()
	imagenFiltrada = I.new('RGB',(x,y))
	c = 1
	for i in range(x):
		for j in range(y):
			px = pixeles[i,j]
			try:
				p1 = pixeles[i+1,j]
				c += 1
			except:
				p1 = (0,0,0)
			try:
				p2 = pixeles[i-1,j]
				c += 1
			except:
				p2 = (0,0,0)
			try:
				p3 = pixeles[i,j+1]
				c += 1
			except:
				p3 = (0,0,0)
			try:
				p4 = pixeles[i,j-1]
				c += 1
			except:
				p4 = (0,0,0)
			
			if(c > 4): 
				c = 4
			r = p1[0] + p2[0] + p3[0] + p4[0]
			g = p1[0] + p2[0] + p3[0] + p4[0]
			b = p1[0] + p2[0] + p3[0] + p4[0]
			
			imagenFiltrada.putpixel((i,j),(r/c,g/c,b/c))
			c = 0
	return imagenFiltrada
		
m = I.open(argv[1])
gris = filtroGrisesPromedio(m)
bordesPorResta(gris,filtroPromedio(filtroPromedio(gris)))
pruido = float(argv[2])
generarRuido(m, pruido)from sys import argv
from PIL import Image as I
import random as R


def generarRuido(m, porcentaje):
	imagenConRuido = m
	p = m.load()
	x,y = m.size
	totalPixeles = x * y
	pixelesMarcados = totalPixeles * porcentaje
	pixelesMarcados = pixelesMarcados / 100
	print(pixelesMarcados)
	for i in range(int(pixelesMarcados)):
		pxx = R.randrange(0,x)
		pxy = R.randrange(0,y)
		sop = R.uniform(0,1)
		pixel = ''
		if(sop > .5):
			pixel = (255,255,255)
		else:
			pixel = (0,0,0)
		imagenConRuido.putpixel((pxx,pxy),pixel)
	imagenConRuido.show()
	quitarRuidoPorVecindad(imagenConRuido)

def quitarRuidoPorVecindad(imagen):
	m = []
	imagen = imagen.convert('RGB')
	x,y = imagen.size
	pixeles = imagen.load()
	c = 1
	for i in range(x):
		for j in range(y):
			px = pixeles[i,j]
			b = px[0]
			if(b == 255 or b == 0):
				m.append((i,j))
				c = 0
				try:
					p1 = pixeles[i+1,j]
					c += 1
				except:
					p1 = (0,0,0)
				try:
					p2 = pixeles[i-1,j]
					c += 1
				except:
					p2 = (0,0,0)
				try:
					p3 = pixeles[i,j+1]
					c += 1
				except:
					p3 = (0,0,0)
				try:
					p4 = pixeles[i,j-1]
					c += 1
				except:
					p4 = (0,0,0)
			
				if(c > 4): 
					c = 4
				r = (p1[0] + p2[0] + p3[0] + p4[0])
				g = (p1[0] + p2[0] + p3[0] + p4[0]) 
				b = (p1[0] + p2[0] + p3[0] + p4[0])
				pxnvo = (r/c,g/c,b/c)
				imagen.putpixel((i,j),pxnvo)
				c = 0
	#SEGUNdA PASADA
	fi = imagen.load()
	for e in m:
		c = 0
		pixel = fi[e]
		i,j = e
		try:
			p1 = fi[i+1,j]
			c += 1
		except:
			p1 = (0,0,0)
		try:
			p2 = fi[i-1,j]
			c += 1
		except:
			p2 = (0,0,0)
		try:
			p3 = fi[i,j+1]
			c += 1
		except:
			p3 = (0,0,0)
		try:
			p4 = fi[i,j-1]
			c += 1
		except:
			p4 = (0,0,0)			
		r = (p1[0] + p2[0] + p3[0] + p4[0])
		g = (p1[0] + p2[0] + p3[0] + p4[0]) 
		b = (p1[0] + p2[0] + p3[0] + p4[0])
		pxnvo = (r/c,g/c,b/c)
		imagen.putpixel((i,j),pxnvo)
		c = 0
	imagen.show()
	return imagen

def bordesPorResta(im, imagen2):
	x,y = im.size
	m1 = im.load()
	m2 = imagen2.load()
	imb = I.new('RGB',(x,y))
	for i in range(x):
		for j in range(y):
			r = m1[i,j][0] - m2[i,j][0]
			g = m1[i,j][1] - m2[i,j][1]
 			b = m1[i,j][2] - m2[i,j][2]
			pixel = (r,g,b)
			imb.putpixel((i,j),pixel)
	imb.show()

def filtroGrisesPromedio(imagen):
	x, y = imagen.size
	px = imagen.load()
	imagenGrises = I.new('RGB',(x,y))
	for i in range(x):
		for j in range(y):
			pixeles = px[i,j]
			prom = sum(pixeles) / 3
			imagenGrises.putpixel((i,j),(prom,prom,prom))
	return imagenGrises

def filtroPromedio(imagen):
	x,y = imagen.size
	pixeles = imagen.load()
	imagenFiltrada = I.new('RGB',(x,y))
	c = 1
	for i in range(x):
		for j in range(y):
			px = pixeles[i,j]
			try:
				p1 = pixeles[i+1,j]
				c += 1
			except:
				p1 = (0,0,0)
			try:
				p2 = pixeles[i-1,j]
				c += 1
			except:
				p2 = (0,0,0)
			try:
				p3 = pixeles[i,j+1]
				c += 1
			except:
				p3 = (0,0,0)
			try:
				p4 = pixeles[i,j-1]
				c += 1
			except:
				p4 = (0,0,0)
			
			if(c > 4): 
				c = 4
			r = p1[0] + p2[0] + p3[0] + p4[0]
			g = p1[0] + p2[0] + p3[0] + p4[0]
			b = p1[0] + p2[0] + p3[0] + p4[0]
			
			imagenFiltrada.putpixel((i,j),(r/c,g/c,b/c))
			c = 0
	return imagenFiltrada
		
m = I.open(argv[1])
gris = filtroGrisesPromedio(m)
bordesPorResta(gris,filtroPromedio(filtroPromedio(gris)))
pruido = float(argv[2])
generarRuido(m, pruido)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
