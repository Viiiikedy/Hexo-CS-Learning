---
title: General Application
tags: Social Science
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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Social Science](/2023/09/11/Project/Social-Science/Social-Science/index.html) > [General Application](/2023/09/11/Project/Social-Science/General-Application/Gender-Difference-on-Family-Satisfaction/index.html) > **[Chinese Political and Diplomatic Dynamics Analysis](/2023/09/11/Project/Social-Science/General-Application/Chinese-Political-and-Diplomatic-Dynamics-Analysis/index.html) </small>***

<ol class="menu-list">
    <div>
        <li><a href="/2023/09/11/Project/Social-Science/General-Application/Gender-Difference-on-Family-Satisfaction/index.html" class="menu-item">Gender Difference on Family Satisfaction&nbsp</a><strong><a href="/2023/09/11/Project/Social-Science/General-Application/Chinese-Political-and-Diplomatic-Dynamics-Analysis/index.html" class="menu-item">Chinese Political and Diplomatic Dynamics Analysis&nbsp</a></strong><a href="/2023/09/11/Project/Social-Science/General-Application/Housing-Policy&Talent-Capability/index.html" class="menu-item">Housing Policy&Talent Capability&nbsp</a></li>
    </div>
</ol>


---

based on the statistical analysis of the CPC's important external exchanges from 2017 to 2021

> Project(word):[here](/zip/Party-in-Chinese.docx)
> Project(pdf):[here](/zip/Party-in-Chinese.pdf)

### 1. Data Processing
We used Python to scrape over 1600 news items related to the Chinese Communist Party's international engagements from the website of the Central Liaison Department. After a political stance analysis, 414 news articles involving 92 left-wing parties and organizations from 77 countries across six continents were selected. Post-cleaning irrelevant data, 387 news articles about interactions between the Chinese Communist Party and these left-wing parties were retained for statistical analysis, focusing on key variables like interacting entities, dates, methods, and contents of these interactions.

### 2. Result Overview

<div class="image-container">
    <img src="https://s2.loli.net/2024/01/06/y8ixws7jZA6UgC9.png" width="60%" height="60%">
    <img src="https://s2.loli.net/2024/01/06/ZvLR7KScNUsnz5P.png" width="60%" height="60%">
</div>
