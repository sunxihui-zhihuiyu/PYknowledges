# **Lesson-02**

## **数组（array）和列表（list）**

> 数组（array）

存储一个固定大小的相同类型元素的顺序集合。数组是用来存储一系列数据，但它往往被认为是一系列相同类型的变量。  
数组的声明并不是声明一个个单独的变量，比如 number0、number1、...、number99，而是声明一个数组变量，比如 numbers，然后使用 numbers[0]、numbers[1]、...、numbers[99] 来代表一个个单独的变量。  
所有的数组都是由连续的内存位置组成。最低的地址对应第一个元素，最高的地址对应最后一个元素。

<img src='_media/4-2-0.png' alt='数组' style='zoom:40%;'/>

> 数组（array）和列表（list）的不同

- 数组
  - C、C++、Java
  - 存储的数据必须是相同数据类型
- 列表
  - Python
  - 存储的数据可以是任意数据类型

## Python 变量的本质

在高级语言中，变量是对内存及其地址的抽象。  
对于 python 而言，python 的一切变量都是对象，变量的存储，采用了引用语义的方式，存储的只是一个变量的值所在的内存地址，而不是这个变量的只本身。

> 引用语义

引用语义：在 python 中，变量保存的是对象(值)的引用，我们称为引用语义。采用这种方式，变量所需的存储空间大小一致，因为变量只是保存了一个引用。也被称为对象语义和指针语义。

> 值语义

值语义：有些语言采用的不是这种方式，它们把变量的值直接保存在变量的存储区里，这种方式被我们称为值语义，例如 C 语言，采用这种存储方式，每一个变量在内存中所占的空间就要根据变量实际的大小而定，无法固定下来。

由于 python 中的变量都是采用的引用语义，数据结构可以包含基础数据类型，导致了在 python 中每个变量中都存储了这个变量的地址，而不是值本身。

<img src='_media/4-2-1.png' alt='变量' style='zoom:40%;'/>

在案例中，根据直观的印象（值语义），是先将 1 存储在变量 a 中，然后将 2 存储在 a 中，替换 1。所以最后 a 的值就是 2.
但是在 python 中，采用的是引用的方式，a=1 的处理方式实质上是将 a 指向 1，然后如果 a=2，则将 a 指向 2。所以这也造成了在 python 中一个变量可存储不同的数据类型。

> Python 变量的语义引用

- b = a

<img src='_media/4-2-2.png' alt='变量' style='zoom:40%;'/>

- a += 1

<img src='_media/4-2-3.png' alt='变量' style='zoom:40%;'/>

- li.append(10)

<img src='_media/4-2-4.png' alt='变量' style='zoom:40%;'/>

- 列表存储

<img src='_media/4-2-5.png' alt='变量' style='zoom:40%;'/>

## 线性表

> 线性表的顺序存储形式

数组中的数据元素本身连续存储，每个元素所占的存储单元大小固定并且相同，所以我们可以通过下标（逻辑地址）依次找到每一个元素。  
而 python 中列表是元素外置的顺序表，列表中实际存储的是对应元素的内存地址。所以能够保证每个元素的大小是相同的，并且可以通过元素地址找到对应的元素。

<img src='_media/4-2-6.png' alt='顺序存储' style='zoom:40%;'/>

在顺序表的存储过程中，如果遇到这样的情况该如何处理？

<img src='_media/4-2-7.png' alt='顺序存储' style='zoom:40%;'/>

在新建顺序表之初，计算机需要定义这个顺序表的最大存储空间、顺序表的类型等信息，Python 中默认 list 的初始内存空间是 80 字节。
如上图所示，假如我们想要拓展这个列表，但是后面的内存已经被占用了，这时候 10 就无法插入列表中。这时候，计算机会重新分配一个更大的内存空间（一般是原来内存的 2 倍），并将原来的列表重新存储在新的内存中。

> 顺序表的链式存储

<img src='_media/4-2-8.png' alt='链式存储' style='zoom:40%;'/>

我们还可以这样存储数据，为线性表中的每个元素单独进行存储，每次存储单个元素的时候，还要存储下一个元素的地址。这样我们就能够依次找到每个元素所在位置了。  
这就是链表。

> 线性结构——链表 (了解)

链表是由一系列节点组成的元素集合。  
每个节点包含两个部分，数据域 item 和指向下一个节点的指针 next。通过节点之间的相互连接，最终串联成一个链表。

```python
class Node:
    def __init__(self, item):
        self.item = item
        self.next = None
```

<img src='_media/4-2-9.png' alt='链表' style='zoom:40%;'/>

## 列表的深入操作

> 试题 1：

```python
a = [1, 2]
b = [1, 2]
a += [3]
print(a)
print(b)
```

> 试题 2：

```python
a = [1, 2]
b = a
a += [3]
print(a)
print(b)
```

- 猜测两个程序的运行结果
- 实际运行两个程序，得到结果
- 通过内存管理，分析运行结果

> 复制列表

```python
a = [1,2,3]

# 切片
b = a[:]

# copy()方法
c = a.copy()
```

> 生成整数列表的方法

```python
# 方法一：
alist = [0,1,2,3,4,5,6,7,8,9]

# 方法二：
alist = list(range(10))

# 方法三：
alist = []
for i in range(10):
    alist.append(i)

# 方法四：（列表推导式、列表解析式）⭐
alist = [i for i in range(10)]
```

> 获取列表的索引和对应的值

```python
# 方法一：
import random
alist = [random.randint(1,100) for i in range(10)]
for i in range(len(alist)):
    print(i, alist[i])

# 方法二：
import random
alist = [random.randint(1,100) for i in range(10)]
for k,v in enumerate(alist):
    print(k, v)
```

## 参考网站

使用数据可视化网站 visualgo 实际操作链表的增删改查等操作。

https://visualgo.net/en/list

<img src='_media/4-2-10.png' alt='可视化网站' size='40%;'/>
