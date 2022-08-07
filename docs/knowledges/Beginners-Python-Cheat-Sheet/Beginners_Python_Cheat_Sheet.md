# 1. 变量和字符串  Variable and String

变量用来存储数据。  
字符串是被单引号或者双引号引用的一系列字符。

> 打印输出`Hello world`
```python
print("Hello world!")
```

> 使用变量存储`Hello world` 并打印输出
```python
msg = "Hello world!"
print(msg)
```

> 拼接字符串（合并字符串）
```python
first_name = 'albert'
last_name == 'einstein'
full_name = first_name + ' ' + last_name
print(full_name)
```

---

# 2. 列表  List

一个列表用来存储以特定顺序排列的一系列数据元素。  
查看列表中的元素，可以通过下标查看，或者使用循环进行查看。

> 创建一个列表
```python
bikes = ['trek','redline','giant']
```

> 从一个列表中获取第一个元素
```python
first_bike = bikes[0]
```

> 从一个列表中获取最后一个元素
```python
last_bike = bikes[-1]
```

> 遍历一个列表
```python
for bike in bikes:
    print(bike)
```

> 向列表中增加一个元素
```python
bikes = []
bikes.append('trek')
bikes.append('redline')
bikes.append('giant')
```

> 创建数字列表
```python
squares = []
for x in range(1,11):
    squares.append(x**2)
```

> 列表推导式
```python
# 列表推导式是Python构建列表（list）的一种快捷方式,可以使用简洁的代码就创建出一个列表.
squares = [x**2 for x in range(1,11)]
```

> 分割列表（切片）
```python
finishers = ['sam','bob','ada','bea']
first_two = finishers[:2]
```

> 复制列表
```python
copy_of_bikes = bikes[:]
```

---

# 3. 元组  Tuple

元组类似于列表，但是元组中的元素不能被改变

> 创建一个元组
```python
dimensions = (1920,1080)
```

---

# 4. If 语句  If statement

if 语句用来测试特定条件和答案的正确性。

> 条件测试
```python
等于          x == 42
不等于        x != 42
大于          x > 42
大于或等于    x >= 42
小于          x < 42
小于或等于    x <= 42
```

> 使用列表进行条件测试
```python
bikes = ['trek','redline','giant']
'trek' in bikes
'surly' not in bikes
```

> 分配布尔值
```python
game_active = True
can_edit = False
```

> 简单的if语句
```python
if age >= 18:
    print("You can votel!")
```

> if-elif-else 语句
```python
if age < 4:
    ticket_price = 0
elif age <18:
    ticket_price = 10
else:
    ticket_price = 15
```

---

# 5. 字典 Dictionary

字典存储彼此之间相互有关联的信息。  
字典中每一个元素就是一对键值对（`key-value`）。

> 一个简单的字典
```python
alien = {'color':'green','points':5}
```

> 获取值的方法
```python
print("The alien's color is" + alien['color'])
```

> 增加新的键值对
```python
alien['x_position'] = 0
```

> 遍历查看所有的键值对
```python
fav_numbers = {'eric': 17, 'ever': 4}
for name, number in fav_numbers.items():
    print(name + ' loves ' + str(number))
```

> 遍历查看所有的键
```python
fav_numbers = {'eric': 17, 'ever': 4}
for name, number in fav_numbers.keys():
    print(name + ' loves a number')
```

> 遍历查看所有的值
```python
fav_numbers = {'eric': 17, 'ever': 4}
for name, number in fav_numbers.values():
    print(str(name) + 'is a favorite')
```

---

# 6. 用户输入  User input

程序中可能需要提供用户一个输入信息的窗口。    
所有的输入信息都会被存储为字符串类型。

>输入一个值
```python
name = input("What's your name? ")
print("Hello, " + name + "!")
```

> 输入一个整数值
```python
age = input("How old are you? ")
age = int(age)

pi = input("What's the value of pi? ")
pi = float(pi)
```

---

# 7. while循环 While loop

当一个确定条件成立时候，while循环会一直重复执行一段代码。

> 一个简单的while循环
```python
current_value = 1
while current_value <= 5:
    print(current_value) current_value += 1
```

>让用户选择什么时候退出
```python
msg = ''
while msg != 'quit':
    msg = input("What's your message? ")
    print(msg)
```

---

# 8. 函数 Function

函数是一段代码块，旨在完成一项特定的工作。传递给函数的信息称为实际参数，函数接收的信息称为形式参数。

> 一个简单的函数
```python
def greet_user():
    """Display a simple greeting.""" 
    print("Hello!")

greet_user()
```

>传入一个实际参数
```python
def greet_user(username):
    """Display a personalized greeting."""
    print("Hello, " + username + "!")

greet_user('jesse')
```

>定义一个默认参数
```python
def make_pizza(topping='bacon'):
    """Make a single-topping pizza."""
    print("Have a " + topping + " pizza!")

make_pizza()
make_pizza('pepperoni')
```

>函数返回值
```python
def add_numbers(x, y):
    """Add two numbers and return the sum."""
    return x + y
    
sum = add_numbers(3, 5)
print(sum)
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