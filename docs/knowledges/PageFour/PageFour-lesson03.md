# **Lesson-03**

## **栈（Stack）**

在生活中，我们会遇到这样的一种结构。

所以的物体都是按照顺序依次叠放，但是取物品的时候遵循这样一个规律：先放置的物体最后拿到，后放置的物体先拿到。
这种结构就是栈。

一摞书就是一个书栈，一摞碟子就是一个栈。乒乓球和羽毛球等球类的摆放就是一个栈。

<img src='_media/4-3-1.png' alt='栈' style='zoom:40%;'/>

观察栈中元素的添加顺序和移除顺序，就能够理解栈的重要思想。

假设桌面一开始是空的，每次往桌上放一本书，如此堆叠，就是一个栈。取书的顺序刚好和放书的顺序相反，由此可用于反转元素的排列顺序。 

观察图中四个元素的顺序是如何改变的。

<img src='_media/4-3-2.png' alt='栈' style='zoom:40%;'/>

> 线性结构——栈

栈`（Stack）`是一个数据集合，可以理解为只能在一端进行插入或者删除操作的列表。  
- 栈的特点：后进先出`LIFO（last-in， first-out）`
- 栈的概念：栈顶、栈底
- 栈的基本操作：
    - `Stack()` 创建一个空栈。它不需要参数，且会返回一个空栈。
    - `push(item)` 入栈。将一个元素添加到栈顶。它需要一个参数 item，且无返回值。
    - `pop()` 出栈。将栈顶端的元素移除。它不需要参数，但会返回顶端的元素，并且修改栈的内容。
    - `peek()` 取栈顶。返回栈顶端的元素，但是并不移除该元素。它不需要参数，也不会修改栈的内容。
    - `isEmpty()` 检查栈是否为空。它不需要参数，且会返回一个布尔值。
    - `size()` 返回栈中元素的数目。它不需要参数，且会返回一个整数。
  
```python
class Stack:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        return self.items.pop()

    def peek(self):
        if len(self.items) > 0:
            return self.items[-1]
        else:
            return None

    def size(self):
        return len(self.items)

```

> 使用一般的列表结构就可以实现栈

将列表右端当做是栈顶。

- 进栈： `list.append()`
- 出栈：`list.pop()`
- 取栈顶：`list[-1]`


## **应用：小括号匹配问题**

括号匹配问题：给一个字符串，其中只包含小括号，求该字符串中的括号是否匹配。
例如：

`()()  `      匹配

`(())  `      匹配

`()( `        不匹配

`(() `        不匹配


<img src='_media/4-3-3.png' alt='栈' style='zoom:40%;'/>

```python
# 方法一：
# 定义栈类
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        return self.items.pop()

    def peek(self):
        if len(self.items) > 0:
            return self.items[-1]
        else:
            return None
    def isEmpty(self):
        return len(self.items) == 0

# 实例化栈解决问题
def brace_match(s):
    stack = Stack()
    balanced = True
    for ch in s:
        if ch == '(':
            stack.push(ch)
        else:
            if stack.isEmpty():
                balanced = False
            else:
                stack.pop()
    if balanced == True and stack.isEmpty():
         return True
    else:
        return False

print(brace_match('()(()'))
print(brace_match('((())(())))'))
```

```python
# 方法二：直接使用列表进行栈的操作

def brackets_match(s):
    stack = []
    balanced = True
    for ch in s:
        if ch == '(':
            stack.append(ch)
        else:
            if len(stack) == 0:
                balanced = False
            else:
                stack.pop()
    if balanced == True and len(stack) == 0:
         return True
    else:
        return False

print(brackets_match('()(()'))
print(brackets_match('((())(())))'))
```

## **应用：括号匹配问题**

括号匹配问题：给一个字符串，其中包含小括号、中括号、大括号，求该字符串中的括号是否匹配。
例如：

`()()[]{}  `      匹配

`([{()}])  `      匹配

`[]( `            不匹配

`[(]) `            不匹配

<img src='_media/4-3-4.png' alt='栈' style='zoom:40%;'/>

```python
# 方法一：
# 定义栈类
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        return self.items.pop()

    def peek(self):
        if len(self.items) > 0:
            return self.items[-1]
        else:
            return None
    def isEmpty(self):
        return len(self.items) == 0

# 实例化栈解决问题
def brace_match(s):
    stack = Stack()
    balanced = True
    match = {'}':'{', ']':'[', ')':'('}
    for ch in s:
        if ch in ['(','[','{']:
            stack.push(ch)
        else:
            if stack.isEmpty():
                balanced = False
            elif stack.peek() == match[ch]:
                stack.pop()
    if balanced == True and stack.isEmpty():
         return True
    else:
        return False

print(brace_match('(([()]){([()])}))'))
```

```python
# 方法二：直接使用列表进行栈的操作

def brackets_match(s):
    stack = []
    balanced = True
    match = {'}':'{', ']':'[', ')':'('}
    for ch in s:
        if ch in ['(','[','{']:
            stack.append(ch)
        else:
            if len(stack) == 0:
                balanced = False
             elif stack[-1] == match[ch]:
                stack.pop()
    if balanced == True and len(stack) == 0:
         return True
    else:
        return False

print(brace_match('(([()]){([()])}))'))
```