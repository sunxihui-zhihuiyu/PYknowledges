# **Lesson-05**

## 一、 Python数据类型

### 1. 一切皆对象。

python中每一个对象都属于一个类型、都有一定的值、都存在于一定的内存位置（id）。

这和我们的世界是相适应的，在现实世界中每一个真实存在的物体就是一个对象，他们也会有所述类型、占用空间、具体内容这样的属性。

python中，有部分的对象类型是已经存在的，使用的时候不需要我们再进行定义，拿来即用即可。

对于python中的对象，我们可以通过id()函数查找对象的内存地址，使用type()函数查找对象的类型。

```python
>>> id(3)   
2058074064
>>> type(3)
<class 'int'>

# 数字3的值是3，3在我这台计算机中的内存地址是2058074064, 3的数据类型是int-整数类型
# 生活中，我的笔记本电脑也是一个实际对象，这台笔记本电脑存放的地址是我的书桌上，它所属的类型是电脑。
```

### 2. Python的内置数据类型

python中，有些类型是已经内置好的，我们直接拿来用就可以了。就像，地球上的物种类别主要有动物、植物、原生生物（无核生物）、原核生物（单细胞真核生物）及真菌五大类。同样的，python中有一些内置的对象类型，主要为**数字类型、序列类型、映射类型、类、实例和异常**六大类。

在关于数据方面，python有六个标准的数据类型，**数字、字符串、元组、列表、集合和字典**。

<img src='_media/3-5-1.png' alt='数据类型' style='zoom:40%;'/>

1. 数字类型中有三类，`整数(int)`、`浮点数(float)`和`复数(complex)`。

    本阶段，我们只对整数和浮点数进行学习。

    数字是单一的、不能再分的数据，属于`基本数据类型`。

2. 实际上计算机是需要同时处理多个数据的，这就需要将多个数据有效组织起来并统一表示，这类能够表示多个数据的类型称为`组合数据类型`。

    这就像一个人做一件事和一个团队做一件事情的区别。每个团队是由多个成员组成的。

    组合数据类型中，分为三类：`序列类型`、`集合类型`和`映射类型`。

    - `序列类型`中的多个数据之间是`存在先后顺序`的，通过序号进行访问，这就像是一个小团队之间的成员都是有各自的位置的，或者排队的人都是有自己的顺序的。访问这些数据的时候，可以通过序号进行访问，这个序号也叫做`下标`或者`索引`。
    
        在之前学习过的字符串和列表就属于序列类型。

    - `集合类型`中的多个数据之间是没有顺序的，并且这些数据之间`不能重复`，数据也只能是不可变的数据类型。
        
        这就像一个家庭就是一个集合，这个家庭中的人员是不会重复的，不会有两个爷爷存在，爷爷本身也不会改变。
    - `映射类型`是`“键-值”`的表示方法，序列类型中的下标和对应的数据也可以看成是特殊的“键-值”。
    
        这就像一个团队中，每个人都有自己的身份，每个身份对应一个唯一的人，这个对应关系就是键值对。

### 3. 序列类型

```python
>>> name = '智慧鱼'   # 字符串类型
>>> scores = [40,60,60,70]  # 列表类型
>>> coordinate = (3,4)   # 元组类型
```

`元组`使用小括号()表示，元素之间使用逗号隔开。其余基本操作和列表都是一致的。

元组类型为tuple。

元组类型表示一组特定的值，这组数值不可以改变。例如上述类型中，（3,4）表示在平面直角坐标系中，一个点的x轴坐标为3，y轴坐标为4。如果坐标值改变，则这个点就要变化。

```python
import turtle
def draw_circle(r,*colors):
    for color in colors:
        turtle.fillcolor(color)
        turtle.begin_color()
        turtle.circle(r)
        turtle.end_color()
        r -= 20

draw_circle(100,'red','green','blue')

# 在函数中，不定长参数colors的类型实际为元组。当传入实际参数后，colors = ('red','green','blue')
```

### 4. 集合类型  --- 集合  set

集合类型中，包含0个或者多个数据的无序组合。在集合中的元素是不可以重复的。所以，我们可以使用集合过滤掉重复的元素。

集合中的元素必须是固定数据类型，也就是不可变数据类型，如数字、元组、字符串等。

集合用大括号`{}`表示，可以用赋值语句生成一个集合。
也可以使用set()函数生成集合，输入的参数可以实任何组合数据类型，返回结果是一个无重复且排序任意的集合。

```python
>>> s = {60,90,80,50,60}
{90,80,50,60}
# 集合能将重复的元素60去掉，保持每个元素的唯一性

>>> p = set('banana')
{'b','a','n'}
```

### 5. 映射类型 --- 字典dict

在映射类型中，每项数据都是由`“键-值”`组成。每个元素就是一个键值对，也就是元素是（key, value）,元素之间是无序的。

我们可以将`键（key）`理解为数据的`属性`，或者类别、标签，将`值（value）`了解为`属性内容`，或者值。

映射类型主要以`字典（dict）`体现。就像常用的新华字典中，通过每个字，找到相对应的字的解释。

字典也是由大括号{}表示，它和集合不同的是创建字典的时候可以通过{}创建一个空字典，但是创建集合的时候需要使用set(）函数进行创建。

如家庭成员中，我们可以使用键值对表示家庭成员的称呼以及姓名，键和值之间使用冒号：进行连接，每组元素之间使用逗号隔开。

我们可以通过字典中的键，索取相对应的值。这个方法和序列类型中的使用方法是一致的，不同的是序列类型中是使用下标或者索引获取相对应的值的。

<img src='_media/3-5-2.png' alt='字典类型' style='zoom:40%;'/>

```python
>>> family = {'爷爷':'老林', '爸爸':'大林', '儿子':'小林'}
>>> family['爷爷']
'老林'
>>> family.keys()
dict_keys(['爷爷', '爸爸', '儿子'])
>>> family.values()
dict_values(['老林', '大林', '小林'])
>>> family.get('妈妈','不存在')   # 获取'妈妈'的值，如果不存在，就返回'不存在'
'不存在'
>>> family.get('爷爷','不存在')   # 获取'爷爷'的值，如果不存在，就返回'不存在'
'老林'
```

## 统计《Python之禅》的单词数量

```python
txt = '''
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
'''
# 创建空字典count
count = {}

# 将所有单词进行小写处理
txt = txt.lower()

# 将文本中特殊字符替换为空格
for ch in "',.--*!@#$%^&()[]{}\|？/<>":
    txt = txt.replace(ch,'')
    
# 使用split()方法将字符串txt按照空格进行分割，返回字符列表存入变量words中
words = txt.split()

# 遍历单词列表，使用get()方法查找字典count中的单词对应的值（单词数量），并在值上累加1
for word in words:
    count[word] = count.get(word, 0) + 1

# 遍历字典中元素，依次输出
for word in count.items():
    print(word)

```