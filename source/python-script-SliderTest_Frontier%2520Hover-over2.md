---
title: python script SliderTest Frontier%2520Hover-over2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'SliderTest Frontier%2520Hover-over2'


Modules used in program: 
* `import time`
* `import HtmlTestRunner`
* `import unittest`
* `import HtmlTestRunner`
* `import unittest`

## python SliderTest Frontier%2520Hover-over2

Python example: SliderTest Frontier%2520Hover-over2

```python
import unittest
import HtmlTestRunner
from HtmlTestRunner import HTMLTestRunner
from io import StringIO
import unittest
import HtmlTestRunner
from selenium import webdriver
from selenium.webdriver.common.action_chains import ActionChains
import time




class allHoverOver(unittest.TestCase):

     @classmethod
     def setUpClass(inst):
        inst.driver = webdriver.Chrome('C://chromedriver.exe');
        inst.driver.maximize_window()
        inst.driver.get('http://frontier.com');
        time.sleep(5)


     def test_btn_business(self):
        element = self.driver.find_element_by_id("js-track-masthead-business-link")
        color1 = element.value_of_css_property('color')
        actions = ActionChains(self.driver)
        actions.move_to_element(element).perform()
        color2 = element.value_of_css_property('color')
        self.assertNotEqual(color1, color2)

     def test_btn_enterprise(self):
        element = self.driver.find_element_by_id("js-track-masthead-enterprise-link")
        color1 = element.value_of_css_property('color')
        actions = ActionChains(self.driver)
        actions.move_to_element(element).perform()
        color2 = element.value_of_css_property('color')
        self.assertNotEqual(color1, color2)

     def test_btn_wholesale(self):

        element = self.driver.find_element_by_id("js-track-masthead-wholesale-link")
        color1 = element.value_of_css_property('color')
        actions = ActionChains(self.driver)
        actions.move_to_element(element).perform()
        color2 = element.value_of_css_property('color')
        self.assertNotEqual(color1, color2)



     def test_menu_shop(self):

        element = self.driver.find_element_by_id("ecomm-rv-anchor-Shop")
        actions = ActionChains(self.driver)
        actions.move_to_element(element).perform()
        respuesta = self.driver.find_element_by_xpath("//*[@id='ecomm-rv-dd-Shop']/ul").is_displayed()
        self.assertTrue(respuesta)

     def test_menu_myAccount(self):

        element = self.driver.find_element_by_id("ecomm-rv-anchor-MyAccount")
        actions = ActionChains(self.driver)
        actions.move_to_element(element).perform()
        respuesta = self.driver.find_element_by_xpath("//*[@id='ecomm-rv-dd-MyAccount']/ul").is_displayed()
        self.assertTrue(respuesta)

     def test_menu_support(self):

        element = self.driver.find_element_by_id("ecomm-rv-anchor-Support")
        actions = ActionChains(self.driver)
        actions.move_to_element(element).perform()
        respuesta = self.driver.find_element_by_xpath("//*[@id='ecomm-rv-dd-Support']/ul").is_displayed()
        self.assertTrue(respuesta)


     def test_btn_shopPlans(self):
        element = self.driver.find_element_by_id("js-track-shop-home-hero")
        color1 = element.value_of_css_property('color')
        actions = ActionChains(self.driver)
        actions.move_to_element(element).perform()
        color2 = element.value_of_css_property('color')
        self.assertNotEqual(color1, color2)


     @classmethod
     def tearDownClass(inst):
        inst.driver.quit()




if __name__ == '__main__':
     unittest.main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
