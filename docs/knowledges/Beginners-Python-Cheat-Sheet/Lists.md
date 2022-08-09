列表以特定顺序存储一系列项目。
列表允许您将一组信息存储在一个地方，无论你只有几件还是几百万件的项目。 列表是 Python 最强大的功能之一。

# 1. 定义一个列表 list

使用方括号定义列表，并使用逗号将列表中的各个项目分开。 使用复数命名列表，使您的代码更易于阅读。

> 创建列表
```python
users = ['val', 'bob', 'mia', 'ron', 'ned']
```

---

# 2. 访问元素

列表中的各个元素根据其访问位置，称为索引。 第一个元素的索引是0，第二个元素的索引为 1，以此类推。负索引是指列表末尾的项目。 
要得到一个特定的元素，写下列表的名称，然后方括号中元素的索引。

> 获取第一个元素
```python
first_user = users[0]
```

> 获取第二个元素
```python
first_user = users[1]
```

> 获取最后一个元素
```python
first_user = users[-1]
```
---

# 3. 修改单个元素

定义列表后，您可以更改列表中的元素。 你可以通过索引来修改对应的元素。

> 修改一个元素
```python
users[0] = 'valerie'
users[-2] = 'ronald'
```

---

# 4. 增加元素

您可以在列表末尾增加一个元素，或者在列表中任意一个位置插入一个元素。

> 在列表尾部增加一个元素
```python
user.append('amy')
```

> 从空列表开始增加元素
```python
users = []
users.append('val')
users.append('bob')
users.append('mia')
```

> 在特定位置插入一个元素
```python
users.insert(0, 'joe')
users.insert(3, 'bea')
```

---

# 5. 删除元素

您可以按元素在列表中的位置或按元素的值来删除元素。

> 按位置删除元素
```python
del users[-1]
```

> 按值删除元素
```python
users.remove('mia')
```

> 分配布尔值
```python
game_active = True
can_edit = False
```

---

# 6. 弹出元素

如果您想使用从列表中要删除的元素，您可以“弹出”该元素。 
默认情况下，` pop()` 返回列表中的最后一个元素，但您也可以从列表中的任何位置弹出元素。

> 弹出列表中最后一个元素
```python
most_recent_user = users.pop()
print(most_recent_user)
```

> 弹出列表中第一个元素
```python
first_user = users.pop(0)
print(first_user)
```

---

# 7. 列表长度

使用 `len()` 函数返回列表中元素的数量。

> 列表长度
```python
num_users = len(users)
print("We have " + str(num_users) + " users.")
```

---

# 8. 列表排序

`sort()` 方法永久更改列表的顺序，也就是改变列表本身的顺序。
`sorted()` 函数返回列表的副本，留下原名单不变。
您可以对列表中的项目进行排序字母顺序或逆字母顺序，你也可以颠倒列表的原始顺序。 请记住，小写和大写字母可能会影响排序顺序。

> 永久改变列表排序方法
```python
users.sort()
```

> 以反向字母的顺序永久改变列表排序方法
```python
users.sort(reverse=True)
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
使用圆括号定义一个元组。 

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