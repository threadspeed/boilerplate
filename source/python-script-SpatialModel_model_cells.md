---
title: python script SpatialModel model cells (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'SpatialModel model cells'


Modules used in program: 
* `import random`

## python SpatialModel model cells

Python mysql example: SpatialModel model cells

```python
from mesa import Agent
import random
from math import pi, pow


class CellAgent(Agent):

    def __init__(self, unique_id, model, cell_type):

        super().__init__(unique_id, model)

        self.age = -1
        self.type = cell_type
        self.state = 1
        self.death_period = -1

        self.wealth = 1
        self.pos = None

    def is_alive(self):

        if self.state == 1:
            return True
        return False

    def is_dead(self):
        if self.state == 0:
            return True
        return False

    def undergo_deterministic_death(self):

        self.age += 1
        if self.age == self.model.age_limit:
            self.state = 0

        if self.is_dead() and self.death_period == self.model.death_period_limit:
            self.model.new_cell2delete(self)

    def undergo_stochastic_death(self):

        self.age += 1
        if random.random() <= self.model.death_ratio:
            self.state = 0

        if self.is_dead() and self.death_period == self.model.death_period_limit:
            self.model.new_cell2delete(self)

    def crowded_neighborhood(self):

        neighbouring_cells = self.model.space.get_neighbors(self.pos, self.model.density_radius)
        for n in neighbouring_cells:
            if n.is_alive():
                print(n.unique_id, "is alive")
            else:
                print(n.unique_id, "is dead")

        def pow_2(x):
            return pow(x, 2)

        if len(neighbouring_cells) >= (pi * pow_2(self.model.density_radius) * self.model.max_cells_per_unit):
            return True

        return False

    def give_money(self):

        cellmates = self.model.grid.get_cell_list_contents([self.pos])
        if len(cellmates) > 1:
            other = random.choice(cellmates)
            other.wealth += 1
            self.wealth -= 1

    def move(self, radius):

        possible_steps = self.model.space.get_neighbors(self.pos, radius=radius)

        new_position = random.choice(possible_steps)
        self.model.grid.move_agent(self, new_position)

    def step(self):

        if self.is_dead():
            self.death_period += 1
            print("Cell {} has death_period of {}".format(self.unique_id, self.death_period))
            return

        if self.model.deterministic_death:
            self.undergo_deterministic_death()
        else:
            self.undergo_stochastic_death()

        if self.is_dead():
            self.model.new_cell2delete(self)
            return



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
