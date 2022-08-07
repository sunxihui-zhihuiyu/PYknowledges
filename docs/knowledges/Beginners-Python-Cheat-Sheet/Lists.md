# 1. 定义一个列表 list

列表以特定顺序存储一系列项目。

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

# 9. 类 Class

一个类定义了对象的行为以及对象可以存储的信息类型。  
类中的信息存储在属性中，属于某个类的函数称为方法。  
子类从其父类继承属性和方法。

> 定一个小狗类
```python
class Dog():
    """Represent a dog."""

    def __init__(self, name):
        """Initialize dog object."""
        self.name = name

    def sit(self):
        """Simulate sitting."""
        print(self.name + " is sitting.")

my_dog = Dog('Peso')

print(my_dog.name + " is a great dog!")
my_dog.sit()
```

> 继承
```python
class SARDog(Dog):
    """Represent a search dog."""

    def __init__(self, name):
        """Initialize the sardog."""
        super().__init__(name)
    
    def search(self):
        """Simulate searching."""
        print(self.name + " is searching.")
        
my_dog = SARDog('Willie')

print(my_dog.name + " is a search dog.")
my_dog.sit()
my_dog.search()
```

---

# 10. 文件操作 Working with file

Python程序可以对文件进行读写操作。  
文件可以以只读模式（'r'）打开，也可以以写模式（'w'）和追加模式（'a'）打开。

> 读取一个文件并存储其每一行内容

```python
filename = 'siddhartha.txt'
with open(filename) as file_object:
    lines = file_object.readlines()
    
for line in lines:
    print(line)
```

> 向一个文件中写入内容
```python
filename = 'journal.txt'
with open(filename, 'w') as file_object:
    file_object.write("I love programming.")
```

> 向一个文件中追加内容
```python
filename = 'journal.txt'
with open(filename, 'a') as file_object:
    file_object.write("\nI love making games.")
```

> 对中文文件读写操作时候，需要设置解码类型为'utf-8'
```python
filename = 'journal.txt'
with open(filename, 'a', encoding='utf-8') as file_object:
    file_object.write("\nI love making games.")
```

---

# 11. 异常 Exception

异常可帮助我们对可能发生的错误做出适当的响应。  
在 try 代码块中放置可能导致错误的代码。  
响应错误而运行的代码位于 except 代码块中。  
仅当 try 代码块成功时才应运行的代码将进入 else 代码块。

> 抛出异常
```python
prompt = "How many tickets do you need? "
num_tickets = input(prompt)

try:
    num_tickets = int(num_tickets)
except ValueError:
    print("Please try again.") 
else:
    print("Your tickets are printing.")
```