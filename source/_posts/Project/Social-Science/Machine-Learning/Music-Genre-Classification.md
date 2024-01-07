---
title: Music Genre Classsification
tags: Social Science-Machine Learning
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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Social Science](/2023/09/11/Project/Social-Science/Social-Science/index.html) > [Machine Learning](/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html) > **[Music Genre Classification](/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html)</small>***

<ol class="menu-list">
    <div>
        <li><strong><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html" class="menu-item">Music Genre Classification&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></strong><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Text-Analysis/index.html"  class="menu-item">Text Analysis&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Others/index.html" class="menu-item">Others&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></li>
    </div>
</ol>


---
<h3 id="machine-learning-section"></h3>

This is the projct report for MCM/ICM （Mathematical Contest In Modeling / Interdisciplinary Contest In Modeling）
<div class="image-container">
    <img src="https://s2.loli.net/2024/01/06/AczVOLmCguHQUTq.png" width="40%" height="40%">
    <img src="https://s2.loli.net/2024/01/06/QxaA84Dng5EeTGF.png" width="52%" height="52%">
</div>

Music genres have diverged since the middle of the last century. With the development of modern technology and people's awakening of the pursuit of entertainment and spiritual life, music creation and change have gradually become complicated and common. After the inhere knowledge of music theory (pause, rhythm or tone, etc.) becomes the foundation, the evolution and development of genres, the interaction between artists and artists, and the correlation between economic society and music have become more quantifiable. 

- **Complex Network Model**:the relationship between people's influence over time and domains
- **Similarity Model**:the similarities and differences at the genre level, and designs four main analysis methods
- **Decision Tree**:more abstract and grand influential factors like time, economy, society, technology national policies, and artist thinking are included. Lengthen the influence cycle and expand the scope of influence under the fully quantitative model mentioned above. 
  
**Key Words**: Complex Network, Principal component analysis, Decision tree, Euclidean distance, Similarity Analysis,Logistic Analysis

> The Mathematical Contest in Modeling [(MCM)](https://contest.comap.com/undergraduate/contests/mcm/)
> Final Report:[here](/pdf/HCI.pdf)

