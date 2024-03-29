# **Lesson-03**

## **面向对象程序设计（Object Oriented Programming）**

1. 导入各种外部库
2. 设计各种全局变量
3. 决定你要的类
4. 给每个类提供完整的一组操作
5. 明确地使用继承来表现不同类之间的共同点
6. 根据需要，决定是否写一个main函数作为程序入口

## **面向过程程序设计（Procedure-Oriented Programming）**

1. 导入各种外部库
2. 设计各种全局变量
3. 写一个函数完成某个功能
4. 写一个函数完成某个功能
5. 写一个函数完成某个功能
6. 写一个函数完成某个功能
7. ......
8. 写一个main函数作为程序入口

## **成长的圆**

> 利用面向对象程序设计的思路以及pygame模块，完成《大圆吃小圆》的游戏，理解面向对象的程序设计思路。
- 需求：
    1. 小圆随机出现在区域内，并自由移动，遇到边缘时候进行反弹；
    2. 大圆受到WSAD键控制进行上下左右移动；
    3. 当大圆碰到小圆的时候，小圆被吃掉，大圆变大（半径变化量为小圆的半径），1s后小圆随机出现在其他位置继续移动。
- 分析：
    1. 两个类-BigCircle、SmallCircle
    2. 大圆和小圆共有属性：半径、坐标；小圆还有x轴速度和y轴速度的属性
    3. 大圆方法：移动、吃小圆
        小圆方法：移动、消失、出现

```python
import pygame
import random
import time

WIDTH = 400
HEIGHT = 600

class BigCircle:
    '''
    圆属性：r，x,y
    圆方法：move(), eat()
    '''
    def __init__(self):
        self.r = 20
        self.x = random.randint(0, WIDTH)
        self.y = random.randint(0, HEIGHT)
        
    def move(self, new_x, new_y):   # 大圆移动到一个新的位置
        if new_x < self.r:   # 移动到左边界，圆停留在左边界，不继续向左
            self.x = self.r
        elif new_x > WIDTH-self.r: # 移动到左边界，圆停留在右边界，不继续向右
            self.x = WIDTH-self.r
        else:
            self.x = new_x

        if new_y < self.r:  # 移动到上边界，圆停留在上边界，不继续向上
            self.y = self.r
        elif new_y > HEIGHT-self.r: # 移动到下边界，圆停留在下边界，不继续向下
            self.y = HEIGHT-self.r
        else:
            self.y = new_y

    def eat(self, change_r):    # 大圆吃小圆，半径变大
        self.r += change_r

class SmallCircle:
    def __init__(self):
        self.r = 10
        self.x = random.randint(0, WIDTH)
        self.y = random.randint(0, HEIGHT)
        self.speed_x = 10
        self.speed_y = 10
        
    def move(self): # 小圆移动
        '''小圆移动'''
        if self.x < self.r:
            self.speed_x = 10
        elif self.x > WIDTH - self.r:
            self.speed_x = -10

        if self.y < self.r:
            self.speed_y = 10
        elif self.y > HEIGHT - self.r:
            self.speed_y = -10

        self.x += self.speed_x
        self.y += self.speed_y

    def disappear(self):  # 小圆消失
        self.r = 0
        
    def appear(self):  # 小圆出现
        self.r = 10
        self.x = random.randint(0, WIDTH)
        self.y = random.randint(0, HEIGHT)
        
# 实例化大圆和小圆对象
big_c = BigCircle()
small_c = SmallCircle()

# 初始化pygame并创建屏幕
pygame.init()
# 设置屏幕尺寸
screen = pygame.display.set_mode((WIDTH, HEIGHT))
# 设置窗口标题（宽、高）
pygame.display.set_caption('大圆吃小圆')
# 设置时钟
clock = pygame.time.Clock()
# 设置屏幕填充色，并进行更新
screen.fill((150, 150, 150))
pygame.display.flip()

# 主程序
while True:
    clock.tick(10)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            exit()
        # 大圆的移动是受到按键控制
        if event.type == pygame.KEYDOWN:
            pygame.draw.circle(screen, (150,150,150), (big_c.x, big_c.y), big_c.r)
            if event.key == pygame.K_w:    # 按下w键
                big_c.move(big_c.x, big_c.y - 10)
            elif event.key == pygame.K_s:   # 按下s键
                big_c.move(big_c.x, big_c.y + 10)  
            elif event.key == pygame.K_a:   # 按下a键
                big_c.move(big_c.x - 10, big_c.y) 
            elif event.key == pygame.K_d:   # 按下d键
                big_c.move(big_c.x + 10, big_c.y)
        pygame.draw.circle(screen, (0,0,255), (big_c.x, big_c.y), big_c.r)

    # 小圆的移动是自主移动
    pygame.draw.circle(screen, (150,150,150), (small_c.x, small_c.y), small_c.r)
    small_c.move()
    pygame.draw.circle(screen, (0,255,0), (small_c.x, small_c.y), small_c.r)

    # 大圆吃小圆的判定
    d = math.sqrt((big_c.x - small_c.x)**2 + (big_c.y - small_c.y)**2)
    if d <= big_c.r + small_c.r:
        big_c.eat(small_c.r)
        pygame.draw.circle(screen, (150,150,150),(small_c.x,small_c.y), small_c.r)
        pygame.draw.circle(screen, (0,0,255),(big_c.x,big_c.y), big_c.r)
        small_c.disappear()
        time.sleep(0.1)
        small_c.appear()

    pygame.display.update()

```

> 生成多个小圆对象

<img src='_media/3-3-1.png' alt='多个小圆' style='zoom:40%;'/>

```python
import random

WIDTH = 400
HEIGHT = 600

class BigCircle:
    '''
    实例属性：r,x,y
    实例方法：move(),eat()
    '''
    def __init__(self):
        self.r = 20
        self.x = random.randint(self.r, WIDTH-self.r)
        self.y = random.randint(self.r, HEIGHT-self.r)

    def move(self, new_x, new_y):
        '''大圆移动到新的位置'''
        if new_x < self.r:
            self.x = self.r
        elif new_x > WIDTH - self.r:
            self.x = WIDTH - self.r
        else:
            self.x = new_x

        if new_y < self.r:
            self.y = self.r
        elif new_y > HEIGHT - self.r:
            self.y = HEIGHT - self.r
        else:
            self.y = new_y

    def eat(self, change_r):
        '''大圆吃小圆，半径变大'''
        self.r += change_r

class SmallCircle:
    '''
    实例属性：r,x,y,speed_x,speed_y
    实例方法：move(),eat()
    '''
    def __init__(self):
        self.r = 10
        self.x = random.randint(self.r, WIDTH-self.r)
        self.y = random.randint(self.r, HEIGHT-self.r)
        self.speed_x = 10
        self.speed_y = 10
        
    def move(self):
        '''小圆移动'''
        if self.x < self.r:
            self.speed_x = 10
        elif self.x > WIDTH - self.r:
            self.speed_x = -10

        if self.y < self.r:
            self.speed_y = 10
        elif self.y > HEIGHT - self.r:
            self.speed_y = -10

        self.x += self.speed_x
        self.y += self.speed_y

    def disappear(self):
        '''小圆消失'''
        self.r = 0

    def appear(self):
        '''小圆出现'''
        self.r = 10
        self.x = random.randint(self.r, WIDTH-self.r)
        self.y = random.randint(self.r, HEIGHT-self.r)

# 实例化对象
big_c = BigCircle()

# 实例化多个小圆对象，并将多个小圆对象存放到列表中
small_c_s = [SmallCircle() for i in range(5)]
'''
# 相当于
small_c_s = []
for i in range(5):
    small_c_s.append(SmallCircle())
'''
import pygame
import math
import time

# 初始化pygame并创建屏幕
pygame.init()

# 设置屏幕尺寸（宽、高）
screen = pygame.display.set_mode((WIDTH, HEIGHT))
# 设置窗口标题
pygame.display.set_caption('大圆吃小圆')
# 设置时钟
clock = pygame.time.Clock()
# 设置屏幕填充色，并进行更新
screen.fill((150,150,150))
# 初始化一个大圆
pygame.draw.circle(screen, (0,0,255),(big_c.x,big_c.y), big_c.r)
# 初始化一个小圆
#pygame.draw.circle(screen, (0,0,255),(small_c.x,small_c.y), small_c.r)
pygame.display.flip()

# 主程序
while True:
    clock.tick(10)
    #screen.fill((150,150,150))
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            exit()
        # 大圆的移动
        if event.type == pygame.KEYDOWN:
            pygame.draw.circle(screen, (150,150,150),(big_c.x,big_c.y), big_c.r)
            if event.key == pygame.K_w:
                big_c.move(big_c.x, big_c.y - 10)
            elif event.key == pygame.K_s:
                big_c.move(big_c.x, big_c.y + 10)
            elif event.key == pygame.K_a:
                big_c.move(big_c.x - 10, big_c.y)
            elif event.key == pygame.K_d:
                big_c.move(big_c.x + 10, big_c.y)
            pygame.draw.circle(screen, (0,0,255),(big_c.x,big_c.y), big_c.r)

    # 将列表中的小圆一一取出，进行移动，并判定和大圆的关系
    for small_c in small_c_s:
        # 小圆的移动
        pygame.draw.circle(screen, (150,150,150),(small_c.x,small_c.y), small_c.r)
        small_c.move()
        pygame.draw.circle(screen, (0,255,0),(small_c.x,small_c.y), small_c.r)
        
        # 大圆吃小圆的判定
        d = math.sqrt((big_c.x - small_c.x)**2 + (big_c.y - small_c.y)**2)
        if d <= big_c.r + small_c.r:
            big_c.eat(small_c.r)
            pygame.draw.circle(screen, (150,150,150),(small_c.x,small_c.y), small_c.r)
            pygame.draw.circle(screen, (0,0,255),(big_c.x,big_c.y), big_c.r)
            small_c.disappear()
            time.sleep(0.1)
            small_c.appear()
        
    pygame.display.update()

```

> 拓展：
- 如何增加分数等？
- 如何判断输赢？
- ...