# **Lesson-14**

## **位置**

> 相对坐标

- 以乌龟自身为坐标原点前进、转弯

<img src='_media/1-14-3.png' alt='walk' style='zoom:40%;'/>

<img src='_media/1-14-4.png' alt='turn' style='zoom:40%;'/>

> 绝对坐标

- 以画布窗体正中心为原点坐标
goto()位移到某一坐标点，seth()转到某一固定方向

<img src='_media/1-14-1.png' alt='walk' style='zoom:40%;'/>

<img src='_media/1-14-2.png' alt='turn' style='zoom:40%;'/>

## **turtle坐标系相关指令**

```python
turtle.setup(width，height,startx, starty)	# 设置窗体大小及位置
turtle.goto(x,y)	# 移动到画布中的特定位置（x,y）处
turtle.penup()	# 抬起画笔，不在画线
turtle.pendown()	# 放下画笔，开始画线
turtle.setheading(angle)	# 别名：seth(anlge)。设置当前朝向为angle角度
turtle.home()	# 设置当前画笔位置为原点，朝向东
turtle.undo()	# 撤销画笔最后一步动作
turtle.done()	# 结束绘画，但不关闭窗体
```

## **三角形案例**

```python
import turtle

turtle.setup(400,400,100,100)  # 设置窗体位置和大小
turtle.pensize(2)    # 设置画笔粗细
turtle.pencolor('green')    # 设置画笔颜色
turtle.speed(3)    # 设置动画速度
turtle.fillcolor('red')    # 设置填充色
turtle.begin_fill()    # 开始填充

# 根据绝对位置绘制等边三角形
turtle.goto(-100,0)
turtle.goto(100,0)
turtle.goto(0,100)
turtle.goto(-100,0)

turtle.end_fill()    # 结束填充
```