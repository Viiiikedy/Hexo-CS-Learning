---
title: Web Development
tags: Note
date: 2023-09-11 
---
*<small>[Home](/Home/index.html) > [Note](/tags/Note/index.html) > **[Web Development](/2023/09/11/Note笔记/Web-Development/index.html)</small>***

## Web Development Method
### 1. [Github Page](https://github.com/)
### 1.1 Choose [*Github Page*](https://pages.github.com/) as the Targeted Page

(1) Create a repository with name following your username
- eg. with my username as <u>Viiiikey</u>,the repository name must be <u>Viiiikey.github.io</u>
  
(2) If you prefer git push instead of the local [github app](https://desktop.github.com/):
```
*cd to folder '123'
cd 123 
git add .
git commit -m 123

git push
```
### 1.2  Github Only Works as A Host 
(1) Name your new repository randomly without Readme.md
(2) copy url to local Github app
(3) push in the github app directly
(4) Delpy the repository to the third party like [Vercel](https://vercel.com/dashboard) and [Netlify](https://www.netlify.com/)

 >*Note: Other Platforms like [aaPanel](https://www.aapanel.com/new/index.html) work the same way*
### 2. [Python Web Development Methods](https://realpython.com/tutorials/web-dev/)
#### 2.1 [Streamlit](https://streamlit.io/) 
It only takes a few lines of code to create an interactive,visual dashboard.
**(1) Case 1:Simple Uploading Files and Inputting Content**
Run it in Anaconda Prompt
```
`streamlit run C:/Users/hp/Main-Streamlit-Page.py`
```

<img src="https://s2.loli.net/2023/09/11/bcjdNFzMhY6aEUS.png" alt="1" style="zoom:50%;" />

```
import streamlit as st
import tempfile
import os
import io
from Bio import SeqIO
import subprocess
from Bio.Blast import NCBIXML
import pandas as pd

st.title("Learn how to build web blast app using streamlit")
you need to change this path to you own

blastn = "D:/Biotools/blast/ncbiblast/bin/blastn"
db = 'D:/Bioinformatics_Intro/streamlit/uploadfiles/blastdb/cpvirus'
tempfile.tempdir = "D:/Bioinformatics_Intro/streamlit/uploadfiles/temp"

fasta = st.text_area(label="you can paste your fasta here",
             value=">seq1\nATCGA",
             height=400)

runblastn = st.button("run blastn")

names = "qseqid sseqid pident length mismatch gapopen qstart qend sstart send evalue bitscore".split()

if runblastn:
    tmp = tempfile.NamedTemporaryFile(suffix=".fasta",delete=False)
    st.write(tmp.name)
tmp.write(bytes(fasta,'utf-8'))
tmp.seek(0)
for rec in SeqIO.parse(tmp.name,'fasta'):
    st.write(rec.id)
    
cmd = [blastn,'-db',db,'-query',tmp.name,'-evalue','0.0001','-outfmt','6']
process = subprocess.Popen(cmd,stdout=subprocess.PIPE,
                           stderr=subprocess.PIPE,
                           universal_newlines=True)
stdout,stderr = process.communicate()

df = pd.read_csv(io.StringIO(stdout),sep="\t",header=None,names=names)
st.dataframe(df)
tmp.close()
os.unlink(tmp.name)

uploaded_file = st.file_uploader("or upload your fasta file here")

if uploaded_file is not None:
    bytes_data = uploaded_file.getvalue()
    #print(type(bytes_data))
    #st.write(bytes_data)
    tmp = tempfile.NamedTemporaryFile(suffix=".fasta",delete=False)
    st.write(tmp.name)
    try:
        tmp.write(bytes_data)
        tmp.seek(0)
        with open(tmp.name,'r') as fr:
            for line in fr:
                if line.startswith(">"):
                    st.write("input seq id is: %s"%(line.strip().replace(">","")))
                
        cmd = [blastn,'-db',db,'-query',tmp.name,'-evalue','0.0001','-outfmt','6']
        process = subprocess.Popen(cmd,stdout=subprocess.PIPE,
                                stderr=subprocess.PIPE,
                                universal_newlines=True)
        stdout,stderr = process.communicate()
        # for record in NCBIXML.parse(io.StringIO(stdout)):
        #     st.write(record.query)
        
        df = pd.read_csv(io.StringIO(stdout),sep="\t",header=None,names=names)
        st.dataframe(df)
    finally:
        tmp.close()
        os.unlink(tmp.name)      
```
**(2) Case 2:Webpage for Conversational Chat by the [ChatGPT API](https://openai.com/blog/introducing-chatgpt-and-whisper-apis)**
<img src="https://s2.loli.net/2023/09/11/quOT7o9EKevDU4S.png" alt="2" style="zoom: 67%;" />
```
import streamlit as st
import openai
# Set Title and Communicate with Each Other

st.title("Chat with ChatGPT")
st.sidebar.header("Function Introduction")
st.sidebar.info(
    '''This is a web application that enables interactive chatting through the OpenAI API and the ChatGPT model. Enter your questions in the text box, press Enter to query, and receive responses from ChatGPT.'''
)
# Set Model and Key

model_engine = "text-davinci-003"
openai.api_key = "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"

def ChatGPT(user_query):
    """
    Generate answers using the OpenAI API, select models, and configure parameters.
    """
    # Use OpenAI API to Generate the Answer
    completion = openai.Completion.create(
        engine=model_engine,
        prompt=user_query,
        max_tokens=1024,
        n=1,
        temperature=0.5,
    )
    response = completion.choices[0].text
    return response
    
def main():
    """
    Get user input, submit it to ChatGPT, and print the output.
    """
    # Get Question Information
    user_query = st.text_input("Input your question here, press Enter to query.", "What is Python？")
    if user_query != ":q" or user_query != "":
        # Give the Question to ChatGPT, Return the Results
        response = ChatGPT(user_query)
        return st.write(f"{response}")
```

**3.Case 3:Random ForestIris**

```
import streamlit as st
import pandas as pd
from sklearn import datasets
from sklearn.ensemble import RandomForestClassifier

# Users input data:
def user_input_features():
    sepal_length = st.sidebar.slider('Sepal length', 4.3, 7.9, 5.4)
    sepal_width = st.sidebar.slider('Sepal width', 2.0, 4.4, 3.4)
    petal_length = st.sidebar.slider('Petal length', 1.0, 6.9, 1.3)
    petal_width = st.sidebar.slider('Petal width', 0.1, 2.5, 0.2)
    data = {'sepal_length': sepal_length, 'sepal_width': sepal_width,
            'petal_length': petal_length, 'petal_width': petal_width}
    features = pd.DataFrame(data, index=[0])
    return features
df = user_input_features()

# Load Iris Set and Train the Model

iris = datasets.load_iris()
X = iris.data
Y = iris.target
clf = RandomForestClassifier()
clf.fit(X, Y)
# Categorize and display input data.
prediction = clf.predict(df)
prediction_proba = clf.predict_proba(df)
st.write('Categorization Results：' + iris.target_names[prediction][0])
```

<img src="https://s2.loli.net/2023/09/11/fwORnaNHQ25GJ71.png" alt="3" style="zoom:50%;" />

 > *Others:*
 > - [Pynecone](https://pynecone.app/) 
 > - [PyWebIO](https://pywebio.readthedocs.io/en/latest/guide.html)

### 3. Other Open Source Web Development Tools
#### 3.1 [NotionNext](https://github.com/for-1-big-picture/NotionNext/blob/main/README_EN.md)
- [Personal Website in Chinese](https://vicky-post-site.vercel.app/)
- [Tutorial](https://docs.tangly1024.com/article/notion-next-themes)
- [Repository](https://github.com/Viiiikedy/NotionNext/blob/main/blog.config.js)
- Template:example,fukasawa,heo,matery,medium,next,nobelium,simple,plog,heo,nexo,landing,gitbook
We could also deploy it on [4everland](https://www.4everland.org/),one web3 cloud platform.
#### 3.2 Hugo(Go)
Visit Locally:
(1) Create a Folder <u>"hugo"</u>,put <u>hugo.exe</u> into it.
(2) Input <u>cmd</u> at the folder path where folder <u>hugo</u> is,input <u>hugo site new site</u>,put the targeted template in the <u>theme</u> folder in the new established <u>site</u>

  > Note：when <u>git clone</u> the online template,you should choose the ones with <u>exampleSite</u>

(3) Open <u>examplesite</u>，copy all the files to the folder <u>site</u>
(4) Delete the automatically generated <u>hugo.toml</u>
> Otherwies, *page not found* will show up

(5) Open <u>config.toml</u>,change the project name as the cloned theme name 
```
theme=" "
# you choose *wiki*,theme="wiki"
```
(6) Back to the folder of <u>site</u>，<u>cmd</u>,input
   ```
   hugo serve
   ```
> If error occurs, you might delete <u>xx.md</u> by searching <u>twitter</u>.
Then push it to cloud:

(7) Continue in the folder of <u>site</u>，<u>cmd</u>,input
```
hugo -D
```
(8) Open the newly generated <u>public</u> file in the <u>site</u> folder,copy it to the folder <u>xx.github.io</u>
 > there are only .git and <u>README</u> in the <u>xx.github.io</u> folder

```
Commit to main,push origin
```
(9) refresh,wait,done! 

(10) You might choose the third party deployment after that.

#### 3.3 [Hexo(Node.js)](https://hexo.io/)
(1) Create folder <u>blog</u>，under the <u>blog</u>,right-click to open <u>git bash</u>，input:
```
hexo init，npm instal，hexo cl,hexo g,hexo s
```
(2) Clone template to the <u>theme</u> folder
```
git clone  https://github.com/PhosphorW/hexo-theme-academia
```
(3) install necessary packages 
```
npm install hexo-renderer-pug hexo-renderer-stylus --save
hexo cl,hexo g,hexo s
```
 > if the content of hexo is blanked,input:
```
 > hexo n post"any title"，hexo cl,hexo g,hexo s
```
(4) Deploy on github：
```
git config --global user.name"viiiikedy"
git config --global user.email "vickydu1213@gmail.com"
ssh-keygen -t rsa -C "vickydu1213@gmail.com"
ssh -T git@github.com
hexo d
hexo cl,hexo g,hexo s
```
(5) Use txt to open <u>id_rsa</u> file to github and refine SSH
(6) Refine the local network address：
```
hexo server -p 5000
```
#### 3.3 [Jekyll(Ruby)](https://jekyllrb.com/)
(1) Download the latest edition of Ruby+Devkit officially
(2) Input <u>ruby -v</u> and <u>gem -v</u> to check whether the installment is successful
(3) Install Jekyll 和 Bundler gems:
```
put gem install jekyll bundler 来安装
```
(4) Input <u>jekyll -v</u> and <u>bundle -v</u> to check 
(5) Choose one empty folder to create new blog site:
```
jekyll new myblog
cd myblog
bundle add webrick
bundle exec jekyll serve 
```
(6) Successful Address: http://127.0.0.1:4000/ 

Use Template:
(1) Create one empty folder, <u>cmd</u>,input:
```
git init
git clone https://github.com/cotes2020/
```
(2) Open the cloned template folder,input:
```
bundle install
bundle exec jekyll serve
```

#### 3.4 [gitbook](https://www.gitbook.com/)
> You need to change the edition of nvm: node 14 for hexo,node 10 for gitbook:
```
nvm install 14
nvm use 14
#or 
nvm install 14
nvm use 14
```

## SEO Follow-Up Optimization
Source Code of [VIRA](https://fusiedtech.com/) Website

```
<title>VIRA | An Education Social Enterprise in China</title>
<html lang="en">
<head>
    <!-- Meta Tags -->
    <meta charset="utf-8">
    <meta content="width=device-width, initial-scale=1, shrink-to-fit=no" name="viewport">
    <!-- Author -->
    <meta name="author" content="Themes Industry">
    <!-- description -->
    <meta name="description" content="MegaOne is a highly creative, modern, visually stunning and Bootstrap responsive multipurpose studio and portfolio HTML5 template with 8 ready home page demos.">
    <!-- keywords -->
    <meta name="keywords" content="Creative, modern, clean, bootstrap responsive, html5, css3, portfolio, blog, studio, templates, multipurpose, one page, corporate, start-up, studio, branding, designer, freelancer, carousel, parallax, photography, studio, masonry, grid, faq">
    <!-- Page Title -->
    <title>VIRA | An Education Social Enterprise in China</title>
    <!-- Favicon -->
    <link href="http://www.fusinnovations.com/uploadfile/202205/d16b7ff08ea7eb.png" rel="icon" />
    <!-- Bundle -->
    <link href="http://www.fusinnovations.com/static/skin/css/bundle.min.css" rel="stylesheet">
    <!-- Plugin Css -->
    <link href="http://www.fusinnovations.com/static/skin/css/LineIcons.min.css" rel="stylesheet">
    <link href="http://www.fusinnovations.com/static/skin/css/revolution-settings.min.css" rel="stylesheet">
    <link href="http://www.fusinnovations.com/static/skin/css/jquery.fancybox.min.css" rel="stylesheet">
    <link href="http://www.fusinnovations.com/static/skin/css/owl.carousel.min.css" rel="stylesheet">
    <link href="http://www.fusinnovations.com/static/skin/css/cubeportfolio.min.css" rel="stylesheet">
    <!-- Style Sheet -->
    <link href="http://www.fusinnovations.com/static/skin/css/style.css" rel="stylesheet">
</head>
```

### Note
#### 1. Tools for Website Developing:
- [Halo](https://www.fit2cloud.com/index.html)
- [Collection](https://www.zhihu.com/question/36861553)
- [System Collection](https://blog.csdn.net/JunyouYH/article/details/119215315)

#### 2. Questions Not Solved
- [How to Configure Website Analytics](https://lizhening.github.io/posts/b467327c/)
- [Connect Notion Page with Current Web Page](https://embednotion.com/)
- [Style Extension:Minimalist](https://theme-next.js.org/)
- [Vue Learning Address](https://cn.vuejs.org/guide/quick-start.html#using-vue-from-cdn)

### My simple Project
> Link:[here](https://drive.google.com/drive/folders/1xQMxR7qYJCzHp7G-CDh55OyQKoC-eyPb?usp=sharing)