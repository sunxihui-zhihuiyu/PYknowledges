# **Lesson-02**

## **继承和多态**

> 封装和继承
- Python相对比与其他语言，有三个主要的特点：封装、继承和多态。
- 在汽车中，如果满足四个轮子、含有发动机提供动力，我们将这些车辆称之为汽车。我们将总结特征的过程，就是可以看作是封装。
- 我们将汽车的所有特性可以封装起来，创建一个类，然后可以根据动力燃料来源，分为燃油车和电动汽车，这些分类既含有汽车的所有特征，又有自己独特的性质，这个过程称之为继承和多态。
- 燃油汽车属拥有汽车的所有属性，这个过程称之为继承；同时汽车又有燃油汽车和电动汽车等多个汽车分类，这称之为多态。

<img src='_media/3-2-1.png' alt='继承和多态' style='zoom:40%;'/>

- 在python中，我们可以定义一个父类，然后定义一个子类，如果子类继承了父类的特征，则在子类后面加上父类名。
- 如果一个子类继承了一个父类，则称之为单继承，如果继承了多个父类，则称之为多继承。多继承时，用逗号隔开多个继承的类。

```python
class ParentClass:
    # 定义父类
    pass

class SubClass1(ParentClass):
    # 定义子类，子类继承父类
    pass
```

> 多态和重构
- 为了体现燃油汽车和电动汽车类的多态，可以在每个子类下定义每种汽车各自不同的方法，比如燃油汽车需要加油，电动汽车需要充电。
在实例化对象之后，分别给燃油汽车对象加油然后跑起来，给电动汽车对象充电然后跑起来。这就体现了类的多态性。
- 在燃油汽车和电动汽车继承汽车类的时候，继承了品牌、型号和生产时间三种属性，但是燃油汽车还需要一个加油数量的属性，电动汽车有充电时长的属性。这些属性是在汽车父类的基础上进行继承，并增加的属性。
在编写子类属性的时候，首先需要进行父类属性的初始化，然后再增加子类的特有属性。
对父类属性的重新构造的顺序为先继承父类属性， 然后对属性进行构造。其写法有两种。
大家可以尝试子类汽车对父类汽车的run(）方法进行重构。

<img src='_media/3-2-2.png' alt='重构' style='zoom:40%;'/>

```python
class Car:
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def run(self):
        print('The {} {} car is running.'.format(self.brand, self.model))

class GasCar(Car):
    def __init__(self, brand, model, year, capacity):
        Car.__init__(self, brand, model, year)    # 对汽车父类进行继承
        # 或者  Super(GasCar,self).__init__(brand, model, year)
        self.capacity = capacity    # 增加属性
    def refuel(self):
        print('The {} {} car has been filled up with {} liters \
 of  gas.'.format(self.brand, self.model, self.capacity))
        
class ElectroCar(Car):
    def __init__(self, brand, model, year, duration):  
        Car.__init__(self, brand, model, year)  # 对汽车父类进行继承
        # 或者  Super(ElectroCar,self).__init__(brand, model, year)
        self.duration = duration  # 增加属性

    def charge(self):
        print('The {} {} car has been charged for {} hours..'.format(self.brand, self.model, self.duration))

my_car = Car('audi', 'A6', 2021)
my_gascar = GasCar('Buick', 'regal', 2021, 5)
my_electrocar = ElectroCar('BYD', 'qin', 2021, 0.5)
my_car.run()
my_gascar.refuel()
my_gascar.run()
my_electrocar.charge()
my_electrocar.run()
```

## **水果与苹果**

<img src='_media/3-2-3.png' alt='面向对象和面向过程' style='zoom:40%;'/>

- 定义水果父类，并定义苹果、香蕉、橘子等子类。
    - 需求：
    1. 所有水果都具有颜色、形状和口味等性质；
    2. 所有水果都可以被吃掉；
    3. 苹果这类水果还具有价格属性；
    4. 我需要购买一定数量的水果，并根据价格计算最终价格；
    5. 买了苹果之后，才能吃苹果。

```python
class Fruit:
    '''定义水果类'''
    def __init__(self, color, shape, taste):
        self.color = color
        self.shape = shape
        self.taste = taste

    def eat(self):
        print('It\'s {}.'.format(self.taste))

class Apple(Fruit):
    '''定义苹果类'''
    def __init__(self, color, shape, taste, price):
        Fruit.__init__(self, color, shape, taste)
        self.price = price
        
    def buy(self,number):
        sum_price = self.price * number
        print('I bought {} apples, which cost me {} yuan.'.format(number, sum_price))
    def eat(self):
        print('The apple is {}.'.format(self.taste))

apple1 = Apple('red','round','sweet',5.0)
apple1.buy(10)
apple1.eat()
```