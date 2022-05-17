# 列表  List

一个列表用来存储以特定顺序排列的一系列数据元素。  
查看列表中的元素，可以通过下标查看，或者使用循环进行查看。

> 创建一个列表
```python
bikes = ['trek','redline','giant']
```

> 从一个列表中获取第一个元素
```python
first_bike = bikes[0]
```

> 从一个列表中获取最后一个元素
```python
last_bike = bikes[-1]
```

> 遍历一个列表
```python
for bike in bikes:
    print(bike)
```

> 向列表中增加一个元素
```python
bikes = []
bikes.append('trek')
bikes.append('redline')
bikes.append('giant')
```

> 创建数字列表
```python
squares = []
for x in range(1,11):
    squares.append(x**2)
```

> 列表推导式
```python
squares = [x**2 for x in range(1,11)]
```

> 分割列表（切片）
```python
finishers = ['sam','bob','ada','bea']
first_two = finishers[:2]
```

> 复制列表
```python
copy_of_bikes = bikes[:]
```