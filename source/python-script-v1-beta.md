---
title: python script v1-beta (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'v1-beta'


Modules used in program: 
* `import tkMessageBox`
* `import tkFont as tkfont`
* `import Tkinter as tk`
* `import random`
* `import ast`

## python v1-beta

Python example: v1-beta

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import ast
import random
import Tkinter as tk
from Tkinter import *
import tkFont as tkfont
from Crypto import Random
from base64 import b64decode, b64encode
from Crypto.Hash import SHA256
from Crypto.PublicKey import RSA
from Crypto.Cipher import AES
import tkMessageBox
from Crypto.Cipher import DES3


class SHAAlgo:
    def __init__(self, inp,  out):
        self.inp = inp
        self.out = out

    def encrypt(self):
        text = self.inp.get()
        digest = SHA256.new()
        digest.update(text)
        self.out.delete(0, END)
        self.out.insert(INSERT, digest.hexdigest())


class RSAAlgo:
    def __init__(self, priinp, pubinp, inp, out, oup1):
        self.inp = inp
        self.out = out
        self.oup1 = oup1
        self.priinp = priinp
        self.pubinp = pubinp
        self.key = RSA.generate(1024, Random.new().read)
        self.publickey = self.key.publickey()
        self.pubinp.delete(0, END)
        self.pubinp.insert(INSERT, self.publickey.exportKey('PEM'))
        self.priinp.delete(0, END)
        self.priinp.insert(INSERT, self.key.exportKey('PEM'))

    def encrypt(self):
        plaintext = self.publickey.encrypt(self.inp.get(), 32)
        self.out.delete(0, END)
        self.out.insert(INSERT, b64encode(plaintext[0]))
        return plaintext

    def decrypt(self):
        plain_text = self.key.decrypt(b64decode(self.out.get()))
        self.oup1.delete(0, END)
        self.oup1.insert(INSERT, plain_text)
        return plain_text


class AESAlgo:
    def __init__(self, inp, out, oup1):
        self.inp = inp
        self.out = out
        self.oup1 = oup1
        self.iv = Random.new().read(AES.block_size)
        self.secret = b'abcdefgh12345678'
        self.key = AES.new(self.secret, AES.MODE_ECB, self.iv)

    def encrypt(self):
        plaintext = self.inp.get()
        try:
            ciphertext = self.iv + self.key.encrypt(plaintext)
            self.out.delete(0, END)
            self.out.insert(INSERT, ciphertext)
        except ValueError:
            tkMessageBox.showerror(
                "Error", "Oops! Input strings must be a multiple of 16 in length")

    def decrypt(self):
        plaintext = self.key.decrypt(self.out.get())
        self.oup1.delete(0, END)
        self.oup1.insert(INSERT, plaintext[16:])
        return plaintext


class DESAlgo:
    def __init__(self, inp, out, oup1):
        self.inp = inp
        self.out = out
        self.oup1 = oup1
        self.iv = Random.new().read(DES3.block_size)
        self.secret = b'abcdefgh12345678'
        self.key = DES3.new(self.secret, DES3.MODE_ECB, self.iv)

    def encrypt(self):
        plaintext = self.inp.get()
        try:
            ciphertext = self.iv + self.key.encrypt(plaintext)
            self.out.delete(0, END)
            self.out.insert(INSERT, ciphertext)
        except ValueError:
            tkMessageBox.showerror(
                "Error", "Oops! Input strings must be a multiple of 8 in length")

    def decrypt(self):
        plaintext = self.key.decrypt(self.out.get())
        self.oup1.delete(0, END)
        self.oup1.insert(INSERT, plaintext[8:])
        return plaintext


class ATBMTTApp(tk.Tk):
    def __init__(self, *args, **kwargs):
        tk.Tk.__init__(self, *args, **kwargs)
        self.title_font = tkfont.Font(
            family='Helvetica', size=18, weight="bold")
        container = tk.Frame(self)
        container.pack(side="top", fill="both", expand=True)
        container.grid_rowconfigure(0, weight=1)
        container.grid_columnconfigure(0, weight=1)

        self.frames = {}
        for F in (WelcomePage, DESApp, AESApp, RSAApp, SHAApp):
            page_name = F.__name__
            frame = F(parent=container, controller=self)
            self.frames[page_name] = frame
            frame.grid(row=0, column=0, sticky="nsew")

        self.show_frame("WelcomePage")

    def show_frame(self, page_name):
        frame = self.frames[page_name]
        frame.tkraise()


class WelcomePage(tk.Frame):
    def __init__(self, parent, controller):
        tk.Frame.__init__(self, parent)
        self.controller = controller
        label = tk.Label(self, text="Ứng dụng demo ATBMTT",
                         font=controller.title_font)
        label.grid(row=0, column=1, pady=10, padx=20)

        cryptos = ['DESApp', 'AESApp', 'RSAApp', 'SHAApp']
        labels = ['DES', 'AES', 'RSA', 'SHA']
        for i in range(4):
            ct = [random.randrange(256) for x in range(3)]
            brightness = int(round(0.299*ct[0] + 0.587*ct[1] + 0.114*ct[2]))
            ct_hex = "%02x%02x%02x" % tuple(ct)
            bg_colour = '#' + "".join(ct_hex)
            l = tk.Button(self,
                          text=labels[i],
                          fg='White' if brightness < 120 else 'Black',
                          bg=bg_colour,
                          font='Helvetica 12 normal',
                          width=20,
                          command=lambda i=i: controller.show_frame(cryptos[i]))
            l.grid(row=i+1, column=1, pady=5)

        footer = tk.Label(self, text="Thực hiện bởi Phạm Trường An (B1302707)",
                          font="Monospace 12 normal")
        footer.grid(row=10, column=1, pady=10, padx=20)


class DESApp(tk.Frame):
    def __init__(self, parent, controller):
        tk.Frame.__init__(self, parent)
        self.controller = controller
        # back button
        button = tk.Button(self, text="Trở về",
                           command=lambda: controller.show_frame("WelcomePage"))
        button.grid(row=1, column=1, ipadx=10, ipady=7)

        label = tk.Label(self, text="Mật mã DES",
                         font=controller.title_font).grid(row=1, column=2, pady=15, ipadx=10, ipady=7)

        # input Plaintext
        l1 = tk.Label(self, text="Plaintext", font="Monospace 12 normal").grid(
            row=3, column=1, padx=10, pady=10, ipady=7)
        e1 = tk.Entry(self, font="Monospace 12 normal")
        e1.grid(row=3, column=2, ipadx=10, ipady=7)
        # output cyphertext
        l2 = tk.Label(self, text="Ciphertext", font="Monospace 12 normal").grid(
            row=4, column=1, padx=10, pady=10, ipady=7)

        e2 = tk.Entry(self, font="Monospace 12 normal")
        e2.grid(row=4, column=2, ipadx=10, ipady=7)

        # output plaintext
        l2 = tk.Label(self, text="Plaintext", font="Monospace 12 normal").grid(
            row=5, column=1, padx=10, pady=10, ipady=7)

        e3 = tk.Entry(self, font="Monospace 12 normal")
        e3.grid(row=5, column=2, ipadx=10, ipady=7)

        # # init rsa
        desx = DESAlgo(e1, e2, e3)
        b1 = tk.Button(self, text="Encrypt",
                       font="Monospace 12 normal",
                       command=desx.encrypt)
        b1.grid(row=3, column=3, padx=15,  ipadx=10, ipady=3)

        b2 = tk.Button(self, text="Decrypt",
                       font="Monospace 12 normal",
                       command=desx.decrypt)
        b2.grid(row=4, column=3, padx=15,  ipadx=10, ipady=3)


class AESApp(tk.Frame):
    def __init__(self, parent, controller):
        tk.Frame.__init__(self, parent)
        self.controller = controller
        # back button
        button = tk.Button(self, text="Trở về",
                           command=lambda: controller.show_frame("WelcomePage"))
        button.grid(row=1, column=1, ipadx=10, ipady=7)

        label = tk.Label(self, text="Mật mã AES",
                         font=controller.title_font).grid(row=1, column=2, pady=15, ipadx=10, ipady=7)

        # input Plaintext
        l1 = tk.Label(self, text="Plaintext", font="Monospace 12 normal").grid(
            row=3, column=1, padx=10, pady=10, ipady=7)
        e1 = tk.Entry(self, font="Monospace 12 normal")
        e1.grid(row=3, column=2, ipadx=10, ipady=7)
        # output cyphertext
        l2 = tk.Label(self, text="Ciphertext", font="Monospace 12 normal").grid(
            row=4, column=1, padx=10, pady=10, ipady=7)

        e2 = tk.Entry(self, font="Monospace 12 normal")
        e2.grid(row=4, column=2, ipadx=10, ipady=7)

        # output plaintext
        l2 = tk.Label(self, text="Plaintext", font="Monospace 12 normal").grid(
            row=5, column=1, padx=10, pady=10, ipady=7)

        e3 = tk.Entry(self, font="Monospace 12 normal")
        e3.grid(row=5, column=2, ipadx=10, ipady=7)

        # # init rsa
        aesx = AESAlgo(e1, e2, e3)
        b1 = tk.Button(self, text="Encrypt",
                       font="Monospace 12 normal",
                       command=aesx.encrypt)
        b1.grid(row=3, column=3, padx=15,  ipadx=10, ipady=3)

        b2 = tk.Button(self, text="Decrypt",
                       font="Monospace 12 normal",
                       command=aesx.decrypt)
        b2.grid(row=4, column=3, padx=15,  ipadx=10, ipady=3)


class RSAApp(tk.Frame):
    def __init__(self, parent, controller):
        tk.Frame.__init__(self, parent)
        self.controller = controller
        # back button
        button = tk.Button(self, text="Trở về",
                           command=lambda: controller.show_frame("WelcomePage"))
        button.grid(row=1, column=1, ipadx=10, ipady=7)

        label = tk.Label(self, text="Mật mã RSA",
                         font=controller.title_font).grid(row=1, column=2, pady=15, ipadx=10, ipady=7)

        # show private key
        l3 = tk.Label(self, text="Private key", font="Monospace 12 normal").grid(
            row=3, column=1, padx=10, pady=10, ipady=7)

        e3 = tk.Entry(self, font="Monospace 12 normal")
        e3.grid(row=3, column=2, ipadx=10, ipady=7)
        # show public key
        l4 = tk.Label(self, text="Public key", font="Monospace 12 normal").grid(
            row=4, column=1, padx=10, pady=10, ipady=7)

        e4 = tk.Entry(self, font="Monospace 12 normal")
        e4.grid(row=4, column=2, ipadx=10, ipady=7)

        # input Plaintext
        l1 = tk.Label(self, text="Plaintext", font="Monospace 12 normal").grid(
            row=5, column=1, padx=10, pady=10, ipady=7)
        e1 = tk.Entry(self, font="Monospace 12 normal")
        e1.grid(row=5, column=2, ipadx=10, ipady=7)
        # output cyphertext
        l2 = tk.Label(self, text="Ciphertext", font="Monospace 12 normal").grid(
            row=6, column=1, padx=10, pady=10, ipady=7)

        e2 = tk.Entry(self, font="Monospace 12 normal")
        e2.grid(row=6, column=2, ipadx=10, ipady=7)

        # output plaintext
        l2 = tk.Label(self, text="Plaintext", font="Monospace 12 normal").grid(
            row=7, column=1, padx=10, pady=10, ipady=7)

        e5 = tk.Entry(self, font="Monospace 12 normal")
        e5.grid(row=7, column=2, ipadx=10, ipady=7)

        # # init rsa
        rsax = RSAAlgo(e3, e4, e1, e2, e5)
        b1 = tk.Button(self, text="Encrypt",
                       font="Monospace 12 normal",
                       command=rsax.encrypt)
        b1.grid(row=5, column=3, padx=15,  ipadx=10, ipady=3)

        b2 = tk.Button(self, text="Decrypt",
                       font="Monospace 12 normal",
                       command=rsax.decrypt)
        b2.grid(row=6, column=3, padx=15,  ipadx=10, ipady=3)


class SHAApp(tk.Frame):
    def __init__(self, parent, controller):
        tk.Frame.__init__(self, parent)
        self.controller = controller
        # back button
        button = tk.Button(self, text="Trở về",
                           command=lambda: controller.show_frame("WelcomePage"))
        button.grid(row=1, column=1, ipadx=10, ipady=7)

        label = tk.Label(self, text="Mật mã SHA",
                         font=controller.title_font).grid(row=1, column=2, pady=15, ipadx=10, ipady=7)

        # input Plaintext
        l1 = tk.Label(self, text="Plaintext", font="Monospace 12 normal").grid(
            row=3, column=1, padx=10, pady=10, ipady=7)
        e1 = tk.Entry(self, font="Monospace 12 normal")
        e1.grid(row=3, column=2, ipadx=10, ipady=7)
        # input cyphertext
        l2 = tk.Label(self, text="Ciphertext", font="Monospace 12 normal").grid(
            row=4, column=1, padx=10, pady=10, ipady=7)

        e2 = tk.Entry(self, font="Monospace 12 normal")
        e2.grid(row=4, column=2, ipadx=10, ipady=7)

        # init sha
        shax = SHAAlgo(e1, e2)
        b1 = tk.Button(self, text="Hash it",
                       font="Monospace 12 normal", command=shax.encrypt)
        b1.grid(row=3, column=3, padx=15,  ipadx=10, ipady=3)


if __name__ == "__main__":
    app = ATBMTTApp()
    app.geometry("450x400")
    app.mainloop()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
