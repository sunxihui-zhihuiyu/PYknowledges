### **2-01：函数定义与调用的通用方法**⭐

**题目：** 可以将常规代码，使用函数进行封装定义，并进行调用。

如：求整数n的阶乘。如5的阶乘为`5 = 5*4*3*2*1`，4的阶乘为`4! = 4*3*2*1 `

**程序分析：** 定义函数fac()，并传入参数n，返回参数n的阶乘结果。

```python
def fac(n):    # 定义函数
    s = 1
    for i in range(1,n+1):
        s = s*i
    return s

result = fac(5)   # 调用函数
print(result)    # 打印结果
```

### **2-02：利用递归函数求整数n的阶乘**⭐

**题目：** 定义函数fac()，并传入参数n，返回参数n的阶乘结果。

**程序分析：** n的阶乘 `n! = n * (n-1)!`

```python
def fac(n):       # 定义函数
    if n == 1:    # 终止条件
        return 1
    return n * fac(n-1)   # 递归调用

result = fac(5)   # 调用函数
print(result)    # 打印结果
```

### **2-03：利用递归函数求数列1到N的前n项之和**⭐

**题目：** 定义函数fac()，并传入参数n，返回1+2+...+n的结果。

**程序分析：** 无

```python
def fac(n):       # 定义函数
    if n == 1:    # 终止条件
        return 1
    return n + fac(n-1)   # 递归调用

result = fac(5)   # 调用函数
print(result)    # 打印结果
```

### **2-04：求年龄** ⭐

**题目：** 有5个⼈坐在⼀起，问第五个⼈多少岁？他说⽐第4个⼈⼤2岁。问第4个⼈岁数，他说⽐第3个⼈⼤2岁。问第三个⼈，⼜说⽐第2⼈⼤两岁。问第2个⼈，说⽐第⼀个⼈⼤两岁。最后问第⼀个⼈，他说是10岁。请问第五个⼈多⼤？

**程序分析：** 递归求解。

```python
def age(n):
    if n == 1:
        c = 10
    else:
        c = age(n - 1) + 2
        return c
    
print ("第五个人的年龄是：", age(5))
```

### **2-05：验证码生成**⭐

**题目：** 设计⼀个函数产⽣指定⻓度的验证码，每⼀位的验证码由⼤⼩写字⺟和数字构成，不同位上的
验证码可以重复，⽐如验证码：qqwww。

**程序分析：** 无

```python
import random
def generate_code(code_len):
    all_chars = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
    last_pos = len(all_chars) - 1
    code = ''
    for i in range(code_len):
        index = random.randint(0, last_pos)
        code += all_chars[index]
    return code

n = int(input("验证码的长度是："))
print(generate_code(n))
```

### **1-06：反向求出生年月**⭐

**题目：** 定义函数birth(), 输入参数年龄age, 通过time模块方向求出出生年份。

**程序分析：** `time.strftime('%Y')`求出现在年份

```python
import time

def birth(age):
    t = time.strftime('%Y')
    bir = int(t) - age
    return '你是{}年出生的。'.format(bir)

result = birth(10)   # 调用函数
print(result)    # 打印结果
```

### **1-07：利用函数绘图**⭐

**题目：** 定义函数drawRect(), 绘制方形，调用函数绘制以下图形。
每个正方形边长为200，颜色分别为`'red'、'green'、'blue'`

<img src='_media/2-17-1.png' alt='函数绘图' style='zoom:40%;'/>

**程序分析：** 无

```python
import turtle

def drawRect(color):
    turtle.fillcolor(color)
    turtle.begin_fill()
    for i in range(4):
        turtle.forward(200)
        turtle.left(90)
    turtle.forward(200)
    turtle.end_fill()
    
drawRect('red')
drawRect('green')
drawRect('blue')
```

### **1-08：掷色子**⭐

**题目：** 每个骰子有1-6个点。随机投掷三个骰子，三个骰子点数之和小于5的时候，则结果显示“小”；三个骰子点数之和大于等于5的时候，则结果显示“大”。

**程序分析：** 随机数模块为random，随机整数函数为randint()

```python
import random

def dice():
    return random.randint(1,6)

n1 = dice()
n2 = dice()
n3 = dice()
print(n1 + n2 + n3)
```