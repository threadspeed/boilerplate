---
title: python script simon (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'simon'

Functions in program: 
* `def newRandomLed():`
* `def blink(color):`
* `def readButton(): `
* `def blinkAll(times):`

Modules used in program: 
* `import random # Import 'random' bibliotheek`
* `import time # importeer de 'time' bibliotheek.`
* `import RPi.GPIO as GPIO # importeer de GPIO bibliotheek.`

## python simon

Python mysql example: simon

```python
import RPi.GPIO as GPIO # importeer de GPIO bibliotheek.
import time # importeer de 'time' bibliotheek.
import random # Import 'random' bibliotheek

# Constanten declaratie
leds = [12,16,20,21]     # array met pinnummers van de leds
buttons = [6,13,19,26] # array met pinnummers van de buttons
aantal = len(leds)      # totaal aantal buttons en leds
wacht = 0.5	            # de tijd in seconden tussen een led aan en uit.1

# Setup
GPIO.setmode(GPIO.BCM) # je kan kiezen tussen BOARD and BCM pin-nummering.
for pin in leds: GPIO.setup(pin, GPIO.OUT) ## Setup the leds to OUT(PUT)
for pin in buttons: GPIO.setup(pin, GPIO.IN)  ## Setup the buttons to IN(PUT)
      
# Methode om alle leds een x aantal keer te laten knipperen
def blinkAll(times):
   for x in range(0,times):
      for pin in leds: GPIO.output(pin, GPIO.HIGH)
      time.sleep(wacht)
      for pin in leds: GPIO.output(pin, GPIO.LOW)
      time.sleep(wacht)

def readButton(): 
   for button in buttons: 
      if GPIO.input(button):
         return buttons.index(button)

   return -1

# Methode om een leds 1x te laten knipperen
# Color is gelijkt aan de index van de array: 0 ..3
def blink(color):
   GPIO.output(leds[color], GPIO.HIGH)
   time.sleep(wacht)
   GPIO.output(leds[color], GPIO.LOW)
   time.sleep(wacht)

def newRandomLed():
   return random.randint(0,3)

# GAME START
blinkAll(1)
print("Het spel is begonnen, herhaal de steeds langer wordende reeks!" )
sequence = []
requiredInputSequence = []
gameOn = True

try: 
	# GAME LOOP
	while gameOn:
	   print(requiredInputSequence)
	   if len(requiredInputSequence) == 0: 
		  sequence.append(newRandomLed())
		  requiredInputSequence = list(sequence)
		  for pin in sequence: blink(pin)
		  continue

	   pressedButton = readButton()
	   while pressedButton == -1: pressedButton = readButton()
	   print("pressed " + str(pressedButton) + ", required " + str(requiredInputSequence[0]))
	   
	   if pressedButton == requiredInputSequence[0]:
		  requiredInputSequence = requiredInputSequence[1:]
		  time.sleep(wacht)
	   else: 
		  print("fail")
		  break
finally:   
	# GAME END
	blinkAll(3)
	print("Game over!")
	print("Score: ", len(sequence)-1)
	GPIO.cleanup() ## clean up all the ports that were used
 


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
