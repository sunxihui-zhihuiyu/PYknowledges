# **Lesson-05**

## **汉诺塔**

> 汉诺塔法则

<img src='_media/2-5-1.png' alt='hanoi' style='zoom:40%;'/>
<img src='_media/2-5-2.png' alt='hanoi' style='zoom:40%;'/>

- 一次只能移动一个圆盘
- 小圆盘必须在大圆盘之上
- 将所有圆盘从A经过B移动到C

> 汉诺塔分析以及程序

- 基本程序

```python
# 汉诺塔目的：将n个圆盘从a柱子，经过b柱子，移动到c柱子
def hanoi(n, a, b, c):
    if n > 0:
        # 第一步：将n-1个圆盘从a柱子，经过c柱子，移动到b柱子
        hanoi(n-1, a, c, b)
        # 第二步：将第n个圆盘从a柱子，移动到c柱子
        print('Moving: {} -> {}.'.format(a, c))
        # 第三步：将n-1个圆盘从b柱子，经过a柱子，移动到c柱子
        hanoi(n-1, b, a, c)

hanoi(1, 'A', 'B', 'C')
print('===============')
hanoi(2, 'A', 'B', 'C')
print('===============')
hanoi(3, 'A', 'B', 'C')
```

- n个圆盘共移动了几步

```python
# 汉诺塔目的：将n个圆盘从a柱子，经过b柱子，移动到c柱子
counter = 0     # 设置计数器，它是一个全局变量

def hanoi(n, a, b, c):
    global counter    # 声明函数内部的变量global是全局变量，而不是局部变量
    if n > 0:
        # 第一步：将n-1个圆盘从a柱子，经过c柱子，移动到b柱子
        hanoi(n-1, a, c, b)
        # 第二步：将第n个圆盘从a柱子，移动到c柱子
        counter += 1             # 每搬运一次，计数器就+1
        print('Moving: {} -> {}.'.format(a, c))
        # 第三步：将n-1个圆盘从b柱子，经过a柱子，移动到c柱子
        hanoi(n-1, b, a, c)

hanoi(4, 'A', 'B', 'C')
print(counter)      # 结果：15
```

## **科赫曲线**
- 如果是0阶，只需要画一条直线即可；
- 如果是1阶，需要转0度，前进1/3长度，左转60°，前进1/3长度，左转-120°，前进1/3长度，左转60°，前进1/3长度即可。前进的长度，相当于0阶科赫曲线；
- 如果是2阶，则每次转弯之后，都绘制1阶的科赫曲线，2阶科赫曲线长度为1阶长度的1/3
- ...
- 如果是n阶，则每次转弯之后，都绘制n-1阶的科赫曲线，n阶科赫曲线长度为n-1阶长度的1/3.

```python
import turtle

def koch(size, n):
    if n == 0:                    # 0阶科赫曲线就是一条直线
        turtle.forward(size)
    else:                        # n阶科赫曲线就是将n-1阶曲线等分3等分，然后转向、绘制n-1阶科赫曲线
        for i in [0, 60, -120, 60]:
            turtle.left(i)
            koch(size/3, n-1)       

# 绘制一条3阶科赫曲线
koch(200, 3)

# 绘制科赫雪花
for i in range(3):
    koch(200, 3)
    turtle.right(120)
```