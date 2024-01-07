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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Social Science](/2023/09/11/Project/Social-Science/Social-Science/index.html) > [General Application](/2023/09/11/Project/Social-Science/General-Application/Gender-Difference-on-Family-Satisfaction/index.html) > **[Chinese Political and Diplomatic Dynamics Analysis](/2023/09/11/Project/Social-Science/General-Application/Chinese-Political-and-Diplomatic-Dynamics-Analysis/index.html)</small>***

<ol class="menu-list">
    <div>
        <li><strong><a href="/2023/09/11/Project/Social-Science/General-Application/Gender-Difference-on-Family-Satisfaction/index.html" class="menu-item">Gender Difference on Family Satisfaction&nbsp</a></strong><a href="/2023/09/11/Project/Social-Science/General-Application/Chinese-Political-and-Diplomatic-Dynamics-Analysis/index.html" class="menu-item">Chinese Political and Diplomatic Dynamics Analysis&nbsp</a><a href="/2023/09/11/Project/Social-Science/General-Application/Housing-Policy&Talent-Capability/index.html" class="menu-item">Housing Policy&Talent Capability&nbsp</a></li>
    </div>
</ol>

---

<h3 id="stata-section"></h3>

### 1. Abstract
Based on Chen and Hu's (2021) research, exploring the impact of traditional gender perspectives on marital and personal satisfaction. Research has found that in traditional marriage, gender division of labor and gender attitudes have an impact on the satisfaction of both spouses. By studying the behavioral outcomes of wives who earn more than their husbands, researchers found that traditional gender attitudes have an impact on the marital satisfaction of both spouses. The wife is more concerned about her husband's economic contribution than his household contribution, while the husband is the opposite. In addition, when the wife's income is higher compared to the husband, the husband is often more dissatisfied with the marriage, while the wife's marital satisfaction is not affected by income differences. This indicates that other factors in the marriage allow wives to maintain a satisfactory attitude towards marriage even if they break traditional gender norms.

### 2. Data Processing
Utilizing the original dataset from the research and the CFPS 2014 dataset, which includes information about adults, family relationships, and household economics.
> Data Address:[here](https://drive.google.com/drive/folders/1GXpJa1XN2CGR2pLfJG-Ht2wONfk5kA11?usp=sharing)
> Project Report Address(word):[here](/zip/Gender.docx)
> Project Report Address(pdf):[here](/zip/Gender.pdf)

### 3. Results Brief
| lag | LL       | LR      | df | p    | FPE     | AIC    | HQIC   | SBIC   |
|-----|----------|---------|----|------|---------|--------|--------|--------|
| 0   | -193.635 |         |    |      | 1.40E+08| 2.16E+01 | 2.16E+01 | 21.6755 |
| 1   | -138.277 | 110.72* | 1  | 0    | 344324  | 15.5863| 15.5999| 15.6852*|
| 2   | -136.933 | 2.6865  | 1  | 0.101| 332175* | 15.5482*| 15.5686*| 15.6966 |
| 3   | -136.817 | 0.23254 | 1  | 0.63 | 368063  | 15.6463| 15.6736| 15.8442 |
| 4   | -136.223 | 1.1892  | 1  | 0.275| 387900  | 15.6914| 15.7255| 15.9387 |

