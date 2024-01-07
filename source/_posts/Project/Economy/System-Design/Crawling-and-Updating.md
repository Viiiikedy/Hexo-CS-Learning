---
title: RPA(Robot Processing Automation)
tags: System Design
date: 2023-09-11 10:15:38
---
<style>
   .image-container {
        display: flex;
        justify-content: space-between; /* 让图片均匀分布在一行中 */
        position: relative;
    }
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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Economy&Business](/2023/09/11/Project/Economy/Economy/index.html) > [System Design](/2023/09/11/Project/Economy/System-Design/RPA(Robot-Processing-Automation)/index.html) > **[Crawling & Updating](/2023/09/11/Project/Economy/System-Design/Crawling-and-Updating/index.html)</small>***

<ol class="menu-list">
    <div>
        <li><a href="/2023/09/11/Project/Economy/System-Design/RPA(Robot-Processing-Automation)/index.html" class="menu-item">RPA(Robotic Process Automation)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><a href="/2023/09/11/Project/Economy/System-Design/ERP(Enterprise-Resource-Planning)-Software/index.html" class="menu-item">ERP(Enterprise Resource Planning) Software&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a>
        <strong><a href="/2023/09/11/Project/Economy/System-Design/Crawling-and-Updating/index.html" class="menu-item">Crawling & Updating&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></strong></li>
    </div>
</ol>

---

## Project 1: News Automatically Crawling and Categorization
> [China Government](https://www.gov.cn) News-Headline

### Step 1: Package Importing

```python
for i in range(len(title)):
    db = pymysql.connect(host='localhost', port=3306, user='root', password='', database='pachong', charset='utf8')
    cur = db.cursor()
    sql = 'INSERT INTO 要闻(title, href, date,classname,score) VALUES (%s,%s,%s,%s,%s)'
    cur.execute(sql, (title[i], href[i], date[i],industry_pro[i],score_pro[i]))
    db.commit()
    cur.close()
    db.close()
```
### Step 2:Crawling

```python
import requests
import re
import pymysql
import time
import pandas as pd
from selenium import webdriver

headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36'}

# Chrome headless mode
chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument('--headless') 
browser = webdriver.Chrome(options=chrome_options)

def getData(url):
    # Declare global variables
    global title
    global href
    global date
    
    # Open the webpage and get the source code, Selenium seems to provide more accurate and easier to handle source code
    browser.get(url)
    data = browser.page_source
    
    # Find title, URL, and date
    ptitle = re.findall('<h4>.*?<a href=.*?>(.*?)</a>', data, re.S)
    phref = re.findall('<h4>.*?<a href="(.*?)">', data, re.S)
    pdate = re.findall('<span class="date">(.*?)</span>', data, re.S)
    
    # Clean up the dates
    for i in range(len(pdate)):
        pdate[i] = pdate[i].strip()
    
    # Store the titles, URLs, and dates as global variables
    title = title + ptitle
    href = href + phref
    date = date + pdate
    return

# Clear the data of the first page
title = []
href = []
date = []

# Collect data from the first five pages
for i in range(5):
    url = 'http://sousuo.gov.cn/column/31421/' + str(i) + '.htm'
    getData(url)

# Create a DataFrame
pd2 = pd.DataFrame()
pd2['Title'] = title
pd2['URL'] = href
pd2['Date'] = date
```
<p align="center">
  <img src="https://s2.loli.net/2024/01/07/8aLvb1BqhJV2iE7.png" style="width: 800px; height: 500px;">
</p>


### Step 3:Categorization
**1. Key words**
Consumer Discretionary,Consumer Staples,Energy,Materials,Finance,Industry,Healthcare,Information Technology,Telecom Services,Utilities,Real Estate——Based on the Global Industry Classification Standard (GICS) 

```python
score = []
Energy_key= ['能源','冶炼','石油','天然气','开采','风能','煤炭','减排','低碳','化石能源','减排','电价','核燃料','燃料','装机','碳达峰','碳中和','有色','绿色'，'降碳'，'二氧化碳'，'太阳能发电'，'节能'，'储能'，'再生资源'，'氢能'，'碳排放']
Macroecon_key=['财政收入','经济增长','宏观调控','物价','汇率','总需求','通货膨胀','总供给','货币政策','税收','央行','供应链','产业链','宏观','RCEP','贸易'，'生产经营'，'金融政策'，'经济圈'，'商业特许经营'，'企业法人'，'市场监督'，'市场主体'，'个体工商户'，'市场监管总局'，'财政部'，'经济体系'，'城乡融合发展'，'国民收入'，'经济周期'，'经济政策'，'通货紧缩']
MFG_key=['制造业','食品加工','酒','饮料','茶','烟草','纺织','服装','服饰','皮革','毛皮','鞋','木材','家具','造纸','汽车','建材'，'钢铁'，'石化化工'、'煤炭开采'、'冶金'、'化纤'，'建设工程'，'农产品'，'养殖'，'电商'，'通用设备'，'专用设备'，'交通运输设备']
Edu_key=['教育','招生','教育机构','培训','进修','研修','辅导','减负','网课','职业院校'，'职业教育'，'办学'，'招生'，'课程'，'学分'，'产教融合'，'教学'，'教师队伍'，'育人机制'，'留学'，'奖学金'，'学费'，'职称评审'，'技能人才'，'学术发展'，'作业']
Medical_key=['医疗保险','救助制度','疫情','防疫','疫苗','医药','门诊','医保','健康'，'医疗'，'疾病'，'大病保险'，'药品'，'医疗救助'，'就医负担'，'看病'，'创新药'，'病种'，'零售药店'，'医用耗材'，'康复'，'护理'，'电子处方'，'银保监'，'药监']
all_keys= dict(能源=Energy_key,宏观经济=Macroecon_key,制造业=MFG_key,教育=Edu_key,医疗=Medical_key)
```
**2. Matching** 
Match the news title and content with the key word.IF matched,the related industry receive 5 score.In this way,we get the final score for every news,such as[5,15,20,5,0]

```python
industry_name = ['Energy', 'Macroeconomics', 'Manufacturing', 'Education', 'Healthcare']
industry_pro = []
score_pro = []

for item in range(len(title)):   
    score = []
    industry = []   
    try:     # Fetch the specific content of each news article
        article = requests.get(href[item], headers=headers, timeout=10).text
    except:
        article = 'Failed to fetch'
        print('Failed to fetch')
    try:
        article = article.encode('ISO-8859-1').decode('utf-8')
    except:
        try:
            article = article.encode('ISO-8859-1').decode('gbk')
        except:
            article = article
    p_article = '<p>(.*?)</p>'
    article_main = re.findall(p_article, article)  # Get the main text information inside <p> tags
    article = ''.join(article_main)  # Convert the list to a string
    
    for i in all_keys:   
        num = 0
        for e in range(len(c[i])):   
            a = c[i][e]
            if (a in article) or (a in title[item]):  # If there's a match, add points
                num += 5
        score.append(num)   # Sum up each score as the total score for that industry
    score_pro.append(max(score))
    
    if max(score) == 0:      # If the news doesn't have any keywords from any industry, categorize as 'Others'
        industry_pro.append('Others')
    else:
        for o in range(len(score)):    
            if score[o] == max(score):
                industry.append(d[o])
        z = '、'.join(industry)   # If multiple industries have the highest score, categorize as 'Energy, Manufacturing', etc.
        industry_pro.append(z)

```
<div class="image-container">
    <img src="https://s2.loli.net/2024/01/07/tlQVIBwk3CcAXNg.png" style="width: 500px; height: 300px;">
    <img src="https://s2.loli.net/2024/01/07/SbJXRqvMijl5HzD.png" style="width: 700px; height: 280px;">
</div>

> Categorized Data [Sample](/zip/.Categoized-Headline.xlsx)

## Project 2: Automatically Transfer PPT to Word
### 1. Extract only the text and images from the PPT.
Use a for loop to iterate through each shape in the PPT, first check if the shape contains a text box, and if so, extract the text within it. All information in computers is stored in binary form (1010), including images. When reading files, the character stream automatically encodes these binaries using a character encoding table, but images are already binary files and don't need to be encoded. 
Based on this principle, retrieve the binary stream of each page in the PPT, determine if it is an image based on the file extension, and if it is, extract and save it as an image, then insert it into a Word document.
```python
# 1. Import necessary libraries and functions
from pptx import Presentation
import os
import docx
from docx.shared import RGBColor
from docx.shared import Inches
from docx.shared import Pt
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.oxml.ns import qn
import time

# 2. Create a blank Word document and set the font
wordfile = docx.Document()
# Can be replaced with any font in Word
wordfile.styles['Normal'].font.name = u'Dengxian' 
wordfile.styles['Normal']._element.rPr.rFonts.set(qn('w:eastAsia'), u'Dengxian')

# 3. Specify the path of the ppt file
filepath = r'C:\Users\lenovo\Desktop\1.pptx'
pptx = Presentation(filepath)

# 4. Iterate through all slides in the ppt file
for slide in pptx.slides:
    # Iterate through all shapes in the slide
    for obj in slide.shapes:
        # Check if the shape contains a text box, if so, execute the code in order
        if obj.has_text_frame:
            # Get the text box
            text_frame = obj.text_frame
            # Iterate through all paragraphs in the text box
            for paragraph in text_frame.paragraphs:
                # Write the paragraph to the Word document
                wordfile.add_paragraph(paragraph.text)
                # Save the Word document
                wordfile.save(r'C:\Users\lenovo\Desktop\2.docx')
        else:
            # Use try/except because non-image elements do not have an Image method and will throw an exception
            try:
                # Get binary character stream
                imdata = obj.image.blob

                # Determine the file suffix type, the content-type of the image should be image/jpg
                imagetype = obj.image.content_type

                # In string, find() returns the position (index) of the letter in the string, 
                # if not found, it returns a special marker npos
                typekey = imagetype.find('/') + 1
                imtype = imagetype[typekey:]

                # Create an image folder to save the extracted images
                path = "./image/"
                if not os.path.exists(path):
                    os.makedirs(path)

                # Image generation
                image_file = path + obj.name + "." + imtype

                # Insert the generated image into the Word document
                wordfile.add_picture(image_file, width=Inches(4), height=Inches(3))
                wordfile.save(r'C:\Users\lenovo\Desktop\2.docx')
            except:
                pass
```

<div class="image-container">
    <img src="https://s2.loli.net/2024/01/07/3a1K46kOWHN72fl.png" style="width: 500px; height: 300px;">
    <img src="https://s2.loli.net/2024/01/07/K9VEWfg1GYlBajw.png" style="width: 600px; height: 280px;">
</div>

### 2. Extract the title of the PPT.
The main difficulty here is that the titles in the PPT are not actually formatted as proper titles, but rather the body content with enlarged and bolded fonts. However, we can observe that all the titles follow a similar format like "1-1," which is "number-number text." Based on this, we can determine if a paragraph is a title in the PPT by checking if it matches this specific format.

<div class="image-container">
    <img src="https://s2.loli.net/2024/01/07/vDemoqz5QnIFlAw.png" style="width: 500px; height: 300px;">
    <img src="https://s2.loli.net/2024/01/07/dAHeIJ24xbiDBOG.png" style="width: 500px; height: 300px;">
</div>