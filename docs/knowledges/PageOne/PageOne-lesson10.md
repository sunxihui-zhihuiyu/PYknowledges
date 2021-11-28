# **Lesson-10**

## **购物需求（二）**

希望能够购买多个商品。

##  **程序实现关键知识点说明**

本节课主要复习 Lesson08 和 Lesson09 课程中的字符串和列表方法。

> 一次增加多件商品

```python
shopping_list = []

product_name = '跑鞋 裤子'    # 一次购买多件商品，商品之间以空格隔开
products = product_name.split(' ')   # 将多件商品的字符串，以空格进行拆分，结果保存到列表中,如：['跑鞋', '裤子']
for good in products:
    shopping_list.append(good)   # 使用列表append方法，将列表中商品一个一个添加到购物车中。
```

> 多次购买商品

使用循环，进行多次购买。这里只是给出一个案例，同学们要灵活应用。

```python
buy = True
shopping_list = []

while buy:
    product_name = input('输入购买商品名称：')
    shopping_list.append(product_name)   # 使用列表append方法，将s商品添加到购物车中。
    buy = eval(input('是否继续购买（True/False）:'))

print('购买完毕，开始结账。')
```