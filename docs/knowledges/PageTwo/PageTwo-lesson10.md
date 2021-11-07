# **Lesson-10**

## **tkinter模块**

`import tkinter`

tkinter 是使用 python 进行窗口视窗设计的模块。tkinter模块(“Tk 接口”)是Python的标准Tk GUI工具包的接口。

> 以作画比喻tkinter的编程

先支一个画架，放上画板，蒙上画布，构思内容，用铅笔画草图，组织结构和比例，调色板调色，最后画笔勾勒。
相应的，对应到tkinter编程，那么我们的显示屏就是支起来的画架，根窗体就是画板，在tkinter中则是Toplevel，画布就是tkinter中的容器（Frame），画板上可以放很多张画布（Convas），tkinter中的容器中也可以放很多个容器，绘画中的构图布局则是tkinter中的布局管理器（几何管理器），绘画的内容就是tkinter中的一个个小组件，一幅画由许多元素构成，而我们的GUI界面，就是有一个个组件拼装起来的，它们就是widget。



## **常用tkinter控件**

|控件|释义|控件|释义|控制|释义|
|:-:|:-:|:-:|:-:|:-:|:-:|
|Button|按钮|Label|标签|Scrollbar|滚动条|
|Canvas|画布|Listbox|列表|Text|文本|
|Entry|输入|Menu|菜单|Toplevel|容器|
|Frame|框架|Scale|范围|Spinbox|输入|
|Menubutton|菜单按钮|PanedWindow|窗口布局|messageBox|消息框|
|Chekbutton|多选|Radiobutton|单选|Message|消息|
|LabelFrame|容器控件|OptionMenu|选择菜单|

### 1. tkinter窗口设置
```python
# 导入tkinter模块，并重命名为tk
import tkinter as tk    

# 创建一个名为window的窗体。
window = tk.Tk()       
# tk.Tk()是tk模块中的Tk()类，在阶段三课程中会涉及到，这里只需要记住即可

# 设置窗体的标题。
window.title('python')   

# 设置窗体的大小。格式为'长x宽+电脑屏幕左侧距离+电脑屏幕上边距离'
window.geometry('500x300+300+300')

'''
 在这里进行控件的程序编写
'''

# 主窗口循环显示
window.mainloop()
# 注意，loop因为是循环的意思，window.mainloop就会让window不断的刷新，如果没有mainloop,就是一个静态的window,传入进去的值就不会有循环，mainloop就相当于一个很大的while循环，有个while，每点击一次就会更新一次，所以我们必须要有循环
# 所有的窗口文件都必须有类似的mainloop函数，mainloop是窗口文件的关键的关键。
```

<img src='_media/2-10-1.png' alt='tkinter' style='zoom:40%;'/>

### 2. Label

Label是tkinter中的标签控件，可以显示文本。

```python
import tkinter as tk    

window = tk.Tk()       
window.title('python')   
window.geometry('500x300+300+300')

# 加载标签控件
label = tk.Label(window, text='Hello World!', bg='green', font=('宋体',14), width=30, height=2)
# 说明： bg为背景，font为字体，width为长，height为高，这里的长和高是字符的长和高，比如height=2,就是标签有2个字符这么高
 
# 放置标签
label.pack()

window.mainloop()
```

<img src='_media/2-10-2.png' alt='label' style='zoom:40%;'/>

### 3. Button

Button是一个标准的tkinter窗口部件，用来实现各种按钮。

按钮可包含文本或图像，且能将其与函数或方法相关联，当按钮被按下时，tkinter自动调用相关联的函数或方法。

```python
import tkinter as tk    

window = tk.Tk()       
window.title('python')   
window.geometry('500x300+300+300')

var = tk.StringVar() # 将label标签的内容设置为字符类型，用var来接收hit_me函数的传出内容用以显示在标签上

label = tk.Label(window, textvariable=var, bg='green', font=('宋体',14), width=30, height=2)
label.pack()

# 定义一个函数功能，供点击Button按键时调用，调用命令参数command=函数名
is_click = False
def click():
    global is_click
    if is_click == False:
        var.set('Hello World!')
        is_click = True
    else:
        var.set('')
        is_click = False

# 在窗口界面设置加载Button按键  
button = tk.Button(window, text='click', font=('Arial', 12), width=10, height=1, command=click)
# 放置按钮
button.pack()

window.mainloop()
```

<img src='_media/2-10-3.png' alt='button' style='zoom:40%;'/>
<img src='_media/2-10-4.png' alt='button' style='zoom:40%;'/>

### 4. Entry

tkinter中提供的一个单行文本输入域，收集键盘输入。

我们需要输入信息时，比如我们平时使用软件、登录网页时，用户交互界面让我们登录账户信息等可以用到。

```python
import tkinter as tk    

window = tk.Tk()       
window.title('python')   
window.geometry('500x300+300+300')

# 在窗口界面设置加载Entry控件 
entry1 = tk.Entry(window, show='*', font=('Arial', 14))   # 显示成密文形式
entry2 = tk.Entry(window, show=None, font=('Arial', 14))  # 显示成明文形式
# 放置输入框
entry1.pack()
entry2.pack()

window.mainloop()
```

<img src='_media/2-10-5.png' alt='entry' style='zoom:40%;'/>

### 5. Text

Text是tkinter中提供的的一个多行文本区域，可用来收集(或显示)用户输入的文字

在需要显示编辑用户、产品多行信息时，比如显示用户详细描述文字、产品简介等，支持随时编辑。

```python
import tkinter as tk    

window = tk.Tk()       
window.title('python')   
window.geometry('500x300+300+300')

# 在窗口界面设置加载Text控件 
text = tk.Text(window, width=20, height=3,  font=('Arial', 14))
# 放置文本显示框
text.pack()

window.mainloop()
```

<img src='_media/2-10-6.png' alt='text' style='zoom:40%;'/>

### 6. messagebox

messagebox是用于显示应用程序的消息框，就是我们平常看到的弹框。

我们首先需要定义一个触发功能，来触发这个弹窗，这里就需要以前学过的button按钮，通过触发功能，调用messagebox部件，点击button按钮就会弹出提示对话框。下面是messagebox提示信息的几种形式：

```python
import tkinter as tk
import tkinter.messagebox  # 需要提前单独导入messagebox模块  

window = tk.Tk()       
window.title('python')   
window.geometry('500x300+300+300')

def click():
    tk.messagebox.showinfo(title='Hi', message='Hello World！')              # 提示信息对话窗
    # tkinter.messagebox.showwarning(title='Hi', message='有警告！')       # 提出警告对话窗
    # tkinter.messagebox.showerror(title='Hi', message='出错了！')         # 提出错误对话窗
    # print(tkinter.messagebox.askquestion(title='Hi', message='确定!'))  # 询问选择对话窗return 'yes', 'no'
    # print(tkinter.messagebox.askyesno(title='Hi', message='Hello World！'))     # return 'True', 'False'
    # print(tkinter.messagebox.askokcancel(title='Hi', message='Hello World！'))  # return 'True', 'False'
 
# 第4步，在图形界面上创建一个标签用以显示内容并放置
button = tk.Button(window, text='click', bg='green', font=('Arial', 14), command=click)
button.pack()

window.mainloop()
```

<img src='_media/2-10-7.png' alt='messagebox' style='zoom:40%;'/>

### 7. 其他控件使用
其他控件的使用可以观看官方网站
<https://docs.python.org/zh-cn/3/library/tk.html>
或者其他老师的博客
<https://www.cnblogs.com/shwee/p/9427975.html>