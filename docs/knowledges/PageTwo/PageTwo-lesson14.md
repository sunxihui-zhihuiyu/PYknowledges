# **Lesson-14**

## **Pygame简易图形**

> pygame中使用draw模块画图

```python
# 1. 画直线
# line(画在哪儿，线的颜色，线的起点，线的终点，线宽=1)
pygame.draw.line(screen,(0,0,255),(100,20),(100,100),3)

# 2. 画折线
# lines(画在哪里，线的颜色，是否闭合=True,多个点的位置，线宽)
points = [(20,20),(40,0),(60,20),(80,0)]
pygame.draw.lines(screen,(0,255,0),True,points,2)

# 3. 画圆
# circle(画在哪儿，线的颜色，圆心坐标，半径，线宽=0)  --线宽默认为0，表示填充
pygame.draw.circle(screen,(255,0,0),(200,300),100,2)

# 4. 画矩形
# rect(画在哪儿，线的颜色，矩形范围，线宽=0)   --矩形范围（左上角坐标，矩形宽，矩形高）
pygame.draw.rect(screen,(255,100,100),(100,200,100,200))

# 5. 画椭圆
# ellipse(画在哪儿，线的颜色，矩形范围，线宽=0) --- 矩形的内切圆
pygame.draw.ellipse(screen,(0,100,100),(300,300,100,200))

# 6. 画弧线
# arc(画在哪儿，线的颜色，矩形范围，起始弧度，终止弧度，线宽=1)  --弧度Π
pygame.draw.arc(screen,(050,0,0),(100,200,100,200), 0, math.pi)
```

<img src='_media/2-14-1.png' alt='draw' style='zoom:40%;'/>

## **pygame动画**

> 动画实现原理

- 在上一节课程中，我们知道，要想达到图形的移动效果，就是在不同帧的图画中，在不同位置画出相同的图形。
- 但是画出相同的图形之后，以前的图形并没有消失，这样就会留下移动的轨迹。
- 如果想要达到真正的图形移动效果，则还需要在移动之前，在原位置上放上一个和背景图颜色一样的图形进行遮盖，然后在移动图形并渲染。

<img src='_media/2-14-2.png' alt='cartoon' style='zoom:40%;'/>

> 变化的气泡

- 向下移动变大，向上移动变小的气泡
- `pygame.draw.circle(screen,(R,G,B),(x,y),r,2)`

<img src='_media/2-14-3.png' alt='bubble' style='zoom:40%;'/>

```python
import pygame 

pygame.init()
WIDTH = 400
HEIGHT = 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption('变化的气泡')
clock = pygame.time.Clock()
screen.fill((255，255，255))

# 初始化圆
y = 50
speed = 1
r = 0
pygame.draw.circle(screen, (0, 0, 255), (200, y), r)
pygame.display.flip()

while True:
    clock.tick(50)
    for event in pygame.event.get():
        if event.type == pygame.QUIT;
            exit()
    # 在画新的圆之前，画一个底色相同的圆，将前一帧的圆遮盖
    pygame.draw.circle(screen, (255, 255, 255), (200, y), r)   
    # 改变y的值和r的值
    y += speed
    r = y // 5
    # 判断上升还是下降，从而改变y增加的值是正值还是负值
    if y >= HEIGHT - r:
        speed = -1
    if y <= 0:
        speed = 1
    # 在后一帧的窗口上画一个新的圆
    pygame.draw.circle(screen, (0, 0, 255), (200, y), r)
    pygame.display.update()
```

> 变化的气泡-进阶

- 尝试和random模块进行结合，完成随机位置、随机大小、随机颜色的气泡
- `pygame.draw.circle(screen,(R,G,B),(x,y),r,2)`

<img src='_media/2-14-4.png' alt='bubble' style='zoom:40%;'/>