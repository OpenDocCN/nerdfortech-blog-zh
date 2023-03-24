# Python 迭代器和可迭代对象

> 原文：<https://medium.com/nerd-for-tech/python-iterators-and-iterables-904abf5518e7?source=collection_archive---------1----------------------->

## 对它们是什么、它们如何工作以及我们如何使用它们的分析。

![](img/e17a4ff28698b23c0f0a4f98e43a4e3b.png)

无限阶梯[https://www.flickr.com/photos/gadl/288607676/](https://www.flickr.com/photos/gadl/288607676/)

# 介绍

一个 Python [迭代器](https://docs.python.org/3.9/glossary.html#term-iterator)被定义为

> *代表数据流的对象。*

简而言之，迭代器是一个可以迭代的对象，这意味着我们可以一个接一个地访问元素，直到一个元素都不剩。

例如，列表是使用循环访问的数据的顺序集合。

```
my_list = ['a','b','c']
for letter in my_list:
  print(letter)
```

我们可以循环的对象被定义为可迭代的。迭代器和 **Iterables** 是两个主要的 Python 概念，有时会产生混淆，因为它们是严格相关的。

这里，我们将分析 Python 迭代器和可迭代对象的定义

**定义**:iterable 是一个我们可以迭代的对象。

**定义**:迭代器是可以被迭代的对象。换句话说，一个允许我们迭代一个*可迭代*对象的对象。

这两个定义听起来可能有点混乱，所以我将解释细节，以便有一个清晰的画面。

从技术角度来看，Python 将**迭代器**定义为实现**迭代器协议**的对象，该协议由两个方法组成:

**__next__** :返回容器的**下一个**项。

**__iter__** :返回**迭代器**本身。

> 重复调用迭代器的 __next__()方法(或将其传递给内置函数 next())会返回流中的连续项。
> 
> 当没有更多的数据可用时，将引发 StopIteration 异常。
> 
> 此时，迭代器对象被耗尽，对它的 __next__()方法的任何进一步调用只是再次引发 StopIteration。

**__next__()** 方法返回数据流中的**个连续项。**

重复调用 **__next__()** 最终会在没有更多可用数据时引发 StopIteration 异常**。**

此时，数据序列被耗尽，对 **__next__()** 的任何进一步调用都会再次引发 **StopIteration** 异常。

# Python 内置的可迭代表

在 Python 中，有**内置的 Iterables** 数据结构，例如

*   列表
*   元组
*   用线串
*   字典

根据定义，一个**可迭代的**是一个我们可以迭代的对象。

我们使用 ***for — in*** 键迭代一个 Iterable。

让我们试着去理解它们是如何工作的，如何在元素间循环。

```
list_of_numbers = [1,2,3,4]
my_tuple = ('first','second','third')
my_str = 'hello world'

for i in list_of_numbers:
    print(i)

#Output
#1
#2
#3
#4

for i in my_tuple:
    print(i)

#Output
#first
#second
#third

for i in my_str:
    print(i)

#Output
#h
#e
#l
#l
#o

#w
#o
#r
#l
#d
```

让我们更深入地看看**可迭代列表**，使用 [**dir** 函数](https://docs.python.org/3/library/functions.html#dir)来显示我们的 *list_of_numbers* 中的所有方法和属性

```
dir(list_of_numbers)
['__add__', '__class__', '__contains__', '__delattr__', '__delitem__', 
'__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', 
'__getitem__', '__gt__', '__hash__', '__iadd__', '__imul__', '__init__', 
'__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', 
'__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__',
 '__rmul__', '__setattr__', '__setitem__', '__sizeof__', '__str__', 
 '__subclasshook__', 'append', 'clear', 'copy', 'count', 'extend', 
 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
```

我们看到，其中有一个 **__iter__()** 方法，用于迭代*list _ of _ numbers*的元素。我们可以通过做来看看它

```
list_of_numbers.__iter__()
<list_iterator object at 0x7fc9700cc220>
```

我们可以通过添加实现 **__iter__()** 方法的对象是**可迭代的**来丰富我们之前的定义，因为我们可以在 od 上循环。

这同样适用于*我的元组*和*我的字符串*

```
dir(my_tuple)
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', 
'__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', 
'__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', 
'__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', 
'__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmul__', 
'__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'count', 'index']dir(my_str)
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', 
'__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', 
'__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', 
'__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', 
'__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', 
'__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 
'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 
'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 
'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 
'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 
'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 
'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 
'upper', 'zfill']
```

但是 **__next__()** 方法在 *my_str* 、 *my_tuple* 和 *list_of_numbers* 中没有实现。因此，根据我们的定义，我们不处理**迭代器**。

```
list_of_numbers.__next__()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'list' object has no attribute '__next__'
>>> next(list_of_numbers)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'list' object is not an iterator
```

正如我们所看到的，list 对象不是迭代器，因为它没有实现**迭代器协议，**，稍后我们将了解原因。

然而，我们可以从我们所知道的开始，在这里施展一些魔法:

list_of_number 有 **__iter__()** 方法，我们可以遍历所有的元素。

```
elem = list_of_numbers.__iter__()
```

**__iter__()** 方法返回一个**迭代器**对象，我们知道一个 Python 迭代器实现了 **__next__()** 方法

```
elem
<list_iterator object at 0x106a36880>
type(elem)
<class 'list_iterator'>
```

因此，如果 *elem* 是一个 Python 迭代器，我们可以使用 **__next()__** 方法，直到 **StopIteration** 异常被引发。

```
elem.__next__()
1
elem.__next__()
2
elem.__next__()
3
elem.__next__()
4
elem.__next__()
Traceback (most recent call last):
  File "<input>", line 1, in <module>
StopIteration
```

一分钱一分货！**迭代器协议**得到验证。

需要记住的重要一点是，由于**没有返回**，**的方法，我们只能用迭代器前进。**

没有办法访问前面的元素，重置迭代器的唯一方法是创建一个新的迭代器，我稍后会展示。

当然，我们通常不会以这种方式使用迭代器，但是它让我们看到了事物内部是如何工作的。

# Iterables 和迭代器有什么区别？

让我们快速回顾一下到目前为止我们所学的内容。

我们已经看到**迭代器**和**迭代器**可以是不同的对象，即使它们并不总是或必须如此。

我们已经知道，如果一个对象实现了 **__iter__()** 和 **__next__()** 方法，就可以定义迭代器。

我们已经验证了列表实现了 **__iter__()** 方法，列表可以定义为 Iterables，但是我们已经证明了列表不是迭代器。

```
next(list_of_numbers)
Traceback (most recent call last):
  File "<input>", line 1, in <module>
TypeError: 'list' object is not an iterator

next(my_tuple)
Traceback (most recent call last):
  File "<input>", line 1, in <module>
TypeError: 'tuple' object is not an iterator
next(my_str)
Traceback (most recent call last):
  File "<input>", line 1, in <module>
TypeError: 'str' object is not an iterator
```

所以，*列表*，*元组*，*字符串*是**可迭代**但是**本身不是迭代器**，但是我们已经看到了如何使 *list_of_numbers* 成为**迭代器**。

**迭代器**和**迭代器**的概念是分开的，因为**迭代器**跟踪元素的内部位置。毕竟，**迭代器**需要维护下一个**返回哪个元素的信息。**

理解这一点很重要

> 如果 Iterables 要维护一个状态，我们一次只能使用一个循环。否则，其他循环会干扰第一个循环产生的状态。
> 
> 迭代器没有这个限制，我们总是可以返回一个新的迭代器对象。

Python **迭代器也是一个可迭代**对象，**但不是每个可迭代对象都是迭代器**。

我们已经知道列表是一个**可迭代**对象，而不是一个**迭代器**。

# 我们如何使用迭代器

以下是使用迭代器的一些最常见的方法

## 带有字符串和列表的 for 循环中的迭代器

```
my_str = 'I like Python'
for letter in my_str:
  print(letter)

my_list = list(my_str)
for letter in my_list:
print(letter)

#Outout 
I

l
i
k
e

P
y
t
h
o
```

## 列表理解中的迭代器

```
[letter for letter in my_list]
['I', ' ', 'l', 'i', 'k', 'e', ' ', 'P', 'y', 't', 'h', 'o', 'n']
```

## 具有字典键和值的迭代器

```
my_dict = {"brand": "motoguzzi","model":"850T5","year":1987}
>>> for key in my_dict:
...     print(key)
... 
brand
model
yearfor key in my_dict.keys():
...     print(key)
... 
brand
model
yearfor val in my_dict.values():
...     print(val)
... 
motoguzzi
850T5
```

## 带上下文管理器的迭代器

我们可以使用上下文管理器轻松地访问和打印文件的内容，因为[*open()*](https://docs.python.org/3/library/functions.html#open)*函数返回一个 **Iterable** 对象*

```
*with open('my_bikes.txt') as bikes:
   for bike in bikes:
      print(bike)*
```

# *iter 内置函数*

*Python 有一个内置的 iter()函数来获取迭代器，还有一个 [**next()** 函数](https://docs.python.org/3/library/functions.html#next)来遍历它的元素。*

***迭代器**可以使用 [**iter()** 内置函数](https://docs.python.org/3/library/functions.html#iter)从序列中轻松创建。*

*我们已经知道 **Iterable** 是一个我们迭代的对象，当传递给**ITER()**函数时，它会生成一个迭代器。*

*🔖可以通过使用[函数 iter()](https://docs.python.org/3/library/functions.html#iter) 从 iterable 创建迭代器。*

*在这个目录下，对象的类需要一个方法 **__iter__** ，它返回一个迭代器，或者一个 **__getitem__** 方法，其顺序索引从 0 开始。*

```
*my_iterator = iter(list_of_numbers)
type(my_iterator)
<class 'list_iterator'>
while my_iterator:
    print(next(my_iterator))

2
3
4
Traceback (most recent call last):
  File "<input>", line 2, in <module>
StopIteration*
```

***iter()** 与调用 **__iter__()** 相同*

***next()** 与调用 **__next__()** 相同*

*让我们看另一个例子。语法现在应该很熟悉了，*

```
*>>> x = iter(["motoguzzi","ferrari","maserati"])
>>> print(next(x))
motoguzzi
>>> print(next(x))
ferrari
>>> print(next(x))
maserati
>>> print(next(x))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
>>>*
```

*当没有更多的项目要处理时，我们看到一个 **StopIteration** 异常被引发。*

*我们不得不说还有一些特殊类型的 **Iterables** ，叫做生成器，我们稍后会看到。*

# *如何构建我们的迭代器*

*一种简单的方法是把迭代器看成一个包含数据的对象。我们已经看到一个对象必须实现 **__iter__()** 和 **__next__()** 方法。*

***__next__()** 方法是产生数据的方法。*

*重要提示:只要定义了 **__iter__()** ，就不必定义 **__next__()** 。*

***__iter_()** 方法返回迭代器对象本身。所以每个**迭代器**也是一个**可迭代的**并且可以在大多数接受其他可迭代的地方使用。*

*让我们构建我们的迭代器，一个计算斐波那契数列的自定义类。*

```
*class FibonacciIterator:
        def __init__(self, max: int):
        self.max = max
        self.a = 0
        self.b = 1
        self.counter = self.a

    def __iter__(self):
        """
        This method returns the iterator itself

        :return:
        """

        return self

    def __next__(self):
        """
        This method returns the next element.

        :return:
        """

        if self.counter > self.max:
            raise StopIteration
        else:
            self.a, self.b = self.b, self.a + self.b
            self.counter = self.a
            return self.counter

series = FibonacciIterator(20)
for num in series:
  print(num)
else:
  print("stop")*
```

*当我们运行它时，我们得到*

```
*1
1
2
3
5
8
13
21
stop*
```

*这里重要的一点是，当我们打印 stop 时，StopIteration 异常被抛出，所以我们的迭代器被耗尽了。*

*如果我们运行它两次，我们将看到没有更多的元素可用。*

```
*for num in series:
        print(num)
    else:
        print("stop")
    for num in series:
        print(num)
    else:
        print("stop")*
```

*我们看到在第一站被打印后，没有更多的条目需要迭代。*

```
*1
1
2
3
5
8
13
21
stop
stop*
```

*这是因为迭代器保持状态。**迭代器需要维护下一个返回哪个元素的信息。***

*如果我们想要一个**迭代器，它永远不会耗尽它的条目**，我们可以在需要的时候启动它。*

```
*for _ in range(10):
        fibonacci_series = [print(num) for num in FibonacciIterator(20)]*
```

*在这种情况下，我们在每个循环中初始化迭代器。*

*另一种实现方式是重构我们的迭代器**，将迭代状态和迭代器对象**分开。让我们看看我们是否能做到，为什么它会有帮助。*

*首先，需要提到的是， **__iter__()** 还可以返回实现 **__next__()** 方法的另一个类的新实例，这意味着我们可以拥有一个只实现 **__iter__()** 方法的类，并在单独的类中定义 **__next__()** 方法。*

> *迭代器必须有一个 __iter__()方法返回迭代器对象本身，所以每个迭代器也是可迭代的，并且可能用在大多数接受其他可迭代的地方。*

*单独的类也可以是迭代器。在这种情况下，我们将迭代器传递给实现迭代器的类，然后接受迭代器。*

*让我们通过添加 *DotheMath* 迭代器类来重构我们最初的例子。*

```
*class DoTheMath:
    def __init__(self, max: int):
        self.max = max
        self.a = 0
        self.b = 1
        self.counter = self.a

    def __next__(self):
        """
        This method returns the next element.

        :return:
        """

        if self.counter > self.max:
            raise StopIteration
        else:
            self.a, self.b = self.b, self.a + self.b
            self.counter = self.a
            return self.counter

class FibonacciIterator:
    def __init__(self, max: int):
        self.max = max

    def __iter__(self):
        """
        This method returns the iterator itself

        :return:
        """

        return DoTheMath(self.max)*
```

*我们可以运行它，看看迭代器永远不会耗尽。*

```
*series = FibonacciIterator(20)
for num in series:
  print(num)
else:
  print("stop")
for num in series:
  print(num)
else:
  print("stop")

1
1
2
3
5
8
13
21
stop
1
1
2
3
5
8
13
21
stop*
```

*或者*

```
*series = FibonacciIterator(20)

for _ in range(10):
  fibonacci_series = [print(num) for num in series]*
```

*我们现在有了一个可重用的迭代器，因为**我们已经分离了迭代状态和迭代器对象**。我们将确保我们的迭代器不会耗尽。*

*我们可以用最初的 FibonacciIterator 类实现同样的行为。*

```
*run_this = iter([num for num in FibonacciIterator(10)])*
```

***iter()** 和调用我们的类 FibonacciIterator 的 **__iter__()** 方法是一样的。*

***next()** 与调用我们的类 FibonacciIterator 的 **__next__()** 方法相同。*

# *结论*

*迭代器是一个可以被迭代的对象，这意味着我们可以一个接一个地访问元素，直到没有元素留下。当没有更多的元素要访问时，会引发 StopIteration 异常。
我们用来迭代的工具是 *for-in* 。所以迭代器和循环是兼容的。
每个实现迭代器协议的对象都可以被视为迭代器。另一件值得一提的事情是迭代器在资源方面也很有效，因为一次只处理一个元素。这就是为什么提供无限元素序列的迭代器永远不会耗尽它的内存分配。
可迭代对象是我们可以迭代的对象。我们使用 *for-in* 来迭代一个 iterable。
一个**迭代器**是一个**可迭代**，但并不是所有的**可迭代**都是**迭代器**。我们已经看到了 list 是如何实现 **__iter__()** 方法却没有实现 **__next__()** 。要理解的重要一点是迭代器维护状态，这意味着它们知道下一个要返回的元素(如果有的话)的位置。Iterables 不保持状态，这很好，因为如果 Iterables 要保持状态，我们一次只能使用一个循环。否则，其他循环会干扰第一个循环产生的状态。
另一方面，迭代器没有这个限制，但是我们可以返回一个新的迭代器对象，创建永远不迭代的迭代器。*