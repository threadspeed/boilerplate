---
title: python script gbz (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gbz'

Functions in program: 
* `def wiki():`
* `def vopros():`
* `def black():`
* `def shutka():`
* `def otvet():`

Modules used in program: 
* `import pygame.mixer, pygame.time`
* `import webbrowser`
* `import sys, os, os.path`

## python gbz

Python mysql example: gbz

```python
#simulyator smoego soseda

import sys, os, os.path
import webbrowser
from Tkinter import *
#import pygame
#from pygame import *
#from PyQt4.QtCore import *
#from PyQt4.QtGui import *
#from PyQt4.QtWebKit import *

import pygame.mixer, pygame.time
time = pygame.time
mixer = pygame.mixer
root = Tk()
root.title("Grobste")
im = PhotoImage(file = '/home/suknark/sites/1.gif')
def otvet():
    import random
    root3=Tk()
    root3.title("Grob-otvet")
    root3.geometry('200x150+300+200')
    a = random.randint(1,5)
    if a==1:
        Label(root3, text = '###').pack(expand=YES, side=TOP)
    if a==2:
        Label(root3, text = '###').pack(expand=YES, side=TOP)
    if a==3:
        Label(root3, text = '###').pack(expand=YES, side=TOP)
    if a==4:
        Label(root3, text = '###').pack(expand=YES, side=TOP)
    if a==5:
        Label(root3, text = '###').pack(expand=YES, side=TOP)
def shutka():
    import random
    im = PhotoImage(file = '/home/suknark/sites/2.ppm')
    root4=Tk()
    root4.title("Umor")
    root4.geometry('500x200+300+200')
    skaz=open("skaz.txt", 'r')
    podl=open("podl.txt", 'r')
    dop=open("dop.txt", 'r')
    opred=open("opred.txt", 'r')
    b=random.randint(1,9)
    c=random.randint(1,9)   
    d=random.randint(1,9)   
    e=random.randint(1,9) 
    sk=skaz.readlines()[b]
    po=podl.readlines()[c]
    do=dop.readlines()[d]
    op=opred.readlines()[e]
    tex1 =op + po +  sk 
    tex2 = do
    tex = tex1 + tex2
    Label(root4, text = tex).pack(expand=YES, fill=BOTH, side=TOP)      
def black():
    #from Tkinter import *
    import pygame
    #from pygame import *
    pygame.init()
    fl=0
    b=pygame.mixer.music.play
    pygame.mixer.music.load('1.mp3')
    #pygame.mixer.music.play
    root2 = Tk()
    root2.title("vkontakte")
    root2.geometry('600x300+300+200')
    def pus(s):
        pygame.init()
        pygame.mixer.music.load('1.mp3')
        pygame.mixer.music.pause
        #Button(root2, text = "Play", command=pygame.mixer.music.play).pack(side=LEFT)
    #    pygame.mixer.music.unpause
        s=pygame.mixer.music.unpause
        return s
    #def play(c):
    #    pygame.init()
    #    pygame.mixer.music.load('1.mp3')
    #    if fl==0 or fl==2:
    #        c=pygame.mixer.music.play
    #    if fl==1:
    #        c=pygame.mixer.music.unpause
    #    return c
    fl=pus(b)
    Label(root2, text = 'OOO! Noviy Black').pack(expand=YES, fill=BOTH, side=TOP)
    #Button(root2, text = "Play", command=pygame.mixer.music.play).pack(side=LEFT)
    t = Button(root2, text="Play",command=b).pack(side=LEFT)
    Button(root2, text = "Pause", command=pus(b)).pack(side=LEFT)
    #Button(root2, text = "Unpause", command=pygame.mixer.music.unpause).pack(side=LEFT)
    Button(root2, text = "Stop", command=pygame.mixer.music.stop).pack(side=LEFT)
    #Button(root2, text = 'otpravit na svidanie', command=root2.quit).pack(side=TOP)
def vopros():
    root3=Tk()
    root3.title("Grob-vopros")
    root3.geometry('400x300+300+200')
    t = Text(root3, width=40, font="Verdana 12", wrap=WORD)
    Button(root3, text = "Poluchit otvet grobstera", command=otvet).pack(side=TOP)
    t.pack()
    root3.mainloop()
def wiki():
    import webbrowser
    import urllib
    import sys
    #from PyQt4.QtCore import *
    #from PyQt4.QtGui import *
    #from PyQt4.QtWebKit import *
    app = QApplication(sys.argv)
    web = QWebView()
    web.load(QUrl('http://ru.wikipedia.org/wiki/Special:Random'))
    web.show()
    sys.exit(app.exec_())
    #root5 = Tk()
    #webbrowser.open('http://ru.wikipedia.org/wiki/%D0%A1%D0%BB%D1%83%D0%B6%D0%B5%D0%B1%D0%BD%D0%B0%D1%8F:Random')
    #url = 'http://ru.wikipedia.org/wiki/%D0%A1%D0%BB%D1%83%D0%B6%D0%B5%D0%B1%D0%BD%D0%B0%D1%8F:Random'
    #urllib.urlretrieve(url, filename='wiki.txt')
    #file = open ("wiki.txt", 'r')
    #wik = file.readlines()
    #Label(root5, text = wik).pack(expand=YES, fill=BOTH, side=TOP)  
Label(root, image = im).pack(expand=YES, fill=BOTH, side=TOP)
Button(root, text='Zadat vopros', command=vopros).pack(side=TOP)
Button(root, text='Pogovorit s Grobzoy', command=wiki).pack(side=TOP)
Button(root, text='Shutka ot grobzi', command=shutka).pack(side=TOP)
Button(root, text = 'Grobster vkontakte', command=black).pack(side=TOP)
Button(root, text = 'otpravit na svidanie', command=root.quit).pack(side=TOP)
root.mainloop()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
