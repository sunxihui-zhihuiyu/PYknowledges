# **Lesson-07**

## **time模块常用函数**

> `time.time()`	 # 返回当前时间的时间戳（1970年1月1日0时0分0秒开始经过的浮点秒数）

```python
>>> import time
>>> time.time()
1634958454.613802
```

> `time.localtime()`	# 格式化时间戳的本地时间（东8区），返回当前时间的九元素时间

```python
>>> import time
>>> time.localtime()
time.struct_time(tm_year=2021, tm_mon=10, tm_mday=23, tm_hour=11, tm_min=8, tm_sec=7, tm_wday=5, tm_yday=296, tm_isdst=0)
```

> `time.strftime()`	# 返回特定格式时间，人类容易读懂的(配合符号使用可显示所需要的时间格式）
例：2021-01-23 12:16:16

```python
>>> import time
>>> time.strftime('%Y-%m-%d %H:%M:%S')
'2021-10-23 11:10:13'
>>> time.strftime('%Y年%m月%d日')
'2021年10月23日'
```

> `time.sleep()`	# 让程序挂起指定时间

```python
import time

print('倒计时程序')

for i in range(5,0,-1):
    print(i)
    time.sleep(1)    # 每间隔1s，打印一个数字
```

## **常用time.strftime()函数中时间字符**

|字符|含义|
|:-:|:-:|
|%Y|四位的年份|
|%y|两位的年份|
|%m|月份|
|%d|日期|
|%H|24小时制|
|%M|分钟|
|%S|秒钟|
|%A|星期全称|

## **数码管时间程序思路**
<img src='_media/2-7-1.png' alt='sector' style='zoom:40%;'/>