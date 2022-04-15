# **Lesson-04**

## **危险的海洋世界**

> 利用面向对象程序设计的思路以及pygame模块，完成《危险海洋世界》的游戏，理解面向对象的程序设计思路。
- 需求：
    1. 假设游戏场景为范围（x，y）为0<=x<=width, 0<=y<=height
    2. 游戏生成1条大鱼和10-20条小鱼，小鱼可以向左移动
    3. 大鱼可以上下左右随机移动，小鱼移动到场景边缘，则穿越屏幕到达另外一端
    4. 大鱼初始体力为100，大鱼每移动依次，体力消耗10
    当大鱼和小鱼的坐标重叠，大鱼吃掉小鱼，大鱼体力增加20，小鱼暂时不计体力
    5. 当大鱼体力值为0，或者小鱼的数量为0

- 分析：
    1. 两个类-BigFish、SmallFish
    2. 大鱼和小鱼共有属性：坐标、体力
    3. 大鱼方法：移动、吃小鱼
        小鱼方法：移动

<img src='_media/3-4-1.png' alt='海洋' style='zoom:40%;'/>
<img src='_media/3-4-2.png' alt='鲨鱼' style='zoom:40%;'/>
<img src='_media/3-4-3.png' alt='小鱼' style='zoom:40%;'/>

- 知识回顾：pygame中加载图片的方法
```python
# 1. 加载图片
image = pygame.image.load('智慧鱼.png')
# 2. 渲染图片（将图片显示在screen上）
screen.blit(image, (100,100))
```

- 《海洋世界》示例代码
```python
import pygame
import sys

# 游戏界面
import random

width = 800
height = 533

# 假设大鱼（10，20），向左移动为负数，向右移动为正数；向下移动为负数，向上移动为正数
class BigFish:
    '''
    大鱼的分析：
        属性：x,y,power=100
        方法：move(), eat()
    '''
    def __init__(self):
        self.x = random.randint(0, width)
        self.y = random.randint(0, height)
        self.power = 100

    def move(self, new_x, new_y):
        '''大鱼移动'''
        if new_x < 0:
            self.x = width
        elif new_x > width:
            self.x = 0
        else:
            self.x = new_x

        if new_y < 0:
            self.y = height
        elif new_y > height:
            self.y = 0
        else:
            self.y = new_y

    def eat(self):
        '''大鱼吃小鱼：大鱼吃掉小鱼，体力增加20'''
        self.power += 20
        
class SmallFish:
    '''
    小鱼类：
        属性：x，y
        方法：move()
    '''
    def __init__(self):
        self.x = random.randint(0, width)
        self.y = random.randint(0, height)

    def move(self):
        # 小鱼可以向左移动
        new_x = self.x - 10
        if new_x < 0:
            new_x = width
        self.x = new_x

# 1、初始化pygame
pygame.init()

# 设置窗口
screen = pygame.display.set_mode((width,height))
pygame.display.set_caption('大鱼吃小鱼')

# 加载图片
background = pygame.image.load('sea.jpg')
fish_img = pygame.image.load('fish.png')
bfish_img = pygame.image.load('bigfish.png')

# 获取乌龟、鱼图片的宽度和高度
bfish_width = bfish_img.get_width() - 5
bfish_height = bfish_img.get_height() - 5
fish_width = fish_img.get_width() - 5
fish_height = fish_img.get_height() - 5

'''
# 加载音乐
pygame.mixer.music.load('')
pygame.mixer.music.play(loops = 0, start = 0,0)
'''
# 创建一个事件对象
clock = pygame.time.Clock()

# 成绩文字显示
count = 0

font = pygame.font.SysFont('arial', 40)
score = font.render(f'score:{count}', True, (255, 255, 255))
status = font.render('Gaming', True, (255, 255, 255))

# 游戏生成1只大鱼
bfish = BigFish()
# 游戏随机生成10-20条鱼
fish_count = random.randint(10, 20)
fishes = [SmallFish() for count in range(fish_count)]
'''
上述代码为列表推导式，等价于以下代码：
fishes = []
for count in range(fish_count):
    fish = SmallFish()
    fishes.append(fish)
'''

# 2、监控用户的操作
while True:
    clock.tick(10)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            exit()
        elif event.type == pygame.KEYDOWN:
            # 通过上下左右键移动大鱼
            if event.key == pygame.K_UP:
                bfish.move(bfish.x, bfish.y - 10)
            elif event.key == pygame.K_DOWN:
                bfish.move(bfish.x, bfish.y + 10)
            elif event.key == pygame.K_LEFT:
                bfish.move(bfish.x - 10, bfish.y)
            elif event.key == pygame.K_RIGHT:
                bfish.move(bfish.x + 10, bfish.y)
        
    # 绘制图片，并更新到窗口
    screen.blit(background, (0,0))
    screen.blit(score, (width-200, 20))
    screen.blit(status, (30,20))

    # 绘制小鱼
    for fish in fishes:
        screen.blit(fish_img, (fish.x, fish.y))
        fish.move()

    # 绘制大鱼
    screen.blit(bfish_img, (bfish.x, bfish.y))

    # 游戏结束
    if bfish.power == 0:
        status = font.render('Game Over: bfish power 0.', True, (255, 255, 255))
        screen.blit(status, (30,20))
    elif len(fishes) == 0:
        status = font.render('Game Over: Fish 0.', True, (255, 255, 255))
        screen.blit(status, (30,20))
    else:
        # 游戏未结束，判断大鱼和小鱼的坐标，如果相同，则大鱼吃掉小鱼
        for fish in fishes:
            if (bfish.x < fish.x + fish_width) and (fish.x < bfish.x + bfish_width) and \
               (bfish.y < fish.y + fish_height) and (fish.y < bfish.y + bfish_height):
                fishes.remove(fish)   # 鱼被吃掉
                count += 1    # 分数加1
                score = font.render(f'score:{count}', True, (255, 255, 255))

    pygame.display.update()

```
