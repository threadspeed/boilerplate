---
title: python script Automate Part1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Automate Part1'


## python Automate Part1

Python example: Automate Part1

```python
##username = input("Please Enter Your Username : ")
##password = input("Please Enter Your Password : ")
##
##if username == "admin" and password == "@dmin":
##    print("Welcome " + username + " To Admin Area")
##    
##elif username == "user" and password == "user":
##        print("Welcome " + username + " To User Area")
##
##else:
##    print("Wrong Username/Password ! Account hac banned")
##



# Example if statemant 2
##age = int(input("How old r u ? "))
##if age>18 :
##    print("Welcome!")
##elif age >= 12:
##    print("Enter your parents id: ")
##else:
##    print("403 Forbidden for your age !")


##spam = 0
##while spam <= 10:
##    print("Hello World " + str(spam))
##    spam = spam +1


##
##name = ''
##while name != "Ahmad":
##    name = input("please enter your name: ")
##    
##print("Thank you Ahmad")


##while True:
##    name = input("Please Type your Name: ")
##    if name == "Ahmad":
##        break
##print("Hello World")



##a = 2 + 2
##b = 4
##
##while a == b:
##    print("Hello")
##    b = b +1
##    a = a + 2



##while True:
##    Username = input("Enter your Username: ")
##    if Username != "admin":
##        continue
##    Password = input("Ok, " + Username + " Please Enter your Password: ")
##    if Password == "admin":
##        break
##print("Welcome " + Username)


##text = "Hello "
##for i in range(1,10):
##    print(text)




##total = 1
##for num in range(101):
##    total = num + total
##
##print(total)





##total = 0
##for i in range(12 , 30):
##    print(i)




##for i in range(10 , -1 , -2):
##    print(i)


# 
# import random
# 
# a = random.randint(0,10)
# 
# if a >= 7:
#    print("Fuck , You Win !!!!!!!!!!!!!!!!! ")
# else:
#    print("Shuttttttt !!!!! you lose !!!!!!!!")



##import random
##
##for i in range(5):
##    print(random.randint(200,300))



##import sys
##
##while True:
##    order = input("Please Enter Exit: ")
##    if order == "exit":
##        sys.exit()




#----------------------------------------------------------------------------------

##def hello():
##    print("Hello")
##    print("What's Up ?")
##
##hello()
##hello()



##def hello(name):
##    print("Hello " + name)
##
##
##hello('name')



##import random
##for i in range(50):
##    def answer(answe):
##        if answe == 1:
##            return "No"
##        elif answe == 2:
##            return "No"
##        elif answe == 3:
##            return "No"
##        elif answe == 4:
##            return "No"
##        elif answe == 5:
##            return "No"
##        elif answe == 6:
##            return "No"
##        elif answe == 7:
##            return "YES , FInily !!!!!"
##        elif answe == 8:
##            return "No"
##        elif answe == 9:
##            return "No"
##
##    ran = random.randint(1,9)
##    output = answer(ran)
##    print(output)

    
##def test():
##    print(("Hello"))
##
##
##if test() == None:
##    print("Shut")
##elif test() != None:
##    print("Fuck")



##print("Hello " , end='')
##print("World")


##print("cat" , "dog" , "frog" , sep=',')



#--------------------------------------------------------------



##def spam():
##     print(eggs)
##     
##
##eggs = 42
##spam()
##print(eggs)



#---------------------------------------------------------


##def spam():
##    global eggs
##    eggs = "Spam"
##    
##    
##
##spam()
##print(eggs)



#------------------------------------------------------------------------


##def hundev(devby):
##    return 100 / devby
##
##
##try:
##    print(hundev(0))
##    
##except ZeroDivisionError:
##    print("FUCK")


#------------------------------------------------------------------------------


##import random
##
##secretnum = random.randint(1 , 20)
##
##print("Let's play! i thinking about a number between 1 and 20 , guess what is it. ")
##
##for myguess in range(7):
##    guess = int(input("Take a guess: "))
##    print()
##    print("####it's your " + str(myguess + 1) + " guess From 7####")
##    print()
##    
##    if guess > secretnum:
##        print("****your guess is too high.****")
##    
##    elif guess < secretnum:
##        print("****your guess is too low.****")
##    
##    else:
##        break
##    
##
##if guess == secretnum:
##    print("Yes , your answer is correct.")
##else:
##    print("Your guesses are over The answer is: " + str(secretnum))



#-------------------------------------------------------------------------------
# 
##def collatz(number):
##    if number % 2 == 0:
##        print(number // 2)
##    elif number %2 == 1:
##        return 3 * number + 1
##try:    
##    num = int(input("Please Enter a Number: "))
##except ValueError:
##    num = int(input("Please Enter a Number: "))
##
##
##print(collatz(num))


#-------------------------------------------------------------


##spam = ["JAck" , "LAck" , "MAc" , "Rack" , "zak"]
##print("Hello " + spam[0])

#================================================================

##spam = [["rick" , "jack"] , "Nick"]
##print(spam[0][1])

#================================================================


##spam = ["JAck" , "LAck" , "MAc" , "Rack" , "zak"]
##print(spam[0] + " is Friend with " + spam[-1])


#---------------------------------------------------------------====

##spam = ["Cat" , "Dog" , "Monkey" , "Donkey"]
##print( spam[1:] )
##print(spam[:])
##print("The len is : " + str(len(spam)))

#=================================================================


##spam = ["cat" , "rat" , "bat" , "dog" ]
##spam[1] = "Gorlil"
##print(spam)


#===============================================================


##a = [1 , 2, 3 ] 
##
##b = ["A" , "B" , "C" ]
##
##print(a+ b == b +a)
##
##print( a +b )
##
##print(( a *3))
##
##print(a[0] + 4)


#==============================================================


# employ = []
# while True:
#     print("Please Enter employer name " + str(len(employ) + 1) + " : " + "NOTE : Press Enter to stop...")
#     name = input()
#     if name == '':
#         break
#     employ = employ + [name]
# 
# print(("there is " + str(len(employ)) + " Employ" ) )
# print("The employers name are : ")
# for name in employ:
#     print(' ' + name)


# ========================================

# spam = ['Cat' , 'Dog' , 'Frog']
# for i in spam:
#     print(i)
#     
# for i in range(len(spam)):
#     print("Index: " + str(i) + " and in the spam is: "  + spam[i] )


#========================================================================

#IMPORTATNT
# username =["admin", "user"]
# password = ["admin" , "user"]
# while True:
#     print("Please Enter Your username: ")
#     user = input()
#     print("Please Enter Your password: ")
#     paswor = input()
#     if user=="" or paswor=="":
#         continue
#     else:
#         break
# for i in username and password:
#     if user== i and paswor== i:
#         print("Welcome! ")
#     else:
#         print("username / password is wrong")
        
        
# =========================================================


# spam = [ "Ahmad" , "Ali" , "Reza" , "Mohammad"]
# 
# name = input("Is he married? ")
# 
# if name in spam:
#     print("Yes " + name + " married")
# else:
#     print("No , " + name + " is single")




#===========================================================




# cat = ['fat', 'black', 'loud']
# 
# size , color , dep = cat
# 
# print((cat))
# 
# print((size))
# print((color))
# print(dep)



#=======================================================


# spam = 42
# spam **= 2
# print(spam)
# text1 = "Hello"
# text2 = " World"
# text1 += text2
# print(text1)
# text2 *= 3
# print((text2))


# =======================================================

# 
# spam  = ["color" , "size" , "love"]
# print(spam.index("color"))
# 
# spam.append("ME")
# print(spam)
# 
# spam.insert(9 , "FUCK")
# spam.insert(5 , "NUCKK")
# print(spam.index("FUCK"))
# 
# 
# del(spam[0])
# print(spam)
# 
# spam.remove("size")
# print(spam)
# 
# 
# spam = [23 ,325,67 ,6 ,8 ,76 ,435]
# spam.sort(reverse = True)
# print(spam)


# ==========================================


# 
# spam = ["A" , "a" , "B" , "b"]
# spam.sort(key=str.lower) # it dosenot work
# print(spam)

# ======================

# import random
# 
# messages = ['It is certain',
#  'It is decidedly so',
#  'Yes definitely',
#  'Reply hazy try again',
#  'Ask again later',
#  'Concentrate and ask again',
#  'My reply is no',
#  'Outlook not so good',
#  'Very doubtful']
# 
# print((messages[random.randint( 0 , len(messages) -1 )]))



# ===================================================================


# name = input("What is your name: ")
# 
# for i in name:
#     print("*********" + i + "*********")

# ===================================================================


# eggs = ("hello" , 32 ,  3.14)
# print(( eggs[1:3]  ))
# print(( len(eggs)))
# print(( type(eggs)))
# eggs =list(eggs)
# print((eggs))


# =====================================================

# name = "AHMAD"
# new = list(name)
# print(new)



# =======================================================
# import copy
# eggs = [1 , 2 ,3 ,4 ,5]
# spam = copy.copy(eggs)
# spam[1] = 20
# print(spam)
# print(eggs)
# 
# 
# ==========================================================

# import copy
# spam = [1, 'hello' , ['jack' , 'lack' , 'mack'] , 42]
# eggs = copy.deepcopy(spam)
# print(eggs)


# =============================================================

# spam = ['apples', 'bananas', 'tofu', 'cats']
# 
# 
# 
# def lale(arg):
#     if len(arg) == 1:
#         return arg[0]
#     else:
#         return "{} , and {}" . format(' , '.join(arg[:-1]) , arg[-1])
#     
# print( lale(spam) )



# ========================================================================


# grid = [['.', '.', '.', '.', '.', '.'],
#  ['.', 'O', 'O', '.', '.', '.'],
#  ['O', 'O', 'O', 'O', '.', '.'],
#  ['O', 'O', 'O', 'O', 'O', '.'],
#  ['.', 'O', 'O', 'O', 'O', 'O'],
#  ['O', 'O', 'O', 'O', 'O', '.'],
#  ['O', 'O', 'O', 'O', '.', '.'],
#  ['.', 'O', 'O', '.', '.', '.'],
#  ['.', '.', '.', '.', '.', '.']]
# 
# 
# # print('\n'.join(map(''.join, zip(*grid))))
# 
# for j in range(6):
#     for i in range(9):
#         print(grid[i][j], end='')
#     print('')
    
    
# =================================================
# 
# spam = {'name': 'ahmad' , 'color':'brown' , 'job':'programmer'}
# print(   spam['name'] + " Have " + spam['color'] + " eyes and " + spam['name'] + " is a " + spam['job']      )


# ===================================================================

# birthdays = {'Alice': 'Apr 1', 'Bob': 'Dec 12', 'Carol': 'Mar 4'}
# 
# while True:
#     print("Enter a Name. (Enter to break) ")
#     name = input()
#     if name== '':
#         break
#     
#     if name in birthdays:
#         print("is the birthday of " + name)
#         
#     else:
#         print('I do not have birthday information for ' + name)
#         print('What is their birthday?')
#         bday = input()
#         birthdays[name] = bday
#         print('Birthday database updated.')
#         print(birthdays)
# 
# 


# =======================================================


# birthdays = {'Alice': 'Apr 1', 'Bob': 'Dec 12', 'Carol': 'Mar 4'}
# 
# for i in birthdays.values():
#     print(i)
# 
# for i in birthdays.keys():
#     print(i)
# 
# for i in birthdays.items():
#     print(i)
#     

# print(list(birthdays.keys()))

# for k , v in birthdays.items():
#     print("Key: " + k + " and value: " + v)
# 
# if 'Alice' in birthdays.keys():
#     print("YES")
# if 'Ahmad' not in birthdays.keys():
#     print("NO")


# =================================================


# 
# picnicItems = {'apples': 5, 'cups': 2}
# print(( "this is a test for apples" + " " + str(picnicItems.get('eggs',":Not Found")  )  ))
# picnicItems.setdefault("dog", "3")
# print(picnicItems.items())


# ===========================================================

# 
# import pprint
# 
# message = 'It was a bright cold day in April, and the clocks were striking thirteen.'
# count = {}
# for i in message:
#     count.setdefault(i , 0)
#     count[i] = count[i] + 1
# 
# pprint.pprint(count)
# 
# print(pprint.pformat(count))

# ==========================================




# theBoard = {'top-L': ' ', 'top-M': ' ', 'top-R': ' ',
#  'mid-L': ' ', 'mid-M': ' ', 'mid-R': ' ',
#  'low-L': ' ', 'low-M': ' ', 'low-R': ' '}
# 
# 
# def printboard(board):
#     print(board['top-L'] + "|" + board['top-M'] + '|' + board['top-R'])
#     print("-+-+-")
#     print(board['mid-L'] + '|' + board['mid-M'] + '|' + board['mid-R'])
#     print('-+-+-')
#     print(board['low-L'] + '|' + board['low-M'] + '|' + board['low-R'])
# 
# 
# turn = 'X'
# for i in range(9):
#     printboard(theBoard)
#     move = input('Turn for ' + turn + '. Move on which space?')
#     theBoard[move] = turn
#     if turn=='X':
#         turn = 'O'
#     else:
#         turn = 'X'
#         
# printboard(theBoard)





# ===================================================



# allGuests = {'Alice': {'apples': 5, 'pretzels': 12},
#  'Bob': {'ham sandwiches': 3, 'apples': 2},
#  'Carol': {'cups': 3, 'apple pies': 1}}
# def totalBrought(guests, item):
#     numBrought = 0
#     for k, v in guests.items():
#         numBrought = numBrought + v.get(item, 0)
#     return numBrought
# print('Number of things being brought:')
# print(' - Apples ' + str(totalBrought(allGuests, 'apples')))
# print(' - Cups ' + str(totalBrought(allGuests, 'cups')))
# print(' - Cakes ' + str(totalBrought(allGuests, 'cakes')))
# print(' - Ham Sandwiches ' + str(totalBrought(allGuests, 'ham sandwiches')))
# print(' - Apple Pies ' + str(totalBrought(allGuests, 'apple pies')))



# ======================================================================================

# spam = {'name' : 'ahmad' , 'age':'17'}
# spam.setdefault('color' , 'black')
# print(spam["color"])


# ======================================================================================




# stuff=  {'rope': 1, 'torch': 6, 'gold coin': 42, 'dagger': 1, 'arrow': 12}

# def displayInventory(inventory):
#     print("inventory:")
#     count =0
#     for x , y in inventory.items():
#         print(str(y) + " : " + str(x))
#         count = count + y
#     print(("Items : "  + str(count)))
    
# displayInventory(stuff)

# ========================================

# spam = r'Ahmad\'s Car'
# print((spam))

# ============================================


# print('''

# Dear Alice,
# Eve's cat has been arrested for catnapping, cat burglary, and extortion.
# Sincerely,
# Bob''')



# ===========================================

# print("Welcome To TALK!\n")
# print("How Are you ?")
# feel = input()

# def answer(ask):
#     ask = ask.lower()
#     if feel=="good thanks":
#         print("have nice day")


# answer(feel)

# =================================================


# spam = input("Enter Anything:")
# if spam.islower():
#     print("The Text is Lowercase")
# elif spam.isupper():
#     print("The Text is uppercase")
# else:
#     print("The Text is Upeer and Lower")


# ================================================

# while True:
#     age = input("Please Enter your age:")
#     if age.isdecimal():
#         break
#     else:
#         print("Please Enter a Number for your age")


# =================================================




# while True:
#     password = input("Please Enter a new password (number and letter): ")
#     if password.isalnum():
#         break
#     else:
#         print("Please Enter a Correct Password with number and letter.")



# ========================================================



# print(' , '.join(['jack' , 'paul' , 'simon']))

# spam = "ali reza ahmad mammad jack"
# spam = spam.split()
# print(spam[1])


# spam = 'MyABCnameABCisABCSimon'
# spam = spam.split('ABC')
# print(spam[0])


# ========================================================


# spam = '''Dear Alice,
# How have you been? I am fine.
# There is a container in the fridge
# that is labeled "Milk Experiment".
# Please do not drink it.
# Sincerely,
# Bob'''

# spam = spam.split('\n')
# print(spam)



# =====================================================

# spam = 'Hello'.ljust(20 , '+')
# print(spam)

# ================================================

# spam = "Hello"
# print(spam.center(11,"="))

# ================================================

# spam = "============HELLO WORLD============"
# print((spam.strip('=')))


# =================================================


# import pyperclip
# spam = "Fuck"
# pyperclip.copy(spam)
# pyperclip.paste()



# =================================================



# spam = "             Hello           "
# print(spam.strip())

# =====================================================


# tableData = [['apples', 'oranges', 'cherries', 'banana'],
#              ['Alice', 'Bob', 'Carol', 'David'],
#              ['dogs', 'cats', 'moose', 'goose']]


# def printTable(table):
#     # create a new list of 3 "0" values: one for each list in tableData
#     colWidths = [0] * len(table)
#     # search for the longest string in each list of tableData
#     # and put the numbers of characters in the new list
#     for y in range(len(table)):
#         for x in table[y]:
#             if colWidths[y] < len(x):
#                 colWidths[y] = len(x)

#     # "rotate" and print(the list of lists)
#     for x in range(len(table[0])):
#         for y in range(len(table)):
#             print(table[y][x].rjust(colWidths[y]), end=' ')
#         print()
#         x += 1


# printTable(tableData)




# ====================================================




# import re
# # rexcom = re.compile(r'Reza|Ahmad are best friends')
# # mo1 = rexcom.search("Reza and Ahmad are best friends")
# # print(mo1.group())



# import pprint
# text = "Risvind@mail.ru:Xelfrekkb eeveenchong@gmail.com:EeVeen55555 the5thvertigo@gmail.com:emerald7 mbchoa@gmail.com:8chainfisT1989 graham.fullerton85@gmail.com:grey2580 travisakins@gmail.com:blanket99 ryangoss01@gmail.com:01july01 danny3528@gmail.com:iamvenom anthony.ingram@gmail.com:room0112 corymacdonald@gmail.com:Cm042000 poli1989@live.co.uk:rp-safepass2008 dnlengls87@Hotmail.com:presario1 howardchia0615@gmail.com:howard0615 Sylux8675309@gmail.com:Corruption3 Pointy29a@gmail.com:ixeweu12 wghavenn@hotmail.com:nerdy123 misiex@gmail.com:Wojtek01 Mhammed.Y@live.Com:iwillkillyou darryl.r.coates@gmail.com:Situbusit1 wddonalds@gmail.com:ibanez540 silvIo.lolshto@gmail.com:1gfhfdjp"
# splited = text.split()
# pprint.pprint(splited)


# =============================================================


# import re

# com1 = re.compile(r'\d+\s+\w+')
# find = com1.findall('12 drummers, 11 pipers, 10 lords, 9 ladies, 8 maids, 7 swans, 6 geese, 5 rings, 4 birds, 3 hens, 2 doves, 1 partridge')
# print(find)

#======================================================================

# import re
# regex1 = re.compile(r'[^abcdef]')
# regex2 = regex1.findall("ahmad ali jack reza mohmmad")
# print(regex2)

#======================================================================

# import re
# regex = re.compile(r'.at.')
# print(regex.findall("cat rat chat khat hater"))

# =========================================================================

# import re
# # text = input("Please Enter anything:")
# regex = re.compile(r'.*' , re.DOTALL)
# text = 'hello my dear friend \n this is a fucking test'
# research = regex.search(text)
# print((research))

#==========================================================

# import re
# text=  "AhMaD is my BEst Friend i ever had"
# regex = re.compile(r'Ahmad' , re.I)
# search = regex.search(text)
# print(search.group())

#==============================================================

# import re
# text = "im going up UP up Up and i hate this up beacuse this is an up"
# regex = re.compile(r'up' , re.I)
# substriction = regex.sub('down' , text)
# print(substriction)

# ========================================================

# import re
# text =  'Agent Alice gave the secret documents to Agent Bob.'
# regex = re.compile(r'Agent \w+')
# substriction = regex.sub('******' , text)
# print(substriction)

# ======================================================

# import re
# phoneRegex = re.compile(r'''(
#  (\d{3}|\(\d{3}\))? # area code
#  (\s|-|\.)? # separator
#  \d{3} # first 3 digits
#  (\s|-|\.) # separator
#  \d{4} # last 4 digits
#  (\s*(ext|x|ext.)\s*\d{2,5})? # extension
#  )''', re.VERBOSE)
# findall= phoneRegex.findall("445-757-7564 exte     7234823846")
# print(findall)

# ===================================================

# import os
# print(os.getcwd())
# os.makedirs('.\\1\\2\\3\\4\\5')

# ==========================================

# import os

# path = "C:\\Windows\\System32\\cmd.exe"

# print(os.path.basename(path))
# print(os.path.dirname(path))

# =============================================

# import os
# pathe = os.getcwd()
# print( os.path.abspath('.')  )
# print( os.path.basename(pathe) + "    " + os.path.dirname(pathe) )
# print(( os.path.split("D:\\Projects\\isphonenumber.py") ))
# paths = "D:\\Projects\\isphonenumber.py"
# print(paths.split(os.path.sep))

#===========================================================

# import os
# path = "D:\\Projects\\isphonenumber.py"
# print(str(os.path.getsize(path)) + " Bytes")
# print(os.listdir(os.getcwd()))

# ============================================================

# import os
# totalsize = 0
# for file in os.listdir("C:\\Windows\\System32"):
#     totalsize += os.path.getsize(os.path.join("C:\\Windows\\System32" , file))

# print(str(totalsize) + " Byte" )

# =============================================================


# import os


# if os.path.exists("x:\\"):
#     print("Yes")
# else:
#     print("No")

# if os.path.isfile("d:\\Projects\\Thonny.py"):
#     print("Yes")
# else:
#     print("No")

# if os.path.isdir("z:\\Projects\\"):
#     print("Yes")
# else:
#     print("No")

# =========================================================

# import os
# file = open("D:\\Projects\\text.txt")
# # text = file.read()
# text = file.readlines()
# print(text)

# ===========================================

# file = open("D:\\Projects\\text.txt" )
# file.write("Fuck You")
# text = file.read()
# print(text)

# ===========================================

# file = open("D:\\Projects\\spam.txt" , "w")
# file.write(input())
# file.close()
# file = open("D:\\Projects\\spam.txt")
# text = file.read()
# print("\n \n Your Text is:")
# print(text)

# ==============================================

# End of Part 1 ------------------> Programmed by Ahmad Foroughi
# Telegram : pyhp2017
# Email: pyhp2017@gmail.com

#Created WITH LOVE

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
