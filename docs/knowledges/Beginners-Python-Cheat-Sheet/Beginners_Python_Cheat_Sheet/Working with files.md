# 文件操作 Working with file

Python程序可以对文件进行读写操作。  
文件可以以只读模式（'r'）打开，也可以以写模式（'w'）和追加模式（'a'）打开。

> 读取一个文件并存储其每一行内容

```python
filename = 'siddhartha.txt'
with open(filename) as file_object:
    lines = file_object.readlines()
    
for line in lines:
    print(line)
```

> 向一个文件中写入内容
```python
filename = 'journal.txt'
with open(filename, 'w') as file_object:
    file_object.write("I love programming.")
```

> 向一个文件中追加内容
```python
filename = 'journal.txt'
with open(filename, 'a') as file_object:
    file_object.write("\nI love making games.")
```

> 对中文文件读写操作时候，需要设置解码类型为'utf-8'
```python
filename = 'journal.txt'
with open(filename, 'a', encoding='utf-8') as file_object:
    file_object.write("\nI love making games.")
```