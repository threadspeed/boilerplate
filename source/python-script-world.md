---
title: python script world (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'world'

Functions in program: 
* `def __simulateHistory(verbose):`
* `def __populateWorld(populationSize, verbose):`
* `def __generateWorld(verbose):`

Modules used in program: 
* `import random`

## python world

Python mysql example: world

```python
import random
from entity import creature

global world_map
global world_season


class worldChunk:
    def __init__(self, chunkX, chunkY, chunkName):
        self.chunk_x = chunkX
        self.chunk_y = chunkY
        self.chunk_name = chunkName


## world.py
# Hard-coded temporarily before getting file reading in.
_master_chunk_name_modifier = ['Ruins of']
_master_chunk_name_list = [
    'Stallon\'s Reach', 'Kaz\'ad\'yol', 'Dur\'dum', 'Endesdroga', 'Saradum',
    'Xerexella', 'Fort Sancticus', 'Emerging Fate', 'Stalwok'
]
_master_entity_list = []
_selected_chunk_names = []
world_map = []


def __generateWorld(verbose):
    print('Preparing world for generation...')
    # Anything you need to do prior, you better do it here.
    print('Generating world using default world seed in project folder...')
    # The world will consist of a small grid to start
    # 0,0 | 1,0 | 2, 0
    # 0,1 | 1,1 | 2, 1
    # 0,2 | 1,2 | 2, 2
    # We're going to genreate the world through a for loop. We know that our world will consist 9 small 'chunks'.
    print('Grabbing world parameters...')
    for chunk_idx in range(3):
        for chunk_idy in range(3):
            # Generate random chunkname.
            temp_rnd_chunkname = _master_chunk_name_list[random.randrange(
                0, len(_master_chunk_name_list))]
            # if the name is inside the selected names array, run a while loop.
            if temp_rnd_chunkname in _selected_chunk_names:
                if verbose: print('[v:] Name already taken! Trying another name...')
                # while the generated name is in the array, look for another name.
                while temp_rnd_chunkname in _selected_chunk_names:
                    temp_rnd_chunkname = _master_chunk_name_list[
                        random.randrange(0, len(_master_chunk_name_list))]
            # Create the chunk with the random, non-taken name.
            chunkObj = worldChunk(chunk_idx, chunk_idy, temp_rnd_chunkname)
            # Add that chunk to the world and chunk name to the list.
            world_map.append(chunkObj)
            _selected_chunk_names.append(temp_rnd_chunkname)
            print('Creating chunk \'' + chunkObj.chunk_name +
                  '\' at location: (' + str(chunkObj.chunk_x) + ', ' +
                  str(chunkObj.chunk_y) + ').')
    # Initialize the _chunk_population variable by creating a dynamic dictionary.
    # This will be used during __populateWorld as a simple tally.
    global _chunks_population
    _chunks_population = {}
    for chunks in world_map:
        _chunks_population[chunks.chunk_name] = 0
    print('COMPLETE: World generation has completed with no errors.')


def __populateWorld(populationSize, verbose):
    # Defaults
    total_population_size = populationSize
    print('Attempting to populate the world...')
    print('Using default pop size:', total_population_size)
    for entity in range(total_population_size):
        # create and spawn a creature with: name, creatureType, creatureClass, and Level.
        _master_entity_list.append(
            creature(
                entity, creature.master_generic_name_list[random.randrange(
                    0, len(creature.master_generic_name_list))],
                creature.master_creature_list[random.randrange(
                    0, len(creature.master_creature_list))],
                creature.master_class_list[random.randrange(
                    0, len(creature.master_class_list))], 1, False))
        # assign creature to region.
        _master_entity_list[entity].assigned_chunk = world_map[
            random.randrange(0, len(world_map))]
        # increase population of that region.
        _chunks_population[_master_entity_list[entity].assigned_chunk.
                           chunk_name] += 1
    print('World has been populated.', populationSize,
          'total have been spawned. Including',
          creature.getLegendaryCreatureCount(), 'legendary creatures and',
          creature.getGodCount(), 'godly deities.')
    if creature.getGodCount() == 0: print('The world is currently Godless.')
    # verbose stuff.
    if verbose: print("[v:]", _chunks_population)


def __simulateHistory(verbose):
    # Simulating minor histroic events.
    creature.fightEntity(
        _master_entity_list[0],
        entityobj=_master_entity_list[random.randrange(
            0, len(_master_entity_list))])
    # iterate through list, and give everyone a turn to 'do something'.
    for entity in _master_entity_list:
        # give them an option to choose from
        entity_actions = ["wander", "fight", "idle", "converse"]
        random_action = entity_actions[random.randrange(
            0, len(entity_actions))]
        if verbose: print("[v:]", entity.name, "has decided to", random_action)
        if random_action == "wander":
            print(entity.name, 'begins to wander around.')
            # perform move function to move to another zone after a couple of wanders
        if random_action == "fight":
            print(
                entity.name, 'has started fighting with',
                _master_entity_list[random.randrange(
                    0, len(_master_entity_list))].name + '!')
            # perform move function to move to another zone after a couple of wanders


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
