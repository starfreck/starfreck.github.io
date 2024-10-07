---
title: "Want to apply as a TA at CU? I got you covered 😊"
date: "2021-07-23"
description: "Want to apply as a TA at CU? I got you covered 😊"
tags: [
    "Python",
    "Automation",
]
categories: ["Python","Coding"]
series: ["Automation"]
cover:
  image: "https://images.unsplash.com/photo-1588196749597-9ff075ee6b5b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxMTc3M3wwfDF8c2VhcmNofDE1fHx0ZWFjaGluZ3xlbnwwfHx8fDE2MjcwNzc0NDM&ixlib=rb-1.2.1&q=80&w=2000"
ShowToc: true
TocOpen: true
ShowReadingTime: true
ShowWordCount: true
---

I started working as Teaching Assistant at [Concordia University](https://www.concordia.ca/) since I was in 3rd semester of my masters. It's really a good experience to work as TA at Concordia. You will learn so many things when you are teaching students. It was really hard to land my first TA job but afterwards it was quite easy. The major trouble was I wanted to apply for all open positions in my department since I didn't know who will hire me as their TA and usually we have at least 300+ openings each semester. So, you can imagine the situation how painful it is to apply for all of them since you have to do it manually.

I used to apply manually but this year I was very busy and it was almost impossible for me apply for all openings. At that time i realized why should i create a script which can do the job for me and i can save some time. Tho it took me roughly 2.5 hours to write the script but it was worthy since I can reuse it (Actually, I cannot unfortunately since It's my last semester so I won't able to work as TA from Winter 2022) as well as others can too!

I have noticed that none of the ENCS portals have  [CAPTCHA](https://en.wikipedia.org/wiki/CAPTCHA) so you can easily automate many things. In my case I have just used for [TAAS](https://fis.encs.concordia.ca/taas/) portal.

## Few Prerequisite & Steps:
1. You should have agree to GSA Teaching Assistant policy manually before you use the script.
2. Update your personal information and Resume (It's must, without this you cannot apply)
3. Afterwards, you can go under the "Make a load request" option from main menu and set filters according to your application. (If you are good at Python you can update my script for that and just let me know I will add you in credits)
4. Download or copy the Python script from below on your system
5. Make sure you install all prerequisites for the Python script ( Selenium & Selenium webdriver ). *See Below*
6. Just add your ENCS username and Password on line number 8 & 9 respectively you run the script and you can leave it running. Make sure that you turn off your screen lock if you aren't planning to use computer whenever you will use this script.

## Code

```python3
# TA.py
# Python program to demonstrate
# selenium

import time
from selenium import webdriver
from selenium.webdriver.common.by import By

username = "" # ENCS Username
password = "" # ENCS Password
number_of_raw = 400 # How many raws you want in one page? Use Max in my case I had 366 raws so I just went with 400 which is > 366 or you can use 366 as well
delay = 5 # seconds

driver = webdriver.Firefox()
driver.get("https://fis.encs.concordia.ca/ta_hiring/")

user_name_xpath = '//*[@id="ProcessLoginAction_bean_login_username"]'
password_xpath = '//*[@id="ProcessLoginAction_bean_login_password"]'
login_submit_xpath = '//*[@id="ProcessLoginAction_loginProcessLoginAction"]'

driver.find_element_by_xpath(user_name_xpath).send_keys(username)
driver.find_element_by_xpath(password_xpath).send_keys(password)
driver.find_element_by_xpath(login_submit_xpath).click()


link = driver.find_element_by_link_text('Make teaching load request')
link.click()

number_of_raw_xpath = '//*[@id="psize"]'
driver.find_element_by_xpath(number_of_raw_xpath).clear()
driver.find_element_by_xpath(number_of_raw_xpath).send_keys(str(number_of_raw))

change_xpath = '/html/body/table[2]/tbody/tr[1]/td[2]/table/tbody/tr[4]/td/div/div[2]/div/form/span[1]/input[2]'
driver.find_element_by_xpath(change_xpath).click()

table_xpath = '//*[@id="row"]'

def apply():
    i = 0
    while True:
        table =  driver.find_element_by_xpath(table_xpath)
        td_xpath = '/html/body/table[2]/tbody/tr[1]/td[2]/table/tbody/tr[4]/td/div/div[2]/div/form/table[2]/tbody/tr[' + str(i) + ']/td[1]'
        td = table.find_elements_by_xpath(td_xpath)
        for elememt in td:
            innter_html = elememt.get_attribute('innerHTML')
            id = innter_html.split('"')[9]
            button =  driver.find_element(By.ID,id)
            if button.get_attribute("value") == "Apply":
                button.click()
                driver.switch_to.alert.accept()
                time.sleep(delay)
                return
        i += 1


j = 1
while number_of_raw:
    print("Applying..."+str(j))
    apply()
    j+=1
```

## Selenium webdrivers

1. [Chrome Webdriver](https://sites.google.com/a/chromium.org/chromedriver/downloads)
2. [Mozilla Gecko Webdriver](https://github.com/mozilla/geckodriver/releases)

## Notes

1. I do not take any responsibility for using this script use it on your own risk.
2. Your ENCS credentials are safe and this script will not share it anywhere except your computer. If you have a little know of Python you may easily see and understand about what's going on here.
3. This script isn't 100% perfect it may stuck in loop once you have applied for all positions and you may have to kill it by yourself if needed. Feel free to modify this script but add proper credits.
4. You can submit your script as an UPDATE on my email or Telegram I will update it with proper credits
5. Thanks reading & Enjoy! If you liked this feel free to drop me a email or a message 😊