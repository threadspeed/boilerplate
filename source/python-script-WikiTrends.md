---
title: python script WikiTrends (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'WikiTrends'

Functions in program: 
* `def log(msg):`

Modules used in program: 
* `import urllib`
* `import re`
* `import os`
* `import datetime`
* `import random`
* `import pickle`
* `import pandas as pd`
* `import csv`
* `import random`
* `import time`

## python WikiTrends

Python example: WikiTrends

```python


import time
from selenium import webdriver
from selenium.webdriver.support.wait import WebDriverWait
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.keys import Keys
import random
import csv
import pandas as pd
import pickle
import random
import datetime
import os
import re
from itertools import izip_longest
import urllib

def log(msg):
    print("{} {}".format(str(datetime.datetime.now()), msg))

class wiki_trends():
    
    def __init__(self):
        self.skills = pickle.load(open('search.p'))
        self.batches = self.batcher(self.skills,5)
        self.driver = webdriver.Firefox()
        self.driver.get('http://www.wikipediatrends.com')
        self.current_filename = ''
        self.current_searched_words = []
        self.current_lst = []
        self.full_df = pd.DataFrame()
        self.cururl = 'http://www.wikipediatrends.com/'

    def batcher(self,lst,n):
        return list(izip_longest(*(iter(lst),) * n))
    

    def scraper(self,lst):
        if self.driver.current_url != 'http://www.wikipediatrends.com':
            self.driver.get('http://www.wikipediatrends.com')
        log('starting to type the things in: ' + str(lst))
        for wrd in lst:
            inputter = self.driver.find_element_by_class_name('tt-input')
            inputter.send_keys(str(wrd)+'\n')
            time.sleep(random.randint(1,2))
            if self.driver.current_url == self.cururl:
                try:
                    log("pressing enter didnt work, doing autocomplete")
                    inputter = self.driver.find_element_by_class_name('tt-input')
                    inputter.send_keys(Keys.DELETE) # delete the old entry that didnt return anything
                    time.sleep(random.randint(1,2))
                    inputter = self.driver.find_element_by_class_name('tt-input')
                    inputter.send_keys(str(wrd))#add the /n so it auto-completes
                    time.sleep(random.randint(1,2))
                    #hover and click the suggestion so we at least get something
                    autocom = self.driver.find_element_by_class_name('tt-suggestion')
                    hov = ActionChains(wt.driver).move_to_element(autocom)
                    hov.perform()
                    autocom.click()
                except:
                    log(wrd + 'is unsearchable')
            self.cururl = self.driver.current_url
            time.sleep(random.randint(2,5))

        self.current_lst = list(lst)
        this_url = self.driver.current_url
        self.searched_words = re.split('.query\[\]=',urllib.unquote_plus(this_url))[1:]
        self.searched_words = [x.replace(' ','_') for x in self.searched_words]
        log('starting download of file')
        csv_button = self.driver.find_element_by_partial_link_text('CSV')
        csv_button.click()
        self.current_filename = '-'.join(self.searched_words) + '-trends_Nov2014.csv' # will need to change next month
        log('file downloaded')
    
    def add_to_df(self, filename):
        log('reading the file')
        try:
            new_df = pd.DataFrame.from_csv('Downloads/'+filename,header=1)
            new_df.columns = [a.replace('"','').strip() for a in new_df.columns]
            new_df.columns = ['_-_'.join(x) for x in zip(new_df.columns,self.current_lst)]
            if len(self.full_df)==0:
                self.full_df = new_df
                log('created df')
            else:
                self.full_df = pd.concat([self.full_df,new_df], axis = 1)
                log('added to df')
            self.full_df.to_csv('full_trend_df.csv')
            os.remove('Downloads/' + filename)
            log('removed ' + filename + ' so it wont clog space')
        except:
            log(str(self.current_lst) + "didnt work")
        
if __name__ == "__main__":
    wt = wiki_trends()
    for btch in wt.batches:
        wt.scraper(btch)w
        time.sleep(5)
        wt.add_to_df(wt.current_filename)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
