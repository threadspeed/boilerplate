---
title: python script Treasurehunt (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Treasurehunt'

Functions in program: 
* `def main():`
* `def userinput():`
* `def printline(sonar,count):`
* `def dist(distance):`

## python Treasurehunt

Python example: Treasurehunt

```python
#Dylan Waters
#1343144
#import random
#rand= random.randint(1,9)
class OceanTreasure:
    def __init__(self):
        #creates the list of lists (board)
        import random
        self.__board =[]
        for x in range(15):
            self.__board.append(["~"]*60)
        #creates the 3 chests
        self.__chests=[]
        for key in range(3):
            valid=False
            while not valid:
                x= random.randint(0,59)
                y=random.randint(0,14)
                if not [x,y] in self.__chests:
                    valid=True
                    self.__chests.append([x,y])

    def drawBoard(self):
    # This method prints out the board with current plays adjacent to a board with index.
        print('  '+" "*11+"1"+" "*9+"2"+" "*9+"3"+" "*9+"4"+" "*9+"5")
        print("   "+"0123456789"*6)
        rownumber=0
        #prints the grid
        for grid in self.__board:
            if rownumber<10:
                print(" ",rownumber,end='')
            else:
                print('',rownumber,end='')            
            for row in grid:
                print(row,end='')
            print(rownumber)
            rownumber+=1
        #i know it's not the way presented in the assignment layout, but it looks a lot better this way in my opinion
        print("   "+"0123456789"*6)     
        print('  '+" "*11+"1"+" "*9+"2"+" "*9+"3"+" "*9+"4"+" "*9+"5")
        #print("   "+"0123456789"*6) 
        
    def cheating(self):
        #makes the chests visible on the board
        for treasure in  self.__chests:
            counter=0
            #print(treasure)
            for row in  self.__board:
                if counter==treasure[1]:
                    row[treasure[0]]="$"
                counter+=1       
    
    def getChests(self):
        #returns the chests
        return self.__chests
    
    def getTreasuresLeft(self):
        #returns the amount of remaining chests
        count=0
        for x in self.__chests:
            count+=1   
        return count    
    
    def dropSonar(self,x,y,sonar):
        #drops the specific sonar mark on the X,Y coords
        if self.__board[y][x]!='~':
            print("You already dropped a sonar there. You lost another sonar device")
        #will replace the old sonar marking
        self.__board[y][x]=sonar
        return 
    
    def checkDistance(self,x,y):
        index=0
        #the max distance for X,Y axis
        Xdistance=10 
        Ydistance=6
        #distance to replaced later
        distance=100
        #if the distance is on X axis or Y axis
        X=False
        Y=True
        #iterates of remaining chests
        for treasure in self.__chests:
            #the absolute  distance between sonar and chest
            deltaX=abs(x-treasure[0])
            deltaY=abs(y-treasure[1])
            if [x,y]==treasure:
                self.__chests.pop(index)
                return 0
            #has to be within the max. distance
            elif deltaX<Xdistance and deltaY<Ydistance: 
                 #if X is smaller than Y and X!=0 or if y=0
                if deltaX<deltaY*2 and not deltaX==0 or deltaY==0:
                    #if this deltaX is smaller than the distances of other chests
                    if deltaX<distance:
                        X=True
                        Y=False                        
                        distance=deltaX
                else:
                    #if Y is smaller than X and Y!=0
                    if deltaY*2<distance and deltaY!=0:
                        Y=True
                        X=False                        
                        distance=deltaY*2
            index+=1             
        #if the distance is X or Y
        if X:
            return distance
        elif Y:
            distance=-distance/2
            return distance
        else:       
            return 600
#reads in the distance and returns the symbol 
def dist(distance):
    if distance==-1:
        return 'a'
    elif distance==-2:
        return 'b'
    elif distance==-3:
        return 'c'
    elif distance==-4:
        return 'd'
    elif distance==-5:
        return 'e'   
    elif distance==0:
        return 'X'
    elif distance==1:
        return '1'
    elif distance==2:
        return '2'
    elif distance==3:
        return '3'
    elif distance==4:
        return '4'
    elif distance==5:
        return '5'  
    elif distance==6:
        return '6' 
    elif distance==7:
        return '7'         
    elif distance==8:
        return '8' 
    elif distance==9:
        return '9' 
    else:
        return 'O'

def printline(sonar,count):
    #Just prints a line, keeps main function cleaner
    found=3-count
    found=str(found)
    count=str(count)
    print("You have",sonar,"sonar devices available. Treasures found:",found+". Still to be found:",count+".")
        
def userinput():
    #takes in user input
    valid=False
    while not valid:
        try:
            xinput=input("Enter your desired x coordinate (or Q to quit and H for help): ")
            yinput=input("Enter your desired y coordinate (or Q to quit and H for help): ")
            #if the user quits
            if xinput.lower() =='q' or  yinput.lower() =='q':
                return 'q','q' 
            #if the user requests help
            elif xinput.lower() =='h' or  yinput.lower() =='h':
                print("\nYou have a total of 20 sonar devices and there are 3 treasure chests to find, randomly scattered in the ocean.")
                print("The game ends when you do not have sonar devices left or you found all three chests.")
                print('To find a chest you need to drop a sonar device at the exact x,y coordinates of the chest. In that case the sonar would indicate "X".')
                print('The sonar devices are twice as sensitive on the column axis than the rows.')
                print('It can detect a chest 9 units away on both sides of the x axis and 5 units away on the y axis.')
                print('If the sonar is dropped too far (more than 9 units away on the x axis and 6 on the y axis) from a chest, the sonar would indicate "O", meaning nothing detected.')
                print('Again, the maximum range of the sonar device is 9 units on the x axis and 5 units on the y axis.')
                print('If the sonar is less than 10 units away from a chest on the x axis, the sonar would indicate the distance (1, 2, ..., 9).')
                print('On the y axis, if the sonar device is closer than 6 units, closer on the y than the x axis and still in the range, the sonar would indicate a for 1, b for 2, c for 3, d for 4 and e for 5 distance units.\n')
            xinput=int(xinput)
            yinput=int(yinput)
        except:
            #if user inputs a str or a invalid int
            print("Please enter a value between 0-59 for X-coord, and 0-14 for Y-coord")
        else:
            if xinput < 0 or yinput < 0 or xinput >= 60 or yinput >= 15:
                print("Please enter a value between 0-59 for X-coord, and 0-14 for Y-coord")
            else:
                return xinput,yinput

def main():
    #intial sonar and count values
    sonar=20
    count=3
    game=OceanTreasure()
    #game.cheating()
    while count!=0: 
        if sonar ==0:
            #if you lost all sonar
            game.drawBoard()
            print("You have lost all 20 sonar devises")
            print("The remaining chests were in:",game.getChests())
            break
        game.drawBoard()
        printline(sonar,count)
        x,y=userinput()
        if x=='q' and y =='q':
            #if you quit
            print("The chests were in:",game.getChests()) 
            print("Thank you for playing Ocean Treasures")
            break
        distance=game.checkDistance(x,y)
        mark= dist(distance)
        game.dropSonar(x,y,mark)
        game.getChests()
        count=game.getTreasuresLeft()
        sonar-=1
    if count==0:
        #if you found all chests
        game.drawBoard()
        print("Well done! You found all the 3 treasure Chests using",20-sonar,"out of 20 sonar devices.")
        
    #print("Quiting Game")
    
main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
