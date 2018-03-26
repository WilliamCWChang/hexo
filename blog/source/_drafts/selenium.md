---
title: Selenium
tags:
    - coding
    - softwaree
    - testing
---



# Selenium Headless

https://intoli.com/blog/running-selenium-with-headless-chrome/

```
from selenium import webdriver

options = webdriver.ChromeOptions()

options.binary_location = '/usr/bin/google-chrome-unstable'
options.add_argument('headless')

# set the window size
options.add_argument('window-size=1200x600')

# initialize the driver
driver = webdriver.Chrome(chrome_options=options)
```



# PageObjects