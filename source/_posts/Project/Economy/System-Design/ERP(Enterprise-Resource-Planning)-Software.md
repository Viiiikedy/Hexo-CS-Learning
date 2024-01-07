---
title: ERP(Enterprise Resource Planning) Software
tags: System Design
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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Economy&Business](/2023/09/11/Project/Economy/Economy/index.html) > [System Design](/2023/09/11/Project/Economy/System-Design/RPA(Robot-Processing-Automation)/index.html) > **[ERP(Enterprise Resource Planning) Software](/2023/09/11/Project/Economy/System-Design/Crawling-and-Updating/index.html)</small>***

<ol class="menu-list">
    <div>
        <li><a href="/2023/09/11/Project/Economy/System-Design/RPA(Robot-Processing-Automation)/index.html" class="menu-item">RPA(Robotic Process Automation)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><strong><a href="/2023/09/11/Project/Economy/System-Design/ERP(Enterprise-Resource-Planning)-Software/index.html" class="menu-item">ERP(Enterprise Resource Planning) Software&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></strong>
        </strong><a href="/2023/09/11/Project/Economy/System-Design/Crawling-and-Updating/index.html" class="menu-item">Crawling & Updating&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></strong></li>
    </div>
</ol>

---
[ERP(Enterprise Resource Planning) Software](https://dynamics.microsoft.com/en-us/erp/what-is-erp/#:~:text=Enterprise%20resource%20planning%20%28ERP%29%20is%20a%20type%20of,of%20truth%20and%20streamlining%20operations%20across%20the%20enterprise) is a type of software system that helps organizations automate and manage core business processes for optimal performanc
<p align="center">
  <img src="https://s2.loli.net/2024/01/05/s5uLoZqvyla6NxF.png">
</p>

### Toothpaste Factory Project
> project zip [here](https://drive.google.com/file/d/1b5ZwZSjZ5Y5_YvLi745sAnNqAJ38S-u2/view?usp=sharing)

#### 1. Procurement Management:
##### 1.1 Simulate a procurement transaction
Purchase Order → Purchase Invoice → Goods Receipt Note (Inventory Management Subsystem) 
→ Payment Order (Pay 50% of the amount).

<p align="center">
  <img src="https://s2.loli.net/2024/01/05/scmyE7FtjZPWfAN.png">
</p>

##### 1.2 Procurement Management 
(hide non-key columns, retain key columns)
<p align="center">
  <img src="https://s2.loli.net/2024/01/05/y9e5nwLr7qUiFKh.png">
</p>

- **Purchase Order Execution Statistics**
- **Purchase Invoice List**
- **Purchase Settlement List**
- **Accounts Payable Management**
  - Payment Order List (Payment Processing - Receipt and Payment Order Query)
  - Voucher Processing - Voucher List
  - Business Ledger - Detailed Business Account

#### 2. Inventory Management:

- **Journal**
- **Receipts and Issues Summary** 
(hide blank data columns through format settings)
- **Inventory Accounting - Voucher List**
<p align="center">
  <img src="https://s2.loli.net/2024/01/05/oCWhwkmAf2ysiVB.png">
</p>

#### 3. Sales Management:

- **Sales Order Execution Statistics**
- **Sales Invoice List**
- **Accounts Receivable Management**
  - Receipt Order List (Receipt Processing - Receipt and Payment Order Query)
  - Voucher Processing - Voucher List
  - Business Ledger - Detailed Business Account

<p align="center">
  <img src="https://s2.loli.net/2024/01/05/dgnuZKfHSDoCOYl.png">
</p>

### More about Yonyou
> Yonyou:https://u8.yonyou.com/

As a crucial software for applying data science to solve business problems, Yonyou U8+ integrates deeply with cloud applications in enterprise cloud migration, offering one-stop "end + cloud" services in finance, marketing, manufacturing, procurement, design, collaboration, HR, and more. It employs a strategy of integrated software and hardware and ecosystem collaboration to empower growth-oriented enterprises in innovation and upgrading in R&D, supply chain, production, finance, and marketing. Yonyou U8+ provides a new platform for business collaboration, online transactions, and intelligent operations based on the Internet.



   





