# **Lesson-01**

## **面向对象**

> 对象
- 一个苹果就是一个具体的对象，一个足球就是一个具体的对象，一台机器就是一个具体的对象，一则故事也是一个具体的对象。
通俗的讲，一个对象就是一个可以操作或者描述的物体或者事情。
- 对象是谁，要解决复杂的问题，就可以找多个不同的对象，各司其职，共同实现，最终完成需求。函数、模块、数字、字符串都是对象，在python中，一切皆对象。
在编程语言中，python属于面向对象的语言，C语言数与面向过程的语言。面向对象和面向过程的就像是盖浇饭和蛋炒饭的过程。
在这个过程中，米饭和西红柿炒蛋是两个独立的对象，两个对象各司其职，共同完成自己在这个过程中的责任。

<img src='_media/3-1-1.png' alt='面向对象和面向过程' style='zoom:40%;'/>

> 对象的属性和方法
- 世界上的对象（物体）包含了两个方面：1、可以对它们做什么（动作）；2、如何描述它们（属性或者特征）。编程亦如此。
- Python中：一个对象的特征（如何描述对象）也称之为属性（attribute）；动作（能够对对象做的操作）称之为方法（method）
- 苹果的属性和方法:
    - 我们可以把洗苹果、切苹果、咬苹果作为独立的代码块，把它们调用出来组合一下，就完成了一项工作。吃苹果就是依次调用洗苹果、切苹果、咬苹果三个功能函数，所以，方法其实就是包含在对象中的函数。

        ```python
        # 苹果的方法
        apple.wash( )
        apple.cut( )
        apple.bite( )
        ```

    - 我们描述苹果颜色是红色的或者青色、重量是100克或者150克，“红色”、“100”这些信息的类型是字符串、数字等，所以苹果的这些属性是一些可变的信息，是变量。所以，属性其实就是包含在对象中的变量。

        ```python
        # 苹果的属性
        apple.color = 'red'
        apple.weight = 100
        ```

- 对象 = 属性 + 方法
- `"."`   对象名与属性/方法名之间的点，是python使用对象属性和方法的一种记录方法，称之为点记法。

## **创建对象与实例化对象**

- 如何创建一个苹果对象？
    - 在纸上画出不同的苹果，首先要认识、想象、描述“苹果”是什么样子的？它能做什么用？我们利用这个描述可以画出很多苹果，这些苹果具有共同的属性和方法。也就是创建一个类（class）。通俗来讲，就是心中有一个虚拟的苹果模板。
    - 然后，使用苹果模板，在纸上画出不同的苹果。也就是使用类来建立一个真正的对象，这个对象称之为这个类的一个实例（instance）

<img src='_media/3-1-2.png' alt='面向对象和面向过程' style='zoom:40%;'/>

- 编程中创建对象的方法？
    - 1、描述对象的属性和方法。也就是创建一个**类（class）**
    - 2、实用类来建立一个实际的对象，也就是这个类的一个**实例（instance）**

    ```python
    class Apple:   # 创建一个苹果类
        
        shape = 'round'     # 苹果类共有的属性
        def __init__(self, color, size, taste):  # 类的初始化方法（设置实例对象的初始化属性）
            self.color = color
            self.size = size
            self.taste = taste
            
        def wash(self):     # 创建苹果类的方法
            print('The {} apple is clean.'.format(self.color))
        def cut(self):
            print('The {} apple has been cut. The apple is {}'.format(self.color, self.size))
        def eat(self):
            print('The {} apple tastes {}.'.format(self.color, self.taste))

    # 实例化第一个苹果对象
    apple1 = Apple('red','big','good')
    # 洗苹果、切苹果、吃苹果
    apple1.wash()
    apple1.cut()
    apple1.eat()
    print('------------')

    # 实例化第二个苹果对象
    apple2 = Apeple('green','small','acerbity')
    # 洗苹果、切苹果、吃苹果
    apple2.wash()
    apple2.cut()
    apple2.eat()
    ```
- `self` 及 `__init__`讲解
    - 在定义`Apple`类的时候，可以为`Apple`类添加一个特殊的`__init__()`方法，当创建实例的时候，`__init__()`方法被自动调用为创建的实例增加实例属性。
    - 在实例化对象的时候，为每个实例都统一加上我们需要的属性。
    - 在`__init__()`方法初始化对象的时候，不要忘记`self`参数，它是类下面所有方法必须的参数。
    - `__init__()` 方法的第一个参数必须是 `self`。`self`代表类的实例，可以用别的名字，但建议使用约定成俗的`self`，后续参数则可以自由指定，和定义函数没有任何区别。
    - 通俗来讲，就是认识苹果的时候，心中有一个虚拟的苹果，这个苹果就是所有苹果的参照物，这个苹果就是 `self`。在画苹果的时候，所有苹果就是这个虚拟苹果在纸上的实际体现。专业来讲，`self` 代表类的实例，是通过类创建的实例 (注意，在定义类时这个实例我们还没有创建，它表示的我们使用类时创建的那个实例)

    - 在创建实例的时候，必须要提供除self以外的参数。

    - 在类的内部，我们使用 `def` 关键字来定义方法，与一般函数定义不同的是，类方法的第一个参数为`self`， `self` 代表的是类的实例（即在你还未创建类的实例），其他参数和普通函数是一样的。

- 创建一个圆类和实例化圆的对象

```python
import math
class Circle:
    pi = math.pi   # 圆的共有属性

    def __init__(self,r):
        self.r = r
        # self.pi = math.pi  还可以这样将pi的值作为一个实例的属性
    
    def area(self):  # 圆的面积方法
        return self.pi * self.r ** 2
    def perimeter(self):  # 圆的周长方法
        return 2 * self.pi * self.r

circle1 = Circle(30)  # 实例化第一个圆
circle2 = Circle(50)  # 实例化第二个圆

print(circle1.area())   # 求第一个圆的面积
print(circle1.perimeter())    # 求第一个圆的周长
print(circle2.area())  # 求第二个圆的面积 
print(circle2.perimeter())  # 求第二个圆的周长
```
