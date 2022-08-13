类是面向对象编程的基础。类代表着你想在你的程序中表示的真实世界的事物，比如狗、猫和机器人。你可以使用类去创建狗、猫或者机器人这样的对象。
一个类定义了一整个类对象可以有的行为（方法）以及信息（属性）。
类可以相互继承，你可以编写一个类来拓展现有的类，这样更能够有效地编写各种各样的代码。

# 1. 创建一个类，并使用一个类

思考一下，我们是如何给汽车建模的？我们会给汽车关联什么样的信息？汽车有什么样的行为？什么属性？
我们将信息存储在变量中，称之为属性；
我们使用函数表示行为，属于类的函数称之为方法。

> 定义一个汽车类
```python
class Car:
    """A simple attempt to model a car."""

    def __init__(self, make, model, year):
        """Initialize car attributes"""
        self.make = make
        self.model = model
        self.year = year

        # Fuel capacity and level in gallons.
        self.fuel_capacity = 15
        self.fuel_level = 0

    def fill_tank(self):
        """Fill gas tank to capacity."""
        self.fuel_level = self.fuel_capacity
        print("Fuel tank is full") 

    def drive(self):
        """Simulate driving."""
        print("The car is moving.")   
```

> 通过类创建一个实际物体（实例化对象）
```python
my_car = Car('audi', 'a4', 2016)
```

> 获取属性值
```python
print(my_car.make)
print(my_car.model)
print(my_car.year)
```

> 调用方法
```python
my_car.fill_tank()
my_car.drive()
```

> 创建更多的对象
```python
my_car = Car('audi', 'a4', 2016)
my_old_car = Car('subaru', 'outback', 2013)
my_truck = Car('toyota', 'tacoma', 2010)
```

---

# 2. 修改属性

你可以直接修改一个对象的属性值，或者你可以写一个方法来更好的更新属性值。

> 直接修改属性值
```python
my_new_car = Car('audi', 'a4', 2016)
my_new_car.fuel_level = 5 
```

> 写一个方法更新属性值
```python
def update_fuel_level(self, new_level):
    """Update the fuel level."""
    if new_level <= self.fuel_capacity:
        self.fuel_level = new_level
    else:
        print("The tank can't hold that much!")
```

> 写一个方法增加属性值
```python
def add_fuel(self, amount):
    """Add fuel to the tank."""
    if (self.fuel_level + amount <= self.fuel_capacity):
        self.fuel_level += amount
        print("Added fuel.")
    else:
        print("The tank won't hold that much.")
```

---

# 3. 类的继承

当一个类继承于另一个类，它会自动获取所有的属性和父类的方法。子类可以接入新的属性和方法，并覆盖父类的属性和方法。

> 子类使用 `__init__()`方法继承父类 
```python
class ElectricCar(Car):
    """A simple model of an electric car."""

    def __init__(self, make, model, year):
        """Initialize an electric car."""
        super().__init__(make, model, year)

        # Attributes specific to electric cars.
        # Battery capacity in kWh.
        self.battery_size = 70
        # Charge level in %.
        self.charge_level = 0
```

> 给子类增加一个新的方法
```python
class ElectricCar(Car):
    --snip--
    def charge(self):
        """Fully charge the vehicle."""
        self.charge_level = 100
        print("The vehicle is fully charged.")
```

> 使用子类的方法和父类的方法
```python
my_ecar = ElectricCar('tesla', 'model s', 2016)
my_ecar.charge()
my_ecar.drive()
```

> 覆盖父类的方法
```python
class ElectricCar(Car):
    --snip--
    def fill_tank(self):
        """Display an error message."""
        print("This car has no fuel tank!")
```

---

# 4. 将实例对象作为属性 

一个类中可以使用对象作为它的属性。这就允许类可以处理更加复杂的情况。

> Battery 类
```python
class Battery:
    """A battery for an electric car."""

    def __init__(self, size=70):
        """Initialize battery attributes."""
        # Capacity in kWh, charge level in %.
        self.size = size
        self.charge_level = 0

    def get_range(self):
        """Return the battery's range."""
        if self.size == 70:
            return 240
        elif self.size == 85:
            return 270
```

> 使用对象作为类的属性
```python
class ElectricCar(Car):
    --snip--

    def __init__(self, make, model, year):
        """Initialize an electric car."""
        super().__init__(make, model, year)
        # Attribute specific to electric cars.
        self.battery = Battery()

    def charge(self):
        """Fully charge the vehicle."""
        self.battery.charge_level = 100
        print("The vehicle is fully charged.")
```

> 使用对象
```python
my_ecar = ElectricCar('tesla', 'model x', 2016)

my_ecar.charge()
print(my_ecar.battery.get_range())
my_ecar.drive()
```

---


# 5. 调用类

您可以将类像函数一样保存在模块中，以便调用。

> 将类存储在模块中
- 文件：car.py

```python
"""Represent gas and electric cars."""

class Car():
    """A simple attempt to model a car."""
    --snip—

class Battery():
    """A battery for an electric car."""
    --snip--

class ElectricCar(Car):
    """A simple model of an electric car."""
    --snip--
```

> 调用一个模块中的类
- 文件：my_cars.py

```python
from car import Car, ElectricCar

my_beetle = Car('volkswagen', 'beetle', 2016)
my_beetle.fill_tank()
my_beetle.drive()

my_tesla = ElectricCar('tesla', 'model s', 
2016)
my_tesla.charge()
my_tesla.drive()
```

> 调用一个模块

```python
import car

my_beetle = car.Car('volkswagen', 'beetle', 2016)
my_beetle.fill_tank()
my_beetle.drive()

my_tesla = car.ElectricCar('tesla', 'model s', 2016)
my_tesla.charge()
my_tesla.drive()
```
