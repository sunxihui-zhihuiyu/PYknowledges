# **Lesson-04**

## **while条件循环**

```python
while  循环条件：
    执行语句
```

- 当条件成立时候，重复做某件事情。

```python
n = 0                       # 计数器初始值为0
while n < 10:               # 当计数器值小于10的时候，重复做以下事情
    print('I am doing...')   # 做一件事
    n = n + 1                # 计数器+1

print('I am done!')
# 结果：10次‘I am doing...’，1次‘I am done!’。
```

## **无限循环**

> 任何条件都满足时的循环

```python
while True:       # 任何条件都为真
    print('I am doing...')
```

> 程序编写有问题，计数器无法满足条件

```python
n = 0                        # 计数器初始值为0
while n < 10:
    print('I am doing...')   # n一直为0，一直满足循环条件，所以产生无限循环。

print('I am done!')
```

## **for遍历循环** VS **while循环**
- for遍历循环的循环次数由序列容器中的元素个数决定，已知循环次数
- while条件循环的循环次数由循环条件和循环主体决定，未知循环次数