# **Lesson-01**

## **Python创始人**

![吉多·范罗苏姆（Guido van Rossum）](_media/Guido.jpg)

## **变量**

```python
name = 'Python'   # 将数据'Python'赋值给name，即将数据存储在变量中
```

- 基本格式：变量名 = 数据

- 要求：
   - 变量名由字母、下划线、数字组成；
   - 变量名不能以数字开头；
   - 变量名不能为关键字；
   - 变量名区分大小写；
   - 变量名要有意义。

## **输入及输出**
> 输入：input( )

- 输入的数据需要使用变量接收

```python
age = input('请输入你的年龄：')
```

- 输入的所有数字都为字符串，如'7'，如果需要后期进行计算，则需要将字符串转换为浮点数或者整数。

```python
age = float(input('请输入你的年龄：'))
age = int(input('请输入你的年龄：'))
```

> 输出：print( )

```python
print(name, age)
```