if 语句允许您检查当前程序状态，并适当地响应该状态。
您可以编写一个简单的 if 语句来检查一个条件，或者您可以创建一系列复杂的 if 语句来判断您所需要的条件。

while 语句是只要某些条件存在，while 循环就会运行。 您可以使用 while 循环让您的程序一直运行，只要您的用户希望他们运行。

# 1. 条件测试

条件测试是一个表达式，可以计算为对或错。 Python 使用 True 和 False 值决定 if 语句中的代码是否应该执行。

> 检查是否相等
- 单个等号为变量赋值。 双等号符号 (==) 检查两个值是否相等。
```python
>>> car = 'bmw'
>>> car == 'bmw'
True
>>> car = 'audi'
>>> car == 'bmw'
False
```

> 比较时忽略大小写
```python
>>> car = 'Audi'
>>> car.lower() == 'audi'
True
```

> 检查是否不相等
```python
>>> topping = 'mushroom'
>>> topping != 'anchovies'
True
```

---

# 2. 数值比较

检测数值大小的方法与检测字符串的值的方法类似。

> 检测相等与不相等
```python
>>> age = 18
>>> age == 18
True
>>> age != 18 
False
```

> 比较运算符
```python
>>> age = 19
>>> age < 21
True
>>> age <= 21
True
>>> age > 21
False
>>> age >= 21
False
```

---

# 3. 多条件检测

您可以同时检测多个条件，如果所有条件检测结果都为 `True`，`and`运算符返回`True`；如果有任意一个条件检测结果为 `True`，`or`运算符返回`True`。

> 使用 `and` 检测多条件
```python
>>> age_0 = 22
>>> age_1 = 18
>>> age_0 >= 21 and age_1 >= 21
False
>>> age_1 = 23
>>> age_0 >= 21 and age_1 >= 21
True
```

> 使用 `or` 检测多条件
```python
>>> age_0 = 22
>>> age_1 = 18
>>> age_0 >= 21 or age_1 >= 21
True
>>> age_0 = 18
>>> age_0 >= 21 or age_1 >= 21
False
```

---

# 4. 布尔值 

布尔值是 `True` 或 `False`。 变量与布尔值通常用于表示某些程序中的条件检测结果。

> 简单的布尔值
```python
game_active = True
can_edit = False
```

---

# 5. if 语句

存在几种 if 语句。 根据检测的条件数量选择不同的 if 语句。您可以根据需要拥有任意数量的 elif 块，并且 else 块始终是可选的。

> 单分支 if 语句
```python
age = 19
if age >= 18:
    print("You're old enough to vote!")
```

> 双分支 if-else 语句
```python
age = 17
if age >= 18:
 print("You're old enough to vote!")
else:
 print("You can't vote yet.")
```

> 多分支 if-elif-else 语句
```python
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
else:
    price = 10

print("Your cost is $" + str(price) + ".")
```

---

# 6. 与列表相关的条件检测

您可以轻松测试某个值是否在列表中。 你还可以在尝试循环之前测试列表是否为空。

> 检测某个值是否在列表中
```python
>>> players = ['al', 'bea', 'cyn', 'dale']
>>> 'al' in players
True
>>> 'eric' in players
False
```

> 检测一个值是否不在列表中
```python
banned_users = ['ann', 'chad', 'dee']
user = 'erin'
if user not in banned_users:
    print("You can play!")
```

> 检测一个列表是否为空
```python
players = []
if players:
    for player in players:
        print("Player: " + player.title())
else:
    print("We have no players yet!") 
```

---

# 7. 输入

您可以允许您的用户使用 `input()` 输入数据。 在 Python3 中，所有输入都存储为字符串。

> 简单输入
```python
name = input("What's your name? ")
print("Hello, " + name + ".")
```

> 接收数字输入
```python
age = input("How old are you? ")
age = int(age)
if age >= 18:
    print("\nYou can vote!")
else:
    print("\nYou can't vote yet.") 
```

---

# 8. while 循环

当条件成立时候，while 循环将重复执行一个代码块。

> 计数到5
```python
#current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1
```

> 让用户选择何时退出
```python
prompt = "\nTell me something, and I'll "
prompt += "repeat it back to you."
prompt += "\nEnter 'quit' to end the program. "

message = ""
while message != 'quit':
    message = input(prompt)

    if message != 'quit':
        print(message)
```

> 标志（flag）的使用
```python
prompt = "\nTell me something, and I'll "
prompt += "repeat it back to you."
prompt += "\nEnter 'quit' to end the program. "

active = True
while active:
    message = input(prompt)

    if message == 'quit':
        active = False
    else:
        print(message)
```

> 使用`break`退出循环
```python
prompt = "\nWhat cities have you visited?"
prompt += "\nEnter 'quit' when you're done. "

while True:
    city = input(prompt)

    if city == 'quit':
        break
    else:
        print("I've been to " + city + "!")
```

> 使用`continue`继续循环
```python
banned_users = ['eve', 'fred', 'gary', 'helen']

prompt = "\nAdd a player to your team."
prompt += "\nEnter 'quit' when you're done. "

players = []
while True:
    player = input(prompt)
    if player == 'quit':
        break
    elif player in banned_users:
        print(player + " is banned!")
        continue
    else:
        players.append(player)

print("\nYour team:")
for player in players:
    print(player)
```

---

# 9. 避免无限循环

每一个循环都需要停止，防止它无限运行。

> 无限循环
```python
while True:
    name = input("\nWho are you? ")
    print("Nice to meet you, " + name + "!")
```

---

# 10. 从列表中删除特定的值

您可以使用`remove()`方法从列表中删除特定的值。但是这个方法只能删除列表中的第一个找到的值，所以还需要使用`while`循环完成这个项目。

> 从列表中删除特定的值
```python
pets = ['dog', 'cat', 'dog', 'fish', 'cat', 'rabbit', 'cat']
print(pets)
while 'cat' in pets:
    pets.remove('cat')
print(pets)
```
