# 函数 Function

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