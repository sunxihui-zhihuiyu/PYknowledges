# **Lesson-16**

## **异常**

> 异常概念

- 程序运行过程中，出现的bug有多样性。
- 有一种bug是由于我们书写的代码不符合解释器或者编译器的语法，而产生的bug，叫做语法错误。这种错误一般会出现在初学者编写的代码中，由于对语法不熟练或者粗心造成的。
  
<img src='_media/2-16-1.png' alt='SyntaxError' style='zoom:40%;'/>

- 另外一种bug是在运行的时候，由于输入、或者逻辑问题而发生错误，并被检测到，叫做异常；大多数的异常都不会被程序处理，都以错误信息的形式展现。

<img src='_media/2-16-2.png' alt=' Exception' style='zoom:40%;'/>

- 程序运行时抛出的异常包含多种信息：最重要的三个部分就是：异常类型，异常描述和异常的位置。方便我们去改正。同学们一定要学会查看异常信息。

<img src='_media/2-16-3.png' alt=' Exception' style='zoom:40%;'/>

> 异常类型

<img src='_media/2-16-4.png' alt=' Exception' style='zoom:40%;'/>

## **异常处理**

> `try/except`：异常捕捉可以使用 try/except 语句。

- 一个 try 语句可能包含多个except子句，分别来处理不同的特定的异常。最多只有一个分支会被执行。

```python
def divisionOperation(n1,n2):
    try:
        return n1/n2
    except ZeroDivisionError:
        return '除数不能为0'
    except:
        return '请输入正确的数字'

print(divisionOperation(5,2))    # 结果：2.5
print(divisionOperation(5,0))    # 结果：除数不能为0
print(divisionOperation(5,'2'))  # 结果：请输入正确的数字
```

> `try/except/else` 语句

- else 子句将在 try 子句没有发生任何异常的时候执行。

```python
def divisionOperation(n1,n2):
    try:
        number = n1/n2
    except:
        return '请输入正确的数字'
    else:
        return number

print(divisionOperation(5,2))    # 结果：2.5
print(divisionOperation(5,0))    # 结果：请输入正确的数字
print(divisionOperation(5,'2'))  # 结果：请输入正确的数字
```