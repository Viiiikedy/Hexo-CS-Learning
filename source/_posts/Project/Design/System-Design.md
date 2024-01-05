---
title: Design-Education
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
</style>

<style type="text/css">
    .bilibili_shortcodes {
        position: relative;
        width: 100%;
        height: 0;
        padding-bottom: 66%;
        margin: auto;
        overflow: hidden;
        text-align: center;
    }

    .bilibili_shortcodes iframe {
        position: absolute;
        width: 100%;
        height: 100%;
        left: 0;
        top: 0;
    }
</style>

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Design](/2023/09/11/Project/Design/Design/index.html) > [System Design](/2023/09/11/Project/Design/System-Design/index.html)</small>*


<ol class="menu-list">
    <div>
        <li><a href="/2023/09/11/Project/Design/System-Design/index.html" class="menu-item">System Design&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><a href="/2023/09/11/Project/Design/Game-Design/index.html" class="menu-item">Game Design&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a>
        <a href="/2023/09/11/Project/Design/Educational-Platform/index.html" class="menu-item">Educational Platformn&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><a href="/2023/09/11/Project/Design/Art-Design/index.html"  class="menu-item">Art Design&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></li>
    </div>
</ol>

---

### 1. Panoramic Poet's Footsteps GPS

Maps have a long and rich history as a scientific expression. 
From ancient times to the modern era, the integration of maps and technology has been a gradual yet significant progression. Out of a deep love for Chinese culture, we have transformed ancient paths into 3D maps, vividly showcasing the footsteps of poets. 
We have also conducted research on the life stories of these poets, enriching the presentation content.
   
> Github: https://github.com/6-200OK/PoetMap.git
> Server Address: http://101.34.228.44:55359/

<div class="bilibili_shortcodes">
    <iframe
        src="https://player.bilibili.com/player.html?aid=941134985&bvid=BV1UW4y117FK&cid=780928055&p=1"
        scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true">
    </iframe>
</div>
<br>

**Technology Stack**
- Front-end: Vue3 + uni-app
- Back-end: SpringBoot
- Database: MySQL
- 3D Visualization Map: Cesium
- Build Tool: Vite


**Project File Tree**
```python
├─ .babelrc
├─ .gitignore
├─ index.html
├─ jsconfig.json
├─ package.json
├─ pnpm-lock.yaml
├─ README.md
├─ src
│  ├─ api
│  │  └─ user.js
│  ├─ App.vue
│  ├─ components
│  │  ├─ cesiumMap.vue
│  │  ├─ poetLife.vue
│  │  ├─ poetLocation.vue
│  │  ├─ searchPoet.vue
│  │  ├─ topBar.vue
│  │  └─ VueTimeline.vue
│  ├─ config
│  │  └─ index.js
│  ├─ graph
│  │  ├─ axis.js
│  │  ├─ cursor.js
│  │  ├─ events.js
│  │  ├─ layout.js
│  │  ├─ timeline.js
│  │  └─ zoom.js
│  ├─ main.js
│  ├─ manifest.json
│  ├─ pages
│  │  └─ index.vue
│  ├─ pages.json
│  ├─ static
│  │  ├─ logo.png
│  │  ├─ models
│  │  │  └─ model.gltf
│  │  └─ topbar.png
│  ├─ stores
│  │  ├─ index.js
│  │  └─ modules
│  │     └─ user.js
│  ├─ uni.scss
│  ├─ ut
│  └─ utils
│     ├─ mapUtils.js
│     └─ request.js
└─ vite.config.js
```



### 2. Blockchain Shared Charging Piles
