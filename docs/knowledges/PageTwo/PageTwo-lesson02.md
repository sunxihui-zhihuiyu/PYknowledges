# **Lesson-02**

## **return语句**
- 程序退出该函数，并返回到函数被调用的地方，选择性地向调用方返回一个表达式。不带参数值的return语句返回None。
- return语句作用：返回值、函数结束

```python
def perimeter(a,b):   
    c = 2 * (a + b)
    print('函数内部：长方形的周长是{}。'.format(c))    # 打印输出c的值，电脑没有保存这个值。
    return c      # 返回c的值-可以认为先保存到了电脑内存中，以便以后调用

a = perimeter(10,20)     # 调用函数，并将结果赋值为变量a
print('函数外部：长方形的周长是{}。'.format(a))    # 结果60
```

```python
def area(a,b):
    s = a * b
    print('函数内部：长方形的面积是{}。'.format(s))

b = area(10,20)        
print('函数外部：长方形的面积是{}。'.format(b))    # 结果：None
```

## **内置函数**
- python提供已经封装好的函数，称之为内置函数。如input()、print()、eval()等。

```python
>>> int(10.0)  # 将一个字符串或者数字转换为整数
10
>>> sum([1,2,3])  # 对数字序列进行求和
6
>>> max(8,10,8,9) # 返回给定参数的最大值
10
>>> abs(-10)     # 返回数值的绝对值
10
```

## **内置函数功能猜想**
```python
def my_len(l):
    n = 0
    for i in l:
        n += 1
    return n

print(my_len([1,2,3]))    # 结果：3
```