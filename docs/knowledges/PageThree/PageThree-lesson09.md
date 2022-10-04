# **Lesson-09**

## 一、 数据分类

计算机中的数据或者信息按照数据格式大体可以分为两种数据类型：结构化数据和非结构化数据。

一般把可以用二维表结构来逻辑表达和实现的数据称之为结构化数据，也就是这些数据可以显示在行和列中以及关系数据库中。

一般把数据结构不规则或者不完整，不方便用数据二维表结构来逻辑表达和实现的数据称之为非结构化数据，包括所有的办公文档、文本、图片、图像、音频、视频、网页等。

<img src='_media/3-9-1.png' alt='数据分类' style='zoom:40%;'/>

例如，我们使用文本文档做出一个简易的测评成绩说明，这段文字中包含了很多测评信息。这个文本文档中所有信息为字符串形式，其中包含了很多测评信息，但是这些信息之间并没有固定的格式和联系，只是进行了简单的罗列。这类信息就是非结构化数据。

如果我们将文本文档中的信息进行提取，分别提取出姓名、年龄、分数这三类数据，每类数据下面对应的有具体类型的数据内容，将这些信息存放在数据库中，这类数据就是结构化数据。

<img src='_media/3-9-2.png' alt='数据分类' style='zoom:40%;'/>

## 二、 数据库

数据库是“按照数据结构来组织、存储和管理数据的仓库”。是一个长期存储在计算机内的、有组织的、可共享的、统一管理的大量数据的集合。

关系型数据库中不同类型数据由于一定格式组成了数据表单，数据表单都附属于某个数据库中。

数据库的核心就是数据表，表单展现了不同类型数据之间的关系，它是一个具有行和列的二元组。要创建要给表单，需要给他命名，明确次序、每一项的名称以及每一列的类型。

某一行或者某几行通常作为表单的主键，在表单中主键的值是独一无二的，防止重复增添 数据项。这些键在查询时被快速索引，类似于图书的索引，方便快速地找到指定行。

每一个表单都附属于某数据库，类似于一个文件都存在于某目录下。两层的层次结构便于 更好地组织和管理。

<img src='_media/3-9-3.png' alt='数据分类' style='zoom:40%;'/>

## 三、 Sqlite3 数据库

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

## 四、 Sqlite3 数据库操作

> 1、调用 `insert语句` 插入单条数据

```python
import sqlite3
con = sqlite3.connect('scores.db') #打开或创建数据库
cur = con.cursor() #获取游标

# 调用insert语句插入单条数据
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

# 调用insert语句插入数值
datas = [('小白',11,90),('小灰',11,85)]
insert_datas_sql = '''insert into score values (?,?,?)'''
cur.executemany(insert_datas_sql, datas)

con.commit()  # 调用提交事务，对数据库的修改生效
cur.close() #关闭游标
con.close() #关闭连接
```

<img src='_media/3-9-7.png' alt='sqlite3操作' style='zoom:40%;'/>

> 3、编写一个具有接收外部输入信息功能，并将信息保存到数据库中的小程序。

```python
import sqlite3
con = sqlite3.connect('scores.db') #打开或创建数据库
cur = con.cursor() #获取游标

# 创建数据表，如果存在则不需要创建
cur.execute('''create table if not exists score(name text, age integer, score integer)''')
datas = []
while True:
    name = input('输入学生姓名（停止输入请按q键）：')
    if name != 'q':
        age = int(input('输入学生年龄：'))
        sco = int(input('输入学生成绩：'))
        datas.append((name,age,sco))
    else:
        break

# 调用insert语n句插入数值
insert_datas_sql = '''insert into score values (?,?,?)'''
cur.executemany(insert_datas_sql, datas)

con.commit()  # 调用提交事务，对数据库的修改生效
cur.close() #关闭游标
con.close() #关闭连接
```

<img src='_media/3-9-8.png' alt='sqlite3操作' style='zoom:40%;'/>
