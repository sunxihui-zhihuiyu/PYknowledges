# 字典 Dictionary

字典存储彼此之间相互有关联的信息。  
字典中每一个元素就是一对键值对（`key-value`）。

> 一个简单的字典
```python
alien = {'color':'green','points':5}
```

> 获取值的方法
```python
print("The alien's color is" + alien['color'])
```

> 增加新的键值对
```python
alien['x_position'] = 0
```

> 遍历查看所有的键值对
```python
fav_numbers = {'eric': 17, 'ever': 4}
for name, number in fav_numbers.items():
    print(name + ' loves ' + str(number))
```

> 遍历查看所有的键
```python
fav_numbers = {'eric': 17, 'ever': 4}
for name, number in fav_numbers.keys():
    print(name + ' loves a number')
```

> 遍历查看所有的值
```python
fav_numbers = {'eric': 17, 'ever': 4}
for name, number in fav_numbers.values():
    print(str(name) + 'is a favorite')
```