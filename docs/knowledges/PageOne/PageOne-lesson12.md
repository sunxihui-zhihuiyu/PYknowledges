# **Lesson-12**

## **购物需求（三）**

- 一、随着深入的测试，发现使用中的缺陷，为了保证账号安全，希望在输错三次的情况下，暂时封停账号。
- 二、投入使用前，请添加多个购物账号。
- 三、在购物过程中，可以一件一件的选择不同属性的商品，然后添加至购物车。

## **程序实现关键知识点说明**

- 本案例主要复习Lesson11 课中跳出循环方法，以及循环知识综合应用。

> 建立多个账号

```python
users = [['jack', '1234', 5000],
         ['David', '2345', 8000],
         ['Robert', '3456', 8000]]
currentUser = []

import time

#是否登录
isUser = 0
#登录次数
loginCount = 1

# 三次登陆演示
while True:
    username = input('请输入您的账号：')
    password = input('请输入您的密码：')
    for user in users:
        if username == user[0] and password == user[1]:
            currentUser = user
            isUser = 1
            print('您好，{}先生/女士: 您的储值卡余额：{}元'.format(username, currentUser[2]))
            print('')
            break     # 如果账号密码正确，则跳出查找用户循环
    if isUser == 1:   
        break     # 如果登陆成功，则跳出登陆账号循环
    if loginCount < 3:
        loginCount += 1
        print('没有此账号或密码错误！！')
    else:
        print('您已输错三次，请1分钟后再试')
        time.sleep(60)

# 重复进行商品购买演示
while True:
    # 查询商品
    if isUser == 1:
        product_type = input('请输入你需要的商品类型（电子产品/服装）：')
        for product in goods_list:
            if product_type == product[2]:
                print('{}:{}元'.format(product[0],product[1]))
        print('')

    # 加入购物车
        product_name = input('请输入你需要的商品名称：')
        products = product_name.split(",")
        for product in products:
            for goods in goods_list:
                if product == goods[0]:
                    shopping_list.append(goods)
                    break    # 如果添加商品成功，则不用继续查找商品
        print('')

        tip = input('按任意键继续购买，如需结账请按quit：')
        if tip == 'quit':
            break     # 如果按退出键，则不在继续购买商品
        else:
            continue   # 如果没有按退出键，则返回循环继续购买商品
```