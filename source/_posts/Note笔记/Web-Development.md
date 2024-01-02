---
title: Web网站开发
tags: Note笔记

---
<!-- English on top, Chinese below -->

## SEO后续优化 SEO Follow-Up Optimization

VIRA网站的源码

```
<title>VIRA | An Education Social Enterprise in China</title>
```



```
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

## 总结：现在可以建站的工具
飞致云Halo：https://www.fit2cloud.com/index.html
合集链接：https://www.zhihu.com/question/36861553
建站系统合集：https://blog.csdn.net/JunyouYH/article/details/119215315


## 待解决问题：

- 如何配置站点统计功能：https://lizhening.github.io/posts/b467327c/

- 将Notion Page接入现有网页：https://embednotion.com/

- 后续风格：英文极简风：https://theme-next.js.org/

- Vue语言学习地址：https://cn.vuejs.org/guide/quick-start.html#using-vue-from-cdn

  

## 方法一：Github Page

### 1.如果想要用github page生成页面

则一定要用和自己的username一样的仓库名

比如我叫Viiiikey,我的仓库名就必须是Viiiikey.github.io

如果不用本地github app单纯用git 推送的话，步骤是

```
*cd到文件夹
cd 123 
git add .
git commit -m 123

git push
```

### 2.不是非要用github生成页面，github只是作为托管

- 随意名字新建仓库

- 复制 url到本地
- 在github desktop里面直接进行push
- 将github仓库部署到类似vercel和netlify这样的第三方平台即可

### 3.通过宝塔进行托管

外网面板地址:  https://39.106.85.178:26377/b8238d5c
内网面板地址:  https://172.21.41.150:26377/b8238d5c
username: gqib6xwz
password: Bt110011

登录内网面板，选择网站，选择下面两个已经备案的网址操作即可

## 方法二：python中的三大网页开发框架

### 一、Streamlit开发

Streamlit是一个搭建网页的Python库，只需几行代码就可以创建一个交互式、可视化的仪表板

#### 1.简易上传文件和输入内容的网页部署

##### (1).运行方法：

在Anaconda Prompt当中运行

```
`streamlit run C:/Users/hp/软件代码/Main-Streamlit网页.py`
```

即可

##### (2).运行截图和代码

<img src="https://s2.loli.net/2023/09/11/bcjdNFzMhY6aEUS.png" alt="1" style="zoom:50%;" />

``````
import streamlit as st
import tempfile
import os
import io
from Bio import SeqIO
import subprocess
from Bio.Blast import NCBIXML
import pandas as pd

st.title("Learn how to build web blast app using streamlit")

# abc = st.text_area(label="paste your fasta here",
#              value=">seq1\nATCGA",
#              height=200)

# #print(abc)
# if st.button('save'):
#     # for line in abc:
#     #     st.write(line)
#     with open('abc.txt','w') as fw:
#         fw.write(abc)
        
#     st.write("OK")
# result = st.button("Click Here")
# 
# # st.write(result)
# print(os.getcwd())
# if result:
#     with tempfile.TemporaryFile() as fp:
#         tmp = tempfile.NamedTemporaryFile(suffix=".fasta",delete=False)
#         st.write(tmp.name)
#         tmp.write(bytes(abc,'utf-8'))
#         tmp.seek(0)
#         with open(tmp.name,'r') as fr:
#             for line in fr:
#                 st.write(line)
#         #os.write(new_file,b'abcde')
#         #st.write("OK")
#         #os.close(new_file)
#         # with open(tmp.name,'w') as fw:
#         #     fw.write(abc)
#     st.write(":smile:")
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
# for record in NCBIXML.parse(io.StringIO(stdout)):
#     st.write(record.query)

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
                
``````

#### 2.用chatgpt接口生成对话聊天的网页

##### (1).运行截图

<img src="https://s2.loli.net/2023/09/11/quOT7o9EKevDU4S.png" alt="2" style="zoom: 67%;" />

##### (2).运行代码

```
import streamlit as st
import openai
# 设置标题, 功能介绍

st.title("和ChatGPT聊天")
st.sidebar.header("功能介绍")
st.sidebar.info(
    '''这是一个web应用程序，通过OpenAI的API和ChatGPT模型实现交互(聊天)功能。在文本框中输入问题，然后按Enter键查询，接收ChatGPT的回答'''
)

# 设置模型和密匙

model_engine = "text-davinci-003"
openai.api_key = "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"

def ChatGPT(user_query):
    """
    使用OpenAI API生成回答, 选择模型, 设置参数
    """
    # 使用OpenAI API生成回答
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
    获取用户输入, 提交给ChatGPT, 打印输出
    """
    # 获取问题信息
    user_query = st.text_input("在这里输入问题，回车查询", "Python是什么？")
    if user_query != ":q" or user_query != "":
        # 将问题提交给ChatGPT, 返回结果
        response = ChatGPT(user_query)
        return st.write(f"{response}")




# 主函数

main()
```

#### 3.随机森林分类Iris

##### (1).运行代码

```
import streamlit as st
import pandas as pd
from sklearn import datasets
from sklearn.ensemble import RandomForestClassifier

# 用户输入数据

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

# 加载Iris并训练模型

iris = datasets.load_iris()
X = iris.data
Y = iris.target
clf = RandomForestClassifier()
clf.fit(X, Y)

# 对输入数据进行分类，并进行展示

prediction = clf.predict(df)
prediction_proba = clf.predict_proba(df)
st.write('分类结果：' + iris.target_names[prediction][0])
```

##### (2).运行截图

<img src="https://s2.loli.net/2023/09/11/fwORnaNHQ25GJ71.png" alt="3" style="zoom:50%;" />

###  二、Pynecone

相关学习网站：https://reflex.dev/docs/getting-started/installation/；https://mp.weixin.qq.com/s/NQLukxLUGMD6Jpeg2CylbQ

### 三.PyWebIO

相关学习网站：https://pywebio.readthedocs.io/en/latest/guide.html



## 方法二：现有代码建站工具

- bt宝塔：需要服务器：https://www.bt.cn/new/index.html
- 开源建站：https://demo.halo.run/
- https://doc.macwk.cc/docs/project-deployment/uniapp/base
- https://github.com/Thecosy/IceCMS



#### 一、Notion个人网页：

##### 1.挂靠Vercel生成个人网页：

Vercel后台链接：https://vercel.com/dwksdmndb-163com/notion-next/Cqzwq7YD9arZ123hW8VKo13tKoKX
修改模板：

- 教程：https://docs.tangly1024.com/article/notion-next-themes

- Github位置：https://github.com/Viiiikedy/NotionNext/blob/main/blog.config.js

  - 模板包括:example,fukasawa,heo,matery,medium,next,nobelium,simple,plog,heo,nexo,landing,gitbook

  - 项目Github地址：https://github.com/Viiiikedy/NotionNext
    [Image]
    （2）挂靠web3的dashboard生成个人网页：
    https://dashboard.4everland.org/hosting/project/Post-Site/64edffdedbecd300071abdc3?tab=commits

    

#### 二、Hugo搭建个人网页(go语言） 

1. 创建一个文件夹"hugo"，将hugo.exe拖入文件夹

2. This PC 右键Property搜索Edit the system environmental variable,右下角Environmental Variables，下方System variables选择Path,新建一个hugo.exe所处文件夹的路径

3. 在hugo所在文件夹的路径位置cmd，输入hugo site new site,将指定hugo模板的项目放置在新建的site里面的theme文件夹里

  > 注意点：git clone网上模板时一定要注意选择有exampleSite的模板

4. 打开examplesite，将里面的所有文件复制到site路径下
   然后记得删掉hugo自动生成的hugo.toml，不然会出现page not found

5. 打开config.toml,将刚刚clone到theme里面的项目名称改为里面theme=""，即可启用

6. 回到site文件夹下，cmd,输入

   ```
   hugo serve
   ```

   如有问题，可以通过搜索twitter删除xx.md选项即可

7. 然后就可以在本地访问了，接下来进行推送到github

8. 继续在site文件夹下刚刚的cmd里输入

  ```
hugo -D
  ```

   然后点开site文件夹里面新生成的public文件，将其复制到xx.github.io的本地Explorer里面，此时文件夹里只有.git和一个README
  在此之前在github里面创建一个username.github.io的respository并git clone到本地，在setting栏的page处修改为可page

9. Commit to main然后push origin，刷新，等待，github部署搞定

10. 后续可以自行选择是否要再次通过github部署到别的云端平台like Vercel和Netfly

#### 三、Hexo搭建个人网页(Hexo nodejs)：

1. 选择好本地位置，创建文件夹比如blog，在blog下面的位置右键打开git bash，输入hexo init，npm instal，hexo cl,hexo g,hexo s
   hexo本地网页部署三件套：hexo cl，hexo g,hexo s

2. 然后克隆选定hexo模板的项目到theme位置，比如，git clone  https://github.com/PhosphorW/hexo-theme-academia

3. 安装一些hexo必要的包：npm install hexo-renderer-pug hexo-renderer-stylus --save然后再次三件套

4. 如果出现搭建好的hexo内容为空白，可以接下来输入hexo n post"any title"，再三件套

5. 接下来挂靠github：

  6. 输入git config --global user.name"viiiikedy"

  7. 输入git config --global user.email "vickydu1213@gmail.com"

  8. ssh-keygen -t rsa -C "vickydu1213@gmail.com"

  9. 再次输入ssh -T git@github.com

  10. 输入hexo d；然后三件套，其中""里面为user小写和账号绑定的邮箱

  11. 在这个过程中会包括本地生成SSH这个步骤，用txt打开id_rsa文件复制到github指定位置修改SSH

​    

###### 3.1 如何改为单页模式

把值改为路径就行,以关于页为例（这种方法仅适用于关于、隐私条款等特殊页面）：

1. 在命令行输入 hexo new page "about " 创建关于页（关于创建页面，参见写作 | Hexo）
2. 输入 hexo g 生成静态文件
3. 在 /public 下找到你在 1. 创建的页面同名的文件夹，打开它，应该会有一个 index.html
4. 记下这个路径，忽略 /public，在此例也就是 /about/index.html
5. 这个路径就是menu: 下 About: 的值，填入 主题的_config.yml 对应位置即可（没有就另起一行新建一项）
   注意
     设成像以下这样不行：
     menu:
   About: /source/about/about.md

为什么？

先来了解一下 hexo g 、 hexo s 和 hexo d 命令：

```
hexo g (hexo generate):
生成静态文件并保存在 /public 目录下
```

```
hexo s (hexo server):
把 /public 目录下的所有文件挂载到本地服务器，以在本地预览网站
```

```
hexo d (hexo deploy):
把 /public 目录下的所有文件上传到指定服务器（如Github Pages，在_config.yml指定）
```

上面的 about.md 文件（使用 hexo new page "about" 命令生成）在执行 hexo g 时会根据它的内容生成 /public/about/index.html ，about.md 不在 /public 目录下，所以服务器找不到 /about/about.md。

###### 3.12 修改本地网络地址：

```
hexo server -p 5000
```



### 四、Jekyll搭建个人网页（ruby语言)

###### 4.1Jekyll 博客本地搭建基础步骤

1. 到 Ruby 官网 下载最新版本的Ruby+Devkit，下载完成后，点击安装文件，全部按照默认安装

2. 安装完成后，在命令行终端中输入 ruby -v 检查 Ruby 是否安装成功

3. 因为安装的是 Ruby+Devkit，Gem 也会附带安装，因此也输入 gem -v 查看 Gem 是否安装成功

4. Gem 安装成功后就可以开始安装 Jekyll 了，输入 gem install jekyll bundler 来安装 Jekyll 和 Bundler gems

5. 安装完成后，输入 jekyll -v 和 bundle -v 查看 Jekyll 和 bundler gem 是否安装成功

6. Jekyll 和 Bundle 安装成功后，在你计划存放你的博客的文件夹打开命令行终端，输入以下命令构建新的 blog site，并在本地运行

  ```
jekyll new myblog
cd myblog
bundle exec jekyll serve
  ```

7. 这一步一般会出现报错，因为 Jekyll3 默认没有附带 webrick。输入 bundle add webrick 下载（注意：这个步骤每次新建一个 Jekyll site 都要再单独给那个 site 添加 webrick）

8. 接下来就可以正常使用了，再次输入 bundle exec jekyll serve，然后在浏览器中打开网址 http://127.0.0.1:4000/ ，即可查看生成的 Jekyll 博客站，到此为止，恭喜你，你已经成功在本地搭建了你的 Jekyll 博客了！
   b.如何使用主题

9. 这里以 Jekyll 主题 jekyll-theme-chirpy 的使用为例，介绍使用主题的最简单的步骤

10. 首先，创建一个空文件夹，在该文件夹中打开命令行终端，输入 git init，将文件夹变成一个 Git 仓库

11. 然后在终端中输入 git clone https://github.com/cotes2020/jekyll-theme-chirpy.git，将 jekyll-theme-chirpy 主题的 Github 仓库克隆到本地

12. 克隆完成后，在该主题文件夹下打开终端，输入 bundle install 来安装缺失的 gems

13. 安装完成后，在终端中输入 bundle exec jekyll serve 即可在本地预览该主题的博客了！
    本地部署语法bundle exec jekyll serve

    

### 五、gitbook使用

###### 5.1gitbook和hexo关于nvm的切换

由于hexo和gitbook要求的node版本有冲突，hexo要求至少node14，gitbook要求为node10，所以通过安装一个nvm来解决，nvm是一个node版本控制器，可以快速安装和切换node版本
**5.11 使用方法**

```
nvm install 版本号数字 可以安装对应的node版本
nvm use 版本号数字 可以使用对应的node版本
```

**5.12使用gitbook**
cd到对应目录下，使用下面命令切换node版本和启动

```
nvm use 10
gitbook serve
```

**5.13使用hexo**
到对应目录下，使用下面命令切换node版本和启动

```
nvm use 14
hexo server
```

### 六、一些网站模板整理：

其它类型：
- 非常酷炫的计算机Hacker网址：https://github.com/akiritsu/pRoJEct-VeXEd
- 非常完美的notebook，适合之后内容多了使用：https://themes.yhz610.com/demo/theme/gatsby-gitbook-starter/；网站二：https://themes.yhz610.com/demo/theme/hexo-theme-3-hexo/
- 做旧的jekyll风格，旧书：https://themes.yhz610.com/demo/theme/jekyll-marat-theme/
- 旧报纸风格的网站：https://github.com/ohduran/the-interesting-times

1. Hexo:
   - 适合做艺术家作品集归纳的网站：https://aflasio.netlify.app/
   - 适合做金融笔记本的网站：https://github.com/wujun234/hexo-theme-tree
   - 学术网站：https://phosphorw.github.io/；https://phosphorw.github.io/publications

- Jekyll：

  - 学术：
    - 可以把PPT做成网页形式的Jekyll链接：http://themes.jekyllrc.org/jekyll-deck/
    - 可以把LaTex论文做成网页形式的Jekyll链接：http://jekyllthemes.org/themes/LatexJekyll/

  - 极简：
    - 我喜欢的素黄简单学术风格：https://taylantatli.github.io/Ramme/
    - 另一个极简风格：https://nandomoreira.dev/
    - 有一个超级极简风格：http://jekyllthemes.org/themes/dev-potfolio-blog/
    - 极简写Paper网站：http://themes.jekyllrc.org/paper/
    - 很好看的时间轴网站：https://iloveu.xyz/archives/

  - 艺术：
        - 奇怪的抽象艺术家风格：http://themes.jekyllrc.org/otter-pop/
        - 艺术家的典雅黄色风格：https://patdryburgh.github.io/hitchens/；https://jekyllthemes.io/theme/hitchens
        - 风格独特的打字机网站（可以作为艺术家的介绍封面）https://github.com/williamcanin/typing-jekyll-template；http://jekyllthemes.org/themes/typing-jekyll-template/
        - 一个适合成熟的设计师的网站：https://luique-hugo.netlify.app/；https://hugothemesfree.com/a-personal-portfolio-hugo-theme/
        - 适合海报封面的网站：https://github.com/klugjo/hexo-theme-magnetic

  - 一个为播客打造的网站：http://jekyllthemes.org/themes/jekyll-podcaster/
  - 我觉得适合做FiXdemy金融建模的网站：https://forestryio.github.io/ubuild-jekyll/
  - 暂时没想到作用的维基百科wiki baike:http://jekyllthemes.org/themes/git-wiki-for-documentation/
  - 一个跟Youtbe风格很类似的网站：http://jekyllthemes.org/themes/jekyll-video/
  - 一个很有意思的网站，可以来装我计算机几个项目的源码：http://jekyllthemes.org/themes/windows-95/；https://h01000110.github.io/windows-95/20170916/markdown-test-page

- Hugo：

  - 学术网站：https://github.com/StefMa/hugo-fresh

  - 一款适合做产品介绍的网站：https://themes.gohugo.io/themes/lotusdocs/

  - 新闻报纸风格：https://github.com/yihui/hugo-xmag

  - 一个有意思的煎鸡蛋风格网站：https://github.com/rullmann/hugo-theme-terminal-cookbook

  - 一个有意思的博文类网站：https://themes.gohugo.io/themes/hugo-theme-spaced-blog/

  - 一个有意思的旅游构成图片建设网站：https://themes.gohugo.io/themes/hugo-split-gallery/

  - 适合艺术家做一个单独作品的网站：https://themes.gohugo.io/themes/hugo-theme-terminal/；https://hugo-mods.github.io/#join

  - 极简风：https://themes.gohugo.io/themes/hugo-toigian/ 

  - 我喜欢的古早博文网站：https://themes.gohugo.io/themes/tatbantheme2.0/

       


### 七、github账号管理：

1. Book管理：Bookvicky；https://github.com/wujun234/hexo-theme-tree；mdl3758301d893@outlook.com；bookvicky.github.io
2. 电脑项目管理：http://jekyllthemes.org/themes/windows-95/；Coolviiiiiikey ;dwksdmndb@gmail.com;coolviiiiiikey.github.io 
3. 视频管理：2467761235dwk@gmail.com；viiikedy.github.io；https://viiickkkkkky.github.io/
4. 学术档案管理：vickydu1213@gmail.com；Viiiikedy.github.io；https://viiiikedy.github.io/
   

### 八、阿里云服务器：

    1. 登录网址：https://dash.cloudflare.com/eda791d48783e6bb5154521448380e8c/workers-and-pages
    2. 免费云服务器申请链接：https://free.aliyun.com/?crowd=personal
    3. 实例ID：i-2zegnmc2e3ibs9qeoc0r
    4. 阿里云用户：aliyun6326379903
    5. 账号ID：1163393224916527
    6. 服务器链接：https://ecs.console.aliyun.com/server/i-2zegnmc2e3ibs9qeoc0r/detail?regionId=cn-beijing
    7. 阿里云购买域名地址：https://wanwang.aliyun.com/domain/1yuan?spm=5176.8048432.308878.d.2dda2cf8a1nkFF
1. 腾讯服务器：https://cloud.tencent.com/
   相关发布链接文章：https://www.sulvblog.cn/posts/blog/hugo_deploy/

## 方法三、拖拽式无代码网站生成平台

- 模板精美，操作简单：[Choose a Starting Point - My Sites - Dashboard - Carrd](https://carrd.co/dashboard/add#sectioned)
- 时尚模板居多，硬照模特：[XPRS Templates (wpagency.io)](https://wpagency.io/themes/vbid-63d9ad0f782a4a11bc2cd0f5fbc53e87/vbid-594b8-gbcdj8hpef)
- 拖拽式，面板较为复杂：[Webydo ID 9613366](https://studio8.webydo.com/studio.aspx?PrivateToken=9881d550-f2ee-4b9b-892e-dadbe6a7ac3a)
- 一个WP的简易模板：[WP One Pager - WordPress theme | WordPress.org](https://wordpress.org/themes/wp-one-pager/)
- 可以涉及APP的平台：[Fintech | Bubble Editor](https://bubble.io/page?name=index&id=fintech-72985&tab=tabs-1)
- 简易网页平台：[Downloads | Grav CMS (getgrav.org)](https://getgrav.org/downloads)
- 拖拽式最方便：wix
- 较为丰富的网站模板：[Examples · Bootstrap (getbootstrap.com)](https://getbootstrap.com/docs/4.0/examples/)



