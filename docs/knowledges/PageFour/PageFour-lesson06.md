# **Lesson-06**

## **双端队列**

> 线性结构——双端队列

<img src='_media/4-6-1.png' alt='双端队列' style='zoom:60%;'/>

双端队列`（deque）`是一个数据集合，任何一端都允许添加或者移除元素。

- 双端队列的基本操作：
  - `Deque()` 创建一个空的双端队列。它不需要参数，且会返回一个空的双端队列。
  - `addFront(item) `从队头入队。将一个元素添加到双端队列的前段。它需要一个参数 item，且无返回值。
  - `addRear(item)` 从队尾入队。将一个元素添加到双端队列的后段。它需要一个参数 item，且无返回值。
  - `removeFront()` 从队头出队。从双端队列的前段移除一个元素。它不需要参数，且返回一个元素，并修改双端队列的内容。
  - `removeRear()` 从队尾出队。从双端队列的后段移除一个元素。它不需要参数，且返回一个元素，并修改双端队列的内容。
  - `isEmpty()` 检查双端队列是否为空。它不需要参数，且会返回一个布尔值。
  - `size()` 返回双端队列中元素的数目。它不需要参数，且会返回一个整数。

```python
class Deque:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def addFront(self, item):
        self.items.insert(0, item)

    def addRear(self, item):
        self.items.append(item)

    def removeFront(self):
        if self.isEmpty():
            return None
        return self.items.pop(0)

    def removeRear(self):
        if self.isEmpty():
            return None
        return self.items.pop()

    def size(self):
        return len(self.items)


```

使用一般的列表结构就可以实现双端队列

- 队尾进队：`list.append(item)`
- 队头进队：`list.insert(0,item)`
- 队头出队：`list.pop(0)`
- 对尾出队：`list.pop()`

## **应用：回文数问题**

设 n 是一任意自然数。若将 n 的各位数字反向排列所得自然数 n1 与 n 相等，则称 n 为一回文数。例如，若 n=1234321，则称 n 为一回文数；但若 n=1234567，则 n 不是回文数。

使用双端队列的思想求解回文数问题。

> 思想 1：将数字倒序，对比原顺序数字和倒序后的数字是否相同，如果相同，说明是回文数。

- 解法 1：使用切片方法，倒序排列原数字，进行比较；
- 解法 2：使用栈的反转特性，倒序排列原数字，进行比较。

<img src='_media/4-6-3.png' alt='双端队列' style='zoom:60%;'/>
<img src='_media/4-6-4.png' alt='双端队列' style='zoom:60%;'/>

> 思想 2：从两端开始，依次对比两端数字，如果都相同，说明是回文数。

- 解法 1：使用索引，取出两端数字，进行比较；
- 解法 2：双端队列，数字依次入队，从两端出队，出队的数字进行比较。$？$

<img src='_media/4-6-2.png' alt='双端队列' style='zoom:60%;'/>

<img src='_media/4-6-5.png' alt='双端队列' style='zoom:60%;'/>

```python
# 方法一：双端队列解题
class Deque:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def addFront(self, item):
        self.items.insert(0, item)

    def addRear(self, item):
        self.items.append(item)

    def removeFront(self):
        if self.isEmpty():
            return None
        return self.items.pop(0)

    def removeRear(self):
        if self.isEmpty():
            return None
        return self.items.pop()

    def size(self):
        return len(self.items)


def palindrome(number):
    deque = Deque()
    for ch in str(number):
        deque.addRear(ch)

    equal = True
    while queue.size() > 1 and equal == True:
        first = deque.removeFront()
        last = deque.removeRear()
        if first != last:
            equal = False
            break
    return equal


print(palindrome(12321))
print(palindrome(1221))

# 方法二：使用列表直接解题
def palindrome(number):
    deque = list(str(number))

    equal = True
    while len(deque) > 1 and equal == True:
        first = deque.pop(0)
        last = deque.pop()
        if first != last:
            equal = False
            break
    return equal


print(palindrome(12321))
print(palindrome(1221))
```

## **应用：混合四则运算求解**

假设一个简单的四则运算由 +、-、*、/ 运算符组成，如 3*7+5\*9；
设表达式的开始符和结束符为“#”；

输入一个四则运算式，输出运算结果。

- 如：
  - 输入：$#3*7+5*9#$
  - 输出：$66$

> 解题思路

1. 设立操作数栈与运算符栈；
2. `'#'` 优先级最低；
3. 若当前字符是操作数，则直接压入操作数栈；
4. 若当前字符是运算符，且运算符的优先级高于栈顶运算符则进栈；否则，从操作数栈中弹出两个操作数并弹出运算符栈的栈顶运算符，经计算后将结果压入操作数栈。

<img src='_media/4-6-6.png' alt='队列' style='zoom:60%;'/>

```python
def operate(n1,n2,symbol):
    if symbol == '+': return n1+n2
    elif symbol == '-': return n1-n2
    elif symbol == '*': return n1*n2
    elif symbol == '/':
        if n2 != 0: return n1/n2
        else: return False

def four_operations(equation):
    symbols = {'#':1,'+':2,'-':2,'*':3,'/':3}
    number_stack = []
    symbol_stack = ['#']

    n = 1
    while n < len(equation):
        # 判断连续数字
        nu = ''
        while equation[n] not in '#+-*/':
            nu += equation[n]
            n += 1
        number_stack.append(eval(nu))

        # 判断符号
        # 如果运算符优先级大于栈顶运算符，则运算符入栈
        if not symbol_stack or symbols[equation[n]] > symbols[symbol_stack[-1]]:
            symbol_stack.append(equation[n])
        # 否则，运算符优先级小于栈顶运算符，则栈顶运算符出栈，并进行优先运算
        else:
            while len(symbol_stack)>1 and symbols[equation[n]] < symbols[symbol_stack[-1]]:
                n2 = number_stack.pop()
                n1 = number_stack.pop()
                symbol = symbol_stack.pop()
                result = operate(n1,n2,symbol)
                print(f'{n1}{symbol}{n2}={result}')
                number_stack.append(result)
            symbol_stack.append(equation[n])
        n += 1
    return number_stack.pop()

print('3*7+5*9=',four_operations('#3*7+5*9#'))
print()
print('3*7+10/5=',four_operations('#3*7+10/5#'))
print()
print('40/5+10/5-2*10=',four_operations('#40/5+10/5-2*10#'))

```
