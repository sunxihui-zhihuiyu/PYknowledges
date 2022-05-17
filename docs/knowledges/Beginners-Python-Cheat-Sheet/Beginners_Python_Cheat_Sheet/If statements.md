# If 语句  If statement

if 语句用来测试特定条件和答案的正确性。

> 条件测试
```python
等于          x == 42
不等于        x != 42
大于          x > 42
大于或等于    x >= 42
小于          x < 42
小于或等于    x <= 42
```

> 使用列表进行条件测试
```python
bikes = ['trek','redline','giant']
'trek' in bikes
'surly' not in bikes
```

> 分配布尔值
```python
game_active = True
can_edit = False
```

> 简单的if语句
```python
if age >= 18:
    print("You can votel!")
```

> if-elif-else 语句
```python
if age < 4:
    ticket_price = 0
elif age <18:
    ticket_price = 10
else:
    ticket_price = 15
```