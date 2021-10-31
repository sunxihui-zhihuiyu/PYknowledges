# **Lesson-09**

## **math模块常用函数**

### **现阶段重要的基础的math模块-（初二及以下学生学习）**

> `math.pi` # 返回常数π的值 ⭐

```python
>>> import math
>>> math.pi
3.141592653589793
```

> `math.fabs(浮点数)` # 返回一个数的绝对值 ⭐

```python
>>> import math
>>> math.fabs(-1.5)
1.5
```

> `math.factorial(整数)` # 返回一个整数的阶乘，传递非整数、负数、小数时报错 ⭐

```python
>>> import math
>>> math.factorial(3)
6
```

> `math.pow(底数，指数)` # 求幂，结果为底数的指数次方 ⭐

```python
>>> import math
>>> math.pow(2, 10)
1024.0
```

> `math.sqrt(浮点数)` # 获取浮点数的平方根 ⭐

```python
>>> import math
>>> math.sqrt(4)
2.0
```

> `math.ceil(浮点数)` # 对浮点数进行向上取整，结果大于或等于参数值的最小整数

```python
>>> import math
>>> math.ceil(3.2)
4
```

> `marh.floor(浮点数)` # 对浮点数进行向下取整，结果小于或等于参数值的最大整数

```python
>>> import math
>>> math.floor(3.6)
3
```

> `math.trunc(浮点数)` # 对浮点数截取取整，直接忽略小数部分

```python
>>> import math
>>> math.trunc(3.6)
3
```

> `math.fsum(可迭代对象)` # 对可迭代对象中的每个元素进行求和

```python
>>> import math
>>> math.fsum([1,2,3])
6.0
```

### **现阶段不重要的基础的math模块-（初三及以上学生学习）**

> `math.sin(弧度)` # 求某一弧度的正弦值

```python
>>> import math
>>> math.sin(math.pi/2)
1.0
```

> `math.cos(弧度)` # 求某一弧度的余弦值

```python
>>> import math
>>> math.cos(math.pi/2)
6.123233995736766e-17
```

> `math.radians(角度)` # 将角度转化为对应的弧度

```python
>>> import math
>>> math.radians(180.0)
3.141592653589793
```

> `math.degrees(弧度)` # 将弧度转化为对应角度

```python
>>> import math
>>> math.degrees(math.pi/2)
90.0
```

### **关于数学的python内置函数** ⭐

> `min()` # python内置函数，求参数的最小值

```python
>>> min(3,5,1,6)
1
```

> `max()` # python内置函数，求参数的最大值

```python
>>> max(3,5,1,6)
6
```

> `sum(可迭代对象)` # python内置函数，求可迭代序列的元素之和

```python
>>> sum([1,2,3])
6
```