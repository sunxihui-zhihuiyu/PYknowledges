# **Lesson-03**

## **for遍历循环**

```python
for  临时变量  in  序列容器：
    执行语句
```

- 将序列容器中的数据元素一个一个拿出来赋值给临时变量

## **range()**
- 返回整数序列

```python
for i in range(3):
    print(i)
# 结果：0 1 2
# 默认从0开始，以1递增，到3结束，但是不包含3
```

```python
for i in range(2,5):
    print(i)
# 结果：2 3 4
# 从2开始，以1递增，到5结束，但是不包含5
```

```python
for i in range(2,5,2):
    print(i)
# 结果：2 4
# 从2开始，以2递增，到5结束，但是不包含5
```

```python
for i in range(5,0,-1):
    print(i)
# 结果：5 4 3 2 1
# 从5开始，以-1递增（以1递减），到0结束，但是不包含0
```

## **print()**

- print(*objects, sep=' ', end='\n')

```python
print('Hello', end='-')
print('World')
# 结果：Hello-World
```
