---
title: Text Analysis
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

*<small>[Home](/Home/index.html) > [Project](/tags/Project/index.html) > [Social Science](/2023/09/11/Project/Social-Science/Social-Science/index.html) > [Machine Learning](/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html)> **[Text Analysis](/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html)</small>***
<ol class="menu-list">
    <div>
        <li><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Music-Genre-Classification/index.html" class="menu-item">Music Genre Classification&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a><strong><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Text-Analysis/index.html"  class="menu-item">Text Analysis&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></strong><a href="/2023/09/11/Project/Social-Science/Machine-Learning/Others/index.html" class="menu-item">Others&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp</a></li>
    </div>
</ol>

---
Here I will start from Paper Text Analysis to the Audio Text Analysis.
<h3 id="r-section"></h3>

### 1. Paper Text Analysis
#### 1.1 NLP Sentiment Analysis
In this research group, the main tool used is the SnowNLP library in NLP.

```python
from selenium import webdriver
from lxml import etree
import time
import requests
import csv

def getData(key):
    options = webdriver.ChromeOptions()
    options.add_argument('--no-sandbox')
    # options.add_argument('--headless')  # 无头参数
    options.add_argument('--disable-gpu')

    prefs = {
        'profile.default_content_setting_values':
            {
                'notifications': 2
            }
    }
    options.add_experimental_option('prefs', prefs)

    options.add_experimental_option('useAutomationExtension', False)
    options.add_experimental_option('excludeSwitches', ['enable-automation'])
    driver = webdriver.Chrome(chrome_options=options)
    driver.maximize_window()

    url=f'https://twitter.com/{key}'

    driver.get(url)

    time.sleep(3)

    js="var q=document.documentElement.scrollTop=0"
    driver.execute_script(js)
    time.sleep(3)

    def save(data):
        file=open('dickc_year_Time.csv','a+',newline='')
        writer=csv.writer(file)
        writer.writerow(data)
        file.close()
    T_div=driver.find_elements_by_xpath('//*[@id="react-root"]/div/div/div[2]/main/div/div/div/div/div/div[2]/div/div/div[2]/section/div/div/div')
    print(len(T_div))
    T_time_A='1'
    k=1
    y_2021=0
    y_2020=0
    y_2019=0
    y_2018=0
    y_2017=0
    for j in range(1, 100):
        for i in range(1, 100):
            try:
                T_time=driver.find_element_by_xpath(f'//*[@id="react-root"]/div/div/div[2]/main//div[2]/div/div/div[2]/section/div/div/div[{i}]/div/div/article/div//a/time').text
                T_time_B = driver.find_element_by_xpath('//*[@id="react-root"]/div/div/div[2]/main//div[2]/div/div/div[2]/section/div/div/div[2]/div/div/article/div//a/time').text

            except:
                js='window.scrollTo(0,document.body.scrollHeight)'
                driver.execute_script(js)
                driver.implicitly_wait(10)
                time.sleep(1)
                print('正在下滑')
                try:
                    T_time_A = driver.find_element_by_xpath(
                        '//*[@id="react-root"]/div/div/div[2]/main//div[2]/div/div/div[2]/section/div/div/div[2]/div/div/article/div//a/time').text
                except:
                    pass
                if (T_time_A == T_time_B):
                    k += 1
                k_num=0
                break
            print(str(T_time)+'*******\n'+str(i))
            if('2016' in str(T_time)):
                save([key,y_2021,y_2020,y_2019,y_2018,y_2017])
                driver.close()
                exit()
            elif('2020' in str(T_time)):
                y_2020+=1
            elif('2019' in str(T_time)):
                y_2019+=1
            elif('2018' in str(T_time)):
                y_2018+=1
            elif('2017' in str(T_time)):
                y_2017+=1
            else:
                y_2021 += 1
            if (k>3):
                save([key,y_2021,y_2020,y_2019,y_2018,y_2017])
                driver.close()
                return
            print(y_2021,y_2020,y_2019,y_2018,y_2017)
            # save([y_2021, y_2020, y_2019, y_2018, y_2017])
    driver.close()

if __name__ == '__main__':
    keys='tonyhawk'
    for key in keys.split():
        print(f'正在采集--{key}')
        getData(key)
        print(f'{key}----------已完成！')

```
<div class="image-container">
    <img src="https://s2.loli.net/2024/01/07/bmCtEsnDI7Ow3or.png" style="width: 15%; height: auto;">
    <img src="https://s2.loli.net/2024/01/07/xULli4mZMypNWsO.png" style="width: 45%; height: auto;">
        <img src="https://s2.loli.net/2024/01/07/Bnp2U16loFNvAi9.png" style="width: 40%; height: auto;">
</div>

#### 1.2 LSTM Sentiment Analysis
Word Vector Model;one-hot；Word2Vec;Tokenizer;RNN
```python
n1 = 0
n2 = 0
n3 = 0
n4 = 0
newLines = ""
#导入数据，对数据打标签
with open("train.txt", "r", encoding="UTF-8",errors='ignore') as f:
    lines = f.readlines()
    f.close()
    for line in lines:
        label,sentence =line.strip().split('\t')
        if int(label) == 0:
            if n1 < 10000:
                n1 += 1
                newLines += label + "\t" + sentence + "\n"
        if int(label) == 1:
            if n2 < 10000:
                n2 += 1
                newLines += label + "\t" + sentence + "\n"
        if int(label) == 2:
            if n3 < 10000:
                n3 += 1
                newLines += label + "\t" + sentence + "\n"
        if int(label) == 3:
            if n4 < 10000:
                n4 += 1
                newLines += label + "\t" + sentence + "\n"
    with open("small_train.txt", "w") as f2:
        f2.write(newLines)
        f2.close()

# 数据过滤
def regex_filter(s_line):
    # 剔除英文、数字，以及空格
    special_regex = re.compile(r"[a-zA-Z0-9\s]+")
    # 剔除英文标点符号和特殊符号
    en_regex = re.compile(r"[.…{|}#$%&\'()*+,!-_./:~^;<=>?@★●，。]+")
    # 剔除中文标点符号
    zn_regex = re.compile(r"[《》！、，“”；：（）【】]+")

    s_line = special_regex.sub(r"", s_line)
    s_line = en_regex.sub(r"", s_line)
    s_line = zn_regex.sub(r"", s_line)
    return s_line

## 加载停用词
def stopwords_list(file_path):
    stopwords = [line.strip() for line in open(file_path, 'r', encoding='utf-8').readlines()]
    return stopwords

word_freqs =Counter()  # 词频
stopword = stopwords_list("停用词.txt")
max_len = 0
with open('train.txt', 'r+', encoding="UTF-8",errors='ignore') as f:
    lines = f.readlines()
    for line in lines:
#         # 取出 label 和句子
        label,sentence =line.strip().split('\t')
        # 数据预处理
        sentence = regex_filter(sentence)
        words = jieba.cut(sentence)
        x = 0
        for word in words:
            # 去除停用词
            if word not in stopword:
                print(word)
                word_freqs[word] += 1
                x += 1
        max_len = max(max_len, x)
print(max_len)
print('nb_words ', len(word_freqs))

MAX_FEATURES = 80000 # 最大词频数
vocab_size = min(MAX_FEATURES, len(word_freqs)) + 2
# 构建词频字典
word2index = {x[0]: i+2 for i, x in enumerate(word_freqs.most_common(MAX_FEATURES))}
word2index["PAD"] = 0
word2index["UNK"] = 1
# 将词频字典写入文件中保存
with open('word_dict.pickle', 'wb') as handle:
    pickle.dump(word2index, handle, protocol=pickle.HIGHEST_PROTOCOL)

# 加载分词字典

with open('word_dict.pickle', 'rb') as handle:
    word2index = pickle.load(handle)

### 准备数据
MAX_FEATURES = 80002 # 最大词频数
MAX_SENTENCE_LENGTH = 110 # 句子最大长度
num_recs = 0  # 样本数

with open('train.txt', 'r+', encoding="UTF-8",errors='ignore') as f:
    lines = f.readlines()
    # 统计样本大小
    for line in lines:
        num_recs += 1

# 初始化句子数组和 label 数组
X = np.empty(num_recs,dtype=list)
y = np.zeros(num_recs)
i=0

with open('train.txt', 'r+', encoding="UTF-8",errors='ignore') as f:
    for line in f:
        label,sentence =line.strip().split('\t')
        words = jieba.cut(sentence)
        seqs = []
        for word in words:
            # 在词频中
            if word in word2index:
                seqs.append(word2index[word])
            else:
                seqs.append(word2index["UNK"]) # 不在词频内的补为 UNK
        X[i] = seqs
        y[i] = int(label)
        i += 1

# 把句子转换成数字序列，并对句子进行统一长度，长的截断，短的补 0
X = sequence.pad_sequences(X, maxlen=MAX_SENTENCE_LENGTH)
# 使用 pandas 对 label 进行 one-hot 编码
y1 = pd.get_dummies(y).values
print(X.shape)
print(y1.shape)

# 数据划分
Xtrain, Xtest, ytrain, ytest = train_test_split(X, y1, test_size=0.1, random_state=42)

## 网络构建
EMBEDDING_SIZE = 256 # 词向量维度
HIDDEN_LAYER_SIZE = 128 # 隐藏层大小
BATCH_SIZE = 64 # 每批大小
NUM_EPOCHS = 5 # 训练周期数
# 创建一个实例
model = Sequential()
# 构建词向量
model.add(Embedding(MAX_FEATURES, EMBEDDING_SIZE,input_length=MAX_SENTENCE_LENGTH))
model.add(SpatialDropout1D(0.2))
# 构建 LSTM 层
model.add(LSTM(HIDDEN_LAYER_SIZE, dropout=0.2, recurrent_dropout=0.2))
# 输出层包含四个分类，激活函数设置为'softmax'
model.add(Dense(4, activation="softmax"))
model.add(Activation('softmax'))
# 损失函数设置为分类交叉熵 categorical_crossentropy
model.compile(loss="SparseCategoricalCrossentropy", optimizer="adam",metrics=["accuracy"])

## 训练模型
model.fit(Xtrain, ytrain, batch_size=BATCH_SIZE, epochs=NUM_EPOCHS,validation_data=(Xtest, ytest))

## 评估模型
y_pred = model.predict(Xtest)
y_pred = y_pred.argmax(axis=1)
ytest = ytest.argmax(axis=1)

print("保存模型")
model.save('my_model.h5')

## 测试模型
print("加载模型")
model = load_model('my_model.h5')

INPUT_SENTENCES = ['一根大阳线','财务报表','数据好看','神经病公司']
XX = np.empty(len(INPUT_SENTENCES),dtype=list)
i=0
for sentence in  INPUT_SENTENCES:
    words = jieba.cut(sentence)
    seq = []
    for word in words:
        if word in word2index:
            seq.append(word2index[word])
        else:
            seq.append(word2index['UNK'])
    XX[i] = seq
    i+=1

XX = sequence.pad_sequences(XX, maxlen=MAX_SENTENCE_LENGTH)
label2word = {0:'喜悦', 1:'愤怒', 2:'厌恶', 3:'低落'}
for x in model.predict(XX):
    print(x)
    x = x.tolist()
    label = x.index(max(x[0], x[1], x[2], x[3]))
    print(label)
    print('{}'.format(label2word[label]))
```
<div class="image-container">
    <img src="https://s2.loli.net/2024/01/07/bmCtEsnDI7Ow3or.png" style="width: 33.3%; height: auto;">
    <img src="https://s2.loli.net/2024/01/07/2g6xlMruRkBLhJE.png" style="width: 33.3%; height: auto;">
</div>

### 2. Audio Text Analysis
#### Voice Reporting Preprocessing
**1.Frame Segmentation and Windowing**
```python
# Frame segmentation function
def enframe(wavData, frameSize, overlap):
    coeff = 0.97  # Pre-emphasis coefficient
    wlen = len(wavData)
    step = frameSize - overlap
    frameNum: int = math.ceil(wlen / step)
    frameData = np.zeros((frameSize, frameNum))
```
**2.Pre-Highlit**
```python
def ZCR(frameData):
frameNum = frameData.shape[1]
frameSize = frameData.shape[0]
zcr = np.zeros((frameNum,1))
for i in range(frameNum):
singleFrame = frameData[:,i]
temp = singleFrame[:frameSize-1]*singleFrame[1:frameSize]
temp = np.sign(temp)
zcr[i] = np.sum(temp<0)
return zcr
```
