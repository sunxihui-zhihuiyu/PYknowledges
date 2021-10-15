# **Lesson-03**

## 常用函数参数类型

> 位置参数/必须参数
- 严格按照参数的顺序进行读取

```python
def my_sum(a,b,c):
    s = a + b + c
    return s

sum1 = my_sum(1,2,3)    # 分别为a、b、c按顺序传递实际参数1、2、3
print(sum1)      # 结果6
```

> 默认参数
- 默认参数及在函数的定义的时候就给了个默认值，在函数调用的时候可以不传这个默认参数。
- 默认参数位于位置参数之后。

```python
def my_sum(a,b,c=10):
    s = a + b + c
    return s

sum1 = my_sum(1,2)    # 分别为a、b按顺序传递实际参数1、2
print(sum1)      # 结果13
```

> 可变参数/不定长参数
- 可变参数是指参数的个数是可变化的，可以是 0 个，可以是 1 个，也可以是多个，可变参数在定义的时候用符号 * 表示，而且在函数被调用的时候参数会被组装成一个 tuple （类似 list 数组的一种基本数据类型）。
- 可变参数位于位置参数之后。

```python
def my_sum(*a):
    s = 0
    for i in a:
        s += i
    return s

sum1 = my_sum(1,2)    # 传递两个实际参数1、2
print(sum1)      # 结果3
sum2 = my_sum(1,2,3)    # 传递三个实际参数1、2、3
print(sum2)      # 结果6
```