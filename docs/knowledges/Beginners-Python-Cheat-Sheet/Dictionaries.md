Python 的字典允许你将两项相关的信息进行匹配连接。 每一条信息在一个字典内存储为键值对。
当你提供一个键，Python 返回关联的值。 您可以遍历所有键值对、所有键或所有值。

# 1. 定义一个字典 dictionary

使用花括号`{}`来定义字典。 使用冒号连接键和值，并使用逗号分隔单独的键值对。

> 创建字典
```python
alien_0 = {'color': 'green', 'points': 5}
```

---

# 2. 访问值

要访问与单个键关联的值，请给出字典的名称，然后将键放在一组方括号内。 如果您要的键不在字典，就会出错。
您还可以使用 `get()` 方法，如果键不存在，该方法返回 `None`，而不是错误。 如果键不在字典，你也可以指定一个默认值，

> 获取存在键值对的值
```python
alien_0 = {'color': 'green', 'points': 5}

print(alien_0['color'])
print(alien_0['points'])
```

> 使用`get()`获取值
```python
alien_0 = {'color': 'green'}

alien_color = alien_0.get('color')
alien_points = alien_0.get('points', 0)

print(alien_color)    # 'green'
print(alien_points)   # 0
```

---

# 3. 增加新的键值对

您可以将任意数量的键值对存储在一个字典，直到您的计算机内存不足。 
可以为现有字典添加一个新键值，方法是给出字典和方括号中的新键，以及将其设置为等于新值。
这也允许您从空字典开始，然后添加相关的键值对。

> 增加一个键值对
```python
alien_0 = {'color': 'green', 'points': 5}

alien_0['x'] = 0
alien_0['y'] = 25
alien_0['speed'] = 1.5
```

> 给一个空字典增加一个键值对
```python
alien_0 = {}

alien_0['color'] = 'green'
alien_0['points'] = 5
```

---

# 4. 修改值 

您可以在通过键修改字典中对应的值。请给出字典的名字和将键放在方括号内，并且提供新的值。

> 修改字典中的值
```python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)

# Change the alien's color and point value.
alien_0['color'] = 'yellow'
alien_0['points'] = 10
print(alien_0)
```

---

# 5. 删除键值对

您可以使用 `del` 关键字、字典名称及后跟方括号中的键，删除键及其关联值。

> 删除键值对
```python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)

del alien_0['points']
print(alien_0)
```

---

# 6. 遍历字典

您可以通过三种方式遍历字典：您可以循环遍历所有键值对、所有键或所有值。
如果要按顺序处理字典信息，您可以对循环中的键进行排序。

> 遍历字典所有键值对
```python
# Store people's favorite languages.
fav_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

# Show each person's favorite language.
for name, language in fav_languages.items():
    print(name + ": " + language)
```

> 遍历字典所有的键
```python
# Show everyone who's taken the survey.
for name in fav_languages.keys():
    print(name)
```

> 遍历字典所有的值
```python
# Show all the languages that have been chosen.
for language in fav_languages.values():
    print(language)
```

> 按顺序遍历字典所有的键
```python
# Show each person's favorite language, 
# in order by the person's name.
for name in sorted(fav_languages.keys()):
    print(name + ": " + language)
```

---

# 7. 字典长度

您可以在字典中找到键值对的数量。

> 字典长度
```python
num_responses = len(fav_languages)
```

---

# 8. 嵌套-字典列表

有时将一组字典存储在列表中很有用，这称为嵌套。

> 将字典存储在列表中
```python
# Start with an empty list.
users = []

# Make a new user, and add them to the list.
new_user = {
    'last':'fermi',
    'first':'enrico',
    'username':'efermi'
    }
users.append(new_user)

# Make another new user, and add them as well.
new_user = {
    'last': 'curie',
    'first': 'marie',
    'username': 'mcurie'
    }
users.append(new_user)

# Show all information about each user.
for user_dict in users:
    for k, v in user_dict.items():
        print(k + ':' + v)
    print('\n')
```

> 您也可以不使用 append(), 直接定义字典列表
```python
# Define a list of users, where each user 
# is represented by a dictionary. 
users = [ 
    { 
        'last': 'fermi', 
        'first': 'enrico', 
        'username': 'efermi'
    },
    { 
        'last': 'curie', 
        'first': 'marie', 
        'username': 'mcurie'
    }
        ]
        
# Show all information about each user. 
for user_dict in users: 
    for k, v in user_dict.items(): 
        print(k + ": " + v) 
    print("\n")
```

> 临时改变列表排序方法
```python
print(sorted(users))
print(sorted(users, reverse=True))
```

> 倒序列表
```python
users.reverse()
```

---

# 9. 遍历列表

列表可以包含数百万个项目，因此 Python 提供了一个循环遍历列表中所有项目的有效方法。 什么时候您设置了一个循环，Python 从列表中提取每个项目一次并将其存储在一个临时变量中。这个临时变量的名字应该是单数列表名称的版本。
缩进的代码块构成了循环，您可以在其中处理每个单独的项目。 任何未缩进的行在循环完成后运行。

> 打印列表中所有的元素
```python
for user in users:
    print(user)
```

> 给每一个元素打印一条信息，并在遍历完成之后发出一个总的信息。
```python
for user in users:
    print("Welcome, " + user + "!")

print("Welcome, we're glad to see you all!")
```

---

# 10. `range()`函数

您可以使用 `range()` 函数来处理一组有效的数字。 `range()` 函数默认从 0 开始，到给出的参数值截止（不包含此参数）。 您可以使用 list() 函数有效地生成一个大量的数字。

> 打印从0-1000的数字
```python
for number in range(1001):
    print(number)
```

> 打印从1-1000的数字
```python
for number in range(1,1001):
    print(number)
```

> 生成1-1000000的数字列表
```python
numbers = list(range(1,1000001))
```

---

# 11. 简单的数据统计

您可以通过包含数字的列表进行简单的数据统计。

> 获取列表中的最小值

```python
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
youngest = min(ages)
```

> 获取列表中的最大值
```python
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
oldest = max(ages)
```

> 获取所有元素的和
```python
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
total_years = sum(ages)
```

---

# 12. 列表切片

您可以使用列表中的任何元素集。 列表的一部分称为切片。 从索引您想要的第一项开始切片列表，然后添加一个冒号和索引你想要的最后一个项目。 
省略第一个索引表示从列表的开头开始切片，省略最后一个索引表示切片到列表的末尾。

> 获取前三个元素
```python
finishers = ['kai', 'abe', 'ada', 'gus', 'zoe']
first_three = finishers[:3]    # ['kai', 'abe', 'ada']
```

> 获取中间三个元素
```python
middle_three = finishers[1:4]    # ['abe', 'ada', 'gus']
```

> 获取最后三个元素
```python
last_three = finishers[-3:]    # ['ada', 'gus', 'zoe']
```

---

# 13. 复制列表

要复制列表，请从第一项开始切片，然后在最后一项结束。 
如果您尝试复制列表而不使用这种方法，无论你对复制的列表做什么，都会影响原始列表。

> 复制列表
```python
finishers = ['kai', 'abe', 'ada', 'gus', 'zoe']
copy_of_finishers = finishers[:]    # ['kai', 'abe', 'ada', 'gus', 'zoe']
```

---

# 14. 列表推导式

您可以根据一个数字范围或另一个列表使用循环生成列表。 这是一个常见的操作，因此 Python 提供了一种更有效的方法来执行此操作。
列表推导起初可能看起来很复杂， 请熟练使用for 循环方法，要编写推导式，请为要存储在列表中的值定义一个表达式，然后编写一个 for 循环来生成制作列表所需的输入值。

> 使用循环生成一个有序数字列表
```python
squares = []
for x in range(1, 11):
    square = x**2
    squares.append(square)
```

> 使用列表推导式生成一个有序数字列表
```python
squares = [x**2 for x in range(1, 11)]
```

> 使用循环将列表中每个元素首字母转换为大写
```python
names = ['kai', 'abe', 'ada', 'gus', 'zoe']

upper_names = []
for name in names:
    upper_names.append(name.upper())
```

> 使用列表推导式将列表中每个元素首字母转换为大写
```python
names = ['kai', 'abe', 'ada', 'gus', 'zoe']

upper_names = [name.upper() for name in names]
```

---

# 15. 元组

元组就像一个列表，但是一旦定义了一个元组，就不能改变它。（你可以覆盖整个元组，但是您不能更改元组中的单个元素。）
元组适合存储在整个生命周期中不应更改的信息一个程序。 
元组使用圆括号包含元组中的信息。 

> 定义一个元组
```python
dimensions = (800, 600)
```

> 遍历一个元组
```python
for dimension in dimensions:
    print(dimension)
```

> 重新编写一个元祖
```python
dimensions = (800, 600)
print(dimensions)

dimensions = (1200, 900)
```

---

# 16. 代码可视化

当您第一次学习数据结构时，例如列表，它有助于可视化 Python 是如何处理程序中的信息。 
<https://pythontutor.com/> 是一个很棒的工具，用于查看 Python 如何跟踪信息列表。
尝试在 pythontutor.com 上运行以下代码，然后运行你自己的代码。

> 创建一个列表并打印列表中的值
```python
dogs = []
dogs.append('willie')
dogs.append('hootz')
dogs.append('peso')
dogs.append('goblin')

for dog in dogs:
    print("Hello " + dog + "!")
print("I love these dogs!")

print("\nThese were my first two dogs:")
old_dogs = dogs[:2]
for old_dog in old_dogs:
    print(old_dog)
    
del dogs[0]
dogs.remove('peso')
print(dogs)
```