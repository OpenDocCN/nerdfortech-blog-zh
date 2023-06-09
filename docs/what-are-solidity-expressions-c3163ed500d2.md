# 什么是坚固性表达？

> 原文：<https://medium.com/nerd-for-tech/what-are-solidity-expressions-c3163ed500d2?source=collection_archive---------7----------------------->

![](img/290ff212853c9a2a67f981a7f1522cc7.png)

# 介绍

编程语言在代码中有一个重要的决策方面。Solidity 提供 if…else，并根据情况切换语句以执行不同的指令。这太重要了，不能遍历多个项目。Solidity 提供了不同的结构，比如 for 循环和 while 语句。

# 坚实度表达式

包含多个操作数和可选的零个或多个运算符的语句称为表达式。产生单个值、对象或函数的结果。操作数可以是变量、文字、函数调用或其他表达式本身。
一个表达式的例子如下:
年龄> 10

在前面的代码中，Age 是一个变量，10 是一个整数。此外，年龄和 10 是操作数。( > )符号大于运算符。该表达式在前面的代码中返回。年龄是一个变量，10 是一个整数。年龄和 10 是操作数，大于符号( > )是运算符。该表达式返回一个布尔值。根据 Age 中存储的值，该值可能是真或假。表达式可能更复杂，包含多个操作数和运算符，如下所示:

((年龄> 10) &&(年龄< 20) ) || ((Age > 40) &&(年龄< 50) )
在前面的代码中有多个运算符在起作用。运算符& &充当两个表达式之间的 AND 运算符，这两个表达式又包含操作数和运算符。[两个复杂表达式之间还有一个由||运算符表示的 OR 运算符](https://www.technologiesinindustry4.com/)。取决于 Age 中存储的值的单个布尔值(真或假)。包含多个操作数和运算符的表达式可能会更复杂，如下所示:
((年龄> 10) & &(年龄< 20) ) ||((年龄> 40) & &(年龄< 50) )
在前面的代码中有多个运算符。运算符& &充当两个表达式之间的 AND 运算符，这两个表达式又包含操作数和运算符。两个复杂表达式之间还有一个由||运算符表示的 OR 运算符。

# if 决策控制

Solidity 在 if…else 指令的帮助下提供了有条件的代码执行。
if…else 的一般结构如下:

**if(该条件/表达式为真){
执行此处指令
}
else if(该条件/表达式为真){
执行此处指令
}
else {
执行此处指令
}**

if 和 if-else 是 Solidity 中的那些关键字，通知编译器它们包含一个决策控制条件，例如 if (a > 10)。在这里，它包含一个可以评估为真或假的条件。如果大于 10 的值为 true，则应该执行一对双括号({)和(})后面的代码指令。else 是一个关键字，如果前面的条件都不为真，它会给出一个替代路径。它也保留一个决策控制指令，并且如果 a > 10 趋于为真，则执行代码指令。以下示例描述了“IF”-“ELSE IF”-“ELSE”条件的使用。声明了具有多个常数的枚举。状态管理函数接受一个 uint8 参数，该参数被转换成一个 enum 常量，并在 if…else 决策控制结构中进行比较。如果值为 1，则返回结果为 1；如果参数包含 2 或 3 作为值，那么 else…如果一部分代码被执行；如果该值不是 1、2 或 3，则执行 else 部分。

# while 循环

我们需要根据条件重复执行一个代码段。坚固性精确地给出了 while 循环。while 循环的常见形式如下:
声明并初始化一个计数器，而我们要用表达式或条件检查计数器的值){执行这里的指令递增计数器的值}
while 是 Solidity 中的那个关键字，它通知编译器它包含一个决策控制指令。如果该表达式的计算结果为 true，则应该执行一对双括号{和}中的代码指令。while 循环将一直执行，直到条件变为假。在下面的示例中，映射与计数器一起声明。计数器有助于循环映射，因为在循环映射的可靠性方面没有现成的支持。只要理解我们在事件被调用时记录信息就足够了。SetNumber 函数将数据添加到映射中，get numbers 函数运行 while 循环来检索映射中的所有条目，并使用事件记录它们。临时变量用作计数器，每次执行 while 循环时递增 1。

更多详情请访问:[https://www . technologiesinindustry 4 . com/2021/01/what-are-solidity-expressions . html](https://www.technologiesinindustry4.com/2021/01/what-are-solidity-expressions.html)