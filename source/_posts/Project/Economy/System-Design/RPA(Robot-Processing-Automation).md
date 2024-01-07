---
title: RPA(Robot Processing Automation)
tags: System Design
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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Economy&Business](/2023/09/11/Project/Economy/Economy/index.html) > [System Design](/2023/09/11/Project/Economy/System-Design/RPA(Robot-Processing-Automation)/index.html) > **[RPA(Robot Processing Automation)](/2023/09/11/Project/Economy/System-Design/RPA(Robot-Processing-Automation)/index.html)</small>***

<ol class="menu-list">
    <div>
        <li><strong><a href="/2023/09/11/Project/Economy/System-Design/RPA(Robot-Processing-Automation)/index.html" class="menu-item">RPA(Robotic Process Automation)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></strong>
        <a href="/2023/09/11/Project/Economy/System-Design/ERP(Enterprise-Resource-Planning)-Software/index.html" class="menu-item">ERP(Enterprise Resource Planning) Software&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><a href="/2023/09/11/Project/Economy/System-Design/Crawling-and-Updating/index.html" class="menu-item">Crawling & Updating&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></li>
    </div>
</ol>

---

### Designing Background
I developed an [automated process](https://www.uipath.com/rpa/robotic-process-automation) to acquire and analyze financial data from annual reports and understand business operations. This process caters to the growing need for financial data processing and analysis in today's digital and information-driven context. 
It enables businesses to effectively gather and analyze financial data from the last three years. The process fetches annual report data, analyzes data, generates analytical reports, and computes financial figures.

> Github:https://github.com/Viiiikedy/RPA 
> Financial Website:http://www.cninfo.com.cn/new/index

### Designing Procedure
<p align="center">
  <img src="https://s2.loli.net/2024/01/05/qHsTQK6Na8vBzWy.png">
</p>
#### 1.	Annual Report Download
Access the annual report download page by logging into the Juchao website and selecting the appropriate time, report type, etc. Based on URL analysis, the reports are efficiently and accurately downloaded locally through HTTP requests.
#### 2.	Data Acquisition
The annual reports are in editable PDF format, allowing for direct text extraction for processing. This involves using a suitable PDF parsing library to extract text from PDF files, which can be achieved by loading the PDFs into memory and utilizing specific functions or methods.
#### 3.	Financial Statement Data Extraction
Considering potential inconsistencies, missing values, and anomalies in annual report formats, it's essential to analyze the text format of the reports. The goal is to locate the compelling text "Section II, Financial Statements" and remove irrelevant text from the beginning and end of the reports using substring and split functions.
#### 4.	Financial Analysis
The extracted financial statement data is cleaned using functions like substring and split. This cleaned data is then used for calculations and written into Word.
#### 5.	Email Sending
The final step involves sending emails using the SMTP protocol.
<p align="center">
  <img src="https://s2.loli.net/2024/01/05/mPQeWRx5sNwjoBI.png">
</p>




### Designing Execution
1.	Open the software, select "project.json," and install the extension for Edge in the tools section.
2.	Delete the already executed .docx, .pdf, and .xlsx files for Shanghai Airport, 2022, and Fujian Expressway. The specific company codes can be found in the "企业列表.xlsx" (Company List.xlsx) file, formatted as follows:
3.	Select the "Main. xaml" file and click "run the file." The annual report download data source is the Juchao website, and the data template is located in "word模板.docx" (word template.docx), formatted as follows: 
| Company Code  | Company Name  | Quick Ratio  |
|---------------|---------------|--------------|
| [Company Code]| [Company Name]| [Quick Ratio]|

4.	Start the process; below is a screenshot of part of the running code.
<div style="display: flex; position: relative;">
  <div class="image-container">
    <img src="https://s2.loli.net/2024/01/05/eFlHxzZ9Kmgwih1.png" style="width: 100%; height: auto;" />
  </div>
  <div class="image-container">
    <img src="https://s2.loli.net/2024/01/05/y8FabYXPEvlwdZx.png" style="width: 100%; height: auto;" />
  </div>
  <div class="image-container">
    <img src="https://s2.loli.net/2024/01/05/5mtwq1JUc9rOaGR.png" style="width: 100%; height: auto;" />
  </div>
  <div class="image-container">
    <img src="https://s2.loli.net/2024/01/05/x9GRYpN3TH47Z1Q.png" style="width: 100%; height: auto;" />
  </div>
</div>






