# **Lesson-12**

## 账单信息管理系统

> 面向对象程序设计(OOP)  `Object Oriented Programming`

<img src='_media/3-12-1.png' alt='账单信息管理系统' style='zoom:40%;'/>

```python
class WalletManageSystem:
    def __init__(self):
        # 连接数据库 wallet.db 如果不存在就创建
        self.conn = sqlite3.connect('wallet.db')
        # 定义操作数据的指针
        self.cur = self.conn.cursor()
        # 判断数据表是否存在，如果不存在就创建
        sql_1 = '''create table if not exists bill
        (日期 date,
        序号 integer,
        餐饮 real, 
        服饰 real,
        文娱 real,
        合计 real)'''
        self.cur.execute(sql_1)

    def read_all_bill(self):
        '''查看全部账单信息'''
        sql_2 = '''select * from bill'''
        self.cur.execute(sql_2)
        bill_list = self.cur.fetchall()
        if not bill_list:
            print('目前系统中没有任何信息！')
            print('\n')
            return
        print('日期\t\t序号\t\t餐饮\t\t服饰\t\t文娱\t\t合计')
        for bill in bill_list:
            for i in bill:
                print(i,end='\t\t')
            print('')
        print('\n')

    def read_bill(self):
        '''查看指定时间账单信息'''
        number = input('请输入要查询账单的日期：')
        sql_3 = '''select * from bill where 日期=?'''
        self.cur.execute(sql_3,(number,))
        result = self.cur.fetchall()
        if not result:
            print('所查询账单不存在！')
            print('\n')
            return
        print('日期\t\t序号\t\t餐饮\t\t服饰\t\t文娱\t\t合计')
        for bill in bill_list:
            for i in bill:
                print(i,end='\t\t')
            print('')
        print('\t')
        
    def add_bill(self):
        '''增加账单信息'''
        date_ = input('请输入账单的日期：')
        number = input('请输入当日序号（按顺序编写）：')
        food = input('请输入餐饮花费：')
        cloth = input('请输入服饰花费：')
        toy = input('请输入文娱花费：')
        total = float(food) + float(cloth) + float(toy)
        sql_4 = '''insert into bill values(?,?,?,?,?,?)'''
        self.cur.execute(sql_4,(date_,number,food,cloth,toy,total))
        self.conn.commit()
        print('添加账单成功！')
        print('\n')

    def update_bill(self):
        '''更新账单信息'''
        date_ = input('请输入账单日期：')
        number = input('请输入当日账单序号：')
        
        if not self.is_in_database(date_):
            print('该账单的信息不存在！')
            print('\n')
            return

        food = input('请输入餐饮花费：')
        cloth = input('请输入服饰花费：')
        toy = input('请输入文娱花费：')
        total = float(food) + float(cloth) + float(toy)
        sql_5 = '''update bill set 餐饮=?,服饰=?,文娱=?,合计=? where 日期=? and 序号=?'''
        self.cur.execute(sql_5,(food,cloth,toy,total,date_,number))
        self.conn.commit()
        print('信息修改成功！')
        print('\n')

    def delete_bill(self):
        '''删除账单信息'''
        date_ = input('请输入账单日期：')
        number = input('请输入当日账单序号：')
        
        if not self.is_in_database(date_):
            print('该账单的信息不存在！')
            print('\n')
            return
        sql_6 = '''delete from bill where 日期=? and 序号=?'''
        self.cur.execute(sql_6,(date_,number))
        self.conn.commit()
        print('信息删除成功！')
        print('\n')

    def is_in_database(self, date_):
        sql_6 = '''select * from bill where 日期=?'''
        self.cur.execute(sql_6,(date_,))
        result = self.cur.fetchall()
        return True if result else False
    
    def close_connection_database(self):
        self.cur.close()
        self.conn.close()
        print('退出系统成功！')
        
import sqlite3

walletManageSystem = WalletManageSystem()

while True:
    print('-----欢迎来到我的钱包管理系统-----')
    print('1. 查看所有账单信息')
    print('2. 查询某天账单信息')
    print('3. 添加账单信息')
    print('4. 修改账单信息')
    print('5. 删除账单信息')
    print('6. 退出系统')
    choiceNumber = input('请输入你的选择：')

    if choiceNumber == '1':
        walletManageSystem.read_all_bill()
    elif choiceNumber == '2':
        walletManageSystem.read_sbill()
    elif choiceNumber == '3':
        walletManageSystem.add_bill()
    elif choiceNumber == '4':
        walletManageSystem.update_bill()
    elif choiceNumber == '5':
        walletManageSystem.delete_bill()
    elif choiceNumber == '6':
        walletManageSystem.close_connection_database()
        break
```

> 面向过程程序设计（POP） `Procedure-Oriented Programming`

```python
import sqlite3


# 连接数据库 wallet.db 如果不存在就创建
conn = sqlite3.connect('wallet.db')
# 定义操作数据的指针
cur = conn.cursor()
# 判断数据表是否存在，如果不存在就创建
sql_1 = '''create table if not exists bill
            (日期 date,
            序号 integer,
            餐饮 real, 
            服饰 real,
            文娱 real,
            合计 real)'''
cur.execute(sql_1)

def read_all_bill():
    '''查看全部账单信息'''
    conn = sqlite3.connect('wallet.db')
    # 定义操作数据的指针
    cur = conn.cursor()
    sql_2 = '''select * from bill'''
    cur.execute(sql_2)
    bill_list = cur.fetchall()
    if not bill_list:
        print('目前系统中没有任何信息！')
        print('\n')
        return
    print('日期\t\t序号\t\t餐饮\t\t服饰\t\t文娱\t\t合计')
    for bill in bill_list:
        for i in bill:
            print(i,end='\t\t')
        print('')
    print('\n')

def read_bill():
    '''查看指定时间账单信息'''
    conn = sqlite3.connect('wallet.db')
    # 定义操作数据的指针
    cur = conn.cursor()
    number = input('请输入要查询账单的日期：')
    sql_3 = '''select * from bill where 日期=?'''
    cur.execute(sql_3,(number,))
    bill_list = cur.fetchall()
    if not bill_list:
        print('所查询账单不存在！')
        print('\n')
        return
    print('日期\t\t序号\t\t餐饮\t\t服饰\t\t文娱\t\t合计')
    for bill in bill_list:
        for i in bill:
            print(i,end='\t\t')
        print('')
    print('\t')
        
def add_bill():
    '''增加账单信息'''
    conn = sqlite3.connect('wallet.db')
    # 定义操作数据的指针
    cur = conn.cursor()
    date_ = input('请输入账单的日期：')
    number = input('请输入当日序号（按顺序编写）：')
    food = input('请输入餐饮花费：')
    cloth = input('请输入服饰花费：')
    toy = input('请输入文娱花费：')
    total = float(food) + float(cloth) + float(toy)
    sql_4 = '''insert into bill values(?,?,?,?,?,?)'''
    cur.execute(sql_4,(date_,number,food,cloth,toy,total))
    conn.commit()
    print('添加账单成功！')
    print('\n')

def update_bill():
    '''更新账单信息'''
    conn = sqlite3.connect('wallet.db')
    # 定义操作数据的指针
    cur = conn.cursor()
    date_ = input('请输入账单日期：')
    number = input('请输入当日账单序号：')
        
    if not is_in_database(date_):
        print('该账单的信息不存在！')
        print('\n')
        return

    food = input('请输入餐饮花费：')
    cloth = input('请输入服饰花费：')
    toy = input('请输入文娱花费：')
    total = float(food) + float(cloth) + float(toy)
    sql_5 = '''update bill set 餐饮=?,服饰=?,文娱=?,合计=? where 日期=? and 序号=?'''
    cur.execute(sql_5,(food,cloth,toy,total,date_,number))
    conn.commit()
    print('信息修改成功！')
    print('\n')

def delete_bill():
    '''删除账单信息'''
    conn = sqlite3.connect('wallet.db')
    # 定义操作数据的指针
    cur = conn.cursor()
    date_ = input('请输入账单日期：')
    number = input('请输入当日账单序号：')
        
    if not is_in_database(date_):
        print('该账单的信息不存在！')
        print('\n')
        return
    sql_6 = '''delete from bill where 日期=? and 序号=?'''
    cur.execute(sql_6,(date_,number))
    conn.commit()
    print('信息删除成功！')
    print('\n')

def is_in_database(date_):
    conn = sqlite3.connect('wallet.db')
    # 定义操作数据的指针
    cur = conn.cursor()
    sql_6 = '''select * from bill where 日期=?'''
    cur.execute(sql_6,(date_,))
    result = cur.fetchall()
    return True if result else False
    
def close_connection_database():
    conn = sqlite3.connect('wallet.db')
    # 定义操作数据的指针
    cur = conn.cursor()
    cur.close()
    conn.close()
    print('退出系统成功！')
        

while True:
    print('-----欢迎来到我的钱包管理系统-----')
    print('1. 查看所有账单信息')
    print('2. 查询某天账单信息')
    print('3. 添加账单信息')
    print('4. 修改账单信息')
    print('5. 删除账单信息')
    print('6. 退出系统')
    choiceNumber = input('请输入你的选择：')

    if choiceNumber == '1':
        read_all_bill()
    elif choiceNumber == '2':
        read_bill()
    elif choiceNumber == '3':
        add_bill()
    elif choiceNumber == '4':
        update_bill()
    elif choiceNumber == '5':
        delete_bill()
    elif choiceNumber == '6':
        close_connection_database()
        break
```
<img src='_media/3-12-2.png' alt='账单信息管理系统' style='zoom:40%;'/>