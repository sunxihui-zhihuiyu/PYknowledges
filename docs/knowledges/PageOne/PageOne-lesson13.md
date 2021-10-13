# **Lesson-13**

## **导入turtle库**

```python
import turtle
```

## **绘图指令**

```python
turtle.forward(100)  # 向前移动100像素
turtle.backward(100) # 向后移动100像素
turtle.right(90)  # 右转90度
turtle.left(90)  # 左转90度
turtle.circle(100)  # 绘制半径为100像素的圆
turlte.circle(100, 90)  # 绘制半径为100像素，弧度为90度的圆弧
turtle.dot(50, 'blue')  # 绘制直径为50，颜色为蓝色的点
```

## **画笔指令**

```python
turtle.pensize(5)  # 设置画笔的宽度为5
turtle.pencolor('blue')  # 设置画笔颜色为蓝色
turtle.speed(1)  # 设置画笔移动速度为1。速度值从 1 到 10，画线和海龟转向的动画效果逐级加快。如果速度值为0，表示没有动画效果。
turtle.fillcolor('blue')  # 绘制图形的填充颜色为蓝色
turtle.begin_fill()  # 准备开始填充图形
turtle.end_fill()  # 填充完成
```

## **三角形案例**

```python
import turtle
turtle.pensize(2)    # 设置画笔粗细
turtle.pencolor('green')    # 设置画笔颜色
turtle.speed(3)    # 设置动画速度
turtle.fillcolor('red')    # 设置填充色
turtle.begin_fill()    # 开始填充
for i in range(3):     # 绘制等边三角形
    turtle.right(120)
    turtle.forward(100)
turtle.end_fill()    # 结束填充
```