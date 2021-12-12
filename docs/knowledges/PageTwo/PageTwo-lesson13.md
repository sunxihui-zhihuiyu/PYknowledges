# **Lesson-13**

## **第三方库安装**

> Pygame库

- `win` + `R` 按键打开运行窗口
- 输入 `cmd` 指令
- 打开电脑运行窗口
- 输入第三方库安装指令：`pip install pygame`
- 由于默认的pip第三方库镜像在国外，所以经常被限制；
如果安装失败，可以使用清华镜像源进行安装
- `pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pygame`

Python Pygame 是一款专门为开发和设计 2D 电子游戏而生的软件包，它支 Windows、Linux、Mac OS 等操作系统，具有良好的跨平台性。Pygame 由  Pete Shinners 于 2000 年开发而成，是一款免费、开源的的软件包。它提供了诸多操作模块，比如图像模块（image）、声音模块（mixer）、输入/输出（鼠标、键盘、显示屏）模块等。相比于开发 3D 游戏而言，Pygame 更擅长开发 2D 游戏，比如于飞机大战、贪吃蛇、扫雷等游戏。

## **游戏动画原理**

动画、电影、游戏在屏幕上显示的实质是有多个图片连续显示的效果，一张图片就叫做一帧。
在下方动图中，小球能够从高处落下，然后触底反弹回到高处，大约需要53帧。即每张图片记录了小球运动轨迹中的不同位置，将这些图片连续起来播放，就形成了小球运动的动画效果。
在制作动画、游戏的时候，我们也同样需要不停的将每一帧的图像制作出来，然后渲染到屏幕上进行显示，这就形成了动画、游戏的显示效果。

<img src='_media/2-13-1.png' alt='fps' style='zoom:40%;'/>

## **游戏循环（Game Loop）**

在使用pygame游戏的时候，最主要的事情是游戏循环，也就是不停的刷新窗口的内容。其中主要包含三个部分：
- 1、程序输入（process input），也就是检测外界的事件，例如鼠标是否移动、是否点击鼠标、键盘按键是否按下等等；
- 2、游戏更新（update game），也就是改变角色的内容，如移动、旋转、大小、颜色，或者是两个物体相撞，我们得规划好它们相撞之后会发生什么事；
- 3、渲染（render），可以理解为画画，将我们所表达的所有内容显示在屏幕上。
最后的时钟表示，我们要控制渲染发生的频率，也就是帧的大小，1秒内播放了多少帧的画面。我们看到的正常动画画面是24帧，也就是肉眼在看超过24帧每秒的静态图片就会认为是连续动态视频。

<img src='_media/2-13-2.png' alt='loop' style='zoom:40%;'/>

## **Pygame最小游戏系统**

- Pygame最小游戏系统是指使用Pygame的游戏框架，无论做什么游戏，以下代码都必须进行编写。

```python
import pygame   # 导入pygame库

pygame.init()   # 初始化Pygame
WIDTH = 400
HEIGHT = 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))   # 设置游戏窗口以及大小
pygame.display.set_caption('My First Game')     # 设置游戏窗口标题
clock = pygame.time.Clock()    # 设置游戏时钟
screen.fill((150，150，150))   # 设置背景填充
pygame.display.flip()     # 窗口渲染

while True:    # 游戏主循环
    clock.tick(50)    # 设置刷新频率（1秒50次）
    for event in pygame.event.get():     # 获取pygame事件
        if event.type == pygame.QUIT:     # 如果点击退出按键
            exit()
    pygame.display.update()     # 刷新整个屏幕
```

<img src='_media/2-13-3.png' alt='pygame' style='zoom:40%;'/>

## **添加与修改图片**

```python
import pygame   # 导入pygame库

pygame.init()   # 初始化Pygame
WIDTH = 400
HEIGHT = 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))   # 设置游戏窗口以及大小
pygame.display.set_caption('My First Game')     # 设置游戏窗口标题
clock = pygame.time.Clock()    # 设置游戏时钟
screen.fill((150，150，150))   # 设置背景填充

# 1. 加载图片
image = pygame.image.load('智慧鱼.png')
# 2. 渲染图片（将图片显示在screen上）
screen.blit(image, (100,100))

# 3. 旋转和缩放
new_image = pygame.transform.rotozoom(image, 180, 0.5)
screen.blit(new_image, (400,400))

pygame.display.flip()     # 窗口渲染

while True:    # 游戏主循环
    clock.tick(50)    # 设置刷新频率（1秒50次）
    for event in pygame.event.get():     # 获取pygame事件
        if event.type == pygame.QUIT:     # 如果点击退出按键
            exit()
    pygame.display.update()     # 刷新整个屏幕
```

<img src='_media/2-13-4.png' alt='image' style='zoom:40%;'/>

## **添加与修改文字**

```python
import pygame   # 导入pygame库

pygame.init()   # 初始化Pygame
WIDTH = 400
HEIGHT = 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))   # 设置游戏窗口以及大小
pygame.display.set_caption('My First Game')     # 设置游戏窗口标题
clock = pygame.time.Clock()    # 设置游戏时钟
screen.fill((150，150，150))   # 设置背景填充

# 1. 加载图片
image = pygame.image.load('智慧鱼.png')
# 2. 渲染图片（将图片显示在screen上）
screen.blit(image, (100,100))

# 3. 旋转和缩放
new_image = pygame.transform.rotozoom(image, 180, 0.5)
screen.blit(new_image, (400,400))

# 1. 创建字体对象
font = pygame.font.Font('C:\Windows\Fonts\SimHei.ttf', 30)
# 2. 创建文字对象
text = font.render('智慧鱼'，True, (0, 0, 255))
# 3. 渲染到窗口上
screen.blit(text, (50, 50))
# 4. 旋转和缩放
new_text = pygame.transform.rotozoom(text, 180, 0.5)
screen.blit(new_text, (50, 100))

pygame.display.flip()     # 窗口渲染

while True:    # 游戏主循环
    clock.tick(50)    # 设置刷新频率（1秒50次）
    for event in pygame.event.get():     # 获取pygame事件
        if event.type == pygame.QUIT:     # 如果点击退出按键
            exit()
    pygame.display.update()     # 刷新整个屏幕
```

<img src='_media/2-13-5.png' alt='image' style='zoom:40%;'/>