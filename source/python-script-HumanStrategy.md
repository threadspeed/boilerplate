---
title: python script HumanStrategy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'HumanStrategy'

Functions in program: 
* `def human_strategy(grid):`

Modules used in program: 
* `import random`

## python HumanStrategy

Python example: HumanStrategy

```python
import random
from Warships import Point
from StrategyTester import test_strategy

wins = [0 for i in range(101)]
num_of_games = 10**6

def human_strategy(grid):
    mode = "HUNT" # It may be "HUNT" or "DESTROY"

    def do_check(coords):
        if not grid.is_checked(coords):
            return grid.check(coords)
        return "MISS"

    def destroy(first_ship_coords):

        def list_of_eligible_coords(coords):
            coords_list = []
            for i in Point.directions:
                try:
                    coords_list.append(coords.move(i))
                except ValueError:
                    pass
            return coords_list

        def find_next_ship_cell(possible_coords):
            while True:  # powtarzaj, dopóki trafisz na pole ze statkiem
                random_coords = random.choice(possible_coords)  # weź dowolne pole z dostępnych
                possible_coords.remove(random_coords)
                result = do_check(random_coords)  # sprawdź to pole
                if "MISS" in result:
                    pass
                elif "HIT" in result:
                    return random_coords
                elif "SUNK" in result:
                    return None # zatopiony, nie trzeba szukać dalej

        def find_direction_of_ship(first_coords, second_coords):
            if first_ship_coords.x == next_coords.x - 1 or first_ship_coords.x - 1 == next_coords.x:  # sprawdzamy na jakiej
                # linii znajduje się statek:
                return ["left", "right"]  # poziomej, czy...
            else:
                return ["down", "up"]  # pionowej

        def find_rest_of_ship(directions, first_coords, next_coords):
            is_ship_cell = True
            direction_1 = random.choice(directions)  # wybierz kierunek startowy
            while is_ship_cell:  # powtarzaj, dopóki skończą się pole statku na linii
                try:
                    next_coords = next_coords.move(direction_1)
                    result = do_check(next_coords)
                    if "MISS" in result:
                        is_ship_cell = False  # skończyła się linia, ale nadal nie zatopiliśmy statku; idziemy w drugą stronę
                    elif "HIT" in result:
                        is_ship_cell = True
                    elif "SUNK" in result:
                        return
                except ValueError:
                    break

            is_ship_cell = True
            directions.remove(direction_1)
            direction_2 = directions[0]
            while is_ship_cell:  # powtarzaj, dopóki skończą się pole statku na linii
                try:
                    first_coords = first_coords.move(direction_2)
                    result = do_check(first_coords)
                    if "MISS" in result:
                        is_ship_cell = False  # NIGDY nie powinno zajść
                    elif "HIT" in result:
                        is_ship_cell = True
                    elif "SUNK" in result:
                        return
                except ValueError:
                    break

        possible_coords = list_of_eligible_coords(first_ship_coords)  # wybierz dostępne pola
        next_coords = find_next_ship_cell(possible_coords)  # znajdź następne pole
        if next_coords is None:
            return
        direction_of_ship = find_direction_of_ship(first_ship_coords, next_coords)
        find_rest_of_ship(direction_of_ship, first_ship_coords, next_coords)

    def hunt():
        coords = Point(random.randint(0, 9), random.randint(0, 9))
        result_of_check = do_check(coords)
        if result_of_check is None or "SUNK" in result_of_check or "MISS" in result_of_check:
            mode = "HUNT"
            first_ship_coords = Point(0,0)
        elif "HIT" in result_of_check:
            mode = "DESTROY"
            first_ship_coords = coords
        return mode, first_ship_coords

    first_ship_coords = None
    while not grid.is_won():
        if mode == "HUNT":
            mode, first_ship_coords = hunt()
        elif mode == "DESTROY":
            destroy(first_ship_coords)
            mode = "HUNT"
test_strategy(human_strategy, 10**2)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
