# **Lesson-06**

## 模块

> 定义

- 一个模块就是包含了你定义的类、函数和变量的文件，其后缀名是.py
- 可以被别的程序引入，以使用该模块中的函数等功能

> 分类

- 内置模块：即python中自带的模块，例如random、time模块等。
- 自定义模块：自定义模块是自己写的文件，某些函数进行封装后供其他程序调用。
- 第三方的开源模块：这部分模块需要通过安装后才能使用，有开源的代码。

> 导入方法

```python
import 模块名    #导入整个模块
例：import random
```

```python    
import 模块名 as 变量名    #导入整个模块，并给模块起个别名
例：import random as r
```

```python
from 模块名 import 函数名    #从模块中导入其中指定的函数
例：from random import randint
```

```python
from 模块名 import 函数名 as 变量名     #从模块中导入指定的函数，并起别名
例：from random import randint as r
```

```python      
from 模块名 import *    #导入模块中的所有内容（不建议常用）
例：from random import *
```

## 模块-包-库
- 模块：具有单独功能的代码片段保存成的文件，也就是一些.py的文件。
- 包：简单的说，包是一个包含__init__.py 文件的文件夹，该文件夹下一定得有这个__init__.py文件和其它模块或子包。
- 库：是具有相关功能模块的集合。这也是Python的一大特色之一，即具有强大的标准库、第三方库以及自定义模块

## 常用内置模块

> random

```python
>>>import random
>>>random.random()
# 结果：0.38476193749
>>>random.randint(1,10)
# 结果： 3
```

> time

```python
>>>import time
>>>time.sleep(2)
# 结果：程序暂停2s
```

> math

```python
>>>import math
>>>math.pi
# 结果：3.141592653589793
>>>math.pow(2,10)
# 结果： 1024.0
```