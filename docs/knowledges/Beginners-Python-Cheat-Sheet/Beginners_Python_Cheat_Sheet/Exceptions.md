# 异常 Exception

异常可帮助我们对可能发生的错误做出适当的响应。  
在 try 代码块中放置可能导致错误的代码。  
响应错误而运行的代码位于 except 代码块中。  
仅当 try 代码块成功时才应运行的代码将进入 else 代码块。

> 抛出异常
```python
prompt = "How many tickets do you need? "
num_tickets = input(prompt)

try:
    num_tickets = int(num_tickets)
except ValueError:
    print("Please try again.") 
else:
    print("Your tickets are printing.")
```