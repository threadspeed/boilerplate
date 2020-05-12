---
title: python script rock%2520paper%2520scissors (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rock%2520paper%2520scissors'

Functions in program: 
* `def button_selected(sender):`

Modules used in program: 
* `import ui`

## python rock%2520paper%2520scissors

Python example: rock%2520paper%2520scissors

```python
# Created by: Heejo Suh
# Created on: Oct 2016
# Created for: ICS3U
# This program shows how to use an if else statement

import ui
from numpy import random # only import random.

# random number to guess
rockPaperScissors_number = random.randint(1, 3) # set random number
print(rockPaperScissors_number)

    	

def button_selected(sender):
    # check the number vs what user selects
    
    # input
    if str(view['ask_textfield'].text) == "Rock" or str(view['ask_textfield'].text) == "Scissor" or str(view['ask_textfield'].text) == "Paper": # if not one of those
        chosen = str(view['ask_textfield'].text)
    else:
        view['retry_label'].text = 'Try again with Rock, Paper, or Scissor'
        
        
    # Process
    global rockPaperScissors_number
    if rockPaperScissors_number== 1:
    	rockPaperScissors = "Rock"
    if rockPaperScissors_number== 2:
    	rockPaperScissors = "Scissor"
    else:
    	rockPaperScissors = "Paper"
    
    if chosen == rockPaperScissors:
    	view['answer_label'].text = "You tied to "+ str(rockPaperScissors)
    	
    if chosen == "Rock":
    	if rockPaperScissors== "Scissor":
    	    win_or_lose = "won"
    	else:
    		win_or_lose = "lost"
    		
    if chosen == "Scissor":
    	if rockPaperScissors== "Paper":
    	    win_or_lose = "won"
    	else:
    		win_or_lose = "lost"
    		
    		
    if chosen == "Paper":
    	if rockPaperScissors== "Rock":
    	    win_or_lose = "won"
    	else:
    		win_or_lose = "lost"
    
    if chosen == "Rock" or chosen == "Scissor" or chosen == "Paper":
    	view['answer_label'].text = "Your " + str(chosen) + " " + win_or_lose + " against "+ str(rockPaperScissors)
    	view['retry_label'].text = ""
    	
view = ui.load_view()
view.present('full_screen')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
