---
title: python script ui2.3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ui2.3'


Modules used in program: 
* `import os`
* `import sys`
* `import random`
* `import wumpus_class`
* `import test`
* `import tkinter as tk`

## python ui2.3

Python mysql example: ui2.3

```python
import tkinter as tk
import test
import wumpus_class
import random
import sys
import os




class Wumpus(tk.Tk):
   def __init__(self, **kwargs):
        super().__init__(**kwargs)

        # add frames
        self.title("Wumpus")
        self.configure(background='white')

        global frame
        frame = tk.Frame()
        frame.pack(side=tk.LEFT,fill=tk.Y)

        frame2 = tk.Frame(self)
        frame2.pack(side=tk.RIGHT,fill=tk.Y)

        frame3 = tk.Frame(frame2)
        frame3.pack(side=tk.TOP)

        frame4 = tk.Frame(frame2)
        frame4.pack(side=tk.BOTTOM)

        # add menu
        menubar = tk.Menu(self)
        filemenu = tk.Menu(menubar, tearoff=0)
        filemenu.add_command(label="New", command=self.donothing)

        filemenu.add_separator()

        filemenu.add_command(label="Exit", command=quit)
        menubar.add_cascade(label="File", menu=filemenu)
        editmenu = tk.Menu(menubar, tearoff=0)
        editmenu.add_command(label="Selct Difficulty", command=self.donothing)

        menubar.add_cascade(label="Settings", menu=editmenu)
        helpmenu = tk.Menu(menubar, tearoff=0)
        helpmenu.add_command(label="Help Index", command=self.donothing)
        helpmenu.add_command(label="About...", command=self.about)
        menubar.add_cascade(label="Help", menu=helpmenu)

        self.config(menu=menubar)

        # add variables
        global message
        message = tk.StringVar()
        message.set("Welcome")

        global color
        color = tk.StringVar()
        color.set("light grey")

        global difficulty
        difficulty = tk.IntVar()
        difficulty.set("1")
        print(difficulty)

        self.select_diff()
        self.title("Wumpus")
        
        # add widgets
        
        text = tk.Message(frame3, textvariable = message , bg = "white", relief=tk.RIDGE, width =  250, pady= 10, justify = tk.LEFT, anchor = tk.W)
        text.grid(row=0,column=0,sticky= tk.W + tk.E)

        lbl = tk.Label(frame3, text="Arrows", relief=tk.RIDGE,width=40,height=2,anchor= tk.W)
        lbl.grid(row=1,column=0)
        
        btn = tk.Button(frame4,text="Up", relief=tk.RAISED,width=8,height=4, command = self.button_up)
        btn.grid(row=2,column=5)
        btn = tk.Button(frame4,text="Down", relief=tk.RAISED,width=8,height=4, command = self.button_down)
        btn.grid(row=5,column=5)
        btn = tk.Button(frame4,text="Left", relief=tk.RAISED,width=8,height=4, command = self.button_left)
        btn.grid(row=5,column=4)
        btn = tk.Button(frame4,text="Right", relief=tk.RAISED,width=8,height=4, command = self.button_right)
        btn.grid(row=5,column=6)

        btn = tk.Button(frame4,text="Shoot", bg = "white", relief=tk.RAISED,width=8,height=4, command = self.button_shoot)
        btn.grid(row=2,column=6)

        Wumpus.updategrid(self)
        Wumpus.message(self)

        # functions

   def donothing(self):
        filewin = tk.Toplevel(self)
        button = tk.Button(filewin, text="Do nothing button")
        button.pack()

   def about(self):
        filewin = tk.Toplevel(self)
        about_dev = tk.Label(filewin, text="Skapat utav Carl Svinge", width=40,height=20)
        about_dev.pack()

   def select_diff(self):
      
        
        filewin = tk.Toplevel(self)
        self.title("Select difficulty")
        filewin.attributes("-topmost", True)
        easy = tk.Button(filewin, text="Easy", command=lambda: difficulty.set(1))
        medium = tk.Button(filewin, text="Medium", command=lambda: difficulty.set(2))
        hard = tk.Button(filewin, text="Hard", command=lambda: difficulty.set(3))
        easy.pack(fill=tk.X)
        medium.pack(fill=tk.X)
        hard.pack(fill=tk.X)

        filewin.wait_variable(difficulty)
        print(difficulty)
        filewin.destroy()


   def button_up(self):
        global y_pos
        global x_pos
        y_pos, x_pos = test.move(y_pos,x_pos,maze,"n", room)
        
        Wumpus.message(self)
        Wumpus.move_wumpus(self)
        Wumpus.updategrid(self)
        #Wumpus.message(self)

   def button_down(self):
        global y_pos
        global x_pos
        y_pos, x_pos = test.move(y_pos,x_pos,maze,"s", room)
        
        Wumpus.message(self)
        Wumpus.move_wumpus(self)
        Wumpus.updategrid(self)
        #Wumpus.message(self)


   def button_left(self):
        global y_pos
        global x_pos
        y_pos, x_pos = test.move(y_pos,x_pos,maze,"a", room)
        
        Wumpus.message(self)
        Wumpus.move_wumpus(self)
        Wumpus.updategrid(self)
        #Wumpus.message(self)


   def button_right(self):
        global y_pos
        global x_pos
        y_pos, x_pos = test.move(y_pos,x_pos,maze,"d", room)
        
        Wumpus.message(self)
        Wumpus.move_wumpus(self)
        Wumpus.updategrid(self)
        #Wumpus.message(self)
        

   def button_shoot(self):
        message.set("Vilken riktning?")

   def updategrid(self):
                
        for r, c in enumerate(maze):
            for col in range(5):
                
                if maze[r][col] == maze[y_pos][x_pos]:
                    color.set("grey")
                    
                elif maze[r][col] in faror[0]:
                    
                    color.set("blue")
                elif maze[r][col] in faror[1]:
                    
                    color.set("green")

                elif maze[r][col] == maze[w_y_pos][w_x_pos]:
                  
                    color.set("red")

                else:
                    color.set("light grey")

                lbl = tk.Label(frame, text=str(maze[r][col]), relief=tk.RIDGE,width=10,height=5, bg = color.get())

                lbl.grid(row=r,column=col)

   def move_wumpus(self):
      global w_y_pos
      global w_x_pos
      
      
      if settings[0] == True:
         
         val = random.randint(1,4)
         if val == 1: val = "n"
         if val == 2: val = "s"
         if val == 3: val = "a"
         if val == 4: val = "d"
         w_y_pos, w_x_pos = test.move(w_y_pos,w_x_pos,maze,val, room)
         
                

   def message(self):
      global y_pos
      global x_pos
      global alive
      
      adjucent = test.adjucent(y_pos,x_pos, maze, room)
      text, y_pos, x_pos, alive = test.danger(adjucent,faror, maze, y_pos, x_pos, alive)
      text = text["vind"]+text["fladdermöss"]+text["wumpus"]+text["dead"]

      message.set(text)

      if alive == False:

        self.title("Game Over")
        filewin = tk.Toplevel(self)
        filewin.attributes("-topmost", True)
        lbl = tk.Label(filewin, text = "You died!")
        lbl.pack(fill=tk.X)
        lbl.config(font=("Courier", 44))
        leave = tk.Button(filewin, text="Quit Game", command = quit, width = 20, height = 5)
        leave.pack(fill=tk.X)
        restart = tk.Button(filewin, text="Restart", command = Wumpus.restart, width = 20, height = 5)
        restart.pack(fill=tk.X) 


   def restart():
      
      python = sys.executable
      os.execl(python, python, * sys.argv)

      


if __name__ == '__main__':

    settings = test.setup(1)

    alive = True
    num_rooms = 40
    parts = 4
    rum = []
    y_pos = 0
    x_pos = 0
    val = 0
    room = wumpus_class.rum(rum,parts,x_pos,y_pos)

    maze = test.spawn_room(parts,room)[1]
    rum = test.spawn_room(parts,room)[0]
    faror, w_y_pos, w_x_pos = test.spawn_danger(rum, maze, settings)

    y_pos = test.spawn_player(maze, faror)[0]
    x_pos = test.spawn_player(maze, faror)[1]
    adjucent = test.adjucent(y_pos,x_pos, maze, room)


    gui = Wumpus()
    gui.mainloop()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
