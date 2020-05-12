---
title: python script pygame snake (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pygame snake'


Modules used in program: 
* `import time`
* `import random`
* `import sys`
* `import random`

## python pygame snake

Python mysql example: pygame snake

```python
import random
import sys
import random
import time


class Game():
    def __init__(self):
        self.screen_width = 720
        self.screen_height = 460

        self.red   = pygame.Color('red')
        self.green = pygame.Color('green')
        self.black = pygame.Color('black')
        self.white = pygame.Color('white')
        self.brown = pygame.Color('brown')

        self.fps_controller = pygame.time.Clock()

        self.score = 0

    check_errors = pygame.init()
    if check_errors[1] > 0:
        sys.exit()
    else:
        print('Ok')

    def set_surface_and_title(self):
        self.play_surface = pygame.display.set_mode((
            self.screen_width, self.screen_height))
        pygame.display.set_caption('Snake Game')

    def event_loop(self, change_to):
        for event in pygame.event.get():
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_RIGHT or event.key == ord('d'):
                    change_to = "RIGHT"
                elif event.key == pygame.K_LEFT or event.key == ord('a'):
                    change_to = "LEFT"
                elif event.key == pygame.K_UP or event.key == ord('w'):
                    change_to = "UP"
                elif event.key == pygame.K_DOWN or event.key == ord('s'):
                    change_to = "DOWN"
                elif event.key == pygame.K_ESCAPE:
                    pygame.quit()
                    sys.exit()
        return change_to
    def refresh_screen(self):
        pygame.display.flip()
        game.fps_controller.tick(23)
    def show_score(self, choice=1):
        s_font = pygame.font.SysFont('monaco', 24)
        s_surf = s_font.render(
            'Score: {}'.format(self.score), True, self.black)
        s_rect = s_surf.get_rect()
        if choice:
            s_rect.midtop = (80, 10)
        else:
            s_rect.midtop = (360, 120)
		self.play_surface.blit(s_surf, s_rect)
    def game_over(self):
		go_font = pygame.font.SysFont('monaco', 72)
		go_surf = go_font.render('Game over', True, self.red)
		go_rect = go_surf.get_rect()
		go_rect.midtop = (360, 15)
		self.play_surface.blit(go_surf, go_rect)
		self.show_score(0)
		pygame.display.flip()
		time.sleep(3)
		pygame.quit()
		sys.exit()
		
		
class Snake():
	def __init__(self, snake_color):
		self.shake_head_pos = [100, 50]
		self.shake_body = [[100, 50], [90, 50], [80, 50]]
		self.snake_color = snake_color
		self.direction = "RIGHT"
		self.change_to = sself.direction
	


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
