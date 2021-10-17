# **Lesson-15**

## turtle库引入方法

> import turtle  &emsp; 直接导入turtle库

```python
import turtle
turtle.forward(100)
```

> import turtle as t &emsp;导入turtle库，并进行重命名

```python
import turtle as t
t.forward(100)
```

> from turtle import *  &emsp; 将turtle库所有功能函数导入

```python
from turtle import *
forward(100)
```

## turtle绘图指令别名

```python
turtle.forward(distance)
turtle.fd(distance)   # (简写)向当前画笔方向移动distance像素长度

turtle.backward(distance)
turtle.back(distance)  # (简写1)向当前画笔相反方向移动distance像素长度
turtle.bk(distance)	 # (简写2)向当前画笔相反方向移动distance像素长度

turtle.right(degree)
turtle.rt(degree)   # (简写)顺时针移动degree°

turtle.left(degree)
turtle.lt(degree)  # (简写)逆时针移动degree°

turtle.penup()
turtle.pu()  # (简写1)抬起画笔，不在画线
turtle.up()  # (简写2)抬起画笔，不在画线

turtle.pendown()
turtle.pd()    # (简写1)放下画笔，开始画线
turtle.down()  # (简写2)放下画笔，开始画线
```

## turtle辅助指令

```python
turtle.shape(name=None)	 # 指定形状“arrow”，“turtle”，“circle”，“square”，“triangle”，“classic”
turtle.clear()	# 从屏幕中删除指定海龟的绘图。不移动海龟。海龟的状态和位置以及其他海龟的绘图不受影响。
turtle.write(arg, font=("Arial", 8, "normal"))	# 书写
```

## turtle官方网站学习

<https://docs.python.org/zh-cn/3/library/turtle.html?highlight=turtle#turtle-methods>