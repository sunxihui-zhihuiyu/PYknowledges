# **Lesson-07**

## 一、 python面向对象对的编程思想

在前期课程中，我们逐渐认识到python面向对象编程思想含义，每一种数据类型都是一个类，每一个数据都是类的实例对象，他们都有属性和方法，我们可以对他们进行相关的操作。

```python
>>> class Student:
        pass

>>> student = Student()

>>> type(student)
<class '__main__.Student'>


>>> file = open('python.txt','r',encoding='utf-8')
>>> type(file)
<class '_io.TextIOWrapper'>

>>> s = {'name':'smartfisher', 'age':8}
>>> type(s)
<class 'dict'>
```

上例中，我们定义了一个Student类，实例了一个student对象，通过type()函数发现student对象的类型就是Student类;  

同理，我们打开一个文本文件，相当于实例化了一个对象file，它的类型就是文本类型；  

我们创建了一个字典s，相当于实例化了一个对象s，它的类型就是字典。  

大家可以使用type()函数查看所有python中遇到的数据属于的类型。


## 二、list.sort()方法及sorted()内置函数

> 1、区别

sort 与 sorted 区别：

1. sort() 是应用在 list 上的方法，属于列表的成员方法，sorted() 可以对所有可迭代的对象进行排序操作。  
2. list 的 sort 方法返回的是对已经存在的列表进行操作，而内建函数 sorted 方法返回的是一个新的 list，而不是在原来的基础上进行的操作。  
3. sort使用方法为`ls.sort()`，而sorted使用方法为`sorted(ls)`

> 2、list.sort()方法

1. list.sort()方法基本使用

    在python中，我们常见的排序方法是使用列表的`sort()方法`将列表元素进行排序。 

    列表sort()方法是对原列表进行直接排序，没有返回值。sort()方法排序原理是，将数字、字符串按照ASCII进行排序，中文按照unicode从小到大排序。

    在sort()方法中，有两个默认的形式参数，第一个是排序的元素，第二个是排序规则。接下来我们对两个参数进行一一介绍。

    `list.sort(key=None, reverse=False)`

        - key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
        -  reverse -- 排序规则，reverse = True 降序， reverse = False 升序（默认）。
        - 该方法没有返回值，但是会对列表的对象进行排序。

    ```python
    >>> number = [3,5,2,1,5,6]
    >>> number.sort()
    >>> number
    [1,2,3,5,5,6]
    ```

2. key参数的使用

    在这里，我们首先可以新建一个功能函数f，这个函数可以返回排序参照的元素，也就是对谁进行排序。  
    在此案例中，我们依据每个元素本身进行排序，则返回的就是元素本身。所以在实际排序中，我们跟key参数进行赋值为函数f。  
    第二个参数代表着升序还是降序，如果参数值为True，则为降序排序，如果为False，则为升序排序。  
    通过对number列表进行排序，排序对象是每个元素本身，排序规则为升序，则列表依据数据大小进行排序。  

    ```python
    def f(x):
        return x

    number = [3,1,4,2,5]

    number.sort(key=f, reverse=True)
    print(number)   # [5,4,3,2,1]

    number.sort(key=f, reverse=False)
    print(number)   # [1,2,3,4,5]
    ```

    如果列表每个元素都是列表或者元组类型呢？要求按照每个元素的某一项进行排序，则该如何进行？  
    例如，在下述案例中，列表score中，每个元素都是列表类型，列表第一项为学生姓名，列表第二项为学生分数，如何按照学生分数进行排序？  
    首先要确定排序面向的元素，然后赋值给key参数，并且确定排序规则即可。  

    ```python
    scores = [['小张',90], ['小王', 78], ['小刘', 82]]

    def f(x):
        return x[1]

    scores.sort(key=f, reverse=True)
    print(scores)  #  [['小张',90],  ['小刘', 82], ['小王', 78]]
    ```

> 3、sorted()函数

`new_list = sorted(iterable，key=None, reverse=False)`

两者中都存在的key参数和reverse参数用法一致。  

大家可以通过列表sort()方法和内置函数sorted()认真对比方法和函数的不同和相同。  

相同点是：方法就是函数。  

不同点是：方法是对象的内置函数，这个函数操作的对象就是点之前已经确定的对象；而内置函数的对象需要在后续参数中给出。

文件可以通过python内置函数`open()`进行打开，打开之后我们使用变量接收文件内容。我们可以将这个部分看作是类的实例化对象。

## 三、《乌鸦和狐狸》词频前十名

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

counts_list = list(counts.items())

# 定义排列参考规则
def f(x):
    return x[1]

# 排列
counts_list.sort(key = f, reverse = True)

#counts_list.sort(key = lambda x: x[1], reverse = True)

for i in range(10):
    word, count = counts_list[i]
    print('{}-{}'.format(word, count))

file.close()
```

## 四、lambda函数

在排序过程中，我们发现需要新建一个函数，这个函数的作用是直接返回一个需要排序的数值。  
我们可以将这种函数简写为`lambda函数`。  
用`lambda函数`首先减少了代码的冗余；其次，用`lambda函数`，不用费神地去命名一个函数的名字，可以快速的实现某项功能；最后，`lambda函数`使代码的可读性更强，程序看起来更加简洁。

`lambda argument_list:expersion`  
`lambda <参数列表> ： <表达式>`  

lambda函数的表达是是唯一的，lambda关键字后面直接跟函数形式参数列表，冒号后加上要返回的表达时即可。

```python
def f(x):
    return x[1]

===>  lambda x: x[1]
```

```python
def my_sum(n1,n2):
    return n1+n2
test = my_sum(3,4)

===> test = (lambda n1, n2: n1+n2)(3,4)
```

> <a href="_media/三国演义.txt" title="三国演义" download="三国演义.txt">三国演义(中文)下载</a>  

> <a href="_media/hamlet.txt" title="hamlet" download="hamlet.txt">哈姆雷特(英文)下载</a