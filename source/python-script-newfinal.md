---
title: python script newfinal (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'newfinal'

Functions in program: 
* `def appear(index, letter):`

Modules used in program: 
* `import SHA256`
* `import random`
* `import Tkinter as tk`

## python newfinal

Python example: newfinal

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*- 

import Tkinter as tk
import random
import SHA256
    
root = tk.Tk()
# width x height + x_offset + y_offset:
root.geometry("800x600+30+30") 

def appear(index, letter):
    # This line would be where you insert the letter in the textbox
    print(letter)
    print(index)
    # Disable the button by index
    i = 0
    while i < len(buttons):
        buttons[i].config(state="normal")
        i = i+1

    buttons[index].config(state="disabled")
    if letter == 'RSA':
        l = tk.Label(root, text='Mật mã RSA')
        l.grid(row=0, column=2, )
    elif letter == 'SHA':
        l = tk.Label(root, text='Mật mã SHA256', font="Monospace 18 normal")
        l.grid(row=0, column=2, ipadx=50, ipady=20)
        l1 = tk.Label(root, text="Plaintext", font="Monospace 12 normal").grid(row=1, column=2, ipady=7 )
        l1 = tk.Label(root, text="Ciphertext", font="Monospace 12 normal").grid(row=2,  column=2, ipady=10)

        e1 = tk.Entry(root, font="Monospace 12 normal")
        e2 = tk.Entry(root, font="Monospace 12 normal")

        e1.grid(row=1, column=3, ipadx=10, ipady=7)
        e2.grid(row=2, column=3, ipadx=10, ipady=7)

        b1 = tk.Button(root, text="Hash it", font="Monospace 12 normal"
                        command=SHA256
                        )
        b1.grid(row=3, column=3, ipadx=30, ipady=7)

letters=["Affine", "DES", "AES", "RSA", "SHA"]

# A collection (list) to hold the references to the buttons created below
buttons = []

for index in range(5): 
    n=letters[index]

    button = tk.Button(root, bg="White", text=n, width=5, height=1, relief=tk.GROOVE,
                    command=lambda index=index, n=n: appear(index, n))

    # Add the button to the window
    button.grid(padx=10, pady=10, row=index, column=1, ipadx=30, ipady=7)

    # Add a reference to the button to 'buttons'
    buttons.append(button)

root.mainloop()     
root.mainloop()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
