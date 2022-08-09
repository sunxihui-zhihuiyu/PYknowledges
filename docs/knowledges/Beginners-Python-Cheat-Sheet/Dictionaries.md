Python 的字典允许你将两项相关的信息进行匹配连接。 每一条信息在一个字典内存储为键值对。
当你提供一个键，Python 返回关联的值。 您可以遍历所有键值对、所有键或所有值。

# 1. 定义一个字典 dictionary

使用花括号`{}`来定义字典。 使用冒号连接键和值，并使用逗号分隔单独的键值对。

> 创建字典
```python
alien_0 = {'color': 'green', 'points': 5}
```

---

# 2. 访问值

要访问与单个键关联的值，请给出字典的名称，然后将键放在一组方括号内。 如果您要的键不在字典，就会出错。
您还可以使用 `get()` 方法，如果键不存在，该方法返回 `None`，而不是错误。 如果键不在字典，你也可以指定一个默认值，

> 获取存在键值对的值
```python
alien_0 = {'color': 'green', 'points': 5}

print(alien_0['color'])
print(alien_0['points'])
```

> 使用`get()`获取值
```python
alien_0 = {'color': 'green'}

alien_color = alien_0.get('color')
alien_points = alien_0.get('points', 0)

print(alien_color)    # 'green'
print(alien_points)   # 0
```

---

# 3. 增加新的键值对

您可以将任意数量的键值对存储在一个字典，直到您的计算机内存不足。 
可以为现有字典添加一个新键值，方法是给出字典和方括号中的新键，以及将其设置为等于新值。
这也允许您从空字典开始，然后添加相关的键值对。

> 增加一个键值对
```python
alien_0 = {'color': 'green', 'points': 5}

alien_0['x'] = 0
alien_0['y'] = 25
alien_0['speed'] = 1.5
```

> 给一个空字典增加一个键值对
```python
alien_0 = {}

alien_0['color'] = 'green'
alien_0['points'] = 5
```

---

# 4. 修改值 

您可以在通过键修改字典中对应的值。请给出字典的名字和将键放在方括号内，并且提供新的值。

> 修改字典中的值
```python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)

# Change the alien's color and point value.
alien_0['color'] = 'yellow'
alien_0['points'] = 10
print(alien_0)
```

---

# 5. 删除键值对

您可以使用 `del` 关键字、字典名称及后跟方括号中的键，删除键及其关联值。

> 删除键值对
```python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)

del alien_0['points']
print(alien_0)
```

---

# 6. 遍历字典

您可以通过三种方式遍历字典：您可以循环遍历所有键值对、所有键或所有值。
如果要按顺序处理字典信息，您可以对循环中的键进行排序。

> 遍历字典所有键值对
```python
# Store people's favorite languages.
fav_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }

# Show each person's favorite language.
for name, language in fav_languages.items():
    print(name + ": " + language)
```

> 遍历字典所有的键
```python
# Show everyone who's taken the survey.
for name in fav_languages.keys():
    print(name)
```

> 遍历字典所有的值
```python
# Show all the languages that have been chosen.
for language in fav_languages.values():
    print(language)
```

> 按顺序遍历字典所有的键
```python
# Show each person's favorite language, 
# in order by the person's name.
for name in sorted(fav_languages.keys()):
    print(name + ": " + language)
```

---

# 7. 字典长度

您可以在字典中找到键值对的数量。

> 字典长度
```python
num_responses = len(fav_languages)
```

---

# 8. 嵌套-列表中嵌套字典

有时将一组字典存储在列表中很有用，这称为嵌套。

> 将字典存储在列表中
```python
# Start with an empty list.
users = []

# Make a new user, and add them to the list.
new_user = {
    'last':'fermi',
    'first':'enrico',
    'username':'efermi'
    }
users.append(new_user)

# Make another new user, and add them as well.
new_user = {
    'last': 'curie',
    'first': 'marie',
    'username': 'mcurie'
    }
users.append(new_user)

# Show all information about each user.
for user_dict in users:
    for k, v in user_dict.items():
        print(k + ':' + v)
    print('\n')
```

> 您也可以不使用 append(), 直接定义字典列表
```python
# Define a list of users, where each user 
# is represented by a dictionary. 
users = [ 
    { 
        'last': 'fermi', 
        'first': 'enrico', 
        'username': 'efermi'
    },
    { 
        'last': 'curie', 
        'first': 'marie', 
        'username': 'mcurie'
    }
        ]

# Show all information about each user. 
for user_dict in users: 
    for k, v in user_dict.items(): 
        print(k + ": " + v) 
    print("\n")
```

---

# 9. 嵌套-字典中嵌套列表

将列表存储在字典中，可以让每个键关联多个值。

> 在字典中存储列表
```python
# Store multiple languages for each person.
fav_languages = {
    'jen': ['python', 'ruby'],
    'sarah': ['c'],
    'edward': ['ruby', 'go'],
    'phil': ['python', 'haskell']
    }

# Show all responses for each person.
for name, langs in fav_languages.items():
    print(name + ": ")
    for lang in langs:
        print("- " + lang)
```

---

# 10. 嵌套-字典中嵌套字典

您可以将字典存储在另一个字典中。 在这个例子中，每个与键关联的值本身就是一个字典。

> 在字典中存储字典
```python
users = {
    'aeinstein': {
        'first': 'albert',
        'last': 'einstein',
        'location': 'princeton',
        },
    'mcurie': {
        'first': 'marie',
        'last': 'curie',
        'location': 'paris',
        }
    }

for username, user_dict in users.items():
    print("\nUsername: " + username)
    full_name = user_dict['first'] + " "
    full_name += user_dict['last']
    location = user_dict['location']

    print("\tFull name: " + full_name.title())
    print("\tLocation: " + location.title())
```

---

# 11. 有序字典（OrderedDict）的使用

标准 Python 字典中的键值对是无序的， 字典只保留每个键与其值之间的关联。 如果你想保留添加键和值的顺序，使用一个有序字典（OrderedDict）。

> 保留键值对的顺序

```python
from collections import OrderedDict

# Store each person's languages, keeping track of who respoded first.
fav_languages = OrderedDict()

fav_languages['jen'] = ['python', 'ruby']
fav_languages['sarah'] = ['c']
fav_languages['edward'] = ['ruby', 'go']
fav_languages['phil'] = ['python', 'haskell']

# Display the results, in the same order they were entered.
for name, langs in fav_languages.items():
    print(name + ":")
    for lang in langs:
        print("- " + lang)
```

---

# 12. 创建1000000个字典

如果所有字典都存在相似数据，可以使用循环生成大量的字典。

> 1000000个aliens
```python
aliens = []

# Make a million green aliens, worth 5 points
# each. Have them all start in one row.
for alien_num in range(1000000):
    new_alien = {}
    new_alien['color'] = 'green'
    new_alien['points'] = 5
    new_alien['x'] = 20 * alien_num
    new_alien['y'] = 0
    aliens.append(new_alien)

# Prove the list contains a million aliens.
num_aliens = len(aliens)

print("Number of aliens created:")
print(num_aliens)
```