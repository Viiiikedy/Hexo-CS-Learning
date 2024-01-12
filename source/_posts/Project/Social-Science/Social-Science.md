---
title: Social Science
tags: Project
date: 2023-09-11 10:15:38
---
<style>
    .menu-item {
        /* existing styles */
    }
    .menu-item:hover {
        /* existing styles */
    }
    .menu-item::before {
        /* existing styles */
    }
    .menu-list {
        /* existing styles */
    }
    .menu-list div {
        /* existing styles */
    }

    /* Updated and added styles */
    .image-link {
        position: absolute;
        bottom: 0;
        right: 0;
        color: white; /* Set text color to white */
        background: rgba(0, 0, 0, 0.5);
        padding: 5px;
        text-decoration: none;
        transition: font-size 0.3s, font-weight 0.3s;
    }
    .image-link span {
        color: white; /* Set text color to white */
        transition: color 0.3s ease; /* Smooth transition for color */
    }
    .image-link:hover {
    font-size: 110%;
    font-weight: bold;
    }
        /* Ensure the text color remains white on hover */
    .image-container:hover .image-link span {
        color: white;
    }

    .image-container img {
        transition: filter 0.3s ease;
    }

    .image-container:hover img {
        filter: blur(4px);
    }

    .image-container {
        width: 47.5%;
        position: relative;
        margin-right: 5%;
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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > **[Social Science](/2023/09/11/Project/Social-Science/Social-Science/index.html)</small>***

Social Science is closely related with the collecting,training and predicting process.Here let's expore more.

## Projects

<div style="display: flex; position: relative;">
  <div class="image-container">
    <img src="https://s2.loli.net/2024/01/05/jgQ7kof6xbC5Rqc.webp" style="width: 100%; height: auto;" />
    <a class="image-link" href="/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html">
      <span>Machine Learning</span>
    </a>
  </div>
  <div class="image-container" style="width: 52.5%;">
    <img src="https://s2.loli.net/2024/01/05/IFJZ8l2yebunfdB.png" style="width: 100%; height: auto;" />
    <a class="image-link" href="/2023/09/11/Project/Social-Science/General-Application/Gender-Difference-on-Family-Satisfaction/index.html">
      <span>General Application</span>
    </a>
  </div>
</div>

## Publication


<div class="papers-container">
    <div class="paper-box-with-buttons">
        <a href="/pdf/Social.pdf" class="paper-button">PDF</a>
        <a href="#tokyo-contract" class="paper-button">Abstract</a>
        <div id="tokyo-contract" class="contract">
            <div class="contract-content">The COVID-19 has caused widespread community seclusion and public concern. This paper focuses on how to focus on the existing problems of bullying, stratification, and discrimination in the current uncertain society and how to use the three major paradigms of social psychology to explain the human response mechanism to lay the groundwork for the future stability of society. Most predecessors explored variables such as happiness and anxiety using experimental data, which has significant limitations. This social experiment was made possible because of COVID-19. Field interviews were conducted to collect the opinions of front-line experts, apply open heat data, adopt scientific sensitivity testing methods, complete the quantitative and qualitative expression of psychological migration and social future changes, and contribute to the formulation of public policies in the future world through data mining of the new normal of society that differs from the past.
            </div>
            <a class="contract-close" href="#publication">x</a>
        </div>
        <div class="paper-box">
            <div class="paper-title">Application of Three Social Psychological Models in Post-epidemic, Based on Statistical Science Summary Test</div>
        </div>
    </div>
</div>
