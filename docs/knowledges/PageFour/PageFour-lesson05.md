# **Lesson-05**

## **队列**

在生活中，我们会遇到这样的一种结构。
所有的对象都按顺序完成一项工作，那么顺序靠前的人先做，顺序靠后的人后做，这就是排队。超市付款、公交车上车、打印机打印文档，都需要排队。
我们将排队的这种结构称之为队列。
队列中先排队的称之为头部（队头），后排队的称之为尾部（队尾）。

<img src='_media/4-5-1.png' alt='队列' style='zoom:60%;'/>

<img src='_media/4-5-2.png' alt='队列' style='zoom:60%;'/>

<img src='_media/4-5-3.png' alt='队列' style='zoom:60%;'/>

> 线性结构——队列

队列`（Queue）`是一个数据集合，仅允许在列表的一段进行插入，在另一端进行删除。  
进行插入的一端称为队尾`（rear）`，插入的动作成为进队或入队`（enqueue）`;  
进行删除的一端成为队头`（front）`，删除动作称为出队`（dequeue）`;

- 队列的性质：

  - 先进先出 `FIFO（First-in，First-out） `

- 队列的基本操作：
  - `Queue() ` 创建一个空队列。它不需要参数，且会返回一个空队列。
  - `enqueue(item)` 入队。将一个元素添加到队尾。它需要一个参数 item，且无返回值。
  - `dequeue()` 出队。将队列头部的元素移除。它不需要参数，但会返回头部的元素，并且修改队列的内容。
  - `isEmpty()` 检查队列是否为空。它不需要参数，且会返回一个布尔值。
  - `size()` 返回队列中元素的数目。它不需要参数，且会返回一个整数。

```python
class Queue:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        return self.items.pop(0)

    def size(self):
        return len(self.items)

```

> 线性结构——队列

使用一般的列表结构就可以实现队列

- 进队： `list.append()`
- 出队：`list.pop(0)`

## **应用：击鼓传花问题/约瑟夫斯问题**

在游戏中，一个孩子在中间不停的敲鼓，其余孩子们围一圈，在并依次尽可能地传递一个花绢。当鼓声停止之后，大家停止传递，此时手里有花绢的孩子就得退出游戏。重复上述过程，直到剩下一个孩子。

<img src='_media/4-5-4.png' alt='队列' style='zoom:60%;'/>

据说著名犹太历史学家 Josephus 有过以下的故事：在罗马人占领乔塔帕特后，39 个犹太人与 Josephus 及他的朋友躲到一个洞中，39 个犹太人决定宁愿死也不要被敌人抓到，于是决定了一个自杀方式。41 个人排成一个圆圈，由第 1 个人开始报数，每报数到第 3 人该人就必须自杀，然后再由下一个重新报数，直到所有人都自杀身亡为止。然而 Josephus 和他的朋友并不想遵从。首先从一个人开始，越过 k-2 个人（因为第一个人已经被越过），并杀掉第 k 个人。接着，再越过 k-1 个人，并杀掉第 k 个人。这个过程沿着圆圈一直进行，直到最终只剩下一个人留下，这个人就可以继续活着。问题是，给定了和，一开始要站在什么地方才能避免被处决。Josephus 要他的朋友先假装遵从，他将朋友与自己安排在第 16 个与第 31 个位置，于是逃过了这场死亡游戏。

> 以上两个案例的核心思想一样

    - 将所有外圈的孩子看作是一个队列，每次拿到鲜花的孩子位于队头。队头的孩子将鲜花传递给第二个孩子，然后队头的孩子出队，并且重新入队，这样第二个孩子就成为了队头。往复循环，直到鼓声停止。鼓声停止之后，鲜花位于队头的孩子手中，我们将队头的孩子出局（出队），鼓声开始，新一轮游戏开始。

> 先将鼓声看作是固定的时间间隔，在这里我们先假设每次的鼓声都传递固定的孩子数量。
> 输入人员列表和传递数量，返回最后一人姓名。

<img src='_media/4-5-5.png' alt='队列' style='zoom:60%;'/>

```python
# 方法一：创建队列类，然后实例化一个队列
class Queue:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        if self.isEmpty():
            return None
        else:
            return self.items.pop(0)

    def size(self):
        return len(self.items)


def passFlowers(nameList, num):
    queue = Queue()
    for name in nameList:
        queue.enqueue(name)

    while queue.size() > 1:
        for i in range(num):
            queue.enqueue(queue.dequeue())
        queue.dequeue()
    return queue.dequeue()


print(passFlowers(['red','yellow','green','blue','black'], 5))
print(passFlowers(['red','yellow','green','blue','black'], 3))

# 方法二：使用列表直接解体
def passFlowers(nameList, num):
    queue = []
    for name in nameList:
        queue.append(name)

    while len(queue) > 1:
        for i in range(num):
            queue.append(queue.pop(0))
        queue.pop(0)
    return queue.pop(0)


print(passFlowers(['red','yellow','green','blue','black'], 5))
print(passFlowers(['red','yellow','green','blue','black'], 3))
```

> 修改鼓声的时间间隔，也就是修改每次的鼓声传递的孩子数量，在这里我们将这个数量设置为随机。
> 输入人员列表，返回最后一人姓名。

```python
import random
def passFlowers(nameList):
    queue = []
    for name in nameList:
        queue.append(name)

    while len(queue) > 1:
        for i in range(random.randint(1,10)):
            queue.append(queue.pop(0))
        queue.pop(0)
    return queue.pop(0)


print(passFlowers(['red','yellow','green','blue','black']))
print(passFlowers(['red','yellow','green','blue','black']))

```

## **应用：士兵报数问题**

某部队进行新兵队列训练，将新兵从一开始按顺序依次编号，并排成一行横队，训练的规则如下：从头开始一至二报数，凡报到二的出列，剩下的向小序号方向靠拢，再从头开始进行一至三报数，凡报到三的出列，剩下的向小序号方向靠拢，继续从头开始进行一至二报数。。。，以后从头开始轮流进行一至二报数、一至三报数直到剩下的人数不超过三人为止。
输入士兵人数，输出剩下的三人编号。

- 如：
  - 输入：40
  - 输出：1 17 19

<img src='_media/4-5-6.png' alt='队列' style='zoom:60%;'/>

```python
class Queue:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        return self.items.pop(0)

    def size(self):
        return len(self.items)



def soldierTraining(number):
    queue = Queue()
    numberList = list(range(1,number+1))
    for number in numberList:
        queue.enqueue(number)

    while queue.size() >3:
        # 1-2报数
        n = queue.size()
        for i in range(n//2):
            queue.enqueue(queue.dequeue())
            queue.dequeue()
        if n % 2 == 1:
            queue.enqueue(queue.dequeue())

        print('1-2报数',queue.items)

        # 1-2-3报数
        n = queue.size()
        for i in range(n//3):
            queue.enqueue(queue.dequeue())
            queue.enqueue(queue.dequeue())
            queue.dequeue()
        if n % 3 == 1:
            queue.enqueue(queue.dequeue())
        elif n % 3 == 2:
            queue.enqueue(queue.dequeue())
            queue.enqueue(queue.dequeue())

        print('1-2-3报数',queue.items)

    result = ''
    for i in range(queue.size()):
        result = result + ' ' + str(queue.dequeue())
    return result

print(soldierTraining(20))
```
