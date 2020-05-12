---
title: python script SliderTest Fontier%2520hover-over (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'SliderTest Fontier%2520hover-over'


Modules used in program: 
* `import random`
* `import time`
* `import unittest`
* `import unittest`
* `import random`
* `import time`
* `import unittest`

## python SliderTest Fontier%2520hover-over

Python mysql example: SliderTest Fontier%2520hover-over

```python
import unittest
#from nose.tools import assert_equal
from selenium import webdriver
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select
from selenium.common.exceptions import NoSuchElementException
import time
import random
import unittest
from io import StringIO
import unittest
from selenium import webdriver
from selenium.webdriver.common.action_chains import ActionChains
import time
import random

class hoverOverFrontier(unittest.TestCase):

    @classmethod
    def setUpClass(self):
        #self.driver = webdriver.Chrome('C://chromedriver.exe');
        self.driver = webdriver.Firefox(executable_path=r"C:\geckodriver.exe");
        self.driver.get('http://frontier.com')
        self.driver.maximize_window()
        time.sleep(5)

    def test_Slider(self):
        #Over en Shop
        Shop = self.driver.find_element_by_id('ecomm-rv-dd-Shop')
        menuShop = self.driver.find_element_by_css_selector('[class="nav header--custom__nav-list js-nav-list"] > [id="ecomm-rv-dd-Shop"] > [class="dropdown-menu"]')
        actions = ActionChains(self.driver)
        actions.move_to_element(Shop).perform()
        self.assertTrue(menuShop.is_displayed())

        #Over en My Account
        MyAccount = self.driver.find_element_by_id('ecomm-rv-dd-MyAccount')
        menuMyaccount = self.driver.find_element_by_css_selector('[class="nav header--custom__nav-list js-nav-list"] > [id="ecomm-rv-dd-MyAccount"] > [class="dropdown-menu"]')
        actions = ActionChains(self.driver)
        actions.move_to_element(MyAccount).perform()
        self.assertTrue(menuMyaccount.is_displayed())

        #Over en Support
        Support = self.driver.find_element_by_id('ecomm-rv-dd-Support')
        menuSupport = self.driver.find_element_by_css_selector('[class="nav header--custom__nav-list js-nav-list"] > [id="ecomm-rv-dd-Support"] > [class="dropdown-menu"]')
        actions = ActionChains(self.driver)
        actions.move_to_element(Support).perform()
        self.assertTrue(menuSupport.is_displayed())

        #Check slider banner
        slider1= self.driver.find_element_by_class_name('data-slick-index="1"')
        slider1 = self.driver.find_element_by_class_name('data-slick-index="2"')
        slider1 = self.driver.find_element_by_class_name('data-slick-index="2"')

        '''
        #Over en Shop plans href
        plans = self.driver.find_element_by_id('js-track-shop-home-hero')
        plans.location_once_scrolled_into_view
        colorfondo1 = plans.value_of_css_property('color')
        self.driver.implicitly_wait(4)
        actions = ActionChains(self.driver)
        actions.move_to_element(plans).perform()
        colorfondo2 = plans.value_of_css_property('color')
        self.assertNotEqual(colorfondo1, colorfondo2)
        
        #Over en Shop plans2 href
        plans2 = self.driver.find_element_by_id('js-track-shop-plans-section-home')
        plans2.location_once_scrolled_into_view
        self.driver.implicitly_wait(4)
        colorfondo1 = plans2.value_of_css_property('color')
        actions = ActionChains(self.driver)
        actions.move_to_element(plans2).perform()
        colorfondo2 = plans2.value_of_css_property('color')
        self.assertNotEqual(colorfondo1, colorfondo2)

        #Over en Shop Check avaliability href js-track-shop-plans-section-home
        ca = self.driver.find_element_by_id('js-track-home-check-availability-section')
        ca.location_once_scrolled_into_view
        self.driver.implicitly_wait(1)
        colorfondo1 = ca.value_of_css_property('color')
        actions = ActionChains(self.driver)
        actions.move_to_element(ca).perform()
        colorfondo2 = ca.value_of_css_property('color')
        self.assertNotEqual(colorfondo1, colorfondo2)
        '''
    @classmethod
    def tearDownClass(self):
        self.driver.quit()

if __name__ == '__main__':
     unittest.main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
