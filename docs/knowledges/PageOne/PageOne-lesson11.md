# **Lesson-11**

## **循环终止的方法**

- `break`：某一条件满足时，退出整个循环，不再执行后续重复的代码。联想：一天有6节课，第3节课有一突发状况发生，则第3、4、5、6节课都不上了。
- `continue`：某一条件满足时，后面的代码不再执行，但是循环依然继。联想：一天有6节课，第3节课有一突发状况发生，则第3节课不上，但是第4、5、6节课还要继续。
- `exit()`函数：无论exit()函数出现在程序中的何处，只要程序在执行过程中调用到exit()函数，程序立即终止运行。联想：一天有6节课，第3节课有一突发状况发生，则直接辍学。

```python

for i in range(10):
    if i == 3:
        print('跳出')
        break         # 当条件满足时候，跳出整个循环
    print(i)

# 结果： 0 1 2 跳出
```

```python
for i in range(10):
    if i == 3:
        print('跳出')
        continue      # 当条件满足时候，跳出当前循环操作，继续下一轮循环操作
    print(i)

# 结果： 0 1 2 跳出 4 5 6 7 8 9
```

```python
for i in range(10):
    if i == 3:
        print('跳出')
        exit()      # 终止整个程序
    print(i)

# 结果： 0 1 2 跳出    (kill the program!)
```

大家可以使用while循环进行案例的运行。

## **循环嵌套**

> 九九乘法表

```python
row = 1
while row <= 9:
    col = 1
    while col <= row:
        print('{}×{}={}'.format(row, col, row*col), end='\t')
        col += 1
    print()
    row += 1
```

大家可以使用for循环进行案例的运行。