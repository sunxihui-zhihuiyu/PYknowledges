# **Lesson-15**

## **Pygame事件类型**

- 游戏的本质就是人机互动。要产生相关游戏动画效果的前提就是游戏控制，也就是程序输入或者检测外界事件的发生。
- pygame中使用event模块来处理事件与事件队列。event模块中常用的事件类型（type）有三类：退出、鼠标和键盘事件。
- 其中退出（QUIT)主要用来关闭窗口，退出游戏。
- 鼠标事件包含三种事件：鼠标按键按下（MOUSEBUTTONDOWN）、鼠标按键抬起（MOUSEBUTTONUP）、鼠标移动（MOUSEMOTION）。同时，我们可以通过鼠标事件中pos属性，得出鼠标的位置信息。
- 键盘事件包含两种事件：键盘按键按下（KEYDOWN）、键盘按键抬起（KEYUP)。

<img src='_media/2-15-1.png' alt='quit' style='zoom:40%;'/>

> 退出事件

```python
while True:
    # Process input(events)
    for event in pygame.event.get():
        if event.type == pygame.QUIT;
            exit()
	     pygame.quit()
    # Update game
    # Render / Draw
    pygame.display.update()
```

<img src='_media/2-15-2.png' alt='quit' style='zoom:40%;'/>

> 鼠标事件

```python
while True:
    # Process input(events)
    for event in pygame.event.get():
        if event.type == pygame.QUIT;
            exit()
	     pygame.quit()

        if event.type == pygame.MOUSEBUTTONDOWN:    # 鼠标按下
            pygame.draw.circle(screen, (255, 0, 0), (50, 50), 50)
        if event.type == pygame.MOUSEBUTTONUP:     # 鼠标抬起
            pygame.draw.circle(screen, (0, 255, 0), (150, 50), 50)    
    
    pygame.display.update()

```

<img src='_media/2-15-3.png' alt='mouse' style='zoom:40%;'/>

- 可以通过event.pos或者pygame.mouse.get_pos()来获取鼠标光标的位置坐标，并储存在mx和my变量中。

```python
while True:
    # Process input(events)
    for event in pygame.event.get():
        if event.type == pygame.QUIT;
            exit()
	     pygame.quit()

        if event.type == pygame.MOUSEMOTION:
            mx, my = event.pos
            print('鼠标坐标({} {})'.format(mx, my))
            pygame.draw.circle(screen, (0, 0, 255), (mx, my), 5,1)    
    
    pygame.display.update()
```

<img src='_media/2-15-4.png' alt='mouse' style='zoom:40%;'/>

> 键盘事件

```python
while True:
    # Process input(events)
    for event in pygame.event.get():
        if event.type == pygame.QUIT;
            exit()
	     pygame.quit()
        if event.type == pygame.KEYDOWN:     # 键盘按下
            print('按键按下', event.key, chr(event.key))
            if chr(event.key) == 'c':     # C键按下
                pygame.draw.circle(screen, (255, 0, 0), (50, 50), 50)
        if event.type == pygame.KEYUP:     # 键盘抬起
            print('按键抬起', event.key, chr(event.key))
            if chr(event.key) == 'c':   # C键抬起
                pygame.draw.circle(screen, (0, 255, 0), (150, 50), 50)    
    pygame.display.update()
```

<img src='_media/2-15-5.png' alt='key' style='zoom:40%;'/>

- 当键盘按下的时候，键盘会发送一个扫描码给系统。扫描码是键盘反馈哪一个按键被按下的方式，不同类型的键盘扫描码不同。再由系统调用相应的函数将其转换为统一的 Unicode 编码。

- key 属性的值是一个数字，为了方便使用，Pygame 将这些数字定义为以下这些常量：

<img src='_media/2-15-6.png' alt='key' style='zoom:40%;'/>

- 我们可以使用两种方法进行监控键盘事件。直接判断event.key的ascii值或者将event.key的ascii值转换为对应的字符串。

```python
if chr(event.key) == 'c':
    ...
if event.key == pygame.K_c:
    ...
```

## **按键控制变化的圆**

- 点击屏幕，在鼠标指针的位置产生气泡；
- 按下a键，气泡往左移动，按下d键，气泡往右移动；
- 气泡向下移动变大，向上移动变小。

<img src='_media/2-15-7.png' alt='ball' style='zoom:40%;'/>

```python
import pygame 
pygame.init()
WIDTH = 400
HEIGHT = 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption('变化的圆')
clock = pygame.time.Clock()
screen.fill((255，255，255))

# 初始化圆变化的属性值
speed_x = 0
speed_y = 2
r = 0
running = False
pygame.display.flip()
while True:
    clock.tick(50)
    for event in pygame.event.get():
        if event.type == pygame.QUIT;
            exit()
        # 当按下鼠标按键，先清空屏幕，然后获取鼠标坐标，在原位置画一个蓝色的圆
        if event.type == pygame.MOUSEBUTTONDOWN:
            screen.fill((255, 255, 255))
            x, y = event.pos
            running = True
            pygame.draw.circle(screen, (0, 0, 255), (x, y), r)
        
        # 按下'a',气泡左移；按下'b',气泡右移
        if event.type == pygame.KEYDOWN:
            if chr(event.key) == 'a':
                running = True
                speed_x = -1
            if chr(event.key) == 'd':
                running = True
                speed_x = 1

    # 气泡向上变大，向下变小
    if running == True:
    pygame.draw.circle(screen, (255, 255, 255), (x, y), r)    
    x += speed_x
    y += speed_y
    r = y // 5                
    if y >= HEIGHT - r:
        speed_y = -1
    if y <= 0:
        speed_y = 1
    if x >= WIDTH - r:
        speed_x = -1
    if x <=  r:
        speed_x = 1  
    pygame.draw.circle(screen, (0, 0, 255), (x, y), r)

    pygame.display.update()
```
