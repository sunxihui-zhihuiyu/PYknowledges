# **Lesson-06**

## **计算机发展**

> 计算机概念

- 是现代一种用于高速计算的电子计算机器，可以进行数值计算，又可以进行逻辑计算，还具有存储记忆功能。是能够按照程序运行，自动、高速处理海量数据的现代化智能电子设备。

> 计算机发展

- 世界上第一台现代计算机：阿塔纳索夫-贝瑞计算机（Atanasoff–Berry Computer，通常简称ABC计算机）是世界上第一台电子计算机。
- 第一代计算机：电子管计算机（1946-1959），采用机器语言或者汇编语言进行编程。
- 第二代计算机：晶体管计算机（1959-1964），采用高级语言进行编程。
- 第三代计算机：中小集成电路计算机（1964-1972），采用高级语言进行编程。
- 第四代计算机：大规模、超大规模集成电路计算机（1972-至今），采用高级语言进行编程。
- 第五代计算机，亦称“智能计算机”，指的是将信息采集、存储、处理、通信同人工智能结合在一起的智能计算机系统。主要面向知识处理，具有形式化推理、联想和理解的能力，能够帮助人们进行判断、决策、开拓未知领域和获取新的知识。

## **计算机语言**

- 人和人之间的对话，使用的是自然语言；人和计算机之间的对话，使用的是计算机语言。
- 计算机语言从低级到高级分别是机器语言、汇编语言和高级语言。
- 机器语言是计算机最原始语言，由0和1的代码构成；汇编语言是一种低级语言，用人类容易记忆的语言和符号来表示一组0和1的代码，例如AND代表加法；高级语言是在低级语言的基础上，采用接近于人类自然语言的单词和符号来表示一组低级语言程序，使编程变得更加简单，易学，且写出的程序可读性强。
- Python属于高级语言中的高级语言，它的语法可读性，逐渐接近于自然语言。
- 在计算机是实际运行期间，输入的高级语言和汇编语言先经过编译器编程成计算机能够识别的机器语言，程序才能够运行。

## **程序运行原理**

> 编译和解释

- 针对于不同的编程语言，由高级语言转变为机器语言，有不同的方法。一种是将高级语言全部写完之后，把这个源代码经过编译器，全部转换成可执行的机器语言，这种方法属于编译；另一种是，每写一条语句，就把这条语句解释为机器语言，并且执行，这种方法属于解释。所以完成Python代码解释的工具，称之为解释器。

- <img src='_media/1-6-1.png' alt='programe' style='zoom:40%;'/>

> 程序的概念

- 程序是实现预期目的而进行操作的一系列语句和指令。
- 程序就是用来处理数据的。

> 程序算法

- 程序是解决问题所写的代码，算法是解决问题的方法。程序说明我要做什么，算法说明怎么做。
- 自然语言和流程图是算法的表示方法。

> 程序运行涉及到的硬件

- CPU是中央处理器，负责主要的数据处理和计算工作；
- 内存是临时储存数据中心，读取数据特别快，但是空间特别小；
- 硬盘是永久储存数据中心，读取数据特别慢，但是空间大，可以储存的数据特别多。
- <img src='_media/1-6-2.png' alt='programe' style='zoom:40%;'/>
- 在程序运行之前，程序是保存在硬盘中的。当一个成需要运行的时候，程序会被加载到内存中，然后CPU来处理内存中的程序。
就像，做好的米饭。我们吃饭的时候，需要用碗盛出一部分，然后吃掉碗里的。这个过程，盛饭的工具由电饭锅变成了碗。程序运行，也是一样的道理。
- <img src='_media/1-6-3.png' alt='programe' style='zoom:40%;'/>

> 内存与变量

- 当数据被加载到内存中之后，内存会分配给这个数据一个位置，并给它一个位置的ID号。当然，这个ID号，不容易记忆，我们可以给每个位置贴上一个标签，这个标签就是变量名。这就是变量的由来。这个数据，就是储存在变量中的值。

- <img src='_media/1-6-4.png' alt='programe' style='zoom:40%;'/>

## **Python数据类型---列表**

> 列表（list）

- 能够用来储存一定顺序的数据内容的容器，称之为列表（list）。使用方括号[ ]表示，数据之间使用逗号间隔。

```python
student = ['小张', '小赵', '小崔', '小王', '小李']    # 创建存储字符串类型的列表
f_num = [1.5, 1.6, 1.7, 1.23, 0.5]    # 创建存储浮点型的列表
int_num = [2, 5, 14, 56, 98]    # 创建存储整数类型的列表
data = [2, ‘小王’, 2.5, True]    # 创建存储不同数据类型的列表
score = ['小张', [89,90,97], '小赵’, [90,98,95]]    # 创建存储嵌套列表
```

> 下标（索引）

- 列表中就像有个一个有顺序的箱子，箱子有编号，从左往右编号0，1，2…，或者从右往左编号-1，-2，-3…。我们可以往这些箱子里放入各种不同类型的数据进行储存。
- 箱子里的数据就是元素，而箱子的编号就是**下标**，我们可以通过下标找到相应箱子里的元素。

- <img src='_media/1-6-5.png' alt='programe' style='zoom:40%;'/>

```python
>>> student = ['小张','小赵','小崔','小王','小李']    
>>> student[0]    # 列表第0个元素
'小张'
>>> student[2]    # 列表第2个元素
'小崔'

num = [1.5, 1.6, 1.7, 23, 5]  
>>> f_num[-1]   # 列表倒数第1个元素
5
>>> f_num[3]    # 列表第3个元素
23
>>> len(num)    # 列表长度（共有多少个元素）
5
```

> for循环遍历列表

```python
students = ['小张','小赵','小崔','小王','小李']
for s in students:
    print(s)
```
