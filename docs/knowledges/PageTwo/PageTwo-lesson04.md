# **Lesson-04**

## 函数的嵌套调用
- 一个函数的内部调用了另外一个函数

```python
def print_line(n, symbol):      # 定义一个画1条分割线的函数print_line
    print(n * symbol)           # 画n个符号，如 ********

def print_lines(m, n, symbol):   # 定义一个画多条分割线的函数print_lines
    for i in range(m):
        print_line(n, symbol)     # 调用print_line

print_lines(3, 5, '*')           
```

## 递归函数
- 如果一个函数调用的函数是它本身，那么这样的函数就叫做递归函数。

```python
def my_sum(n):
    # 求前n项整数之和，如 1 + 2 + ... + n
    if n == 1:              # 结束条件
        return 1
    if n > 1:               # 相邻两项之间的关系
        return n + my_sum(n-1)    # 前n项之和等于前n-1项之和加第n项

print(my_sum(100))
# 结果：5050
```

> 递归函数特点

- 1、递归函数必须有一个明确的结束条件（什么时候退出循环）
- 2、递归函数本质是一个方法的循环调用，注意：有可能出现死循环
- 3、相邻两次重复之间有紧密的联系，前一次要为后一次做准备(通常前一次的输入就是作为后一次的输入)
- 4、递归效率不高，递归层次过多会导致栈溢出。


## 斐波那契数列

```python
def fib(n):
    # 斐波那契数列第n项
    if n == 1:              # 结束条件1
        return 1
    if n == 2:              # 结束条件2
        return 1

    return fib(n-1) + fib(n-2)    # 第n项的值等于前两项的数值之和

print(fib(12))
# 结果：144
```