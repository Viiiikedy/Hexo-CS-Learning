---
title: Design
tags: Project
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
    figcaption:hover {
    transform: scale(1.5);
    font-weight: bold;
    }
    
</style>

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Design](/2023/09/11/Project/Design/Design/index.html)</small>*


<div style="text-align: center;">
  <figure style="display: inline-block; margin-right: 10px;">
    <img src="https://s2.loli.net/2024/01/05/iTgFthBM7dlORoD.png" style="border-radius: 50%; width: 300px; height: 300px; object-fit: cover; box-shadow: 0 8px 15px rgba(0,0,0,0.3);" />
    <figcaption style="text-align: center; font-size: 20px; transition: transform 0.3s, font-weight 0.3s;">
      <a href="/2023/09/11/Project/Design/Game-Design/index.html" style="color: inherit; text-decoration: none;">Game Design</a>
    </figcaption>
  </figure>
  <figure style="display: inline-block; margin-right: 10px;">
    <img src="https://s2.loli.net/2024/01/05/AYbfuXmCcrgIsBT.png" style="border-radius: 50%; width: 300px; height: 300px; object-fit: cover; box-shadow: 0 8px 15px rgba(0,0,0,0.3);" />
    <figcaption style="text-align: center; font-size: 20px; transition: transform 0.3s, font-weight 0.3s;">
      <a href="/2023/09/11/Project/Design/Educational-Platform/index.html" style="color: inherit; text-decoration: none;">Educational Platform</a>
    </figcaption>
  </figure>
  <figure style="display: inline-block;">
    <img src="https://s2.loli.net/2024/01/05/LRuwUh9Fcjode7s.png" style="border-radius: 50%; width: 300px; height: 300px; object-fit: cover; box-shadow: 0 8px 15px rgba(0,0,0,0.3);" />
    <figcaption style="text-align: center; font-size: 20px; transition: transform 0.3s, font-weight 0.3s;">
      <a href="/2023/09/11/Project/Design/Art-Design/index.html" style="color: inherit; text-decoration: none;">Art Design</a>
    </figcaption>
  </figure>
</div>

---
More about My Design:
- [Vicky Typing Artiest](https://jekyll-typing-artist.vercel.app/)
- [Vicky Gallery Design](https://vicky-gallery-site.vercel.app/)