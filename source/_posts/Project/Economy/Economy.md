---
title: Economy & Business
tags: Project
date: 2023-09-11 10:15:38
---

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > **[Economy&Business](/2023/09/11/Project/Economy/index.html)</small>***

<style>
    .image-container {
        display: flex;
        justify-content: space-between; /* 让图片均匀分布在一行中 */
        position: relative;
        hover ~ img {
        filter: blur(100000px); /* 鼠标碰到按钮后，图片变模糊 */
        }
    }
    .image-box {
        position: relative;
        margin: 22px;
        text-align: center;
    }

    .image-box img {
        width: 303.3px;
        height: 417.6px;
        border-radius: 20px;
        filter: blur(0); /* 图片清晰，初始状态不模糊 */
        transition: filter 0.3s;
    }

    .like-count {
        position: absolute;
        top: 10px;
        left: 50%; /* 左上角水平居中 */
        transform: translateX(-50%); /* 左上角水平居中 */
        color: red;
        font-size: larger;
    }

    .button-container {
    position: absolute;
    bottom: 10px;
    left: 50%; /* 左下角水平居中 */
    transform: translateX(-50%); /* 左下角水平居中 */
    background-color: rgba(255, 255, 255, 0.9); /* 带透明度的白色背景 */
    padding: 6px 16px; /* 缩小按钮内边距 */
    border-radius: 20px;
    font-size: medium; /* 缩小按钮字体 */
    white-space: normal;
    text-align: center;
    display: block;
    text-decoration: none;
    color: black; /* 黑色字体 */
    transition: transform 0.3s, background-color 0.3s;
    }

    .button-container:hover {
        transform: translateX(-50%) scale(1.2); /* 放大按钮 */
        background-color: rgba(255, 255, 255, 1); /* 鼠标悬停时背景色变为更不透明的白色 */
    }

    /*点赞数设定*/
    .like-count {
        position: absolute;
        top: 10px;
        left: 50%;
        transform: translateX(-50%);
        color: red;
        font-size: larger;
        transition: transform 0.3s;
    }

    .like-count:hover {
        animation: shake 0.5s ease-in-out;
    }

    @keyframes shake {
        0% { transform: translateX(-50%) rotate(-5deg); }
        25% { transform: translateX(-50%) rotate(5deg); }
        50% { transform: translateX(-50%) rotate(-5deg); }
        75% { transform: translateX(-50%) rotate(5deg); }
        100% { transform: translateX(-50%) rotate(0deg); }
    }


    /* 经济论文标题的样式 */
    .papers-container {
        display: flex;
        flex-direction: column;
        align-items: flex-start; /* 对齐到左边 */
    }

    .paper-box-with-buttons {
        display: flex;
        align-items: center; /* 按钮与长方形垂直居中对齐 */
        margin-bottom: 20px; /* 底部间距 */
    }

    .paper-box {
        background-color: black;
        color: white;
        padding: 15px;
        margin-left: 10px; /* 长方形与按钮之间的间距 */
        width: 100%;
        text-align: center;
        border-radius: 10px;
    }

    .paper-button {
        background-color: white;
        color: black;
        padding: 5px 10px;
        text-decoration: none;
        border-radius: 5px;
        margin-right: 10px; /* 按钮之间的间距 */
        transition: background-color 0.3s;
    }

    .paper-button:hover {
        background-color: lightgrey;
    }
    /*白色方框*/

    .contract {
      display: none;
      position: fixed;
      left: 20%;
      right: 20%;
      top: 40%;
      margin: auto;
      background: rgba(255, 255, 255, .97);
      border: 1px solid lightgrey;
      padding: 10px;
      border-radius: 5px;
      box-shadow: 2px 5px 5px rgba(0, 0, 0, .5);
    }
    .contract:target {
      display: block;
    }
    .contract-close {
      position: absolute;
      right: -10px;
      top: -10px;
      width: 25px;
      height: 25px;
      background: black;
      text-align: center;
      color: white!important;
      border-radius: 50%;
      justify-content: center;
      align-items: center;
      display: flex;
      box-shadow: 1px 1px 3px rgba(255, 255, 255, .5);
    }
    .contract-close:hover {
      text-decoration: none!important;
    }

</style>

Here I view from the perspecitve of business analysts.By using quantitative tools to mine the most important factors to make decisions.

## Projects
<div class="image-container">
    <div class="image-box">
        <img src="/picture/Big-Dog.png">
        <span class="like-count">❤️ 49</span>
        <a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Quantitative-Portfolio-Trading/index.html" 
           class="button-container">Automatical Trade; CryptoCurrency</a>
    </div>
    <div class="image-box">
        <img src="/picture/Car-Chain.png">
        <span class="like-count">❤️ 28</span>
        <a href="/2023/09/11/Project/Economy/System-Design/RPA(Robot-Processing-Automation)/index.html" 
           class="button-container">System Design</a>
    </div>
    <div class="image-box">
        <img src="/picture/powerbi.png">
        <span class="like-count">❤️ 86</span>
        <a href="/2023/09/11/Project/Economy/Business-Visualization/index.html" 
           class="button-container">Business Visualization</a>
    </div>
</div>

## Publication
<div class="papers-container">
    <div class="paper-box-with-buttons">
        <a href="/pdf/Tokyo.pdf" class="paper-button">PDF</a>
        <a href="#tokyo-contract" class="paper-button">Abstract</a>
        <div id="tokyo-contract" class="contract">
            <div class="contract-content">As stock investment has become an increasingly mainstream way of wealth management, researchers have increasingly attached importance to the study of stock price prediction and constantly use various methods to predict its price trend. This paper pays attention to the JPX Tokyo Stock Exchange Prediction. The Kaggle platform provides the dataset. We hybrid LightGBM and DNN to predict the stock price. Sharpe Ratio is our evaluation metric. The results show that our hybrid model owns the best performance with the highest Sharpe Ratio score of 0.152, which is 0.041, 0.032, and 0.004 higher than Xgboost, Lightgbm, and DNN, respectively.
            </div>
            <a class="contract-close" href="#publication">x</a>
        </div>
        <div class="paper-box">
            <div class="paper-title">Tokyo Stock Exchange Prediction with a Hybrid Model of Lightgbm and DNN</div>
        </div>
    </div>
    <div class="paper-box-with-buttons">
        <a href="/pdf/Application.pdf" class="paper-button">PDF</a>
        <a href="#application-contract" class="paper-button">Abstract</a>
        <div id="application-contract" class="contract">
            <div class="contract-content">No matter the period, housing is the most basic demand in people's lives and is closely related to people's daily lives. Although many domestic and foreign experts have researched and predicted housing prices, the causes of housing prices are complex. The results of housing price research in different regions and periods are very different. Most forecasting models have limitations in their use. Therefore, this article is based on the performance of support vector regression, which depends on the characteristics of crucial parameter selection and uses a genetic algorithm to optimize the penalty parameters, kernel function parameters, and insensitive loss function of the support vector regression model. The optimized parameters are used to establish a support vector regression prediction model, and the housing price is predicted through the prediction model. The simulation results show the convergence speed and prediction accuracy of the support vector regression prediction model optimized by the genetic algorithm have been greatly improved, and the prediction results verify the feasibility and effectiveness of the model.
            </div>
            <a class="contract-close" href="#publication">x</a>
        </div>
        <div class="paper-box">
            <div class="paper-title">Application of Support Vector Regression in Prediction Model Using Genetic Algorithm Optimized</div>
        </div>
    </div>
    <div class="paper-box-with-buttons">
        <a href="/pdf/Economic.pdf" class="paper-button">PDF</a>
        <a href="#economic-contract" class="paper-button">Abstract</a>
        <div id="economic-contract" class="contract">
            <div class="contract-content">Based on the sound economic development trends in Chongqing in recent years, the significant changes in GDP increments of the subordinate districts and counties, and the gradual attention paid to the characteristics of regional economic regions. This article used the idea of sampling to establish comprehensive economic development indicators. The back propagation neural network model of extensive economic development can accurately predict the overall economic development of Chongqing and southern regions in the next five years and explore its correlation with the country's overall economic growth. Through the application of principal component analysis and dimensionality reduction time series analysis, it fits the relationship between the comprehensive indicator data of the Chongqing area from 2000 to 2019 obtained from the National Bureau of Statistics, financial reports, and annual reports to carry out model training, analysis, and prediction. The conclusion from this passage has strong universality in the current situation of regional economic differentiation and commonality. Promoting and establishing a mechanism to obtain a regional financial overview by sampling representative cities in various regions will significantly boost the formulation and modification of macroeconomic policies.
            </div>
            <a class="contract-close" href="#publication">x</a>
        </div>
        <div class="paper-box">
            <div class="paper-title">Economic Forecast of the Southern China on BP Neural Network - Taking Chongqing as an Example</div>
        </div>
    </div>
</div>

## Paper
I once analyzed on Progress and Practices of Internationalization of Chinese Multinational Enterprises (MNEs)

**Abstract**:
The history of international entrepreneurship in China dates to the Reform and Opening-up policy in 1978. Academically, there has been sizable academic research on the international entrepreneurship of Chinese companies (e.g., Deng 2014), focusing on both qualitative and quantitative analysis. In this article, we analyze the historical, political, and economic factors of Chinese internationalization. We also explore the statistical relationship between multiple indicators for internationalization in MNEs, ranging from the MNEs’ brands to R&D, Human Resources, to Asset Distribution. The results show that the location and sector differences matter the most for MNEs’ internationalization. Our findings may provide some implications for Chinese MNEs when developing internationalization strategies and plans for the future. 

**Key Words**: Internationalization Strategy, Regression Analysis, Entrepreneurship, Outward FDI  

> Project report(word):[here](/zip/Progress.docx)
> Project Report(pdf):[here](/zip/Progress.pdf)
