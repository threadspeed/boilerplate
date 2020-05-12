---
title: python script random walk (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random walk'


## python random walk

Python example: random walk

```python
from random import choice

class RandomWalk():
    """КЛАСС ДЛЯ ГЕНЕРИРОВАНИЯ СЛУЧАЙНЫХ БЛУЖДАНИЙ"""
    def __init__(self, num_points=5000):
        """атрибуты блуждания. количество точек"""
        self.num_points = num_points
        
        #все блуждания начинаются с точки (0,0)
        self.x_values = [0]
        self.y_values = [0]
        
    def fill_walk(self):
        """ВЫЧИСЛЯЕТ ВСЕ ТОЧКИ БЛУЖДАНИЯ"""
        
        while len(self.x_values) < self.num_points: #шаги генерируются до достижения нужной длины
            #определяем направление и длины перемещения
            x_direction = choice([1, -1]) #выбирает значение  x_direction, возвращает 1 для движения вправо, и -1 влево
            x_distance = choice([0, 1, 2, 3, 4]) #определяет дальность перемещения в этом направлении
            x_step = x_direction * x_distance #определяем длину шага в направлении x, при+результате смещает вправо, если -, то влево
            #при нулевом результате - вертикально
            y_direction = choice([1, -1])
            y_distance = choice([0, 1, 2, 3, 4])
            y_step = y_direction * y_distance #при + результатае вверх, - вниз, нулевой - горизонтально
            #если оба значения 0, то движение останавливается, но цикл продолжается
            
            #отклонение нулевых перемещений
            if x_step == 0 and y_step == 0:
                continue
            
            #вычисление следующих значений x и y
            next_x = self.x_values[-1] + x_step #получаем следующее значение x, прибавляя к x_step последнее значение из x_values
            next_y = self.y_values[-1] + y_step
            
            self.x_values.append(next_x) #как значения получены они прибавляются к next_x
            self.y_values.append(next_y)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
