Notes on by 关, 赵 - 看漫画学 Python

written from 2022/02/07 to

# Chapter 1

## 1.1 Python 的历史

1989, Guido van Rossum, 为了打发圣诞节的闲暇时间, 开发了一门解释型编程语言

创造时间早, 直到最近几年才因广泛应用而在中国流行起来

命名来源于蟒蛇或 Monty python

Python 的发展史

1990: 公开版发布

2000: 2.0 发布

2008: 3.0 发布

2020: 2.7 停止维护

## 1.2 Python 的特点

Python 之所以受到大家的欢迎

简单, 易学, 免费, 开源

解释型

看似比编译型语言慢, 但是存在即合理

可移植

编译型语言没有可移植性, 但是解释型语言可以

代码规范

通过缩进而不是`{}`来标识代码块

面向对象

胶水语言

因为 Python 可以调用 C 语言, 所以可以通过 Python 作为媒介来粘合 C 和 Java 的代码块

也因此, Python 可以控制硬件

丰富的库

动态类型

C/C++和 Java 都是静态语言

Python 不会检查数据类型

## 1.3 搭建 Python 开发环境

Python 解释器

安装时注意点选`加入Path`, 这样就可以在`命令提示符`使用 Python 的指令

Python 运行所需要的基础库

交互式运行工具—Python Shell

## 1.4 动动手

### 1.4.1 交互方式

使用 IDLE

```python
# >>> indicates user inputs
>>> s = 'hello world
>>> s
'hello world' # returned value
```

在光标所在语句输入`Enter`可直接复制此语句

选中一段代码时输入`Enter`则可赋值此段代码

使用 Python Shell

python Shell 没有文本的高亮显示

### 1.4.2 文件方式

也成为脚本方式运行

使用文本编辑工具或者 IDE(Integrated Development Environments)

在 Windows 下, 记事本就是系统自带的文本编辑器

注意编码字符集选择`UTF-8`, 文件后缀名选择`.py`

使用 python 指令运行文件

在当前文件夹的地址栏输入`cmd, Enter`可以在此地址下直接打开后台

`python file.py`

在 Windows 平台不需要区分大小写, 其他平台只能用`python`

切换硬盘分区要使用 DOS 指令`disc-id:`

## 1.5 练一练

使用交互方式和文本方式运行`hello world`

# Chapter 2 编程基础的那点事!

## 2.1 标识符

注意事项

区分大小写: Myname 和 myname 是两个不同的标识符

首字符可以是下划线`_`或字母, 但不能是数字

字母包括非拉丁字母外的 character

除首字符外的其他字符必须是下划线, 字母和数字

关键字不能作为标识符

不要使用 Python 的内置函数作为自己的标识符

虽然非拉丁文字母可以作为标识符使用, 但不建议使用

关键字和标识符的区别

关键字是语言定义好的字符串, 有特殊含义

而标识符是用户自定义的

书中标识符的举例

合法的标识符

`身高`, `_sys_val`, `User_Name`

非法的标识符

`2mail`, `$Name`, `class`, `room#`

## 2.2 关键字

Python 的关键字并不多, 可见其比较简单

有些语言的关键字有上百个, 关键字又分为几类, 有些关键字还可以作为标识符使用

不要把关键字背下来

除`None`, `True`, `False`之外的关键字都是小写

## 2.3 变量

在 Python 中对一个变量赋值的同时就声明了该变量

声明变量, 变量的数据类型根据赋值数据所属的类型推导出来

动态类型允许变量改变数据类型, 静态类型则不允许

书中例子

```python
greeting = 'HelloWorld'
student_score = 0.0
y = 20
y = True
```

## 2.4 语句

遗憾代码表示一条语句, 在一般情况下语句结束时不加分号

虽然不属于编程规范, 但是 Python 支持连等

## 2.5 代码注释

`#`位于注释行的开头

`#`后有一个`Space`, 接着是注释内容, 这是好的编程规范

编程往往是团体开发, 所以要遵守好编程规范

在 Python 程序的最前面一般带有一个语句, 来标识该文件的编码集

`# coding=uft-8`

亦可写作`# _#_ coding: uft-8 _#_`

## 2.6 模块

一个模块就是一个文件

可以包含多个变量, 函数, 类等

模块中的程序元素就指上面这些

导入语句有如下三种方式

`import module`

`from module import code-element`

`from module import code-element as alias`

方法 1 会导入该模块的所有元素, 而且使用时必须用`module.element`的格式

## 2.7 动动手

模块的使用

world 模块

```python
# coding=utf-8

x = '你好'
y = True
z = 20.0
```

hello 模块

```python
# coding=utf-8

import world
from world import z
from world import x as x2

x = 100
y = 20

print(y)  # 访问当前模块变量y
print(world.y)  # 访问world模块变量y
print(z)  # 访问world变量z
print(x2)  # x2是world模块x别名
```

注意在模块命名是也不要使用关键字或函数名, 要遵守 Python 规范

## 2.8 练一练

# Chapter 3

## 3.1 Python 中的数据类型

6 中内置数据类型:

Python 所提供的数据类型

数字, 字符串, 列表, 元组, 集合和字典

列表, 元组, 集合和字典可容纳多项数据, 本书中统称为容器型数据

4 种数字类型:

整数, 浮点, 复数和布尔

相同的数据类型可以进行运算, 不同的数据类型则需要转换

Python 中的所有数据值都是类的实例

## 3.1 整数类型

Python3.0 之后整数类型统一为`int`

整数的不同表示方法

十进制

`0b`开头加上二进制

`0o`加上八进制

`0x`加上十六进制

```python
28
0b11100
0o34
0x1c
```

## 3.3 浮点类型

浮点的存储方式和小数存储的方式是不同的

小数用二进制表示十分复杂

不同的计算机在进行浮点运算时都不会像数学那样精确

位数的保留和精确度都是存在的问题

浮点数的表示方法

小数点表示

科学计数法表示, 用`E`或`e`

## 3.4 复数类型

复数在数学中被表示为: `a + bi`, 其中`a`为实部, `b`为虚部, `i`为虚部单位

在计算机实际应用中, `j`取代了`i`为虚部

复数的类型是`complex`

## 3.5 布尔类型

布尔类型是`bool`

在 C/C++中, `1`和`0`可以用来表示布尔类型, 但 Python 却不可以

其他数据类型可以通过`bool()`来转换为布尔类型

空值为`False`, 反之为`True`

`0`为空值

## 3.6 数字类型的互相转换

隐式类型的转换

自动完成的转换

显式类型的转换

通过函数完成的转换

转换规律

| 操作数 1 的类型 | 操作数 2 的类型 | 转换后的类型 |
| --------------- | --------------- | ------------ |
| bool            | int             | int          |
| bool, int       | float           | float        |

转换函数

`int()`

`float()`

`bool()`

# Chapter 4 运算符

## 4.1 算数运算符

| 运算符 | 名称     | 例子     | 说明           |              |
| ------ | -------- | -------- | -------------- | ------------ |
| +      | 加       | a + b    | 求和           |              |
| -      | 减       | a - b    | 求差           |              |
| \*     | 乘       | a \* b   | 求积           |              |
| /      | 除       | a / b    | 求商           | 所得为浮点数 |
| %      | 取余     | a % b    | 求余           |              |
| \*\*   | 幂       | a \*\* b | 求幂           |              |
| //     | 地板除法 | a // b   | 求商的最大整数 | 所得为整数   |

## 4.2 比较运算符

| 运算符 | 名称     | 例子   | 说明                                     |
| ------ | -------- | ------ | ---------------------------------------- |
| ==     | 等于     | a == b | a 等于 b 时返回 True, 否则返回 False     |
| !=     | 不等于   | a != b | 与==相反                                 |
| >      | 大于     | a > b  | a 大于 b 时返回 True, 否则返回 False     |
| <      | 小于     | a < b  | a 小于 b 时返回 True, 否则返回 False     |
| >=     | 大于等于 | a >= b | a 大于等于 b 时返回 True, 否则返回 False |
| <=     | 小于等于 | a <= b | a 小于等于 b 时返回 True, 否则返回 False |

`1.0 = 1`是 True

## 4.3 逻辑运算符

| 运算符 | 名称   | 例子    | 说明                                             |
| ------ | ------ | ------- | ------------------------------------------------ |
| not    | 逻辑非 | not a   | a 为 True 时, 值为 False, 反之亦然               |
| and    | 逻辑与 | a and b | a, b 全为 True 时, 值为 True, 其他全部为 False   |
| or     | 逻辑或 | a or b  | a, b 全为 False 时, 值为 False, 其他全部为 False |

逻辑与和逻辑或具有短路特征

| 表达式 1 | and | 表达式 2 | 返回 False |
| -------- | --- | -------- | ---------- |
| False    |     | 不再计算 |            |

| 表达式 1 | or  | 表达式 2 | 返回 True |
| -------- | --- | -------- | --------- |
| True     |     | 不再计算 |           |

example, 测试逻辑短路

```python
a = 1
b = 0
def f1()
		print('--进入函数f1--')
		retur True

(a > b) or f1() # short
(a < b) or f1()
(a < b) and f1() # short
(a > b) and f1()
```

## 4.4 位运算符

| 运算符 | 名称   | 例子   | 说明                               |                            |
| ------ | ------ | ------ | ---------------------------------- | -------------------------- |
| ~      | 位反   | ~x     | 将 x 的值按位取反                  |                            |
| &      | 位与   | x & y  | 将 x 与 y 按位进行位与运算         | 都为 1 为 1, 其余为 0      |
| \|     | 位或   | x \| y | 将 x 与 y 按位进行位或运算         | 有一个为 1 为 1, 其余为 0  |
| ^      | 位异或 | x ^ y  | 将 x 与 y 按位进行位异或运算       | 不同时为 1, 相同时为 0     |
| >>     | 右移   | x >> a | 将 x 右移 a 位, 高位采用符号位补位 | 正数首位为 0, 负数首位为 1 |
| <<     | 左移   | x << a | 将 x 左移 a 位, 低位用 0 补位      |                            |

左移是乘法, 右移是除法

位取反运算设计源码, 补码, 反码运算, 比较麻烦, 可简单按如下公式计算

`~a = (a + 1) * -1`

example, 位运算

```python
a = 10110010
b = 01011110
a | b = 11111110
a & b = 00010010
a ^ b = 11101100
a >> 2 = 00101100
a << 2 = 11001000
```

## 4.5 赋值运算符

| 运算符 | 名称         | 例子      | 说明         |
| ------ | ------------ | --------- | ------------ |
| +=     | 加赋值       | a += b    | a = a + b    |
| -=     | 减赋值       | a -= b    | a = a - b    |
| \*=    | 乘赋值       | a \*= b   | a = a \* b   |
| /=     | 除赋值       | a /= b    | a = a / b    |
| %=     | 取余赋值     | a %= b    | a = a % b    |
| \*\*=  | 幂赋值       | a \*\*= b | a = a \*\* b |
| //=    | 地板除法赋值 | a //= b   | a = a // b   |
| &=     | 位与赋值     | a &= b    | a = a & b    |
| \| =   | 位或赋值     | a \| = b  | a = a \| b   |
| ^=     | 位异或赋值   | a ^= b    | a = a ^ b    |
| <<=    | 左移赋值     | a <<= b   | a = a << b   |
| >>=    | 右移赋值     | a >>= b   | a = a >> b   |

## 4.6 运算符的优先级

| 优先级 | 运算符               | 说明                 |
| ------ | -------------------- | -------------------- |
| 1      | ()                   | 小括号               |
| 2      | \*\*                 | 幂                   |
| 3      | ~                    | 位反                 |
| 4      | +, -                 | 正负号               |
| 5      | \*, /, %, //         | 乘, 除, 取余, 地板除 |
| 6      | +, -                 | 加, 减               |
| 7      | <<, >>               | 位移                 |
| 8      | &                    | 位与                 |
| 9      | ^                    | 位异或               |
| 10     | \|                   | 位或                 |
| 11     | <, <=, >, >=, !=, == | 比较                 |
| 12     | not                  | 逻辑非               |
| 13     | and, or              | 逻辑与, 逻辑或       |

## 4.7 练一练

# Chapter 5 程序流程控制

程序具有分支, 循环还有判断, 使得程序更加智能

## 5.1 分支语句

Python 没有多分支语句(`switch`语句), 只有`if`语句

`if`

`if-else`

`if-elif-else`

syntax

```python
if condition:
		codes # 4-space indentation
```

### 5.1.1 if 结构

example, 成绩

```python

# coding=utf-8

score = int(input("请输入你的成绩:")

if score >= 85:
		print("你真优秀!")
if score < 60:
		print("你需要加倍努力!")
if (score >= 60) and (score < 85):
		print("你的成绩还可以, 仍需要继续努力!")
```

### 5.1.2 if-else 结构

syntax

```python
if condition:
		code-block-1
else:
		code-block-2
```

example, 成绩

```python
# coding=utf-8

score = int(input("请输入你的成绩:"))

if score >= 60:
		if score >= 85:
				print("你真优秀!")
		else:
				print("你的成绩还可以, 仍需要继续努力!")
else:
		print("你需要加倍努力!")
```

### 5.1.3 if-elif-else 结构

syntax

```python
if condition:
		code-block-1
elif conditon:
		code-block-2
else:
		code-block-3
```

example, 成绩转换五分制

```python
# coding=utf-8

score = int(input("请输入你的成绩:"))

if score >= 90:
		grade = 'A'
elif score >= 80
		grade = 'B'
elif score >= 70:
		grade = 'C'
elif score >= 60:
		grade = 'D'
else:
		grade = 'F'

print("Grade = " + grade)
```

## 5.2 循环语句

### 5.2.1 while 语句

Python 中有两种循环语句, `while`和`for`语句

syntax

```python
while condition:
		code-block-1
[else:
		code-block-2]
```

else 语句在此为可省略部分, 如果循环正常结束, 则可进入 else 语句

当循环被打断, 有 break, return 和异常这三种情况, 此时不会进入 else 语句

example

```python
# coding=utf-8

i = 0

while i * i < 1000
		i += 1

print("i = " + str(i))
print("i * i = " + str(i * i))
```

```python
# coding=utf-8

i = 0

while i * i < 10
		i += 1
		if i == 3
				break
		print(str(i) + ' *' + str(i) + ' =', i * i)
else:
		print('while over')
```

### 5.2.2 for 语句

syntax

```python
for var in 可迭代对象
		code-block-1
[else:
		code-block-2]
```

example

```python
# coding=utf-8

print('string')
for item in 'hello':
		print(item)

# 声明整数列表
numbers = [43, 32, 55, 74]
print('整数列表')
for item in numbers:
		print(item)

for item in range(10)
		print(item)
else:
		print('for over')
```

## 5.3 跳转语句

跳转语句能够改变程序的执行顺序, 包括`break`, `continue`和`return`

`return`仅适用于函数和方法

### 5.3.1 break 语句

无条件执行`break`是允许的, 但没有意义, 通常`break`都用在一个条件语句后, 用于循环语句中

满足条件之后就执行`break`, 即退出

### 5.3.2 continue 语句

`continue`和`break`的最大区别就是, `continue`是中止本次循环, 而`break`则是退出整个循环

example

```python
# coding=utf-8

for item in range(10)
		for item == 3
				break
		print(item)
# output 0, 1, 2

for item in range(10)
		for item == 3
				continue
		print(item)
# output 0, 1, 2, 4, 5, 6, 7, 8, 9
```

# Chapter 6 容器类型数据

容器的结构是不同的, 可装的物体也是不同的

主要包括以下几种数据类型: 序列, 列表, 元组, 集合和字典

## 6.1 序列

序列(sequence)是一种可迭代的, 元素有序的容器数据类型

第一个元素的编号是`0`, 最后一个元素的编号是`长度-1`

### 6.1.1 序列的索引操作

正值索引和负值索引

正值索引第一个元素是`0`, 最后一个元素是`长度-1`

负值索引第一个元素是`长度的负数`, 最后一个元素是`-1`

```python
hello
01234

 h  e  l  l  o
-5 -4 -3 -2 -1
```

example

```python
a = 'hello'
a[0] # h
a[-5] # h
a[4] # o
a[-1] # o
a[5] # IndexError
max(a) # o
min(a) # h
len(a) # 5
```

### 6.1.2 加和乘操作

加和乘可用于字符串的操作, 以达到重复和粘合的作用

example

```python
a = 'hello'
b = 'world'

a * 2 # hellohello
a + ', ' + b # hello, world
```

### 6.1.3 切片操作

切片运算符的语法形式为`[start:end:step]`

其中, start 是开始索引, end 是结束索引, step 是步长(切片时获取元素的间隔, 可以为正整数, 也可以为负整数)

不包括结束索引

正数是从左往右切

负数是从右往左切

example

```python
hello
01234

 h  e  l  l  o
-5 -4 -3 -2 -1

a = 'hello'

a[1:3] # 开始索引是1, 结束索引是3, 没有步长, 所以全取
# el
a[:3] # 省略了开始索引, 使用默认索引0, 所以等同于a[0:3]
# hel
a[0:] # 省略了结束索引, 实用默认序列长度5, 所以等同于a[0:5]
# 亦等同于a[:]
# hello
a[1:-1] # 正负索引混合实用
# ell
```

### 6.1.4 成员测试

Python 没有字符只有字符串类型

成员测试实用`in`语句, 返回 bool

example

```python
a = 'hello'
'e' in a
# return True
'E' in a
# return False
```

## 6.2 列表

学习容器类型数据需要注意其特点, 抓住特点就抓住了这个类型

列表是有序, 而且可变的序列类型, 重点是可变性

可以追加, 插入, 删除和替换列表中的元素

### 6.2.1 创建列表

创建列表

通过函数创建, list 就是列表的构造函数

`list(iterable)`

构造函数是创建类的实例的函数

创建之后就会有一个可迭代的对象

通过`[]`把列表中的元素都罗列出来

example

```python
list('hello')
[1, 2, 3, 4, 5]

# more example
[20, 10, 50, 30]
[] # empty list
['hello', 'world', 1, 2, 3]
a = [10]
b = [10,] # both are the same
list('hello')
# ['h', 'e', 'l', 'l', 'o']
```

### 6.2.2 追加元素

追加单个元素

`.append(element)`

追加多个元素

`+ list`

序列可使用加法和乘法运算

`.extend(list)`

example

```python
s = [20, 10, 50, 30]
s.append(80)
# [20, 10, 50, 30, 80]
t = [1, 2, 3]
s += t
# [20, 10, 50, 30, 1, 2, 3]
s.extend(t)
# [20, 10, 50, 30, 1, 2, 3]
```

### 6.2.3 插入元素

可以使用 insert(index, element)方法

example

```python
list = [20, 10, 50, 30]
list.insert(2, 80)
# [20, 10, 80, 50, 30]
```

### 6.2.4 替换元素

使用`list[index]`访问元素然后通过`=`赋值来替换元素

example

```python
list = [20, 10, 50, 30]
list[1] = 80
# list is [20, 80, 50, 30]
```

### 6.2.5 删除元素

使用`.remove(element)`方法

example

```python
list = [20, 80, 50, 30]
list.remove(80)
# [20, 50, 30]

list.append(80)
list.append(80)
list.remove(80)
# [20, 50, 30, 80]
```

## 6.3 元组 Tuple

元组是一种不可变的序列类型

类似序列, 元组也有两种方式来创建

`tuple(iterable)`函数

`(tuple1, tuple2 ...)`罗列的方法

example

```python
tuple([21, 32, 43, 45]) # 此处使用列表作为可迭代对象
(21, 32, 43, 45)
# more example
21, 32, 43, 45 # 创建元组时,使用罗列方法()可省略
('hello', 'world') # 创建字符串元组
('hello', 'world', 1, 2, 3) # 创建字符串和数字混合的元组
# 使用tuple实例方法创建元组
tuple('hello') # 获得('h', 'e', 'l', 'l', 'o')
tuple([21, 32, 43, 45])
t = 1, 2, 3
t = 1, # 表示创建只有一个元素的元组 (1,)
a = () # 创建空元组
```

### 6.3.2 元组拆包

元组的创建过程就等同于给数据打包

元组拆包的过程相当于是赋值给新的变量

example

```python
# 创建元组
tuple = 102, 'John'
# 拆包元组
t_id, t_name = (102, 'John')
t_id # 102
t_name # 'John'
```

## 6.4 集合

不同于 Java 中的集合, 更类似数学中的集合

特点是不能有重复元素, 所以不能通过索引来访问其中元素

集合是可迭代的, 无序的, 不能包含重复元素的容器类型的数据

### 6.4.1 创建集合

创建集合也有两个方法

`set(iterable)`函数

`{element1, element2 ...}`

不可以用`{}`语法来定义空集合

`{}`属于字典类型

example

```python
set('hello') # 'h', 'e', 'l', 'o'
{20, 15, 10, 30, 20, 15} # 20, 15, 10, 30
# 以上元素是无序的

# more example
s = {'John', 'Jane', 'Joe'}
s.add('Joy')
s # {'John', 'Jane', 'Joe', 'Joy'}
s.remove('Joe')
'Joe' in s # False
s.clear()
s # set() 空集合
```

### 6.4.2 修改集合

.add(element)添加元素, 如果元素已经存在, 则不能添加, 但不会抛出错误

.remove(element)删除元素, 如果元素不存在, 则会抛出错误

.clear()清除集合

## 6.5 字典

数据类型为 dict

字典是可迭代的, 通过键来访问元素的可变的容器类型的数据

键视图不能包括重复对象, 但值视图能

键视图中, 键和值是成对出现的

键其实是集合类型

有些语言中, 字典被成为映射(map)

### 6.5.1 创建字典

两种方式来创建字典

dict({dict})函数

{key1: value1, key2: value2 ...}

example

```python
dict({102: 'John', 105: 'Jane', 109: 'Joe'}) # 参数为另一个字典
# {102: 'John', 105: 'Jane', 109: 'Joe'}
dict(((10
```
