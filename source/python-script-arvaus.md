---
title: python script arvaus (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'arvaus'


Modules used in program: 
* `import random #tuodaan Random-kirjasto`

## python arvaus

Python mysql example: arvaus

```python
import random #tuodaan Random-kirjasto

arvausTaken = 0 

print("Kerro nimesi.") #nimen kysyminen, jonka alla sen kirjoitus
minunNimi = input() 

numero = random.randint(1, 50) #Satunnaislukugeneraattori
print("Noh, " + minunNimi + ", ajattelen jotain lukua 1 ja 50 väliltä") #Tulostaa ohjeita käyttäjälle.

while arvausTaken < 10: #Annetaan pelaajan arvata lukua 10 kertaa
      print("Arvaa mikä luku.")
      arvaus = input()
      arvaus = int(arvaus)
      
      arvausTaken = arvausTaken + 1 #Arvausten laskeminen
      
      if arvaus < numero: #Liian pienen numeroarvauksen kertominen
        print("Liian pieni luku.")
        
      if arvaus > numero: #Liian suuren numeroarvauksen kertominen.
        print("Liian suuri luku.")
      
      if arvaus == numero: #Jos arvaus menee oikein.
        break

if arvaus == numero: 
    arvausTaken = str(arvausTaken) #Lasketaan arvausten määrä
    print("Onnea " + minunNimi +", arvasit oikean luvun " + arvausTaken + " arvauksella!") #Onnitellaan pelaajaa

if arvaus != numero: 
    numero = str(numero) #Tarkistetaan luku jota yritettiin arvata.
    print("Väärin. Luku jota ajattelin, oli" + numero +".") #Kerrotaan pelaajalle oikea luku.
quit()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
