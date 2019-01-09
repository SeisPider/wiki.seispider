+++
title = "Fundamental Python"
date = "2017-08-02T16:24:01+08:00"
+++

# 迭代和解析
## 列表嵌套循环
```python
[ expression for target1 in iterables [if condition1]
             for target2 in iterables [if condition2]
             for target3 in iterables [if condition3]
             ......]
```
例如:
```python
>>> [(x, y, z) for x in range(4) if x % 2 ==0
           for y in range(4，9) if z % 2 ==0
           for z in range(9，11) if z % 2 ==0]
[(0, 4, 10), (0, 6, 10), (0, 8, 10), (2, 4, 10), (2, 6, 10), (2, 8, 10)]
```
## 列表解析和map
以下三种方式均能获得myfile中字符并去除`'\n'`
```python
>>>[line.rstrip() for line in open('myfile').readlines()]
['aaa', 'bbb', 'ccc']
>>>[line.rstrip() for line in open('myfile')]
['aaa', 'bbb', 'ccc']
>>>list(map(lambda line: line.strip()), open('myfile'))
['aaa', 'bbb', 'ccc']
```
## 生成器
生成器表达式就与列表解析的表达式类似
```python
>>>G = (x ** 2 for x in range(4))
<generator object <genexpr> at 0x7fd3836308c0>
>>>next(G)
0
>>>next(G)
1
>>>next(G)
4
>>>next(G)
9
>>>next(G)
StopIteration                             Traceback (most recent call last)
<ipython-input-11-380e167d6934> in <module>()
----> 1 next(G)

StopIteration:
```
则列表解析即像一次性生成所有的迭代结果
```python
>>>[x ** 2 for x in range(4)]
[0, 1, 4, 9]
```
## Python 3.0解析语法概括
* 对于集合，新的常量形式{1, 3, 2}等同于set([1, 3, 2]),并且新的集合解析语法{f(x) for x in S if P(x)}就像是生成器表达式set(f(x) for x in S if P(x))，其中f(x)是任意表达式。
* 对于字典，新的字典解析语法{key, val for (key,val) in zip(keys, vals)}
像dict(zip(keys, vals))形式一样工作，并且{x:f(x) for x in items}像生成器表达式dict((x,f(x)) for x in items)

# 函数与类
## 函数变量
### 关键字参数和默认参数的混合:
```python
def func(spam, eggs, toast=0, ham=0):
  print ((spam, eggs, toast, ham))
func(1, 2) # output: (1,2,0,0)
func(1, ham=1, eggs=0) # output: (1, 0, 0, 1)
func(toast=1, eggs=2, spam=3) # output: (3, 2, 1, 0)
func(1, 2, 3, 4)  # output: (1, 2, 3, 4)
```
* 关键字参数调用时，参数排列的位置并没有关系

### 收集参数
\* 在函数定义中，在元组中收集不匹配的位置参数
```python
def f(*args): print(args)
```
调用该函数时，Python将所有位置参数收集在新的元组中，并将这个元组赋予变量args。因它时一个一般的元组对象，能够索引或在一个for循环中进行步进。
```python
f() # output:()
f(1) # o: (1,)
f(1,2,3,4) # o: (1,2,3,4)
```
\** 特性类似，但是只对关键字参数有效，将这些关键字参数传递给一个新的字典，这个字典将能够通过一般的字典工具进行处理。
```python
def f(**args): print (args)
f(a=2, b=2) # out={'a'=2, 'b'=2}
```
