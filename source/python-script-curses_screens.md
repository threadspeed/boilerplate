---
title: python script curses screens (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'curses screens'

Functions in program: 
* `def main():`
* `def draw_menu(stdscr):`
* `def get_file_contents(file):`
* `def generate_network(format_draw=True):`
* `def generate_box(common=False, hostname="sensenet_"):`

Modules used in program: 
* `import string`
* `import random`
* `import random`
* `import time`
* `import curses`
* `import sys,os`

## python curses screens

Python mysql example: curses screens

```python
import sys,os
import curses
import time
import random
from asciitree import LeftAligned
from collections import OrderedDict as OD

from scapy import data
import random
import string

from asciitree import LeftAligned
from asciitree.drawing import BoxStyle, BOX_DOUBLE, BOX_BLANK, BOX_LIGHT,BOX_HEAVY

def generate_box(common=False, hostname="sensenet_"):
    TCP_REVERSE = dict((data.TCP_SERVICES[k], k) for k in data.TCP_SERVICES.keys())
    VOWELS = "aeiou"
    CONSONANTS = "".join(set(string.ascii_lowercase) - set(VOWELS))
    ports = []       
    for i in range(random.randint(1,10)):
        pc=(random.choice([21,22,23,25,53,67,137,138,443]))
        ports.append((pc, TCP_REVERSE[pc]))
    for i in range(random.randint(1,5)):
        pc = random.choice(list(TCP_REVERSE.keys()))
        ports.append((pc, TCP_REVERSE[pc]))
    ports = set(ports)
    for i in range(random.randint(1,10)):
        if i % 2 == 0:
            hostname += random.choice(CONSONANTS)
        else:
            hostname += random.choice(VOWELS)
    return hostname, ports

def generate_network(format_draw=True):
    boxes = []
    for x in range(random.randint(1,6)):
        h,p = generate_box()
        boxes.append(("["+h+"]",OD([("OS : WINDOWS",{}),
                                    ("CVE: ",{}),
                                    ("PORTS",OD([(port,{}) for port in p]))])))
        
    nw = {"192.168.56.0/24":OD(boxes)}
    air_tr = LeftAligned(draw=BoxStyle(gfx=BOX_LIGHT,
                                   horiz_len=10,
                                   label_space=0,
                                   label_format='{}',
                                   indent=1))
    return air_tr(nw)



def get_file_contents(file):
    with open(file, 'r') as deffile: # defined file
        contents = []
        for line in deffile:
            contents.append(line.strip("\n"))
            pass
        pass
    return contents
    pass


def draw_menu(stdscr):

    stdscr.clear()
    stdscr.refresh()
    curses.use_default_colors()
    for i in range(0, curses.COLORS):
        curses.init_pair(i, i, 235);
    curses.init_pair(0, i, -1);
    # Start colors in curses
    curses.start_color()

    lns=curses.LINES - 1
    cols=curses.COLS - 1
    
    height, width = stdscr.getmaxyx()
    
    def splash_screen():
        stdscr.clear()
        stdscr.bkgd('.', curses.color_pair(1))
        stdscr.addstr(0, 0, "HELO WELCOME TO MY APP ") 
        stdscr.refresh()
        k = stdscr.getch()
        return
    
    def read_log(log, last_lines=30):
        with open(log, "r")  as f:
            return '\n '.join(f.read().split('\n')[-last_lines:])

    
    splash_screen()
    win = curses.newwin(height-5, int((width/2)-2), 1,1)#(nlines, ncols, begin_y, begin_x)
    win2 = curses.newwin(int((height/2)-5), int((width/2)-2), 6,int((width/2)+1))#(nlines, ncols, begin_y, begin_x)
    win3 = curses.newwin(int((height/2)-5), int((width/2)-2), int((height/2)+2),int((width/2)+1))
    bar = curses.newwin(3, int((width)-2), int((height)-3),1)#(nlines, ncols, begin_y, begin_x)
    status = curses.newwin(4,int((width/2)-30), 1,int((width/2)+1))
    stdscr.bkgd('.',curses.color_pair(0))
    scrcolor = 85
    count=0
    while (True):
        win.border(0)
        win2.border(0)
        win3.border(0)
        bar.border(0)
        status.border(0)
        
        stdscr.refresh() 
        status.refresh()
        win.refresh()
        win2.refresh()
        win3.refresh()
        bar.refresh()
        
        stdscr.erase()
        win.erase()
        win2.erase()
        win3.erase()
        bar.erase()
        status.erase()

        
        
        count+=1
        stdscr.scrollok(1)
        win.scrollok(1)    
        win2.scrollok(1)  
        win3.scrollok(1)  
        
        win.bkgd(' ', curses.color_pair(scrcolor))
        win2.bkgd(' ', curses.color_pair(scrcolor)) 
        win3.bkgd(' ', curses.color_pair(scrcolor))
        bar.bkgd(' ', curses.color_pair(scrcolor))
        status.bkgd(' ', curses.color_pair(scrcolor))


        
        height, width = stdscr.getmaxyx()
        title = "WMCLIENT"[:width-1]
        subtitle = "Ex Nihilo. Alea Iacta Est."[:width-1]
        statusbarstr = "Press 'q' to exit | Press '8' to dispense meme |"

        start_y = int(4)

        stdscr.addstr(1, (width-len(title)-1), title)
        stdscr.addstr(3, (width-len(subtitle)-1), subtitle)

        win2.addstr(0, 0, "NETWORK") 
        
        win.addstr(1,1,generate_network())

        #for pos, line in enumerate(get_file_contents("cmds")[-20:]):
            #win2.addstr(pos+2, 2, line)
        #for pos, line in enumerate(get_file_contents("cmds")[-20:]):
            #win3.addstr(pos+2, 2, line)
        win3.addstr(2, 20, read_log("frontend.py", last_lines=30))
        scrcolor = 160
        if count > 2:
            scrcolor = 160
            status.addstr(1, 2, "MODE: ATTACK ")
            status.addstr(2, 2, "SHELL ACTIVE: SENSENET_K   |  CURRENT USER: ??  ")
            metershell="meterpreter > pwd\n"\
                        "c:\\n"\
                        "meterpreter > cd c:\windows\n"\
                        "meterpreter > run post/windows/gather/hashdump\n" \
                        "[*] Obtaining the boot key...\n"\
                        "[*] Calculating the hboot key using SYSKEY 8528c78df7ff55040196a9b670f114b6...\n"\
                        "[*] Obtaining the user list and keys...\n"\
                        "[*] Decrypting user keys...\n"\
                        "[*] Dumping password hashes...\n"\
                        "mccoy_pauley:1003:81cbcea8a9af93bbaad3b4"\
                        "35b51404ee:561cbdae13ed5abd30aa94ddeb3cf52d:::\n"\
                        "meterpreter >\n"
            win2.addstr(1, 2, metershell)
        else:
            scrcolor = 85
            status.addstr(1, 2, "MODE: RECON ")
            status.addstr(2, 2, "CURRENT TARGET: 192.168.56.0/24   |  INTEREST: 5  ")
  

        
        
        time.sleep(random.randint(1,2))


def main():
    curses.wrapper(draw_menu)

if __name__ == "__main__":
    main()

    

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
