# **Lesson-16**

## **扇形的画法**
- 一条圆弧和经过这条圆弧两端的两条半径所围成的图形叫扇形（半圆与直径的组合也是扇形）。
- 扇形是圆的一部分。
- 在圆（或者扇形）中，圆弧切线与半径垂直。

<img src='_media/1-16-1.jpg' alt='sector' style='zoom:100%;'/>
<img src='_media/1-16-2.jpg' alt='draw_sector' style='zoom:100%;'/>

> 顺时针画扇形

```python
import turtle
turtle.seth(100)
turtle.forward(200)
turtle.left(90)
turtle.circle(200,60)
turtle.left(90)
turtle.forward(200)
```

> 逆时针画扇形

```python
import turtle
turtle.seth(100)
turtle.forward(200)
turtle.right(90)
turtle.circle(200,60)
turtle.right(90)
turtle.forward(200)
```

## **turtle颜色模式**

> turtle颜色值的两种模式

- color(colorstring)   设置填充颜色为 colorstring 指定的 Tk 颜色描述字符串，例如 "red"、"yellow" 或 "#33cc8c"。
- color(R,G,B)   设置填充颜色为以 r, g, b 元组表示的 RGB 颜色。RGB颜色可以为0-255整数值，也可以为0-1的小数值。使用时，需提前设置模式。

```python
import turtle

turtle.colormode(255)
turtle.pencolor(100,100,255)

turtle.colormode(1)
turtle.pencolor(0.1,0.1,1)
```

> python中RGB值

|英文名称|RGB整数值|RGB小数值|中文名称|
|:-:|:-:|:-:|:-:|
|white|255,255,255|1,1,1|白色|
|yellow|255,255,0|1,1,0|黄色|
|magenta|255,0,255|1,0,1|洋红|
|cyan|0,255,255|0,1,1|青色|
|blue|0,0,255|0,0,1|蓝色|
|black|0,0,0|0,0,0|黑色|
|purple|160,32,240|0.63,0.13,0.94|紫色|