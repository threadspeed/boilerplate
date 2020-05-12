---
title: python script Warships (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Warships'

Functions in program: 
* `def gen_rand_grid():`

Modules used in program: 
* `import random`

## python Warships

Python mysql example: Warships

```python
import random


class Cell:
    def __init__(self):
        self.is_ship_cell = False
        self.checked = False

    def check(self, *args):
        if len(args) == 0:
            return self.checked
        elif args[0]:
            self.checked = True

    def ship_cell(self, *args):
        if len(args) == 0:
            return self.is_ship_cell
        elif args[0]:
            self.is_ship_cell = True

    def __eq__(self, other):
        return self.ship_cell() == other.ship_cell and self.check() == other.check()

class Point:
    directions = ["left", "right", "up", "down"]

    def __init__(self, x, y):
        if x < 0 or x > 9:
            raise ValueError("X must be in range 0-9!")
        if y < 0 or y > 9:
            raise ValueError("Y must be in range 0-9!")
        self.x, self.y = x, y

    def move(self, direction: str):
        direction = direction.lower()
        if direction == "left":
            return Point(self.x - 1, self.y)
        elif direction == "right":
            return Point(self.x + 1, self.y)
        elif direction == "up":
            return Point(self.x, self.y - 1)
        elif direction == "down":
            return Point(self.x, self.y + 1)
        else:
            raise ValueError("Direction must be 'up', 'down', 'left' or 'right'!")

    def __eq__(self, other):
        if self.x == other.x and self.y == other.y:
            return True
        return False

class LengthError(Exception):
    pass

class SunkError(Exception):
    pass

class Ship:

    def __init__(self, length):
        self.points = []
        self.length = length
        self.hits = 0

    def add_point(self, point):
        if len(self.points) < self.length:
            self.points.append(point)
        else:
            raise LengthError("Can't assign more than {} points to ship of length {}!".format(self.length, self.length))

    def has_point(self, point_to_find):
        for point in self.points:
            if point == point_to_find:
                return True
        return False

    def hit(self):
        if self.hits < self.length:
            self.hits += 1
        else:
            raise SunkError("The ship had sunk previously!")

    def is_sunk(self):
        return self.hits == self.length

    def __len__(self):
        return self.length

class Grid:
    def __init__(self):
        self.grid = self.generate_blank_grid()
        self.checked_cells = 0
        self.checked_ship_cells = 0
        self.ships = []

    def generate_blank_grid(self):
        grid = []
        for x in range(10):
            grid.append([])
            for y in range(10):
                grid[x].append(Cell())
        return grid

    def place_ship(self, coords, direction, length):
        ship = Ship(length)
        valid_coords = []
        for i in range(length):
            self.__check_ship_nearby(coords)
            valid_coords.append(coords)
            if i != (length - 1):
                coords = coords.move(direction)
        for coord in valid_coords:
            self.__cell_at(coord).ship_cell(True)
            ship.add_point(coord)
        self.ships.append(ship)

    def __check_ship_nearby(self, coords):
        def check_offset(coords, x_offset, y_offset):
            if coords.x + x_offset < 0 or coords.x + x_offset > 9:
                return
            if coords.y + y_offset < 0 or coords.y + y_offset > 9:
                return
            if self.__cell_at(Point(coords.x + x_offset, coords.y + y_offset)).ship_cell():
                raise ValueError("You can't place ship here!")

        offsets = [-1, 0, 1]
        for x in offsets:
            for y in offsets:
                check_offset(coords, x, y)

    def __cell_at(self, coords):
        return self.grid[coords.y][coords.x]

    def check(self, coords):
        self.__cell_at(coords).check(True)
        self.checked_cells += 1
        if self.__cell_at(coords).ship_cell():
            self.checked_ship_cells += 1
            for i in self.ships:
                if i.has_point(coords):
                    i.hit()
                    if i.is_sunk():
                        return "SUNK", len(i)
                    return "HIT"
        return "MISS"

    def is_checked(self, coords):
        return self.__cell_at(coords).check()

    def is_won(self):
        return self.checked_ship_cells == (4 * 1 + 3 * 2 + 2 * 3 + 1 * 4)

    def __str__(self):
        string = " 0123456789\n"
        for i, row in enumerate(self.grid):
            string += str(i)
            for item in row:
                if item.ship_cell():
                    if item.check():
                        string += "V"
                    else:
                        string += "O"
                else:
                    if item.check():
                        string += "X"
                    else:
                        string += "."
            string += "\n"
        return string


def gen_rand_grid():
    grid = Grid()

    def place_random_ship(size):
        ship_placed = False
        while not ship_placed:
            coords = Point(random.randint(0, 9), random.randint(0, 9))
            direction = random.choice(Point.directions)
            try:
                grid.place_ship(coords, direction, size)
                ship_placed = True
            except ValueError:
                pass

    for i in range(1):
        place_random_ship(4)
    for i in range(2):
        place_random_ship(3)
    for i in range(3):
        place_random_ship(2)
    for i in range(4):
        place_random_ship(1)

    return grid


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
