# Lesson-02
## eval()函数
```python
   eval('3+2')  # 结果为 5
```
执行一个字符串表达式，并返回表达式的值
即去掉字符串两侧引号，如果是可以计算的算术式，则返回这个算术式的值
```python
   eval('python')  # 结果为 Error，因为返回为不加引号的python，是一个变量
```
## 运算符
### 算术运算符
加（+） 减（-） 乘（*） 除（/ ）
### 比较运算符
大于（>） 小于（<） 相等（==） 不相等（!=）
### 字符与ASCII码
```pyhthon
   chr('a')   # 返回字符  ASCII码  97
   ord(97)    # 返回ASCII码对应的字符 'a'
```
## 判断语句（if条件句）（重点）
### 单分支条件句
```python
   number = eval(input('请输入一个数字：'))
   if number < 5: 
       print(number)
   print('结束了！')
```
### 二分支条件句
```python
    number = eval(input('请输入一个数字：'))
    if number < 5:
        print(number)
    else: 
        print(‘这个数太大了。')
    print('结束了！')
```
