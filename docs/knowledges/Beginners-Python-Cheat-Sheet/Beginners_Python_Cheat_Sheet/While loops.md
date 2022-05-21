# while循环 While loop

当一个确定条件成立时候，while循环会一直重复执行一段代码。

> 一个简单的while循环
```python
current_value = 1
while current_value <= 5:
    print(current_value) current_value += 1
```

>让用户选择什么时候退出
```python
msg = ''
while msg != 'quit':
    msg = input("What's your message? ")
    print(msg)
```
