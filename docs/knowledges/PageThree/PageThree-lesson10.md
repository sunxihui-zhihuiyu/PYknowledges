# **Lesson-10**

## 一、sqlite 数据库复习

sqlite本身是一个不需要系统配置的数据库，也就是不需要安装或管理。它本身非常小，也就是占用内存很小，可以在多数系统中进行运行。

在python中我们可以直接使用`import sqlite3`指令导入`sqlite3模块`，然后使用sql语句进行数据库的操作。

为了方便我们观察我们操作的数据库，我们可以下载SQLite数据库管理工具，进行可视化管理。

SQLite数据库管理工具: <https://sqlitestudio.pl/>

<img src='_media/3-9-4.png' alt='数据库管理工具' style='zoom:40%;'/>

> 数据库操作

数据库的操作一般可以分为四个部分：调用模块、数据库连接、数据库操作、关闭数据库释放资源。
跟文本文档的操作步骤相似（打开文件、操作文件、关闭文件）
具体实施到python程序中，有5个小步骤：连接数据库、创建游标、数据库操作、提交操作、释放资源。

<img src='_media/3-9-5.png' alt='数据库管理工具' style='zoom:40%;'/>

## 二、 Sqlite3 数据库操作

> 1、调用 `insert语句` 插入单条数据

```python
import sqlite3
con = sqlite3.connect('scores.db') #打开或创建数据库
cur = con.cursor() #获取游标

# 调用insert()语句插入单条数据
cur.execute('''insert into score values('小黑',10,95)''')

con.commit()  # 调用提交事务，对数据库的修改生效
cur.close() #关闭游标
con.close() #关闭连接
```

<img src='_media/3-9-6.png' alt='sqlite3操作' style='zoom:40%;'/>

> 2、调用 `insert语句` 插入多条数据

```python
import sqlite3
con = sqlite3.connect('scores.db') #打开或创建数据库
cur = con.cursor() #获取游标

# 调用insert()语句插入数值
datas = [('小白',11,90),('小灰',11,85)]
insert_datas_sql = '''insert into score values (?,?,?)'''
cur.executemany(insert_datas_sql, datas)

con.commit()  # 调用提交事务，对数据库的修改生效
cur.close() #关闭游标
con.close() #关闭连接
```

<img src='_media/3-9-7.png' alt='sqlite3操作' style='zoom:40%;'/>

> 3、使用`delete语句`删除数据

使用主关键词 `rowid=1` 删除一整条数据

```python
import sqlite3
con = sqlite3.connect('scores.db') #打开或创建数据库
cur = con.cursor() #获取游标

# 使用主关键词 rowid=1 删除一整条数据
delete_datas_sql = '''delete from score where rowid = 1'''

cur.execute(select_datas_sql)

result = cur.fetchone()
print(result)

con.commit()  # 调用提交事务，对数据库的修改生效
cur.close() #关闭游标
con.close() #关闭连接
```

<img src='_media/3-10-1.png' alt='sqlite3操作' style='zoom:40%;'/>

或者使用关键词 `name='小白' `删除指定的一整条数据

```python
delete_data_sql = '''delete from score where name = '小白' '''
```

<img src='_media/3-10-2.png' alt='sqlite3操作' style='zoom:40%;'/>

> 4、使用`select语句`查询数据

```python
import sqlite3
con = sqlite3.connect('scores.db') #打开或创建数据库
cur = con.cursor() #获取游标

# 使用select语句查询数据
select_datas_sql = '''select * from score where score > 80 '''

cur.execute(select_datas_sql)

result = cur.fetchone()
print(result)

con.commit()  # 调用提交事务，对数据库的修改生效
cur.close() #关闭游标
con.close() #关闭连接
```

<img src='_media/3-10-3.png' alt='sqlite3操作' style='zoom:40%;'/>

> 5、使用`update语句`修改数据

```python
import sqlite3
con = sqlite3.connect('scores.db') #打开或创建数据库
cur = con.cursor() #获取游标

#delete_datas_sql = '''delete from score where rowid = 1'''

update_data_sql = '''update score set score = 90 where name = '小灰' '''

cur.execute(update_data_sql)

con.commit()  # 调用提交事务，对数据库的修改生效
cur.close() #关闭游标
con.close() #关闭连接
```

<img src='_media/3-10-4.png' alt='sqlite3操作' style='zoom:40%;'/>

> 6、编写一个具有接收外部输入信息功能，并将信息保存到数据库中的小程序。

```python
import sqlite3
con = sqlite3.connect('scores.db') #打开或创建数据库
cur = con.cursor() #获取游标

# 创建数据表，如果存在则不需要创建
cur.execute('''create table if not exists score(name text, age integer, score integer)''')
datas = []
while True:
    name = input('输入要插入学生姓名（停止输入请按q键）：')
    if name != 'q':
        age = int(input('输入学生年龄：'))
        sco = int(input('输入学生成绩：'))
        datas.append((name,age,sco))
    else:
        break

# 调用insert语n句插入数值
insert_datas_sql = '''insert into score values (?,?,?)'''
cur.executemany(insert_datas_sql, datas)

# 调用select语句查询数据
name = input('输入查询学生姓名：')
select_data_sql = '''select * from score where name = ?'''
cur.execute(select_data_sql,(name,))
result = cur.fetchall()
print(result)

# 调用update语句修改数据
alter = input('是否需要修改（Y/N）：')
if alter == 'Y':
    age = int(input('请输入修改的年龄：'))
    sco = int(input('请输入修改的分数：'))
    update_data_sql = '''update score set age = ? , score = ? where name = ?'''
    cur.execute(update_data_sql,(age,sco,name))
    
# 调用delet语句删除数据
name = input('输入删除的学生：')
dele = input('是否需要删除（Y/N）：')
if dele == 'Y':
    delete_data_sql = '''delete from score where name = ?'''
    cur.execute(delete_data_sql,(name,))

print('修改成功')
con.commit()  # 调用提交事务，对数据库的修改生效
cur.close() #关闭游标
con.close() #关闭连接
```
<img src='_media/3-10-5.png' alt='sqlite3操作' style='zoom:40%;'/>