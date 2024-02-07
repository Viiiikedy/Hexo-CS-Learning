---
title: 👋Hello Everyone
date: 2023-09-02 10:15:38
---

<style>
.shake-image:hover {
  animation: shake 2s; /* 增加动画持续时间 */
  animation-iteration-count: infinite;
}

@keyframes shake {
  0% { transform: translate(2px, 2px) rotate(0deg); }
  10% { transform: translate(-2px, -4px) rotate(-2deg); }
  20% { transform: translate(-4px, 0px) rotate(2deg); }
  30% { transform: translate(4px, 4px) rotate(0deg); }
  40% { transform: translate(2px, -2px) rotate(2deg); }
  50% { transform: translate(-2px, 4px) rotate(-2deg); }
  60% { transform: translate(-4px, 2px) rotate(0deg); }
  70% { transform: translate(4px, 2px) rotate(-2deg); }
  80% { transform: translate(-2px, -2px) rotate(2deg); }
  90% { transform: translate(2px, 4px) rotate(0deg); }
  100% { transform: translate(2px, -4px) rotate(-2deg); }
}
.button-container {
  text-align: center; /* Center aligns the contents */
}

.button {
  background-color: black;
  border: 1px solid transparent;
  text-align: center;
  border-radius: 5px;
  padding: 8px 15px;
  display: inline-block;
  font-size: 17px;
  color: white !important;
  text-decoration: none;
  margin: 15px; /* Increased margin */
}

.button:hover {
        background-color: rgba(0, 100, 200, 0.8);
        color: white;
    }

    .bubble-container {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 10px;
        text-align: left; /* Changed from center to left */
    }

    .bubble {
        display: inline-block;
        padding: 10px;
        margin: 5px;
        border-radius: 50%;
        background-color: rgba(0, 100, 200, 0.8);
        color: white; /* Changed from black to white */
        text-decoration: none;
        font-size: 14px;
        transition: transform 0.3s;
    }
    .bubble:hover {
        transform: scale(1.2);
        animation: shake 1s;
    }
    /* You can add specific styles for each bubble to vary their sizes */
    #python {
        font-size: 16px; /* Larger font size for larger bubble */
    }
</style>
<script>
  document.querySelectorAll('.bubble').forEach(bubble => {
      bubble.addEventListener('mouseenter', () => {
          bubble.classList.add('shake');
      });
      bubble.addEventListener('mouseleave', () => {
          bubble.classList.remove('shake');
      });
  });
</script>

<div align=center>
  <img src="https://s2.loli.net/2024/01/12/MhqePj7W8pO3Jm5.png" width = "350" height = "350" class="shake-image"/>  
  <br>
  <strong><font size=5>Self-Introduction</font></strong>
  <br>
</div>

<br>

<div align=center>
Wenke Du major in <strong>finance</strong> and <strong>business</strong> but with strong passion 
to apply <strong>data-driven</strong> solutions to solve more general social issues.
</div>


***


```python
class Me:
    def __init__(self):
        self.name = "Wenke Du"
        self.prefer_name = "Vicky"
        self.born_year = 2001
        self.MBTI = "ENTJ"
        self.hometown = "Kaizhou, Chongqing, CN"
        self.curr_location = "Haidian, Beijing, CN"
        self.grad_school = "Universidad Isabel I, Big Data and Intelligence"
        self.undergrad_school = "Maine, Management Information System"
        self.undergrad_school = "RUC, Intelligent Accounting"
```
<p align="center">&#8595;</p>

## Technical Background
📟- My expertise in languages includes [Python](https://www.w3schools.com/python/), [My SQL](https://www.mysql.com/), [HTML](https://www.w3schools.com/html/), [CSS](https://www.w3schools.com/Css/), [Javascript](https://www.w3schools.com/js/DEFAULT.asp), [Matlab](https://www.mathworks.com/products/matlab.html), and [R](https://www.rstudio.com/categories/rstudio-ide/)
🖨️- The software I use includes [Office](https://www.office.com/), [STATA](https://www.stata.com/), [Anaconda](https://www.anaconda.com/), [Visual Studio Code](https://code.visualstudio.com/), and [Figma](https://www.figma.com/file/Tdf7OnEMmbOljZPTxINAOB/Social-Media-Ui-KIT?type=design&node-id=14804%3A4364&mode=design&t=q6iCQUZ0eeZdljTU-1)
🖱️- The frameworks I am familiar with include [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning), [Node.js](https://nodejs.org/en), [Pytorch](https://pytorch.org/), [Numpy](https://numpy.org/), and [UIUX](https://www.figma.com/file/Tdf7OnEMmbOljZPTxINAOB/Social-Media-Ui-KIT?type=design&node-id=14804%3A4364&mode=design&t=q6iCQUZ0eeZdljTU-1).
📈- I'm familiar with applying data science techniques to fix real-world problems in economy and social science.
🎮- I'm recently learning game design [Unity](https://unity.com/) and IOS software development [Swift](https://en.wikipedia.org/wiki/Swift_(programming_language))
💻- My commonly used computer is the Windows [HP](https://www.hp.com/ca-en/home.html) series


<!DOCTYPE html>
<html>
<head>
    <title>Interactive Bubbles</title>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
    <div class="bubble-container">
        <a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Quantitative-Portfolio-Trading/index.html#python-section" class="bubble" id="python">Python</a>
        <a href="/2023/09/11/Project/Design/System-Design/index.html#my-sql-section" class="bubble" id="my-sql">My SQL</a>        
        <a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Decentralized-Cryptocurrency-Exchange/index.html#c++-section" class="bubble" id="c++">C++</a>
        <a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Derivative-Mathematical-Pricing/index.html#matlab-section" class="bubble" id="matlab">MATLAB</a>
        <a href="/2023/09/11/Project/Social-Science/General-Application/index.html#stata-section" class="bubble" id="stata">STATA</a>        
        <a href="/2023/09/11/Project/Social-Science/Machine-Learning/Text-Analysis/index.html#r-section" class="bubble" id="r">R</a>     
        <a href="/2023/09/11/Project/Design/System-Design/index.html#java-section" class="bubble" id="java">Java</a>
        <a href="/2023/09/11/Project/Design/Educational-Game/index.html#html-section" class="bubble" id="html">HTML</a>        
        <a href="/2023/09/11/Project/Design/Art-Design/index.html#css-section" class="bubble" id="css">CSS</a>
        <a href="/2023/09/11/Note/Web-Development/index.html#javascript-section" class="bubble" id="javascript">Javascript</a>
        <a href="/2023/09/11/Project/Economy/Business-Visualization/index.html#thinkcell-section" class="bubble" id="thinkcell">Thinkcell</a>        
        <a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Quantitative-Portfolio-Trading/index.html#vba-section" class="bubble" id="vba">VBA</a>   
        <a href="/2023/09/11/Project/Economy/Business-Visualization/index.html#tableau-section" class="bubble" id="tableau">Tableau</a>
        <a href="/2023/09/11/Project/Economy/Business-Visualization/index.html#power-bi-section" class="bubble" id="power-bi">Power BI</a>        
        <a href="/2023/09/11/Project/Design/Educational-Game/index.html#figma-section" class="bubble" id="figma">Figma</a>
        <a href="/2023/09/11/Project/Design/Educational-Game/index.html#unity-section" class="bubble" id="unity">Unity</a>
        <a href="/2023/09/11/Interview/CS-Tutorial/index.html#swfit-section" class="bubble" id="swift">Swift</a>        
        <a href="/2023/09/11/Post/Young/index.html#visual-studio-code-section" class="bubble" id="visual-studio-code">Visual Studio Code</a>     
        <a href="/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html#machine-learning-section" class="bubble" id="machine-learning">Machine Learning</a>
    </div>
    <script src="script.js"></script>
</body>
</html>

## Other Website


<div class="button-container">
  <a href="https://vicky-post-site.vercel.app/" class="button">My Chinese Finance Blog</a>
  <a href="https://jekyll-typing-artist.vercel.app/" class="button">My Art Design Website</a>
  <a href="https://korean-book.netlify.app" class="button">My Korean Learning Book</a>
  <a href="https://viiiikedy-academy.vercel.app/" class="button">My Academic Site</a>
  <a href="https://vicky-youtube-video.netlify.app" class="button">My Video Site</a>
</div>

***
## Contact

<html>
    <head>
        <title>Contact</title>
    </head>
    <body>
        <img src="/picture/mail.png" width="20" height="20" style="float: left;"/>
        <a href="mailto:vickydu1213@gmail.com">vickydu1213@gmail.com</a>
        <br/>
        <img src="/picture/github.png" width="20" height="20" style="float: left;"/>
        <a href="https://github.com/Viiiikedy">Github</a>
        <br/>
        <img src="/picture/ins.png" width="20" height="20" style="float: left;"/>
        <a href="https://www.instagram.com/viii.iiicky/">Instagram</a>
        <br/>
        <img src="/picture/bachelor-cap.png" width="20" height="20" style="float: left;"/>
        <a href="https://viiiikedy-academy.vercel.app/">Academic Website</a>
    </body>
</html>
