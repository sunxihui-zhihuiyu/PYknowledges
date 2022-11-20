# **Lesson-08**

## **random模块常用函数**

> `random.random()`    # 返回一个0-1之间的随机浮点数

```python
>>> import random
>>> random.random()
0.3922292574839563
```

> `random.randint()`    # 须在括号内添加下限与上限值，下限<=返回值<=上限

```python
>>> import random
>>> random.randint(0,10)   # 返回0-10之间的随机数，包含0和10
2
```

> `random.randrange()`    # 括号内可添加三个值，下限、上限、步长，下限<= 返回值<上限，且返回值是下限值加步长或加步长的倍数

```python
>>> import random
>>> random.randrange(0,10,3)  # 返回0，3，6，9中的随机数
3
```

> `random.choice()`    # 用来从序列中选择一个元素，这个序列可以是字符串、元组、列表

```python
>>> import random
>>> str= 'hello word'
>>> random.choice(str)   # 在'hello word'中随机选取一个字母元素
'e'
```

