# 智能合同中的委托呼叫

> 原文：<https://medium.com/nerd-for-tech/delegate-call-in-smart-contract-431ba5caf576?source=collection_archive---------1----------------------->

![](img/d34725c75a0acc23a4d101c300a86079.png)

一些开发人员对“委托调用”这个术语持谨慎态度，因为它被描述为“危险的”恐惧和危险来自于对事物如何工作以及如何安全使用的知识的缺乏。例如，我们大多数人并不害怕开车，因为我们知道它是如何工作的，以及如何安全地驾驶。当一个契约使用委托调用来调用一个函数时，它从另一个契约加载并执行该函数代码，就好像它是自己的一样。

当通过委托调用执行函数时，这些值不会改变:

*   地址(这个)
*   msg.sender
*   消息值

使用委托调用加载和执行函数的协定执行对状态变量的读取和写入。持有检索到的函数的契约永远不会被读取或写入。

如果 ContractA 利用委托调用来调用 ContractB 中的函数，则以下两种说法是正确的:

*   ContractA 的状态变量可以读写。
*   ContractB 的状态变量从不被读取或写入。

ContractB 的函数可以读写 ContractA 和 ContractB 声明的状态变量的值。只有 ContractA 的状态变量被读取或写入。

> *delegatecall 影响使用 delegatecall 调用函数的契约的状态变量。持有被借用的函数的契约的状态变量不被读取或写入。*

# 例子

让我们看一个基本的例子。
合同方有以下内容:

*   address(this)= = 0x 2791 BCA 1 F2 de 4661 ed 88 a 30 c 99 a7a 9449 aa 84174
*   名为“字符串令牌名”的状态变量的值是“FunToken”
*   名为“initialise()”的外部方法，该方法使用 delegatecall 来调用 ContractB 的“settokenname(string calldata _ newName)”函数。

合同 b 包含以下条款:

*   地址(this)= = 0x6b 175474 e 89094 c 44 da 98 b 954 eedeac 495271d 0f
*   状态变量字符串“tokenName”的值是“BoringToken”
*   “setTokenName(string calldata _newName)”是一个外部函数，它将“TokenName”状态变量更新为“_ newName”值。

这是用 2 ETH 调用 ContractA 中的“初始化()”函数时发生的情况:

1.  这些值是这样设置的:

*   address(this)= = 0x 2791 BCA 1 F2 de 4661 ed 88 a 30 c 99 a7a 9449 aa 84174
*   msg . sender = = 0x ab 5801 a7 d 398351 b 8 be 11 c 439 e 05 C5 b 3259 AEC 9b
*   消息值== 2 ETH

2.使用委托调用,“initialise()”方法调用 ContractB 中的“setTokenName”函数。运行“setTokenName”时，将返回以下值。他们一点都没变。

*   address(this)= = 0x 2791 BCA 1 F2 de 4661 ed 88 a 30 c 99 a7a 9449 aa 84174
*   msg . sender = = 0x ab 5801 a7 d 398351 b 8 be 11 c 439 e 05 C5 b 3259 AEC 9b
*   消息值== 2 ETH

3.在 ContractA 中，字符串“tokenName”状态变量的值被更改。即使代码源自 ContractB，也不会在 ContractB 中更改。

Solidity addresses 有一个“委托调用”方法，允许您进行委托调用。此方法返回一个布尔状态变量，该变量指示函数调用是否被反转。委托调用函数返回第二个值，这是函数调用的返回值。请参见上面的示例代码。

# 如何安全地使用委托调用

既然您已经理解了委托调用是如何工作的，那么让我们来看看如何安全地使用它。

## 1.控制委托调用执行的内容

不受信任的代码不应该与委托调用一起运行，因为它可能会更改状态变量或调用“自毁”来破坏调用协定。可以使用权限、身份验证或其他类型的控制来指定或更改委托调用函数和契约。

## 2.仅呼叫有代码的地址上的委托呼叫

如果在不是约定的地址上调用 Delegatecall，因此没有代码，它将为状态值返回“True”。如果代码期望委托调用函数在不能运行时返回“False ”,这可能会导致错误。

如果您不确定当对某个地址变量进行委托调用时，该变量是否总是保留带有代码的地址，请在调用该变量之前检查该变量中的任何地址是否带有代码，如果没有，则进行恢复。以下是检查地址中代码的代码示例:

# 结论

因此，我们学习了智能契约中的委托调用，如何小心使用它，以及当我们使用用例时它如何为我们带来好处。

> *你可以在这里* *买一杯咖啡支持我和我的内容☕* [***。***](https://www.buymeacoffee.com/amanagarwal)
> 
> *关注我上*[***Twitter***](https://twitter.com/02amanag)*和*[***LinkedIn***](https://www.linkedin.com/in/02amanag/)*。*

# 了解更多信息

[](https://learn.block6.tech/oracle-blockchain-47b5ad917aa6) [## Oracle 区块链

### Oracle 区块链是什么？

学习. block6.tech](https://learn.block6.tech/oracle-blockchain-47b5ad917aa6) [](https://enlear.academy/off-chain-transaction-of-blockchain-7b9fa3f9b94a) [## 区块链的链外交易

### 什么是外链交易？

enlear .学院](https://enlear.academy/off-chain-transaction-of-blockchain-7b9fa3f9b94a) [](/geekculture/ethereum-v-s-hyperledger-f1b0c5e05b40) [## 以太坊虚拟分类帐

### Hyperledger 和以太坊是世界上使用最广泛的两个区块链平台。两者都是免费使用的。他们…

medium.com](/geekculture/ethereum-v-s-hyperledger-f1b0c5e05b40) 

> [Learn 发布的内容。Block6.tech](https://learn.block6.tech)
> 
> 👉[电报](https://t.me/block6_tech) —新鲜想法
> 
> 👉[推特](https://twitter.com/block6_tech) —最新文章
> 
> 👉 [LinkTr.ee](https://linktr.ee/block6)