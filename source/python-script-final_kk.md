---
title: python script final kk (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'final kk'

Functions in program: 
* `def choose_mode():`
* `def kk():`

Modules used in program: 
* `import termcolor`

## python final kk

Python mysql example: final kk

```python
import termcolor
def kk():
    koniec = False
    board = [1,2,3,4,5,6,7,8,9]
    wygrana = [(0,1,2),(0,4,8),(0,3,6),(3,4,5),(6,7,8),(2,4,6),(1,4,7),(2,5,8)]
    X = termcolor.colored('X', 'red', None, ['bold'])
    O = termcolor.colored('O', 'blue', None, ['bold'])

    def tablica():
        print("")
        print((board[6], "|", board[7], "|", board[8]))
        print(("---------"))
        print((board[3], "|", board[4], "|", board[5]))
        print(("---------"))
        print((board[0], "|", board[1], "|", board[2]))
        print(("")        )
    

def choose_mode():
    choose=0
    while choose == 0:
        mode = input("Do you want to play with computer(c), stupid computer(s) or another player(p)?")
        if mode == 'p':
            choose = 1
        elif mode == 'c':
            level = input("Please choose level: easy (e) or hard (h)")
            if level == 'e':
                choose = 2
            else:
                print("Please choose level: easy (e) or hard (h)")
            if level == 'h':
                choose = 3
            else:
                print("Please choose level: easy (e) or hard (h)")
        else: 
            print("Please type c (computer), s (stupid computer) or p (player) to choose a mode.")
    return choose


    def gracz1 ():
        n = liczba()
        if board[n] == X or board[n] == O:
            print(("The place is already taken! Try again."))
            gracz1()
        else: 
            board[n] = X
    
    def gracz2():
        n = liczba()
        if board[n] == X or board[n] == O:
            print(("The place is already taken! Try again."))
            gracz2()
        else:
            board[n] = O

    

    def liczba():
        a=input()
        try:
            a=int(a)
        except ValueError:
            print(("please type the number between 1-9"))
            return liczba()
        a-=1
        if a in range(0,9):
            return (a)
        else:
            print(("please give the value of 1-9"))
            return liczba()
    
    def gra():
      pola=0
      for a in wygrana:
          if board[a[0]] == board[a[1]] == board[a[2]] == "X":
              return 1
    
      for a in wygrana:
          if board[a[0]] == board[a[1]] == board[a[2]] == "O":
              return 1

      for a in range(9):
          if board[a] == "X" or board[a] == "O":
              pola += 1
          if pola == 9:
              return 2
               

    def AIe ():
        import random
        u = random.choice ('012345678')
        wybor = int(u)
        if board[wybor] != X and board[wybor] != O:
            board[wybor] = O
        else: 
            return AIe()

        
            


    def AI():
        X = termcolor.colored('X', 'red', None, ['bold'])
        O = termcolor.colored('O', 'blue', None, ['bold'])
        ruch = False
        import random
        for a in wygrana:
                # Na zwyciestwo
            if board[a[0]] == O and board[a[1]] == O and board[a[2]] != X:
                board[a[2]] = O     
                ruch = True         
                break
            if board[a[1]] == O and board[a[2]] == O and board[a[0]] != X:
                board[a[0]] = O   
                ruch = True              
                break
            if board[a[0]] == O and board[a[2]] == O and board[a[1]] != X:
                board[a[1]] = O      
                ruch = True             
                break

        for a in wygrana:
            if ruch == False:
                # Obrona
                if board[a[0]] == X and board[a[1]] == X and board[a[2]] != O:
                    board[a[2]] = O    
                    ruch = True            
                    break
                if board[a[1]] == X and board[a[2]] == X and board[a[0]] != O:
                    board[a[0]] = O 
                    ruch = True            
                    break
                if board[a[0]] == X and board[a[2]] == X and board[a[1]] != O:
                    board[a[1]] = O  
                    ruch = True              
                    break

        if not ruch:                
            u = random.choice ('012345678')
            wybor = int(u)
            if board[wybor] != X and board[wybor] != O:
                board[wybor] = O
            else: 
                return AIe()
            
        
               
        
                
           

    def AIGame():
        name1 = input('Player1, please enter your name:')
        name2 = input('Player2, please enter your name:')
        koniec = False
        while not koniec:
            tablica()
            koniec = gra()
            if koniec == True:
                break
            print("name1")
            gracz1()
            print()
            tablica()
            koniec = gra()
            if koniec == True: 
                break
            print("name2")
            AI()
            print()
           
     def AIeGame():
        name1 = input('Player1, please enter your name:')
        name2 = input('Player2, please enter your name:')
        koniec = False
        while not koniec:
            tablica()
            koniec = gra()
            if koniec == True:
                break
            print("name1")
            gracz1()
            print()
            tablica()
            koniec = gra()
            if koniec == True: 
                break
            print("name2")
            AIe()
            print()     

    def Multiplayer():
      punkty_Player1=0
      punkty_Player2=0
      koniec = 0 
      name1 = input('Player1, please enter your name:')
      name2 = input('Player2, please enter your name:')
          while koniec != 1 and koniec != 2:
              tablica()
              koniec = gra()
              if koniec == 1:
                  punkty_Player2 = 1
                  print("{}:{} {}:{}".format(name1,name2, punkty_Player1, punkty_Player2))
                  break
              if koniec == 2:
                  print("Nobody won! {}:{} {}:{}".format(name1,name2, punkty_Player1, punkty_Player2))
                  break
              print(name1)
              gracz1()
              print()
              tablica()
              koniec = gra()
              if koniec == 1: 
                  punkty_Player1 = 1
                  print("{}:{} {}:{}".format(name1,name2, punkty_Player1, punkty_Player2))
                  break
              if koniec == 2:
                  print("Nobody won! {}:{} {}:{}".format(name1,name2, punkty_Player1, punkty_Player2))
                  break
              print(name2)
              gracz2()
              print()
            
    def kolejna_gra():    
    another_game = input("Do you want to play again? Yes (y) or no (n)).)
    if another_game == y:
        return True
    else:
        return False  

    while play:
        game_mode = 0
        game_mode=choose_mode()
        if game_mode == 1:
            Multiplayer()
        elif game_mode == 2:
            AIeGame()  
        elif game_mode == 3:
            AIGame()  
        play=kolejna_gra()  
    
kk()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
