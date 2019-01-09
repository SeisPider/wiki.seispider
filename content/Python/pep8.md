+++
date = "2017-08-02T16:24:01+08:00"
title = "pep8"
+++
[PEP8](https://www.python.org/dev/peps/pep-0008/)是Python官方给出的编程规范，用以指导Python代码写作。

# Pep8检查工具
[autopep8](https://pypi.python.org/pypi/autopep8)可用于检查代码中与PEP8不相符的部分，通过指定`-i`选项可直接修改源代码。

[pep8](https://pypi.python.org/pypi/pep8)仅用于检测与PEP8不相符的代码部分并输出检测报告。

[pyflakes](https://pypi.python.org/pypi/pyflakes/1.5.0)可检测Python源码中简单的语法错误。

[Pylint](https://www.pylint.org/)可同时检测Pep8的源码风格与语法错误。但对于一般小型脚本而言，检测标准过于严苛。

安装代码：
```
pip install -upgrade autopep8 pep8 pyflakes
```
```
sudo yum install pylint
```
# PEP8风格介绍
完整的风格介绍参见：

[PEP8--Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/)

[PEP8--编程规范中文指南](http://nanshu.wang/post/2015-07-04/)

本文仅记录较常错误的项。

## 续行缩进
悬挂缩进准则：第一行不应该包括参数，并且在续行中需要再缩进一级以便清楚表示。
正确范例：
```python
# 同开始分界符(左括号)对齐
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# 续行多缩进一级以同其他代码区别
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# 悬挂缩进需要多缩进一级
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)
```
错误的范例：
```python
# 采用垂直对齐时第一行不应该有参数
foo = long_function_name(var_one, var_two,
    var_three, var_four)

# 续行并没有被区分开，因此需要再缩进一级
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```
## 多行if语句
```python
# 不采用额外缩进
if (this_is_one_thing and
    that_is_another_thing):
    do_something()

# 增加一行注释，在编辑器中显示时能有所区分
# supporting syntax highlighting.
if (this_is_one_thing and
    that_is_another_thing):
    # Since both conditions are true, we can frobnicate.
    do_something()

# 在条件语句的续行增加一级缩进
if (this_is_one_thing
        and that_is_another_thing):
    do_something()
```
多行结束右圆/方/花括号可以单独一行书写，和上一行的缩进对齐：
```python
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )
```
也可以多行开始的第一个字符对齐：
```python
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```
## Imports
* Imports应该分行写，而不是都写在一行：
```python
# 分开写
import os
import sys
# 不要像下面一样写在一行
import sys, os
```
或者写为：
```
from subprocess import Popen, PIPE
```
* Imports应该写在代码文件的开头，位于模块注释和文档字符串之后，模块全局变量和常量声明之前。
Imports应该按照下面的顺序分组来写：
1. 标准库Imports
2. 相关第三方Imports
3. 本地应用/库的特定Imports

不同组的imports之前用空格隔开

* 推荐使用绝对(absolute)imports，因为这样通常更易读，在import系统没有正确配置（比如中的路径以sys.path结束）的情况下，也会有更好的表现（或者至少会给出错误信息）：
```
import mypkg.sibling
from mypkg import sibling
from mypkg.sibling import example
```
然而，除了绝对imports，显式的相对imports也是一种可以接受的替代方式。特别是当处理复杂的包布局(package layouts)时，采用绝对imports会显得啰嗦。
```
from . import sibling
from .sibling import example
```
* 当从一个包括类的模块中import一个类时，通常可以这样写
```
from myclass import MyClass
from foo.bar.yourclass import YourClass
```
如果和本地命名的拼写产生了冲突，应当直接import模块：
```
import myclass
import foo.bar.yourclass
```
然后使用”myclass.MyClass”和”foo.bar.yourclass.YourClass”.
