---
title: python script wrapper-1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'wrapper-1'


Modules used in program: 
* `import random`
* `import json`
* `import pandas as pd`
* `import tensorflow as tf`
* `import numpy as np`

## python wrapper-1

Python example: wrapper-1

```python
# -*- coding: utf-8 -*-
import numpy as np
import tensorflow as tf
import pandas as pd
import json
import random

from poke_env.player_configuration import PlayerConfiguration
from poke_env.player.env_player import Gen7EnvSinglePlayer
from poke_env.player.random_player import RandomPlayer
from poke_env.player.frozen_rl_player import FrozenRLPlayer
from poke_env.player.frozen_rl_player_ratio import FrozenRLPlayerRatio
from poke_env.server_configuration import LocalhostServerConfiguration

from rl.agents.cem import CEMAgent
from rl.policy import LinearAnnealedPolicy, EpsGreedyQPolicy
from rl.memory import SequentialMemory, EpisodeParameterMemory
from tensorflow.keras.layers import Dense, Flatten, Activation
from tensorflow.keras.models import Sequential
from tensorflow.keras.optimizers import Adam


# We define our RL player
# It needs a state embedder and a reward computer, hence these two methods
class SimpleRLPlayer(Gen7EnvSinglePlayer):
    def embed_battle(self, battle):
        # -1 indicates that the move does not have a base power
        # or is not available
        moves_base_power = -np.ones(4)
        moves_dmg_multiplier = np.ones(4)
        for i, move in enumerate(battle.available_moves):
            moves_base_power[i] = (
                move.base_power / 100
            )  # Simple rescaling to facilitate learning
            if move.type:
                moves_dmg_multiplier[i] = move.type.damage_multiplier(
                    battle.opponent_active_pokemon.type_1,
                    battle.opponent_active_pokemon.type_2,
                )

        # We count how many pokemons have not fainted in each team
        remaining_mon_team = (
            len([mon for mon in battle.team.values() if mon.fainted]) / 6
        )
        remaining_mon_opponent = (
            len([mon for mon in battle.opponent_team.values() if mon.fainted]) / 6
        )

        # Final vector with 10 components
        return np.concatenate(
            [
                moves_base_power,
                moves_dmg_multiplier,
                [remaining_mon_team, remaining_mon_opponent],
            ]
        )

    def compute_reward(self, battle) -> float:
        return self.reward_computing_helper(
            battle, fainted_value=2, hp_value=1, victory_value=30
        )


class MaxDamagePlayer(RandomPlayer):
    def choose_move(self, battle):
        # If the player can attack, it will
        if battle.available_moves:
            # Finds the best move among available ones
            best_move = max(battle.available_moves, key=lambda move: move.base_power)
            return self.create_order(best_move)

        # If no attack is available, a random switch will be made
        else:
            return self.choose_random_move(battle)

NB_TRAINING_STEPS = 10000
NB_EVALUATION_EPISODES = 100

# variable for naming .csv files.
# Change this according to whether the training process was carried out against a random player or a max damage player
TRAINING_OPPONENT = 'RandomPlayer'
FROZEN_RL_PRESENT = True

tf.random.set_seed(0)
np.random.seed(0)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
