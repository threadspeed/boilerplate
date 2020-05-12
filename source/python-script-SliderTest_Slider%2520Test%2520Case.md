---
title: python script SliderTest Slider%2520Test%2520Case (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'SliderTest Slider%2520Test%2520Case'


Modules used in program: 
* `import random`
* `import time`
* `import unittest`
* `import unittest`

## python SliderTest Slider%2520Test%2520Case

Python example: SliderTest Slider%2520Test%2520Case

```python
import unittest
from io import StringIO
import unittest
from selenium import webdriver
from selenium.webdriver.common.action_chains import ActionChains
import time
import random


class paginaBanco(unittest.TestCase):
        @classmethod
        def setUpClass(self):
            self.driver = webdriver.Chrome('C://chromedriver.exe');
            self.driver.get('https://surfmangd.se/data/20')
            self.driver.maximize_window()
            time.sleep(5)

        def test_Slider(self):
            slider = self.driver.find_element_by_xpath("//*[@id='root']/div/div[3]/div[1]/div[2]")
            posicionXY1 = slider.location
            posicionX1 = posicionXY1['x']
            monto1 = int(self.driver.find_element_by_xpath("//*[@id='root']/div/div[2]").text)
            print('El monto inicial era:')
            print(monto1)
            nuevaPos = random.choice(range(0, 100))
            #nuevaPos = 50
            print('La nueva posicion aleatoria es')
            print(nuevaPos)
            if nuevaPos>monto1:
                avanzar = nuevaPos-monto1
                print('El cabezal se movio a la derecha la cantidad de')
                print(avanzar)
                avanzarReal = avanzar*18.5
                actions = ActionChains(self.driver)
                actions.move_to_element(slider).drag_and_drop_by_offset(slider, avanzarReal, 0)
                actions.perform()
                time.sleep(2)
                posicionXY2 = slider.location
                posicionX2 = posicionXY2['x']
                monto2 = int(self.driver.find_element_by_xpath("//*[@id='root']/div/div[2]").text)
                montocalculado = monto1+avanzar
                self.assertTrue(monto2==montocalculado)
            else:
                if nuevaPos < monto1:
                    avanzar = monto1 - nuevaPos
                    print('El cabezal se movio a la izquierda la cantidad de')
                    print(avanzar)
                    avanzarReal = avanzar * 18.5
                    actions = ActionChains(self.driver)
                    actions.move_to_element(slider).drag_and_drop_by_offset(slider, -avanzarReal, 0)
                    actions.perform()
                    time.sleep(2)
                    posicionXY2 = slider.location
                    posicionX2 = posicionXY2['x']
                    monto2 = int(self.driver.find_element_by_xpath("//*[@id='root']/div/div[2]").text)
                    montocalculado = monto1 - avanzar
                    self.assertTrue(monto2 == montocalculado)
                else:
                    avanzar = 0
                    avanzarReal = avanzar * 18.5
                    actions = ActionChains(self.driver)
                    actions.move_to_element(slider).drag_and_drop_by_offset(slider, avanzarReal, 0)
                    actions.perform()
                    time.sleep(2)
                    posicionXY2 = slider.location
                    posicionX2 = posicionXY2['x']
                    monto2 = int(self.driver.find_element_by_xpath("//*[@id='root']/div/div[2]").text)
                    montocalculado = monto1 + avanzar
                    self.assertTrue(monto2 == montocalculado)

        @classmethod
        def tearDownClass(self):
            self.driver.quit()

if __name__ == '__main__':
     unittest.main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
