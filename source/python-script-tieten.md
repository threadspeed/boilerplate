---
title: python script tieten (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'tieten'

Functions in program: 
* `def zoekletterindex(woord2,letter):`

Modules used in program: 
* `import random`

## python tieten

Python mysql example: tieten

```python
#dit programma bevat het spel galgje
#we beginnen met import random zodat er een willekeurig woord gekozen kan worden als je tegen de computer speelt
import random
print('Welkom, het spel dat je speelt is Galgje!')
galg = (
    """

|
|
|
|
|
|
--------
""",
        """
_______
|
|
|
|
|
|
--------
""",
        """
_______
|     |
|
|
|
|
--------
""",
        """
_______
|     |
|     O
|
|
|
|
--------
""",
        """
_______
|     |
|     O
|     |
|
|
|
--------
""",
        """
_______
|     |
|     O
|    /|
|
|
|
--------
""",
        """
_______
|     |
|     O
|    /|/
|
|
|
--------
""",
        """
_______
|     |
|     O
|    /|/
|    / 
|
|
--------
""",
        """
_______
|     |
|     O
|    /|/
|    //
|
|
--------
""")
#dweze functie kan ik aanroepen met een woord en een letter, wat je terug krijgt is de plek in het woord waar de letter(s) staan
def zoekletterindex(woord2,letter):
    indexes = []
    for index,letter2 in enumerate(woord2):
        if letter2 == letter:
            indexes.append(index)
    return indexes
            
woord = ''
aantal_fouten = len(galg)-1
woorden = ('skyrim', 'minecraft', 'worldofwarcraft', 'portal', 'thewitcher', 'darksouls', 'rocketleague')
woordnummer = random.randint(0 ,len(woorden) -1)
fouten = 0
letters = []

spelers = input('Speel je alleen of met zijn 2en? Voer 1, 2 of S in. 1 betekent 1 speler, 2 betekent 2 spelers en S betekent stoppen')
if spelers == '1':
    woord = random.choice(woorden)
    lengte = (["_ "]*len(woord))
elif spelers == '2':
    woord = input('Typ een woord in en zorg dat de andere speler deze niet ziet')
    lengte = (["_ "]*len(woord))
elif spelers == 's':
    input('Je hebt ervoor gekozen om het programma af te sluiten, druk op enter om dit voort te zetten')
    SystemExit
    
while fouten < aantal_fouten != woord:
    print(galg[fouten])
    print('Je hebt de letters', letters, 'al gebruikt')
    print('Je hebt tot nu toe het woord\n', lengte)
    letter = input('\nGeef een letter ')
    letters.append(letter)
    print(woord)

    if letter in woord:
        locaties = zoekletterindex(woord,letter)
        for index,locatie in locaties:
            lengte[locatie] is letter
            
        print('Hoppa lekker bezig hij zit er in')
    elif letter not in woord:
        print('Jammer pik die zit er niet in')
        fouten = fouten + 1
        
print(galg[fouten])
print('ja je bent af homo')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
