# 类 Class

一个类定义了对象的行为以及对象可以存储的信息类型。  
类中的信息存储在属性中，属于某个类的函数称为方法。  
子类从其父类继承属性和方法。

> 定一个小狗类
```python
class Dog():
    """Represent a dog."""

    def __init__(self, name):
        """Initialize dog object."""
        self.name = name

    def sit(self):
        """Simulate sitting."""
        print(self.name + " is sitting.")

my_dog = Dog('Peso')

print(my_dog.name + " is a great dog!")
my_dog.sit()
```

> 继承
```python
class SARDog(Dog):
    """Represent a search dog."""

    def __init__(self, name):
        """Initialize the sardog."""
        super().__init__(name)
    
    def search(self):
        """Simulate searching."""
        print(self.name + " is searching.")
        
my_dog = SARDog('Willie')

print(my_dog.name + " is a search dog.")
my_dog.sit()
my_dog.search()
```
