### **1-01：分数归档**⭐

**题目：** 利用条件运算符的嵌套来完成此题：学习成绩>=90分的同学用A表示，60-89分之间的用B表示，60分以下的用C表示。

**程序分析：** 用条件判断即可。

```python
points = int(input('输入分数：'))
if points >= 90:
    grade = 'A'
elif points >= 60:
    grade = 'B'
else:
    grade = 'C'
print(grade)
```
### **1-02：反向输出**⭐

**题目：** 给一个不多于5位的正整数，要求：一、求它是几位数，二、逆序打印出各位数字。

**程序分析：** 学会分解出每一位数,用字符串的方法总是比较省事。

```python
n=int(input('输入一个正整数：'))
n=str(n)
print('{}位数'.format(len(n)))
print(n[::-1])
```
### **1-03：反向输出II**⭐

**题目：** 按相反的顺序输出列表的值。

**程序分析：** 无。

```python
a = ['one', 'two', 'three']
print(a[::-1])
```
### **1-04：连接字符串II** ⭐

**题目：** 两个字符串连接程序。

**程序分析：** 无。

```python
a = 'guangtou'
b = 'feipang'
print(b+a)
```
### **1-05：1-100求和**⭐

**题目：** 统计 1 到 100 之和。

**程序分析：** 无

```python
res = 0
for i in range(1,101):
    res += i
print(res)
```
### **1-06：数字比大小**⭐

**题目：** 数字比较。

**程序分析：** 无

```python
a = int(input('a='))
b = int(input('b='))
if a < b:
    print('a<b')
elif a > b:
    print('a>b')
else:
    print('a=b')
```
### **1-07：遍历列表**⭐

**题目：** 循环输出列表

**程序分析：** 无。

```python
li = ['moyu','niupi','xuecaibichi','shengfaji','42']

# 通过列表元素下标，输出列表元素
for i in range(len(li)):
    print(l[i])

# 直接遍历列表元素
for j in li:
    print(j)
```
### **1-08：打印星星** ⭐

**题目：** 读取7个数（1—50）的整数值，每读取一个值，程序打印出该值个数的＊。

**程序分析：**无。

```python
for i in range(3):
    n = int(input('input a number: '))
    print('*' * n)
```
### **1-09：数字组合** ⭐⭐

**题目：** 有四个数字：1、2、3、4，能组成多少个互不相同且无重复数字的三位数？各是多少？

**程序分析：** 遍历全部可能，把有重复的剃掉。

```python
total = 0
for i in range(1,5):
    for j in range(1,5):
        for k in range(1,5):
            if (i!=j) and (j!=k) and (k!=i):
                print(i,j,k)
                total += 1
print(total)
```

### **1-10：复读机相加** ⭐⭐

**题目：** 求s=a+aa+aaa+aaaa+aa...a的值，其中a是一个数字。例如2+22+222+2222+22222(此时共有5个数相加)，几个数相加由键盘控制。

**程序分析：** 用字符串解决。

```python
a = input('被加数字：')
n = int(input('加几次？：'))
res = 0
for i in range(n):
    res += int(a)
    a += a[0]
print('结果是：',res)
```
### **1-11：“turtle绘图”** ⭐⭐

**题目1：** 使用turtle绘图绘制'8'字形（雪人⛄形），上圆半径为25，填充红色；下圆半径50，填充蓝色。

**程序分析：** 熟练掌握turtle绘图指令。

```python
import turtle

turtle.fillcolor('red')
turtle.begin_fill()
turtle.circle(25)
turtle.end_fill()

turtle.fillcolor('blue')
turtle.begin_fill()
turtle.circle(-50)
turtle.end_fill()
```

**题目2：** 使用turtle绘图绘制'回'字形，将内部方形边长20，红色；外部边长40，蓝色。

**程序分析：** 多种解决方案，多多思考，以下为其中一种。

```python
import turtle

turtle.penup()
turtle.goto(-10,-10)
turtle.pendown()
turtle.pencolor('red')
for i in range(4):
    turtle.forward(20)
    turtle.left(90)

turtle.penup()
turtle.goto(-20,-20)
turtle.pendown()
turtle.pencolor('blue')
for i in range(4):
    turtle.forward(40)
    turtle.left(90)
```


### **1-12：九九乘法表**⭐⭐

**题目：** 输出 9*9 乘法口诀表。

**程序分析：** 分行与列考虑，共9行9列，i控制行，j控制列。

```python
for i in range(1,10):
    for j in range(1,i+1):
        print('{}*{}={}'.formate(i,j,i*j),end='')
    print()
```

### **1-13：所有水仙花数**⭐⭐

**题目：** 打印出所有的"水仙花数"，所谓"水仙花数"是指一个三位数，其各位数字立方和等于该数本身。例如：153是一个"水仙花数"，因为153=1的三次方＋5的三次方＋3的三次方。

**程序分析：** 利用for循环控制100-999个数，每个数分解出个位，十位，百位。

```python
# 方法一：
for i in range(100,1000):
    s = str(i)
    one = int(s[-1])
    ten = int(s[-2])
    hun = int(s[-3])
    if i == one**3 + ten**3 + hun**3:
        print(i)
        
# 方法二：
for i in range(100,1000):
    hun = i // 100
    ten = (i - hun * 100) // 10
    one = i - hun * 100 - ten * 10 
    if i == one**3 + ten**3 + hun**3:
        print(i)

# 方法三：
for i in range(1,10):     # 百位数字
    for j in range(0,10):   # 十位数字
        for z in range(0,10):    # 个位数字
            n = i*100 + j*10 + z
            if i**3 + j**3 + z**3 == n:
                print(n)
```


### **1-14：计算复读次数**⭐⭐

**题目：** 计算字符串中子串出现的次数。

**程序分析：** 无。

```python

s1='xuebixuebixuebixuebixuebixuebixuebixue'
s2='xuebi'
print(s1.count(s2))

```


### **1-15：数据加密**⭐⭐

**题目：** 某个公司采用公用电话传递数据，数据是四位的整数，在传递过程中是加密的，加密规则如下：每位数字都加上5,然后用除以10的余数代替该数字，再将第一位和第三位交换，第二位和第四位交换。  
如'1352'，首先将'1'做加密（1+5）% 10 = 6，则首位变为 '6'，同理，各位数加密之后变为'6807';  
然后将一三位置数字交换、二四位置数字交换，得到最终结果'0678'

**程序分析：** 无。

```python
n = input()
n = str(n)
a = []
for i in range(4):
    a.append((int(n[i]) + 5) % 10)
a[0],a[2] = a[2],a[0]
a[1],a[3] = a[3],a[1]

s = ''
for i in a:
    s += str(i)
print (s)
```
### **1-19：三数排序**⭐⭐

**题目：** 输入3个数a,b,c，按大小顺序输出。

**程序分析：** 我们想办法把最小的数放到x上，先将x与y进行比较，如果x>y则将x与y的值进行交换，然后再用x与z进行比较，如果x>z则将x与z的值进行交换，这样能使x最小。然后比较y与z的值就可以。

```python
# 方法一：
x = int(input('x: '))
y = int(input('y: '))
z = int(input('z: '))

if x > y:
    x, y = y, x
if x > z:
    x, z = z, x
if y > z:
    y, z = z, y
    
print(x,y,z)

# 方法二：
raw = []
for i in range(3):
    x=int(input('int{}：'.format(i+1)))
    raw.append(x)
    
for i in range(len(raw)):
    for j in range(i,len(raw)):
        if raw[i] > raw[j]:
            raw[i], raw[j] = raw[j], raw[i]
print(raw)

# 方法三：
raw2=[]
for i in range(3):
    x = int(input('int{}：'.format(i+1)))
    raw2.append(x)
print(sorted(raw2))
```
### **1-16：回文数**⭐⭐

**题目：** 设n是一任意自然数。若将n的各位数字反向排列所得自然数n1与n相等，则称n为一回文数。例如，若n=1234321，则称n为一回文数；但若n=1234567，则n不是回文数。

**程序分析：** 用字符串比较方便,就算输入的不是数字都ok。

```python
# 方法一：将对称位置的数字进行比较
n = input("输入：")
a = 0
b = len(n) - 1
flag = True
while a<b:
    if n[a] != n[b]:
        print('不是回文串')
        flag = False
        break
    a,b = a+1,b-1
if flag:
    print('是回文串')

# 方法二：数字倒序排列与原数字比较
n = input('输入：')
m = n[::-1]
if n == m:
    print('是回文串')
else:
    print('不是回文串')
```


### **1-17：列表转字符串**⭐⭐

**题目：** 按逗号分隔列表。

**程序分析：** 无。

```python
L = [1,2,3,4,5]
print(','.join(str(n) for n in L))
```


### **1-18：连接字符串**⭐⭐

**题目：** 连接字符串。

**程序分析：** 无。

```python
delimiter = ','
mylist = ['Brazil', 'Russia', 'India', 'China']
print(delimiter.join(mylist))
```


### **1-19：养兔子**⭐⭐⭐

**题目：** 有一对兔子，从出生后第3个月起每个月都生一对兔子，小兔子长到第三个月后每个月又生一对兔子，假如兔子都不死，问每个月的兔子总数为多少？

**程序分析：** 考虑到三个月成熟，可以构建四个数据，其中：一月兔每个月长大成为二月兔，二月兔变三月兔，三月兔变成年兔，成年兔（包括新成熟的三月兔）生等量的一月兔。

```python
month = int(input('繁殖几个月？： '))
month_1 = 1
month_2 = 0
month_3 = 0
month_elder = 0
for i in range(month):
    month_1,month_2,month_3,month_elder = month_elder + month_3, month_1, month_2, month_elder + month_3
    print('第%d个月共'%(i+1),month_1+month_2+month_3+month_elder,'对兔子')
    print('其中1月兔：',month_1)
    print('其中2月兔：',month_2)
    print('其中3月兔：',month_3)
    print('其中成年兔：',month_elder)
```

### **1-20：分解质因数**⭐⭐⭐

**题目：** 将一个整数分解质因数。例如：输入90,打印出90=2*3*3*5。

**程序分析：** 根本不需要判断是否是质数，从2开始向数本身遍历，能整除的肯定是最小的质数。

```python
target=int(input('输入一个整数：'))
print(target, '= ', end='')

if target < 0:
    target = abs(target)
    print('-1*', end='')

flag = 0
if target <= 1:
    print(target)
    flag = 1


while True:
    if flag:
        break
    for i in range(2, int(target+1)):
        if target % i == 0:
            print("{}".format(i), end='')
            if target == i:
                flag = 1
                break
            print('*', end='')
            target /= i
            break
        
```

### **1-21：字符串构成**⭐⭐⭐

**题目：** 输入一行字符，分别统计出其中英文字母、空格、数字和其它字符的个数。

**程序分析：** 利用 while 或 for 语句,条件为输入的字符不为 '\n'。

```python
string = input("输入字符串：")
alp = 0
num = 0
spa = 0
oth = 0
for i in range(len(string)):
    if string[i].isspace():
        spa += 1
    elif string[i].isdigit():
        num += 1
    elif string[i].isalpha():
        alp += 1
    else:
        oth+=1
print('space: ',spa)
print('digit: ',num)
print('alpha: ',alp)
print('other: ',oth)
```

### **1-22：高空抛物**⭐⭐⭐

**题目：** 一球从100米高度自由落下，每次落地后反跳回原高度的一半；再落下，求它在第10次落地时，共经过多少米？第10次反弹多高？

**程序分析：** 无

```python
high = 200
total = 100
for i in range(10):
    high /= 2
    total += high
    print(high/2)
print('总长：', total)
```

### **1-23：猴子偷桃**⭐⭐⭐

**题目：** 猴子吃桃问题：猴子第一天摘下若干个桃子，当即吃了一半，还不瘾，又多吃了一个第二天早上又将剩下的桃子吃掉一半，又多吃了一个。以后每天早上都吃了前一天剩下的一半零一个。到第10天早上想再吃时，见只剩下一个桃子了。求第一天共摘了多少。

**程序分析：** 按规则反向推断：猴子有一个桃子，他偷来一个桃子，觉得不够又偷来了与手上等量的桃子，一共偷了9天。

```python
peach = 1
for i in range(9):
    peach = (peach+1) * 2
print(peach)
```

### **1-24：斐波那契数列II**⭐⭐⭐

**题目：** 有一分数序列：2/1，3/2，5/3，8/5，13/8，21/13...求出这个数列的前20项之和。

**程序分析：** 就是斐波那契数列的后一项除以前一项。

```python
a = 2.0
b = 1.0
s = 0
for n in range(1,21):
    s += a / b
    a,b = a + b,a
print (s)
```

### **1-25： 阶乘求和**⭐⭐⭐

**题目：** 求1+2!+3!+...+20!的和。

**程序分析：** 1+2!+3!+...+20!=1+2(1+3(1+4(...20(1))))

```python
res = 1
for i in range(20,1,-1):
    res = i * res + 1
print(res)
```

### **1-26：算素数**⭐⭐⭐

**题目：** 求100之内的素数。  

素数又叫质数，指的是 "大于1的整数中，只能被1和这个数本身整除的数"。  如2、3、5是素数（质数）

**程序分析：** 用else执行for循环的奖励代码（如果for是正常完结，非break）。

```python

for i in range(2,101):
    for j in range(2,i):
        if (i % j) == 0:
            break
        else:
            print(i)
```

### **1-27：排序**⭐⭐⭐

**题目：** 对10个数进行排序。

**程序分析：** 无。

```python
raw=[]
for i in range(10):
    x = int(input('int{}: '.format(i)))
    raw.append(x)
    
for i in range(len(raw)):
    for j in range(i,len(raw)):
        if raw[i] > raw[j]:
            raw[i],raw[j] = raw[j],raw[i]
print(raw)
```