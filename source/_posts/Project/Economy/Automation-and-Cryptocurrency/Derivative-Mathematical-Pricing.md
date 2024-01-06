---
title: Derivative Mathematical Pricing
tags: Automatic Trading & Cryptocurrency
date: 2023-09-11 10:15:38
---
<style>
    .image-container {
        display: flex;
        justify-content: space-between; /* 让图片均匀分布在一行中 */
        position: relative;
        hover ~ img {
        filter: blur(100000px); /* 鼠标碰到按钮后，图片变模糊 */
        }
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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Economy&Business](/2023/09/11/Project/Economy/Economy/index.html) > [Automatical Trading and Cryptocurrency](/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Quantitative-Portfolio-Trading/index.html) > **[Derivative Mathematical Pricing](/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Derivative-Mathematical-Pricing/index.html)</small>***
<ol class="menu-list">
    <div>
        <li><a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Quantitative-Portfolio-Trading/index.html" class="menu-item">Quantitative Portfolio Trading&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a>
        <a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Decentralized-Cryptocurrency-Exchange" class="menu-item">Decentralized CryptoCurrency Exchange&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><a href="/2023/09/11/Project/Economy/Automation-and-Cryptocurrency/Derivative-Mathematical-Pricing" class="menu-item">Derivative Mathematical Pricing&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></li>
    </div>
</ol>

---

<!DOCTYPE html>
<html>
<head>
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

<h3 id="matlab-section">Plain Vanilla</h3>
I took the related exercising for this pricing [here](https://colab.research.google.com/drive/18y8GSmrwECzgv3c385CnVVefUjEXtWaj?usp=sharing).

### 2. Barrier Option Return Strategy
It's a type of exotic option where the payoff depends on whether the underlying asset's price reaches a certain level, or barrier, during its life. For this internship exercise, here I will cover the mathematical Principles, for detailed algorithm structure, refer to my GitHub Repository
> Github: https://github.com/Viiiikedy/Barrier-option-returns-issue
<div class="image-container">
    <img src="https://s2.loli.net/2024/01/06/FVxCeRfK4zSpjNs.png" style="width: 30%; height: auto;">
    <img src="https://s2.loli.net/2024/01/06/SA9FNqhtyzVafGv.png" style="width: 30%; height: auto;">
    <img src="https://s2.loli.net/2024/01/06/lHg8AWBTh1C9Uwf.png" style="width: 30%; height: auto;">
</div>


#### 2.1 Basic Steps for Exotic Option Pricing
1. Start with some financial product
2. Model asset prices involved (SDEs)
3. Calibrate the model to market data (numerics, optimization)
4. Model product price correspondingly (P(I)DE or integral)
5. Price the derivative product of interest (numerics, MC)
6. Set up a hedge to remove the risk to the derivative product (optimization)

#### 2.2 Mathematical Deduction

<body>
    <p>
       European Down and In Call (Under the condition of GBM)
        \[
        c = S \exp^{-q(T-t)} \left( \frac{H}{S} \right)^{2 \lambda} N(y) - X \exp^{-r(T-t)} \left( \frac{H}{S} \right)^{2 \lambda - 2} N(y - \sigma \sqrt{T-t})
        \]
        European Up and In Put:
        $$
        p=X\exp^{-r(T-t)}(H/S)^{2\lambda-2}N(-y+\sigma \sqrt{T-t}) - S \exp^{-q(T-t)}(H/S)^{2\lambda}N(-y)
        $$

whereas r is market return, q is dividend rate and r_f is risk free rate. And:
$$
\lambda = \frac{r-r_f+\sigma^2/2}{\sigma^2}
$$
$$
y = \frac{\log{[H^2/(SX)]}}{\sigma \sqrt{T-t}} + \lambda \sigma \sqrt{T-t}
$$

**Theorem**
> Down: H < S
> Up: H>S

For the original case, S < K < H, up and in put option the formula is:

$$
p=K\exp^{-r(T-t)}(H/S)^{2\lambda-2}N(-y+\sigma \sqrt{T-t}) - S \exp^{-q(T-t)}(H/S)^{2\lambda}N(-y)
$$

using the common formalism. If we assume the underlying asset does not pay dividends we can a simplification:

$$
p=K\exp^{-r(T-t)}(H/S_0)^{2\lambda-2}N(-y+\sigma \sqrt{T-t}) - S_0 (H/S_0)^{2\lambda}N(-y)
$$
where
$$
\lambda = \frac{r+\sigma^2/2}{\sigma^2}
$$
$$
y = \frac{\log{[H^2/(S_0K)]}}{\sigma \sqrt{T-t}} + \lambda \sigma \sqrt{T-t}
$$

We will do **Jump Diffusion model**

$$
dS_t = (r-r_J)S_t dt + \sigma S_t dZ_t +J_tS_tdN_t
$$

Here, S_t is the spot price at t; r_t is constant short rate; r_J is drift correction term of the jump; Z_t Wiener process; J_t jump magnitude, it follows a normal distribution of $$N(\mu, \delta^2)$$ N_t is Poisson process $$\sim P(\lambda)$$

Needless to say, the Poisson process isn't correlated with the Wiener process. To simulate such a price dynamic, the Euler discretization:

$$
S_t = S_{t-\Delta t}\Big( e^{(r-r_J-\sigma^2/2)\Delta t+\sigma \sqrt{\Delta t}z_t^1}+\Big(e^{\mu_J+\delta z_t^2}-1\Big)\Big)
$$

$$
r_J \equiv \lambda\Big(e^{\mu_J+\delta^2/2}-1\Big)
$$

### 3. Extension
You could aslo refer to my [tutorial](/2023/09/11/Interview/Quant-Tutorial/Quant-Tutorial/index.html) where I introduced more based on the most classical books in the financial engineering.
    </p>
</body>
</html>