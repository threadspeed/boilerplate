---
title: python script date (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'date'

Functions in program: 
* `def radiosidewinder(bot, trigger):`

## python date

Python mysql example: date

```python
from random import choice

from willie import module

location = [
    "Go on a search for as many good climbing trees as possible",
    "Go to a major chain bookstore",
    "Have them dressed up as a ghost and you dress up as Pacman",
    "Create photo evidence suggesting that you went on an adventure",
    "Dress up as superheroes",
    "Build forts out of furniture and blankets",
    "Try and visit as many people as you can in one night",
    "Go to the airport",
    "Write a piece of fiction together",
    "Dress to the nines",
    "Do the lamest tourist thing in your area that you have both secretly wanted to do forever",
    "In the middle of the night, drive to the beach",
    "Drive somewhere unknown",
    "Go to a minor league baseball game under the stars",
    "Go around the city",
    "Walk around a city",
    "With camera and pair of boots",
    "Walk around the city all night",
    "Go to a restraunt",
    "Rent a movie you've never seen before"
]

activities = [
    "climb as high as you both can",
    "leave notes to future readers",
    "Walk around downtown holding hands",
    "stop at least one petty crime ie. jaywalking, littering",
    "wage war with paper airplanes",
    "turn as many things inside their apartment upside down as you can",
    "get the cheapest, soonest departing flight to anywhere when you show up",
    "Ask strangers when you get stuck",
    "test drive very expensive vehicles at an auto dealership",
    "Have an unabashed good time",
    "Have a breakfast picnic, then fall asleep together",
    "have dinner in a city you've never been to",
    "Tell each other stories about how bad you are at athletics",
    "draw hearts with equations inside",
    "Perform short silent plays",
    "Make photolog of a day in the life of the invisible man",
    "Find a place to eat breakfast",
    "Convince the cook to create something completely new for you",
    "Set on mute and improvise dialogue",
]

twists = [
    "Compile photo evidence",
    "In copies of your favorite books",
    "Whenever anyone sees you two, pretend to be embarrassed, and run off screaming 'wocka wocka wocka'",
    "That didn't really happen",
    "Without them noticing",
    "Stay there for a weekend",
    "Ask strangers when you get stuck",
    "Have an unabashed good time!",
    "Bring a parasol",
    "With fake names",
    "Eat lots of Cracker Jacks",
    "On random things",
    "In front of security cameras",
    "Find a place to eat breakfast at dawn",
]

idea = lambda: "{location}. {activity}. {twist}.".format(
    location=choice(location).capitalize(),
    activity=choice(activities).capitalize(),
    twist=choice(twists).capitalize()
)


@module.rule('date idea')
def radiosidewinder(bot, trigger):
    bot.reply(idea())
        


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
