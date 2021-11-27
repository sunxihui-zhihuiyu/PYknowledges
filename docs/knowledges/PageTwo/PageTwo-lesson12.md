# **Lesson-12**

## **第三方库安装**

> jieba库

jieba（“结巴”）是Python中一个重要的第三方中文分词函数库。

> wordcloud库

wordcloud（“词云”）是对文本中出现频率较高的词语给予视觉化展示的图形, 是一种常见的文本挖掘的方法。

> 第三方库安装方法

- `win` + `R` 按键打开运行窗口
- 输入 `cmd` 指令
- 打开电脑运行窗口

<img src='_media/2-12-1.png' alt='cmd' style='zoom:40%;'/>

- 输入第三方库安装指令：`pip install jieba`

<img src='_media/2-12-2.png' alt='pip' style='zoom:40%;'/>

- 回车，等待安装

<img src='_media/2-12-3.png' alt='pip' style='zoom:40%;'/>

- 输入第三方库安装指令：`pip install wordcloud`
- 回车，等待安装

## **jieba库**

jieba库支持三种分词模式：
- 精确模式，将句子最精确地切开，适合文本分析；
- 全模式，把句子中 所有可以成词的词语都扫描出来，速度非常快， 但是不能解决歧义；
- 搜索引擎模式，在精确模式基础上，对长词再次切分，提高召回率，适合用于搜索引擎分词。

```python
>>> import jieba

>>> jieba.lcut('智慧鱼是最好的人工智能教育学校')    # 精确模式（我们最常用的模式）
['智慧', '鱼', '是', '最好', '的', '人工智能', '教育', '学校']

>>> jieba.lcut('智慧鱼是最好的人工智能教育学校'，cut_all = True)
['智慧', '鱼', '是', '最好', '的', '人工', '人工智能', '智能', '教育', '教育学', '学校']

>>> jieba.lcut_for_search('智慧鱼是最好的人工智能教育学校')
['智慧', '鱼', '是', '最好', '的', '人工', '智能', '人工智能', '教育', '学校']

>>> jieba.add_word('智慧鱼')   # 向词库中增加 “智慧鱼” 这个词
>>> jieba.add_word('人工智能教育')   # 向词库中增加 “人工智能教育” 这个词
>>> jieba.lcut('智慧鱼是最好的人工智能教育学校') 
['智慧鱼', '是', '最好', '的', '人工智能教育', '学校']
```

## **wordcloud库**

> 词云的编程基础步骤：

- 第一步导入wordcloud库；
- 第二步创建词云对象，我们可以对我们设置的这个词云进行大小、形状的一些设置，这就是python中的面向对象编程（具体知识点会在第三阶段进行学习）；
- 第三步给词云对象加载相关文本；
- 第四步将词云对象保存为图片。

> 显示英文

```python
import wordcloud       # 导入wordcloud库

my_wordcloud = wordcloud.WordCloud()    # 创建我的词云
my_wordcloud.generate('Smartfisher is the best Artificial Intelligence education school')   # 词云加载的文本内容
my_wordcloud.to_file('my_wordcloud.png')    # 将创建的词云保存为图片
```

<img src='_media/2-12-4.png' alt='wordcloud' style='zoom:40%;'/>

> 显示中文

```python
import wordcloud       # 导入wordcloud库
font = 'C:\Windows\Fonts\SimHei.ttf'   # 设置词云显示中文文本字体
my_wordcloud = wordcloud.WordCloud(font_path=font)    # 创建我的词云
my_wordcloud.generate('智慧鱼是最好的人工智能教育学校')   # 词云加载的文本内容
my_wordcloud.to_file('my_wordcloud.png')    # 将创建的词云保存为图片
```

<img src='_media/2-12-5.png' alt='wordcloud' style='zoom:40%;'/>

> 创建词云时候的参数

```python
import wordcloud 
font = 'C:\Windows\Fonts\SimHei.ttf'
my_wordcloud = wordcloud.WordCloud(font_path = font,width = 800,height = 600,max_words = 20,background_color = 'White')
'''
font_path:字体路径； 
width:词云图片宽度； 
height:词云图片高度；
max_words:最大字号；
background_color:图片背景色
'''
my_wordcloud.generate('智慧鱼 是最好的 人工智能教育 学校')
my_wordcloud.to_file('my_wordcloud.png')
```

<img src='_media/2-12-6.png' alt='wordcloud' style='zoom:40%;'/>