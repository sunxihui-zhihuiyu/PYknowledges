# **Lesson-11**

## **文本输入框相关操作**

```python
entry1 = tk.Entry(win, show=None, font=('微软雅黑',20),bg='white',width=20)
entry1.place(x=250,y=150)
entry1.insert(0,'用户名')   # 在第0个位置，设置'用户名'文本内容
print(entry1.get())        # 返回Entry文本框控件中文本信息
```

## **变量信息输入到Tkinter窗口控件上**

```python
# 将变量信息输入到Label控件上
message = tk.StringVar()    # 首先使用tk.StringVar()接收变量信息
label4 = tk.Label(win, textvariable=message,font=('微软雅黑',15))
label4.place(x=150,y=400)
message.set('登陆成功')      # 使用set()函数设置变量信息
```

## **主窗口与子窗口**

> 使用Toplevel(主窗口)方法，定义一个子窗口。子窗口使用方法和主窗口一致。

```python
win_sign = tk.Toplevel(win)  # 定义一个子窗口
```

## **Tkinter控件列表**

|控件|释义|控件|释义|控制|释义|
|:-:|:-:|:-:|:-:|:-:|:-:|
|Button|按钮|Label|标签|Scrollbar|滚动条|
|Canvas|画布|Listbox|列表|Text|文本|
|Entry|输入|Menu|菜单|Toplevel|容器|
|Frame|框架|Scale|范围|Spinbox|输入|
|Menubutton|菜单按钮|PanedWindow|窗口布局|messageBox|消息框|
|Chekbutton|多选|Radiobutton|单选|Message|消息|
|LabelFrame|容器控件|OptionMenu|选择菜单|	
