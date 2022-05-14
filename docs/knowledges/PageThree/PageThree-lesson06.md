# **Lesson-06**

## 一、 文件类型

一般进行词汇量的统计，或者进行词云的设计，面向的对象不是一段字符，而是进行文本文件中词汇量的所有统计。

文件是数据的集合和抽象，文件包含两种类型：`文本文件`和`二进制文件`。

**文本文件**一般由单一特定编码的字符组成，如ascii编码、UTF-8编码，内容容易同意展示和阅读。文本文件可以看成是存储在磁盘上的长字符串，如txt文件。

**二进制文件**直接由0和1组成，没有统一字符编码。二进制是信息按照非字符但特定格式形式的文件，常见的二进制文件有可执行程序、图形、图像、声音等等。

<img src='_media/3-6-1.png' alt='文件类型' style='zoom:40%;'/>

## 二、文本文件操作

文本文件可以使用`文本文件方式`和`二进制文件方式`两种方式打开。打开之后，两种方式的操作不同：
使用文本文件打开之后，文件经过编码能够形成字符串，打印出有意义的字符；
使用二进制文件方式打开之后，文件被解析为字节（Byte）流，一个字符由两个字节表示。

```python
file_1 = open('python.txt','rt',encoding='utf-8')
print(file_1.readline())
file_close()

>>> 青少年人工智能基础教育Python课程   # 以文本形式打开文本文件

file_1 = open('python.txt','rb',encoding='utf-8')
print(file_1.readline())
file_close()

>>>  b'\xe9\x9d\x92\xe5\xb0\x91\xe5\xb9\xb4\xe4\xba\xba\xe5\xb7\xa5\xe6\x99\xba\xe8\x83\xbd\xe5\x9f\xba\xe7\xa1\x80\xe6\x95\x99\xe8\x82\xb2python\xe8\xaf\xbe\xe7\xa8\x8b\r\n'   # 以二进制形式打开文本文件
```

文件的操作步骤分为三步：打开-操作-关闭。

电脑系统中文件一般默认处于存储状态，所以需要进行文件的打开。当打不开的时候需要创建文件。
当文件打开之后，文件处于占用状态，这时候我们可以通过一些方法对文件进行操作，例如读取文件中内容，或者往文件中写入内容。这时候的文件作为一个对象进行存在，采用`<a>.<b>()`方式进行操作，也就是文件对象的操作方法。

当操作之后，文件就需要关闭，关闭文件之后，内存释放对文件的控制使文件恢复存储状态。

大家思考一下，如果打开文件之后，不关闭会有什么后果？

<img src='_media/3-6-2.png' alt='文件操作' style='zoom:40%;'/>

文件可以通过python内置函数`open()`进行打开，打开之后我们使用变量接收文件内容。我们可以将这个部分看作是类的实例化对象。

`open()`函数有两个参数：`文件名`和`打开模式`。

如果文件和程序文件在同一文件夹位置，则直接使用文件名即可，如果位于不同文件夹，则需要是文件的完整路径名称。

文件的打开模式，有读写两种模式，默认是'r'模式。

|打开模式|说明|
|:---:|:---|
|`r`|只读模式，如果文件不存在，则返回异常|
|`w`|	覆盖写模式，文件不存在则创建，存在则完全覆盖|
|`x`|	创建写模式，文件不存在则创建，存在则返回异常|
|`a`|	追加写模式，文件不存在则创建，存在则在文件最后追加内容|
|`b`|	二进制文件模式|
|`t`|	文本文件模式，默认值|
|`+`|	与r/w/x/a一同使用，在原功能基础上同时读写功能。|

### 1. 文件读取

```python
file = open('python.txt', 'r', encoding = 'utf-8')
print(file.readline(1))
file.close()
```

|语句|说明|
|:---:|:---|
|`file_name.read(size=-1)`|从文件中读入整个文件内容，如果给出参数，读入签size长度的字符串或者字节流
|`file_name.readline(size=-1)`|从文件中读入一行内容，如果给出参数，读入该行前size长度的字符串或者字节流
|`file_name.readlines(hint=-1)`|从文件中读入所有行，以每行为元素形成一个列表，如果给出参数，读入hint行

### 2. 文件写入

```python
ls = ['我是智慧鱼','今年7岁了']

file = open('python.txt', 'a+', encoding = 'utf-8')
file.writelines(ls)
file.seek(0)
file.close()
```

|语句|说明|
|:---:|:---|
|`file_name.write(s)`|向文件写入一个字符串或者字节流
|`file_name.writelines(lines)`|将一个元素拳为字符串的**列表**写入文件
|`file_name.seek(offset)`|改变当前文件操作指针的位置，offset的值：(0——文件开头；1——当前位置；2——文件结尾。)

## 三、《乌鸦和狐狸.txt》


> <a href="_media/乌鸦和狐狸.txt" title="乌鸦和狐狸" download="乌鸦和狐狸.txt">乌鸦贺狐狸文本(中文)下载</a>

> <a href="_media/crow and fox.txt" title="乌鸦和狐狸" download="crow and fox.txt">乌鸦贺狐狸文本(英文)下载</a>

```python
import jieba

txt = '乌鸦和狐狸.txt'

file = open(txt, 'r', encoding = 'utf-8')
s = file.read()

words = jieba.lcut(s)

counts = {}
for word in words:
    if len(word) == 1:
        continue
    else:
        counts[word] = counts.get(word, 0) + 1

for count in counts.items():
    print(count)
    
file.close()

```