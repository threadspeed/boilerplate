---
title: python script SpatialModel model process (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'SpatialModel model process'


Modules used in program: 
* `import random`

## python SpatialModel model process

Python mysql example: SpatialModel model process

```python
from mesa import Model
from mesa.space import ContinuousSpace
from mesa.time import RandomActivation
from model_cells import CellAgent
import random


class ProcessModel(Model):

    def __init__(self, initial_densities, width, height, density_radius=1, max_cells_per_unit=10,
                 deterministic_death=False, age_limit=20, death_ratio=0.2, death_period_limit=0):

        super().__init__()

        self.num_selfish, self.num_cooperative, self.num_tkiller = initial_densities
        self.num_tumor_cells = self.num_selfish + self.num_cooperative
        self.num_total = self.num_tumor_cells + self.num_tkiller

        self.space = ContinuousSpace(width, height, True)
        self.schedule = RandomActivation(self)

        self.density_radius = density_radius
        self.max_cells_per_unit = max_cells_per_unit
        self.deterministic_death = deterministic_death
        self.age_limit = age_limit
        self.death_ratio = death_ratio
        self.death_period_limit = death_period_limit

        self.cells2add = []
        self.cells2delete = []

        added_selfish, added_cooperative, added_tkiller = 0, 0, 0
        random.seed(100)

        def n_cells():
            return added_selfish + added_cooperative + added_tkiller

        while n_cells() < self.num_total:

            rnd_i = random.randrange(3)

            if rnd_i == 0 and added_selfish < self.num_selfish:
                a = CellAgent(n_cells(), self, rnd_i)
                added_selfish += 1

            elif rnd_i == 1 and added_cooperative < self.num_cooperative:
                a = CellAgent(n_cells(), self, rnd_i)
                added_cooperative += 1

            elif rnd_i == 2 and added_tkiller < self.num_tkiller:
                a = CellAgent(n_cells(), self, rnd_i)
                added_tkiller += 1

            else:
                continue

            self.schedule.add(a)

            # Add the agent to a random pos
            x = random.uniform(0, self.space.width)
            y = random.uniform(0, self.space.height)
            self.space.place_agent(a, (x, y))

        print(self.get_density())

    def get_density(self):
        density = [0, 0, 0]
        for cell in self.schedule.agents:
            density[cell.type] += 1
        return density

    def new_cell2add(self, cell):
        self.cells2add.append(cell)

    def new_cell2delete(self, cell):
        self.cells2delete.append(cell)

    def step(self):


        cells_to_add = []
        cells_to_delete = []


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
