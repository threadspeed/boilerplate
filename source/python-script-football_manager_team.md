---
title: python script football manager team (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'football manager team'


Modules used in program: 
* `import random`

## python football manager team

Python mysql example: football manager team

```python
import random


class Team:
    """
    team has a single manager - one to one
    team has many players - one to many
    team has a place/ranking in a league - one to one
    team plays games against other teams
    """

    def __init__(self, name):
        self.name = name
        self.players = list()

        self.wins = 0
        self.losses = 0


class Manager:
    """
    runs a team

    """
    pass


class Game:
    """
    game belongs to a league
    plays a game between two leagues
    """

    def __init__(self, league, home_team, away_team):
        self.league = league
        self.home_team = home_team
        self.away_team = away_team

        print("{} vs. {}".format(self.home_team, self.away_team))

    def play(self):
        """
        play the game, return who won
        True - home team won, False - away team won
        """
        print("Play begins")

        print("Play ends")
        print("Home team wins")

        return True


class League:
    """
    league has many teams
    each team is going to have a ranking within this league
    """

    def __init__(self, name='League 1'):
        self.name = name
        self.teams = list()

        self.ranking = 0

    def set_teams(self, teams):
        self.teams = teams

    def play_season(self, num_of_rounds):
        """
        play 10 rounds between all teams in the season
        :param num_of_rounds games to be played in season
        :return:
        """
        num_of_rounds = 10
        for i in range(num_of_rounds):
            self.play_round()

    def play_round(self):
        """
        play a round, which has 10 games
        """
        num_teams = len(self.teams)
        num_games = num_teams // 2

        teams_to_play = self.teams.copy()

        for game_num in range(num_games):
            home_team = random.choice(teams_to_play)
            teams_to_play.remove(home_team)

            away_team = random.choice(teams_to_play)
            teams_to_play.remove(away_team)

            game = Game(self, home_team, away_team)
            winner = game.play()

            if winner:

                home_team.wins += 1
                away_team.losses += 1

            else:
                away_team_team.wins += 1
                home_team.losses += 1


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
