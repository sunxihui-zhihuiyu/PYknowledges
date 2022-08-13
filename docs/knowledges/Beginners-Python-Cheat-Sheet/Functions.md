函数是命名的旨在执行一项特定的工作的代码块。 根据你需要，就可以运行函数完成同样的任务。 函数可以输入他们需要的信息，并产生返回他们期望的结果。 有效地使用函数让你的程序更易于编写、阅读、测试和修复。

# 1. 定义函数

函数的第一行，是使用 `def` 关键字定义一个函数，函数名后跟一组括号和冒号。
一个文档字符串需要使用三个引号，用来描述函数的作用。
函数的主体需要缩进一级。
要调用函数，只需要给出函数名称级后面的括号即可。

> 定义一个函数
```python
def greet_user():
    """Display a simple greeting."""
    print("Hello!")
greet_user()
```

---

# 2. 向函数内传入信息（参数）

定义函数时候传递给函数的信息称之为形式参数，调用函数时候传递给函数的信息称之为实际参数。

> 传递一个参数
```python
def greet_user(username):
    """Display a simple greeting."""
    print("Hello, " + username + "!")

greet_user('jesse')
greet_user('diana')
greet_user('brandon')
```

---

# 3. 位置参数和关键字参数

有两种主要的参数就是位置参数和关键字参数。当你使用位置参数时候，Python自动依次从第一个位置匹配定义函数和调用函数时候的参数。当你是用关键字参数的时候，调用函数时候，实际参数前面添加上形式参数，这样就无需关注参数的位置。

> 使用位置参数
```python
def describe_pet(animal, name):
    """Display information about a pet."""
    print("\nI have a " + animal + ".")
    print("Its name is " + name + ".")

describe_pet('hamster', 'harry')
describe_pet('dog', 'willie')
```

> 使用关键字参数
```python
def describe_pet(animal, name):
    """Display information about a pet."""
    print("\nI have a " + animal + ".")
    print("Its name is " + name + ".")

describe_pet(animal='hamster', name='harry')
describe_pet(name='willie', animal='dog')
```

---

# 4. 默认参数 

在定义函数时候，可以给形式参数一个实际的值。在调用函数的时候，如果不给这个形式参数一个实际值，函数则自动调用已经设置好的值。

> 使用默认参数
```python
def describe_pet(name, animal='dog'):
    """Display information about a pet."""
    print("\nI have a " + animal + ".")
    print("Its name is " + name + ".")

describe_pet('harry', 'hamster')
describe_pet('willie')
```

> 使用 `None` 使参数可选
```python
def describe_pet(animal, name=None):
    """Display information about a pet."""
    print("\nI have a " + animal + ".")
    if name:
        print("Its name is " + name + ".")

describe_pet('hamster', 'harry')
describe_pet('snake')
```

---

# 5. 返回值

一个函数可以返回一个值或者返回一系列值。当一个函数返回了一个值后，调用函数的时候，必须提供一个变量存储这个返回值。
同时，返回值的语句也表示函数运行截止。

> 返回一个值
```python
def get_full_name(first, last):
    """Return a neatly formatted full name."""
    full_name = first + ' ' + last
    return full_name.title()

musician = get_full_name('jimi', 'hendrix')
print(musician)
```

> 返回一个字典
```python
def build_person(first, last):
    """Return a dictionary of information
    about a person.
    """
    person = {'first': first, 'last': last}
    return person

musician = build_person('jimi', 'hendrix')
print(musician)
```

> 返回一个具有可选值的字典
```python
def build_person(first, last, age=None):
    """Return a dictionary of information
    about a person.
    """
    person = {'first': first, 'last': last}
    if age:
        person['age'] = age
    return person

musician = build_person('jimi', 'hendrix', 27)
print(musician)

musician = build_person('janis', 'joplin')
print(musician)
```

---

# 6. 向函数中传入一个列表

您可以向函数中传入一个列表参数，并且使用函数处理列表中的值。
函数中对列表的改变都会对原始列表产生影响（列表能够被函数改变）。
您可以复制这个列表当做列表的副本，将副本当做是函数的参数，从而保证函数不改变原始列表。

> 函数中传入列表参数
```python
def greet_users(names):
    """Print a simple greeting to everyone."""
    for name in names:
        msg = "Hello, " + name + "!"
        print(msg)

usernames = ['hannah', 'ty', 'margot']
greet_users(usernames)
```

> 允许函数修改列表
- 在下列案例中，初始列表是空列表，第二个列表是非空列表。
```python
def print_models(unprinted, printed):
    """3d print a set of models."""
    while unprinted:
        current_model = unprinted.pop()
        print("Printing " + current_model)
        printed.append(current_model)

# Store some unprinted designs,
# and print each of them.
unprinted = ['phone case', 'pendant', 'ring']
printed = []
print_models(unprinted, printed)

print("\nUnprinted:", unprinted)
print("Printed:", printed)
```

> 阻止函数修改列表
- 在下列案例中，初始列表没有被改变。
```python
def print_models(unprinted, printed):
    """3d print a set of models."""
    while unprinted:
        current_model = unprinted.pop()
        print("Printing " + current_model)
        printed.append(current_model)

# Store some unprinted designs,
# and print each of them.
original = ['phone case', 'pendant', 'ring']
printed = []

print_models(original[:], printed)
print("\nOriginal:", original)
print("Printed:", printed)
```

---

# 7. 传入可变参数

有时候，您不会提前知道函数会接收多少个参数。Python允许您将任意数量的参数放入一个参数中,只需要在这个参数名称前加上 "*" 即可。可变参数一定放到函数参数列表的最后。
"**" 符号允许函数接收可变数量的关键字参数。

> 接收任意数量的参数
```python
def make_pizza(size, *toppings):
    """Make a pizza."""
    print("\nMaking a " + size + " pizza.")
    print("Toppings:")
    for topping in toppings:
        print("- " + topping)

# Make three pizzas with different toppings.
make_pizza('small', 'pepperoni')
make_pizza('large', 'bacon bits', 'pineapple')
make_pizza('medium', 'mushrooms', 'peppers', 'onions', 'extra cheese')
```

> 接收任意数量的关键字参数
```python
def build_profile(first, last, **user_info):
    """Build a user's profile dictionary."""
    # Build a dict with the required keys.
    profile = {'first': first, 'last': last}

    # Add any other keys and values.
    for key, value in user_info.items():
        profile[key] = value

    return profile

# Create two users with different kinds
# of information.
user_0 = build_profile('albert', 'einstein', location='princeton')
user_1 = build_profile('marie', 'curie', location='paris', field='chemistry')

print(user_0)
print(user_1)
```

---

# 8. 模块

您可以将含有函数的程序存储在一个python文件中，这个文件就称之为模块。
您可以使用`import`从模块中调用这个函数。

> 将函数存储在模块中
- 文件：pizza.py
```python
def make_pizza(size, *toppings):
    """Make a pizza."""
    print("\nMaking a " + size + " pizza.")
    print("Toppings:")
    for topping in toppings:
        print("- " + topping)
```

> 调用一个存在的模块
- 文件：making_pizzas.py
```python
import pizza

pizza.make_pizza('medium', 'pepperoni')
pizza.make_pizza('small', 'bacon', 'pineapple')
```

> 调用一个特殊函数
- 只调用这个模块中的一个函数
```python
from pizza import make_pizza

make_pizza('medium', 'pepperoni')
make_pizza('small', 'bacon', 'pineapple')
```

> 给模块起一个别名
```python
import pizza as p

p.make_pizza('medium', 'pepperoni')
p.make_pizza('small', 'bacon', 'pineapple')
```

> 给函数起一个别名
```python
from pizza import make_pizza as mp

mp('medium', 'pepperoni')
mp('small', 'bacon', 'pineapple')
```

> 调用模块中的所有函数
- 一般情况下不建议使用这种方式，因为它可能会由于函数重名而造成错误。
```python
from pizza import *

make_pizza('medium', 'pepperoni')
make_pizza('small', 'bacon', 'pineapple')
```

