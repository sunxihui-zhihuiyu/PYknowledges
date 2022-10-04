# **Lesson-11**

## 班级信息管理系统

在学习了面向对象程序设计方法以及数据库管理系统之后，我们生活中很多结构化的数据就可以使用数据库进行存储管理。

例如班级信息管理系统中，我们就可以创建一个班级信息管理系统对象，使用面向对象的程序设计方法完成系统的设计。

在班级管理系统中，有3个属性和7个方法（函数）。

3个属性为数据库的连接、游标、数据表。

7个方法为查看班级信息、查询单个学生信息、添加学生信息、修改学生信息、删除学员信息、关闭系统和查看学生是否存在数据库中。

<img src='_media/3-11-1.png' alt='班级信息管理系统' style='zoom:40%;'/>

<img src='_media/3-11-2.png' alt='班级信息管理系统' style='zoom:40%;'/>

```python
class ClassManageSystem:
    def __init__(self):
        # 连接数据库 student_info.db 如果不存在就创建
        self.conn = sqlite3.connect('class_info.db')
        # 定义操作数据的指针
        self.cur = self.conn.cursor()
        # 判断数据表是否存在，如果不存在就创建
        sql_1 = '''create table if not exists students
        (学号 integer, 
        姓名 text, 
        年龄 real)'''
        self.cur.execute(sql_1)

    def read_all_student(self):
        '''查看全部学员信息'''
        sql_2 = '''select * from students'''
        self.cur.execute(sql_2)
        student_list = self.cur.fetchall()
        if not student_list:
            print('目前系统中没有任何信息！')
            print('\n')
            return
        print('学号\t姓名\t年龄')
        for student in student_list:
            for i in student:
                print(i,end='\t')
            
            print('')
        print('\t')

        return student_list

    def read_student(self):
        '''查看指定学生信息'''
        number = input('请输入要查询学生的学号：')
        sql_3 = '''select * from students where 学号=?'''
        self.cur.execute(sql_3,(number,))
        result = self.cur.fetchone()
        if not result:
            print('所查询学生不存在！')
            print('\n')
            return
        print('查询结果如下：')
        print('学号\t姓名\t年龄')
        
        for i in result:
            print(i,end='\t')
            
        print('')
        
    def add_student(self):
        '''增加学生信息'''
        number = input('请输入学生的学号：')
        while True:
            if self.is_in_database(number):
                print('该学号已存在！')
                number = input('请重新输入学生的学号：')
            else:
                break
        name = input('请输入姓名：')
        age = input('请输入年龄：')
        sql_4 = '''insert into students values(?,?,?)'''
        self.cur.execute(sql_4,(number,name,age))
        self.conn.commit()
        print('添加学生成功！')
        print('\n')

    def update_student(self):
        '''更新学生信息'''
        number = input('请输入学生的学号：')
        
        if not self.is_in_database(number):
            print('该学生的信息不存在！')
            print('\n')
            return

        name = input('请输入姓名：')
        age = input('请输入年龄：')
        sql_5 = '''update students set 姓名=?,年龄=? where 学号=?'''
        self.cur.execute(sql_5,(name,age,number))
        self.conn.commit()
        print('信息修改成功！')
        print('\n')

    def delete_student(self):
        '''删除学生信息'''
        number = input('请输入学生的学号：')
        
        if not self.is_in_database(number):
            print('该学生的信息不存在！')
            print('\n')
            return
        sql_6 = '''delete from students where 学号=?'''
        self.cur.execute(sql_6,(number,))
        self.conn.commit()
        print('信息删除成功！')
        print('\n')

    def is_in_database(self, number):
        sql_6 = '''select * from students where 学号=?'''
        self.cur.execute(sql_6,(number,))
        result = self.cur.fetchall()
        return True if result else False
    
    def close_connection_database(self):
        self.cur.close()
        self.conn.close()
        print('退出系统成功！')
        
import sqlite3

classManageSystem = ClassManageSystem()

while True:
    print('-----欢迎来到学生管理系统-----')
    print('1. 查看所有学生信息')
    print('2. 查询学生信息')
    print('3. 添加学生信息')
    print('4. 修改学生信息')
    print('5. 删除学生信息')
    print('6. 退出系统')
    choiceNumber = input('请输入你的选择：')

    if choiceNumber == '1':
        classManageSystem.read_all_student()
    elif choiceNumber == '2':
        classManageSystem.read_student()
    elif choiceNumber == '3':
        classManageSystem.add_student()
    elif choiceNumber == '4':
        classManageSystem.update_student()
    elif choiceNumber == '5':
        classManageSystem.delete_student()
    elif choiceNumber == '6':
        classManageSystem.close_connection_database()
        break
```