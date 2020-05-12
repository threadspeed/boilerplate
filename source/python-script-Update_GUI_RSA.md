---
title: python script Update GUI RSA (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Update GUI RSA'

Functions in program: 
* `def giai_ma_aes_ecb():`
* `def ma_hoa_aes_ecb():`
* `def giai_ma_cbc():`
* `def ma_hoa_cbc():`
* `def giai_ma_ecb():`
* `def ma_hoa_ecb():`
* `def giaima():`
* `def clicked():`
* `def decryptAF(txt,a,b,m):`
* `def encryptAF(txt,a,b,m):`
* `def xgcd(b, a):`
* `def Num2Char(n):`
* `def Char2Num(c):`

Modules used in program: 
* `import ast`

## python Update GUI RSA

Python example: Update GUI RSA

```python
# -*- coding: utf-8 -*-
from Crypto.Cipher import DES3
from Crypto.Cipher import AES
from Crypto.PublicKey import RSA
from Crypto import Random

# 1. Sinh kh�a v� luu kh�a

key = b'abcdefgh12345678'

# 2. �?c kh�a v� t?o m?t m� / gi?i m?t m� DES (ECB, CBC)
iv = Random.new().read(DES3.block_size)
cipher_mode_ecb = DES3.new(key, DES3.MODE_ECB , iv)
cipher_mode_cbc = DES3.new(key, DES3.MODE_CBC , iv)

plaintext = b'I do it!'

# ma hoa
msg_ecb = iv + cipher_mode_ecb.encrypt(plaintext)
msg_cbc = iv + cipher_mode_cbc.encrypt(plaintext)
# print(msg_ecb)
# print(msg_cbc)
# # giai ma
# print(cipher_mode_ecb.decrypt(msg_ecb))

# # 3. �?c kh�a v� t?o m?t m� / gi?i m?t m� AES (ECB)
# iv = Random.new().read(AES.block_size)
# cipher = AES.new(key, AES.MODE_ECB, iv)
# msg = iv + cipher.encrypt(b'I do itRight now')

# print(msg)
# 4. X�y d?ng Demo � giao di?n d? h?a (tham kh?o bu?i 1)

from Tkinter import *

window = Tk()
window.title("Demo ATBMTT")

lb0 = Label(window, text="  ", font=("Arial Bold", 10))
lb0.grid(column=0, row=0)

lb1 = Label(window, text="Chuong trinh demo", font=("Arial Bold", 20))
lb1.grid(column=1, row=1)

lb2 = Label(window, text="Mat ma Afine", font=("Arial Bold", 15))
lb2.grid(column=0, row=2)

plainlb3 = Label(window, text="Plain text", font=("Arial Bold", 14))
plainlb3.grid(column=0, row=3)

plaintxt = Entry(window, width=20)
plaintxt.grid(column=1, row=3)

KEYlb4 = Label(window, text="KEY PAIR",font=("Arial", 14))
KEYlb4.grid(column=2, row=3)
KEYA1 = Entry(window,width=3)
KEYA1.grid(column=3, row=3)
KEYB1 = Entry(window,width=5)
KEYB1.grid(column=4, row=3)
lb5 = Label(window, text="CIPHER TEXT",font=("Arial", 14))
lb5.grid(column=0, row=4)
ciphertxt3 = Entry(window,width=20)
ciphertxt3.grid(column=1, row=4)
denctxt3 = Entry(window,width=20)
denctxt3.grid(column=3, row=4)
def Char2Num(c):
	return ord(c)-65
def Num2Char(n):
	return chr(n+65)

def xgcd(b, a):
	tmp = a
	x0, x1, y0, y1 = 1, 0, 0, 1
	while a != 0:
		q, b, a = b//a, a, b%a
		x0, x1 = x1, x0 - q*x1
		y0, y1 = y1, y0 - q*y1
	if x0 < 0:
		x0 = tmp + x0
	return x0
def encryptAF(txt,a,b,m):
	r=""
	for c in txt:
		e = (a*Char2Num(c)+b )%m
		r = r + Num2Char(e)
	return r
def decryptAF(txt,a,b,m):
	r = ""
	a1 = xgcd(a,m)
	for c in txt:
		e = (a1*(Char2Num(c)-b ))%m
		r = r + Num2Char(e)
	return r

def clicked():
	a, b, m = int(KEYA1.get()),int(KEYB1.get()),26
	entxt = encryptAF(plaintxt.get(),a,b,m)
	ciphertxt3.delete(0,END)
	#a=int(KEYA1.get())
	ciphertxt3.insert(INSERT,entxt)

def giaima():

	a,b,m=int(KEYA1.get()),int(KEYB1.get()),26
	detxt=decryptAF(ciphertxt3.get(),a,b,m)
	denctxt3.delete(0,END)
	#a=int(KEYA1.get())
	denctxt3.insert(INSERT,detxt)

AFbtn = Button(window, text="M� H�a", command=clicked)
AFbtn.grid(column=5, row=3)
DEAFbtn = Button(window, text="Gi?i M� ", command=giaima)
DEAFbtn.grid(column=2, row=4)


#  today
lb1 = Label(window, text="Chuong trinh demo mat ma DES", font=("Arial Bold", 20))
lb1.grid(column=1, row=8)

cipher_mode_ecb = None
def ma_hoa_ecb():
	iv = Random.new().read(DES3.block_size)
	cipher_mode_ecb = DES3.new(key, DES3.MODE_ECB , iv)
	global cipher_mode_ecb
	plaintext = mh_des_ecb_entry.get()
	msg_ecb = iv + cipher_mode_ecb.encrypt(plaintext)
	clipher_des_ecb_entry.delete(0,END)
	clipher_des_ecb_entry.insert(INSERT,msg_ecb)

def giai_ma_ecb():
	plain_text = cipher_mode_ecb.decrypt(clipher_des_ecb_entry.get())
	decrypt_mh_des_ecb_entry.delete(0, END)
	decrypt_mh_des_ecb_entry.insert(INSERT, plain_text[8:])

# plain text
mh_des_ecb = Label(window, text="Ma hoa ECB", font=("Arial Bold", 14))
mh_des_ecb.grid(column=0, row=9)

mh_des_ecb_entry = Entry(window, width=20)
mh_des_ecb_entry.grid(column=1, row=9)

mh_des_ecb_btn = Button(window, text="Ma hoa", command=ma_hoa_ecb)
mh_des_ecb_btn.grid(column=2, row=9)

# clipher text
clipher_des_ecb = Label(window, text="Clipher text", font=("Arial Bold", 14))
clipher_des_ecb.grid(column=0, row=10)

clipher_des_ecb_entry = Entry(window, width=20)
clipher_des_ecb_entry.grid(column=1, row=10)

# gia ma
decrypt_mh_des_ecb = Label(window, text="Giai ma DES-ECB", font=("Arial Bold", 14))
decrypt_mh_des_ecb.grid(column=0, row=11)

decrypt_mh_des_ecb_entry = Entry(window, width=20)
decrypt_mh_des_ecb_entry.grid(column=1, row=11)

decrypt_mh_des_ecb_btn = Button(window, text="Giai ma", command=giai_ma_ecb)
decrypt_mh_des_ecb_btn.grid(column=2, row=11)

# DES-CBC
cipher_mode_cbc = None
def ma_hoa_cbc():
	iv = Random.new().read(DES3.block_size)
	cipher_mode_cbc = DES3.new(key, DES3.MODE_CBC , iv)
	global cipher_mode_cbc
	plaintext = mh_des_cbc_entry.get()
	# print(plaintext)
	msg_cbc = iv + cipher_mode_cbc.encrypt(plaintext)
	clipher_des_cbc_entry.delete(0,END)
	clipher_des_cbc_entry.insert(INSERT,msg_cbc)

def giai_ma_cbc():
	plain_text = cipher_mode_cbc.decrypt(clipher_des_cbc_entry.get())
	decrypt_mh_des_cbc_entry.delete(0, END)
	decrypt_mh_des_cbc_entry.insert(INSERT, plain_text[8:])

# plain text
mh_des_cbc = Label(window, text="Ma hoa cbc", font=("Arial Bold", 14))
mh_des_cbc.grid(column=0, row=12)

mh_des_cbc_entry = Entry(window, width=20)
mh_des_cbc_entry.grid(column=1, row=12)

mh_des_cbc_btn = Button(window, text="Ma hoa", command=ma_hoa_cbc)
mh_des_cbc_btn.grid(column=2, row=12)

# clipher text
clipher_des_cbc = Label(window, text="Cipher text", font=("Arial Bold", 14))
clipher_des_cbc.grid(column=0, row=13)

clipher_des_cbc_entry = Entry(window, width=20)
clipher_des_cbc_entry.grid(column=1, row=13)

# gia ma
decrypt_mh_des_cbc = Label(window, text="Giai ma DES-cbc", font=("Arial Bold", 14))
decrypt_mh_des_cbc.grid(column=0, row=14)

decrypt_mh_des_cbc_entry = Entry(window, width=20)
decrypt_mh_des_cbc_entry.grid(column=1, row=14)

decrypt_mh_des_cbc_btn = Button(window, text="Giai ma", command=giai_ma_cbc)
decrypt_mh_des_cbc_btn.grid(column=2, row=14)


# AES
lb2 = Label(window, text="Chuong trinh demo mat ma AES-ECB", font=("Arial Bold", 20))
lb2.grid(column=1, row=15)

cipher_mode_aes_ecb = None
def ma_hoa_aes_ecb():
	iv = Random.new().read(AES.block_size)
	cipher_mode_aes_ecb = AES.new(key, AES.MODE_ECB, iv)
	global cipher_mode_aes_ecb
	plaintext = mh_des_aes_ecb_entry.get()
	msg_aes_ecb = iv + cipher_mode_aes_ecb.encrypt(plaintext)
	clipher_des_aes_ecb_entry.delete(0,END)
	clipher_des_aes_ecb_entry.insert(INSERT,msg_aes_ecb)

def giai_ma_aes_ecb():
	plain_text = cipher_mode_aes_ecb.decrypt(clipher_des_aes_ecb_entry.get())
	decrypt_mh_des_aes_ecb_entry.delete(0, END)
	decrypt_mh_des_aes_ecb_entry.insert(INSERT, plain_text[16:])

# plain text
mh_des_aes_ecb = Label(window, text="Ma hoa aes_ecb", font=("Arial Bold", 14))
mh_des_aes_ecb.grid(column=0, row=16)

mh_des_aes_ecb_entry = Entry(window, width=20)
mh_des_aes_ecb_entry.grid(column=1, row=16)

mh_des_aes_ecb_btn = Button(window, text="Ma hoa", command=ma_hoa_aes_ecb)
mh_des_aes_ecb_btn.grid(column=2, row=16)

# clipher text
clipher_des_aes_ecb = Label(window, text="Clipher text", font=("Arial Bold", 14))
clipher_des_aes_ecb.grid(column=0, row=17)

clipher_des_aes_ecb_entry = Entry(window, width=20)
clipher_des_aes_ecb_entry.grid(column=1, row=17)

# gia ma
decrypt_mh_des_aes_ecb = Label(window, text="Giai ma AES - ECB", font=("Arial Bold", 14))
decrypt_mh_des_aes_ecb.grid(column=0, row=18)

decrypt_mh_des_aes_ecb_entry = Entry(window, width=20)
decrypt_mh_des_aes_ecb_entry.grid(column=1, row=18)

decrypt_mh_des_aes_ecb_btn = Button(window, text="Giai ma", command=giai_ma_aes_ecb)
decrypt_mh_des_aes_ecb_btn.grid(column=2, row=18)



import ast
# RSA

# show public key
public_mh_rsa = Label(window, text="Private key", font=("Arial Bold", 14))
public_mh_rsa.grid(column=0, row=23)

public_mh_rsa_entry = Entry(window, width=20)
public_mh_rsa_entry.grid(column=1, row=23)

# show private key
private_mh_rsa = Label(window, text="Public key", font=("Arial Bold", 14))
private_mh_rsa.grid(column=0, row=24)

private_mh_rsa_entry = Entry(window, width=20)
private_mh_rsa_entry.grid(column=1, row=24)


class RSASelf:
	def __init__(self):
		self.key = RSA.generate(1024, Random.new().read)
		self.publickey = self.key.publickey()
		
		public_mh_rsa_entry.delete(0, END)
		public_mh_rsa_entry.insert(INSERT, self.publickey.exportKey('PEM'))
		private_mh_rsa_entry.delete(0, END)
		private_mh_rsa_entry.insert(INSERT, self.key.exportKey('PEM'))

	def encrypt(self):
		plaintext = self.publickey.encrypt(mh_rsa_entry.get(), 32)
		clipher_mh_rsa_entry.delete(0, END)
		clipher_mh_rsa_entry.insert(INSERT, str(plaintext))
		return plaintext

	def decrypt(self):
		plain_text = self.key.decrypt(ast.literal_eval(str(clipher_mh_rsa_entry.get())))
		decrypt_mh_rsa_entry.delete(0, END)
		decrypt_mh_rsa_entry.insert(INSERT, plain_text)
		return plain_text


rsa = RSASelf()
# enc =  rsa.encrypt('hello world RSA')
# print(enc)

# dec = rsa.decrypt(enc)
# print(dec)

# RSA
lb3 = Label(window, text="Chuong trinh demo mat ma RSA", font=("Arial Bold", 20))
lb3.grid(column=1, row=19)
# plain text
mh_rsa = Label(window, text="Ma hoa RSA", font=("Arial Bold", 14))
mh_rsa.grid(column=0, row=20)

mh_rsa_entry = Entry(window, width=20)
mh_rsa_entry.grid(column=1, row=20)

mh_rsa_btn = Button(window, text="Ma hoa", command=rsa.encrypt)
mh_rsa_btn.grid(column=2, row=20)

# clipher text
clipher_mh_rsa = Label(window, text="Clipher text", font=("Arial Bold", 14))
clipher_mh_rsa.grid(column=0, row=21)

clipher_mh_rsa_entry = Entry(window, width=20)
clipher_mh_rsa_entry.grid(column=1, row=21)

# show public key



# giai ma
decrypt_mh_rsa = Label(window, text="Giai ma RSA", font=("Arial Bold", 14))
decrypt_mh_rsa.grid(column=0, row=22)

decrypt_mh_rsa_entry = Entry(window, width=20)
decrypt_mh_rsa_entry.grid(column=1, row=22)

decrypt_mh_rsa_btn = Button(window, text="Giai ma", command=rsa.decrypt)
decrypt_mh_rsa_btn.grid(column=2, row=22)


window.geometry('800x600')
window.mainloop()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
