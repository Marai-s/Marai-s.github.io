---
title: Python | Python基本语法
mermaid: true
mathjax: true
---

By Zhaoyang Song

2021年3月29日编写，后续会根据自己的学习进度再优化本文档

-------

# 1 一些语法

列举一些不是太常见的但是感觉蛮有用的语法。

## format

格式化字符串的函数 **str.format()**，它增强了字符串格式化的功能。

```python
"{} {}".format("hello", "world")    # 不设置指定位置，按默认顺序
'hello world'

"{0} {1}".format("hello", "world")  # 设置指定位置
'hello world'

"{1} {0} {1}".format("hello", "world")  # 设置指定位置
'world hello world'
```

# 2 控制流

在Python中有三种控制流语句——if、for 和 while

## if 语句 

if 语句用以检查条件：如果条件为真（True），我们将运行一块语句（称作 *if-block* 或 *if* 块），否则我们将运行另一块语句（称作 *else-block* 或 *else* 块）。其中 *else* 从句是可选的。

```python
if...:	#...代表相关代码
elif...:	#注意不要忘记冒号:
else...:	
#需要注意的是if语句在结尾处包含一个冒号——我们借此向Python指定接下来会有一块语句在后头
```

## while 语句 

while 语句能够让你在条件为真的前提下重复执行某块语句。while 语句是循环（*Looping*）语句的一种。while 语句同样可以拥有 else 子句作为可选选项。

```python
while...:
else...:
```

## for 循环

for...in 语句是另一种循环语句，其特点是会在一系列对象上进行迭代（*Iterates*），意即它会遍历序列中的每一个项目。

```python
for i in range(1, 5): 
	print(i) 
else:
	print('The for loop is over')
```

## break 语句

break 语句用以中断（Break）循环语句，也就是中止循环语句的执行，即使循环条件没有变更为 False ，或队列中的项目尚未完全迭代依旧如此。 有一点需要尤其注意，如果你的中断了一个 for 或 while 循环，任何相应循环中的 else 块都将不会被执行。 

## continue 语句 

continue 语句用以告诉 Python 跳过当前循环块中的剩余语句，并继续该循环的下一次迭代。

```python
while True:
    s = input('Enter something : ')
    if s == 'quit':
        break
    if len(s) < 3:
        print('Too small')
        continue		#如果其长度小于3，我们便通过使用 continue 语句跳过代码块中的其余语句
    print('Input is of sufficient length')
```

# 3 函数

函数（Functions）是指可重复使用的程序片段。它们允许你为某个代码块赋予名字，允许你通过这一特殊的名字在你的程序任何地方来运行代码块，并可重复任何次数。这就是所谓的调用（*Calling*）函数。我们已经使用过了许多内置的函数，例如 len 和 range 。 

函数可以通过关键字 def 来定义。这一关键字后跟一个函数的标识符名称，再跟一对圆括号，其中可以包括一些变量的名称，再以冒号结尾，结束这一行。随后而来的语句块是函数的一部分。

## 函数参数

函数可以获取参数，这个参数的值由你所提供，借此，函数便可以利用这些值来做一些事情。这些参数与变量类似，这些变量的值在我们调用函数时已被定义，且在函数运行时均已赋值完成。 

函数中的参数通过将其放置在用以定义函数的**一对圆括号中指定**，并**通过逗号予以分隔**。当我们调用函数时，我们以同样的形式提供需要的值。要注意在此使用的术语——在定义函数时给定的名称称作*“*形参*”*（*Parameters*），在调用函数时你所提供给函数的值称作*“*实参*”*（*Arguments*）。

```python
def print_max(a, b): 
	if a > b: 
		print(a, 'is maximum') 
	elif a == b: 
		print(a, 'is equal to', b) 
	else:
		print(b, 'is maximum')
```

## 局部变量

当你在一个函数的定义中声明变量时，它们不会以任何方式与身处函数之外但具有相同名称的变量产生关系，也就是说，这些变量名只存在于函数这一局部（*Local*）。这被称为变量的作用域（*Scope*）。所有变量的作用域是它们被定义的块，从定义它们的名字的定义点开始。 

## global 语句 

如果你想给一个在程序顶层的变量赋值（也就是说它不存在于任何作用域中，无论是函数还是类），那么你必须告诉 Python 这一变量并非局部的，而是全局（*Global*）的。我们需要通过 global 语句来完成这件事。因为在不使用 global 语句的情况下，不可能为一个定义于函数之外的变量赋值。

你可以使用定义于函数之外的变量的值（假设函数中没有具有相同名字的变量）。然而，这种方式**不会受到鼓励而且应该避免**，因为它对于程序的读者来说是含糊不清的，无法弄清楚变量的定义究竟在哪。而通过使用 global 语句便可清楚看出这一变量是在最外边的代码块中定义的。 

```python
x = 50 

def func(): 
    global x 
    
    print('x is', x) 
    x = 2 
    print('Changed global x to', x) 

func() 
print('Value of x is', x)

#    输出：
#    x is 50 
#    Changed global x to 2 
#    Value of x is 2

#    global 语句用以声明 x 是一个全局变量——因此，当我们在函数中为 x 进行赋值时，这 一改动将影响到我们在主代码块中使用的 x 的值。
```

你可以在同一句 global 语句中指定不止一个的全局变量，例如 global x, y, z 

## 关键字参数

如果你有一些具有许多参数的函数，而你又希望只对其中的一些进行指定，那么你可以通过命名它们来给这些参数赋值——这就是关键字参数（*Keyword Arguments*）——我们使用命名（关键字）而非位置（一直以来我们所使用的方式）来指定函数中的参数。 

这样做有两大优点——其一，我们不再需要考虑参数的顺序，函数的使用将更加容易。其二，我们可以只对那些我们希望赋予的参数以赋值，只要其它的参数都具有默认参数值。 

```python
def func(a, b=5, c=10): 
    print('a is', a, 'and b is', b, 'and c is', c) 

func(3, 7) 
func(25, c=24) 
func(c=50, a=100)
#	输出：
#	a is 3 and b is 7 and c is 10 
#	a is 25 and b is 5 and c is 24 
#	a is 100 and b is 5 and c is 50
```

## 可变参数

有时你可能想定义的函数里面能够有任意数量的变量，也就是参数数量是可变的，这可以通过使用星号来实现。

```python
def total(a=5, *numbers, **phonebook): 
    print('a', a) 
    
    #遍历元组中的所有项目 
    for single_item in numbers: 
        print('single_item', single_item) 
        
	#遍历字典中的所有项目 
    for first_part, second_part in phonebook.items():
	print(first_part,second_part) 
    
print(total(10,1,2,3,Jack=1123,John=2231,Inge=1560))
```

输出如下

```python
a 10 
single_item 1 
single_item 2 
single_item 3 
Inge 1560 
John 2231 
Jack 1123 
None
```

当我们声明一个诸如 *param 的星号参数时，从此处开始直到结束的所有位置参数（Positional Arguments）都将被收集并汇集成一个称为“param”的元组（Tuple）。 

类似地，当我们声明一个诸如 **param 的双星号参数时，从此处开始直至结束的所有关键字参数都将被收集并汇集成一个名为 param 的字典（Dictionary）。 

## return 语句

return 语句用于从函数中返回，也就是中断函数。我们也可以选择在中断函数时从函数中返回一个值。

```python
def maximum(x, y): 
    if x > y: 
        return x 
    elif x == y: 
        return 'The numbers are equal' 
    else:
        return y 
    
print(maximum(2, 3))
# 输出为3
```

## DocStrings

Python 有一个甚是优美的功能称作文档字符串（*Documentation Strings*），在称呼它时通常会使用另一个短一些的名字*docstrings*。DocStrings 是一款你应当使用的重要工具，它能够帮助你更好地记录程序并让其更加易于理解。令人惊叹的是，当程序实际运行时，我们甚至可以通过一个函数来获取文档。 

```python
def print_max(x, y): 
    '''Prints the maximum of two numbers.打印两个数值中的最大数。 
    
    The two values must be integers.这两个数都应该是整数。''' 
    # 如果可能，将其转换至整数类型 
    x = int(x) 
    y = int(y) 
    
    if x > y: 
        print(x, 'is maximum') 
	else:
        print(y, 'is maximum') 

print_max(3, 5) 
print(print_max.__doc__)
```

运行结果：

```python
5 is maximum
Prints the maximum of two numbers.打印两个数值中的最大数。

    The two values must be integers.这两个数都应该是整数。
```

函数的第一行逻辑行中的字符串是该函数的文档字符串（*DocString*）。这里要注意文档字符串也适用于模块（Modules）与类（Class） 。

该文档字符串所约定的是一串多行字符串，其中第一行以某一大写字母开始，以句号结束。第二行为空行，后跟的第三行开始是任何详细的解释说明。在此强烈建议你在你所有重要功能的所有文档字符串中都遵循这一约定。 

我们可以通过使用函数的 __doc__ （注意其中的双下划线）属性（属于函数的名称）来获取函数 print_max 的文档字符串属性。只消记住 Python 将所有东西都视为一个对象，这其中自然包括函数。

# 4 模块

如果你想在你所编写的别的程序中重用一些函数的话，答案是模块（Modules）。

编写模块有很多种方法，其中最简单的一种便是创建一个包含函数与变量、以 .py 为后缀的文件。另一种方法是使用撰写 Python 解释器本身的本地语言来编写模块。举例来说，你可以使用 C 语言来撰写 Python 模块，并且在编译后，你可以通过标准 Python 解释器在你的 Python 代码中使用它们。 

一个模块可以被其它程序导入并运用其功能。我们在使用 Python 标准库的功能时也同样如此。

## from..import 语句 

如果你希望直接将 sqrt 变量导入你的程序（为了避免每次都要输入 math. ），那么你可以通过使用 from math import sqrt 语句来实现这一点。 

```python
from math import sqrt 
print("Square root of 16 is", sqrt(16))
```

> 警告：一般来说，你应该尽量避免使用 from···import 语句，而去使用 import 语句。这是为了避免在你的程序中出现名称冲突，同时也为了使程序更加易读。 

## 编写你自己的模块 

案例（保存为 mymodule.py ）： 

```python
def say_hi(): 
	print('Hi, this is mymodule speaking.') 
__version__ = '0.1' 
```

上方所呈现的就是一个简单的模块。正如你所看见的，与我们一般所使用的 Python 的程序相比其实并没有什么特殊的区别。我们接下来将看到如何在其它 Python 程序中使用这一模块。 

要记住该模块应该放置于与其它我们即将导入这一模块的程序相同的目录下，或者是放置在 sys.path 所列出的其中一个目录下。 

另一个模块（保存为 mymodule_demo.py ）： 

```python
import mymodule 

mymodule.say_hi() 
print('Version', mymodule.__version__) 
```

输出

```python
$ python mymodule_demo.py 
Hi, this is mymodule speaking. 
Version 0.1
```

你会注意到我们使用相同的点符来访问模块中的成员。

# 5 数据结构

数据结构（Data Structures）基本上人如其名——它们只是一种结构，能够将一些数据聚合在一起。换句话说，它们是用来存储一系列相关数据的集合。 

Python 中有四种内置的数据结构——列表（*List*）、元组（*Tuple*）、字典（*Dictionary*）和集合（*Set*）。

## 列表

列表是一种用于保存一系列有序项目的集合，也就是说，你可以利用列表保存一串项目的序列。想象起来也不难，你可以想象你有一张购物清单，上面列出了需要购买的商品，除开在购物清单上你可能为每件物品都单独列一行，**在 Python 中你需要在它们之间多加上一个逗号**。

**项目的列表应该用方括号括起来**，这样 Python 才能理解到你正在指定一张列表。一旦你创建了一张列表，你可以添加、移除或搜索列表中的项目。既然我们可以添加或删除项目，我们会说列表是一种可变的（*Mutable*）数据类型，意即，这种类型是可以被改变的。 

## 元组

元组（Tuple）用于将多个对象保存到一起。你可以将它们近似地看作列表，但是元组不能提供列表类能够提供给你的广泛的功能。元组的一大特征类似于字符串，**它们是不可变的**，也就是说，你不能编辑或更改元组。 

元组是通过特别指定项目来定义的，在指定项目时，你可以给它们**加上括号**，并在**括号内部用逗号进行分隔 **。元组通常用于保证某一语句或某一用户定义的函数可以安全地采用一组数值，意即元组内的数值不会改变。 

我们可以通过在方括号中指定项目所处的位置来访问元组中的各个项目。这种使用方括号的形式被称作索引（*Indexing*）运算符。

## 字典

字典就像一本地址簿，如果你知道了他或她的姓名，你就可以在这里找到其地址或是能够联系上对方的更多详细信息，换言之，我们将键值（*Keys*）（即姓名）与值（*Values*）（即地址等详细信息）联立到一起。在这里要注意到键值必须是唯一的，正如在现实中面对两个完全同名的人你没办法找出有关他们的正确信息。

另外要注意的是你只能使用不可变的对象（如字符串）作为字典的键值，但是你可以使用可变或不可变的对象作为字典中的值。基本上这段话也可以翻译为你只能使用简单对象作为键值。

> 在字典中，你可以通过使用符号构成 d = {key : value1 , key2 : value2} 这样的形式，来成对地指定键值与值。在这里要注意到成对的键值与值之间使用冒号分隔，而每一对键值与值则使用逗号进行区分，它们全都由一对花括号括起。 

## 序列

列表、元组和字符串可以看作序列（Sequence）的某种表现形式，可是究竟什么是序列，它又有什么特别之处？ 

序列的主要功能是资格测试（*Membership Test*）（也就是 in 与 not in 表达式）和索引操作（*Indexing Operations*），它们能够允许我们直接获取序列中的特定项目。上面所提到的序列的三种形态——列表、元组与字符串，同样拥有一种切片（*Slicing*）运算符，它能够允许我们序列中的某段切片——也就是序列之中的一部分。 

```python
shoplist = ['apple', 'mango', 'carrot', 'banana'] 
name = 'swaroop' 

# Indexing or 'Subscription' operation # 
# 索引或“下标（Subscription）”操作符 # 
print('Item 0 is', shoplist[0]) 
print('Item 1 is', shoplist[1]) 
print('Item 2 is', shoplist[2]) 
print('Item 3 is', shoplist[3]) 
print('Item -1 is', shoplist[-1]) #位置计数将从队列的末尾开始。因 此，shoplist[-1] 指的是序列的最后一个项目，shoplist[-2] 将获取序列中倒数第二个项目。
print('Item -2 is', shoplist[-2]) 
print('Character 0 is', name[0]) 

# Slicing on a list # 
print('Item 1 to 3 is', shoplist[1:3]) 
print('Item 2 to end is', shoplist[2:]) 
print('Item 1 to -1 is', shoplist[1:-1]) 
print('Item start to end is', shoplist[:]) 

# 从某一字符串中切片 # 
print('characters 1 to 3 is', name[1:3]) 
print('characters 2 to end is', name[2:]) 
print('characters 1 to -1 is', name[1:-1]) 
print('characters start to end is', name[:]) 
```

输出

```python
Item 0 is apple 
Item 1 is mango 
Item 2 is carrot 
Item 3 is banana 
Item -1 is banana 
Item -2 is carrot 
Character 0 is s 
Item 1 to 3 is ['mango', 'carrot'] 
Item 2 to end is ['carrot', 'banana'] 
Item 1 to -1 is ['mango', 'carrot'] 
Item start to end is ['apple', 'mango', 'carrot', 'banana'] 
characters 1 to 3 is wa 
characters 2 to end is aroop 
characters 1 to -1 is waroo 
characters start to end is swaroop 
```

# 6 面向对象编程

在至今我们编写的所有程序中，我们曾围绕函数设计我们的程序，也就是那些能够处理数据的代码块。这被称作面向过程（*Procedure-oriented*）的编程方式。还有另外一种组织起你的程序的方式，它将数据与功能进行组合，并将其包装在被称作“对象”的东西内。在大多数情况下，你可以使用过程式编程，但是当你需要编写一个大型程序或面对某一更适合此方法的问题时，你可以考虑使用面向对象式的编程技术。 

类与对象是面向对象编程的两个主要方面。一个类（**Class**）能够创建一种新的类型（*Type*），其中对象（**Object**）就是类的实例（**Instance**）。可以这样来类比：你可以拥有类型 int 的变量，也就是说存储整数的变量是 int 类的实例（对象）。

# 7 杂

- 标识符名称是区分大小写的。

- 新行：\n

- 制表符： \t 

- 整除：// ；表示x除以y并对结果向下取整至最接近的整数。 13 // 3 输出 4 。 -13 // 3 输出 -5 

- 不等于：!=

----------

一个放置在末尾的反斜杠表示字符串将在下一行继续，但不会添加新的一行。来看看例子：

```python
"This is the first sentence. \
This is the second sentence."
#相当于"This is the first sentence. This is the second sentence."
```

----

要注意到 （变量 = 变量 运算 表达式） 会演变成 （变量 运算 = 表达式） 。 如下例子：

```python
a = 2 
a *= 3
```

------------


## 原始字符串 

如果你需要指定一些未经过特殊处理的字符串，比如转义序列，那么你需要在字符串前增加r或R来指定一个原始（Raw） 字符串。下面是一个例子：

```python
r"Newlines are indicated by \n"
```

## 逻辑行与物理行

所谓物理行（Physical Line）是你在编写程序时你所看到 的内容。所谓逻辑行（Logical Line）是 Python 所看到 的单个语句。

Python之中暗含这样一种期望：Python鼓励每一行使用一句独立语句从而使得代码更加可读。

如果你有一行非常长的代码，你可以通过使用反斜杠将其拆分成多个物理行。这被称作显式行连接（Explicit Line Joining）

```python
s = 'This is a string. \ 
This continues the string.' 
print(s)
```

输出

```txt
This is a string. This continues the string.
```
