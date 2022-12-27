# **Lesson-04**

## **应用：十进制转二进制**

<img src='_media/4-4-1.png' alt='栈' style='zoom:30%;'/>

将十进制整数转化为二进制

<img src='_media/4-4-2.png' alt='栈' style='zoom:60%;'/>

```python
# 方法一：
# 定义栈
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

# 实例化栈，解决问题
def divideBy2(decNumber):

    stack = Stack()  # 新建一个空栈

    while decNumber > 0:
        rem = decNumber % 2
        stack.push(rem)
        decNumber = decNumber // 2

    result = ''
    while not stack.isEmpty():
        result = result + str(stack.pop())

    return result

print(divideBy2(781))
```

```python
# 方法二：直接使用列表进行栈的操作
def divideBy2(decNumber):
    stack = []
    while decNumber > 0:
        rem = decNumber % 2
        stack.append(rem)
        decNumber = decNumber // 2

    binString = ''
    for i in range(len(stack)):
        binString += str(stack.pop())

    return binString

print(divideBy2(38))
```

## **应用：十进制转其他进制**

<img src='_media/4-4-3.png' alt='栈' style='zoom:30%;'/>

将十进制整数转化为其他进制

<img src='_media/4-4-4.png' alt='栈' style='zoom:60%;'/>

```python
# 方法一：
# 定义栈
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

# 实例化栈，解决问题
def divideByAny(decNumber, base):

    digits = '0123456789ABCDEF'

    stack = Stack()  # 新建一个空栈

    while decNumber > 0:
        rem = decNumber % base
        stack.push(rem)
        decNumber = decNumber // base

    result = ''
    while not stack.isEmpty():
        result = result + digits[stack.pop()]

    return result

print(divideByAny(769,10))
```

```python
# 方法二：直接使用列表进行栈的操作
def divideByAny(decNumber, base):

    digits = '0123456789ABCDEF'

    stack = []  # 新建一个空栈

    while decNumber > 0:
        rem = decNumber % base
        stack.append(rem)
        decNumber = decNumber // base

    result = ''
    while stack:
        result = result + digits[stack.pop()]

    return result

print(divideByAny(769,10))
```