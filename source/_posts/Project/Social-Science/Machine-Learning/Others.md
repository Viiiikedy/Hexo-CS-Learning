---
title: Handwritten Digit Recognition
tags: Social Science-Machine Learning
date: 2023-09-11 10:15:38
---
<style>
    .menu-item {
        display: inline-block; /* Ensure elements are horizontally aligned */
        margin-right: 20px;
        position: relative;
        padding: 5px;
        color: grey;
        text-decoration: none;
        font-size: 90%; /* Reduce font size */
    }
    .menu-item:hover {
        font-weight: bold;
        color: grey !important;
    }
    .menu-item::before {
        content: counter(item) " ";
        counter-increment: item;
        border: 1px solid black;
        background-color: transparent;
        border-radius: 50%;
        width: 20px;
        height: 20px;
        display: inline-block;
        text-align: center;
        line-height: 20px;
        margin-right: 1px;
        color: grey;
    }
    .menu-list {
        list-style: none; 
        counter-reset: item;
        padding: 0; /* Remove default padding */
    }
    .menu-list div {
        white-space: nowrap; /* Prevent wrapping of list items */
    }
</style>

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Social Science](/2023/09/11/Project/Social-Science/Scoial-Science/index.html) > [Machine Learning](/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html) > **[Others](/2023/09/11/Project/Social-Science/Machine-Learning/Others/index.html)</small>***


<ol class="menu-list">
    <div>
        <li><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html" class="menu-item">Music Genre Classification&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Text-Analysis/index.html"  class="menu-item">Text Analysis&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><strong><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Others/index.html" class="menu-item">Others&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></strong></li>
    </div>
</ol>


---
In my past year, I also exercised on some foundamental datasets
### Project 1:Handwritten Digit Recognition

1. Dataset:**MNIST** 
- 70,000 images of handwritten digits: 60,000 for training and 10,000 for testing. 
- The images are in grayscale, 28x28 pixels, and are centered to reduce preprocessing and speed up operations.
2. Model:**convolutional neural network** 
- in PyTorch and train it to recognize handwritten digits using the MNIST dataset. 

> Supported Code:https://drive.google.com/drive/folders/1Z-HiImmdSsFBaxXdVuQEJT5QSvueNj5J?usp=sharing

### Project 2:Twitter Influencer Analysis
In this study, we analyze the influence and correlation by scraping data such as posting frequency and likes from celebrities' tweets on Twitter.

```python
from selenium import webdriver
from lxml import etree
import time
import requests
import csv

def getData(key):
    options = webdriver.ChromeOptions()
    options.add_argument('--no-sandbox')
    # options.add_argument('--headless')  # 无头参数
    options.add_argument('--disable-gpu')
    # 關閉瀏覽器左上角通知提示
    prefs = {
        'profile.default_content_setting_values':
            {
                'notifications': 2
            }
    }
    options.add_experimental_option('prefs', prefs)
    # 關閉'chrome目前受到自動測試軟體控制'的提示
    options.add_experimental_option('useAutomationExtension', False)
    options.add_experimental_option('excludeSwitches', ['enable-automation'])
    driver = webdriver.Chrome(chrome_options=options) #chrome_options=
    driver.maximize_window()

    url=f'https://twitter.com/{key}'

    driver.get(url)

    time.sleep(3)

    js="var q=document.documentElement.scrollTop=0"
    driver.execute_script(js)
    time.sleep(3)

    def save(data):
        file=open('dickc_year_Time.csv','a+',newline='')
        writer=csv.writer(file)
        writer.writerow(data)
        file.close()
    T_div=driver.find_elements_by_xpath('//*[@id="react-root"]/div/div/div[2]/main/div/div/div/div/div/div[2]/div/div/div[2]/section/div/div/div')
    print(len(T_div))
    T_time_A='1'
    k=1
    y_2021=0
    y_2020=0
    y_2019=0
    y_2018=0
    y_2017=0
    for j in range(1, 100):
        for i in range(1, 100):
            try:
                T_time=driver.find_element_by_xpath(f'//*[@id="react-root"]/div/div/div[2]/main//div[2]/div/div/div[2]/section/div/div/div[{i}]/div/div/article/div//a/time').text
                T_time_B = driver.find_element_by_xpath('//*[@id="react-root"]/div/div/div[2]/main//div[2]/div/div/div[2]/section/div/div/div[2]/div/div/article/div//a/time').text

            except:
                js='window.scrollTo(0,document.body.scrollHeight)'
                driver.execute_script(js)
                driver.implicitly_wait(10)
                time.sleep(1)
                print('正在下滑')
                try:
                    T_time_A = driver.find_element_by_xpath(
                        '//*[@id="react-root"]/div/div/div[2]/main//div[2]/div/div/div[2]/section/div/div/div[2]/div/div/article/div//a/time').text
                except:
                    pass
                if (T_time_A == T_time_B):
                    k += 1
                k_num=0
                break
            print(str(T_time)+'*******\n'+str(i))
            if('2016' in str(T_time)):
                save([key,y_2021,y_2020,y_2019,y_2018,y_2017])
                driver.close()
                exit()
            elif('2020' in str(T_time)):
                y_2020+=1
            elif('2019' in str(T_time)):
                y_2019+=1
            elif('2018' in str(T_time)):
                y_2018+=1
            elif('2017' in str(T_time)):
                y_2017+=1
            else:
                y_2021 += 1
            if (k>3):
                save([key,y_2021,y_2020,y_2019,y_2018,y_2017])
                driver.close()
                return
            print(y_2021,y_2020,y_2019,y_2018,y_2017)
            # save([y_2021, y_2020, y_2019, y_2018, y_2017])


    driver.close()

if __name__ == '__main__':
    keys='tonyhawk'

    # year='user 2021 2020 2019 2018 2017'
    # file = open('dickc_year_Time.csv', 'a+', newline='')
    # writer = csv.writer(file)
    # writer.writerow(year.split())
    # file.close()

    for key in keys.split():
        print(f'正在采集--{key}')
        getData(key)
        print(f'{key}----------已完成！')
```
