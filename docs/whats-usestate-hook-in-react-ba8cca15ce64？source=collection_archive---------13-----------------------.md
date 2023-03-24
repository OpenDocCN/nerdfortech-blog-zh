# React 中状态钩子有什么用

> 原文：<https://medium.com/nerd-for-tech/whats-usestate-hook-in-react-ba8cca15ce64?source=collection_archive---------13----------------------->

![](img/bebe05dc2588ebe46a682cfa8f7e7221.png)

你好，程序员们，在这篇文章中，我将解释网页设计中使用的新技术。作为一名 web 开发人员，如果您正在使用 react，这是您必须完成的任务。让我们从头开始……

> 你在 react 中使用过状态特性吗？

别担心。让我展示一个简单的例子，不使用任何特殊的东西。有时候你会很熟悉这段代码。这是为了让应用程序在单击相关按钮时增加和减少名为 count 的变量的值。

图一

在这个例子中，我使用 class base 使用状态来更改 count 的值。在这个方法中，我们使用基类组件。通常我们不得不在渲染和返回中使用 jsx 代码段。

> ***什么是钩子？***

钩子是 React 16.8 版本中引入的新特性。在 react 中，它允许在不使用类的情况下使用状态、效果和其他 react 特性。

钩子不是基类组件。它是一个基于功能的组件。当我们使用钩子时，有一些规则要遵守。

> *以后想看这个故事吗？* [*保存在日志中。*](https://usejournal.com/?utm_source=medium.com&utm_medium=noteworthy_blog&utm_campaign=tech&utm_content=guest_post_read_later_text)

01) ***只调用顶层的钩子***——不调用循环、条件或嵌套函数内的钩子。

02) ***只从 React 函数*** 调用钩子——不能从常规 JavaScript 函数调用钩子。相反，你可以从 React 函数组件调用钩子。

当我们学习 react 挂钩时，我们可以学习 useState、useEffect、UseRef，或者我们可以在 react 组件中构建自定义挂钩。在本文中，我只讨论 useState react 钩子。

> ***useState 钩子有什么用？***

钩子是一个特殊的函数，可以让你“钩入”React 特性。例如，useState 是一个钩子，它允许您向函数组件添加 React 状态。

为了让你更清楚，我用 react useState react hook 编写了上面的例子。

图二

让我们逐一比较这几段代码。然后你可以得到更多的澄清，以反应钩。

# **类** VS 功能

这是我在第一段代码中使用的基于类的 react 组件的一个例子(图 1)。

```
class App extends React.Component {render() {
      return (
         //you can code what would you return
)
}
}
```

正如我前面所说的，我们在 react 钩子中使用了基于函数的组件。像这样的函数基础组件。

```
function App() { return (
           //you can code what would you return
     )
}
```

# 声明状态变量

当我们在 react 中使用状态特性时，我们必须声明变量来存储状态。

在类组件中，我们必须通过在构造器中将 **this.state** 设置为 **{count:0}** 来声明 count 变量并存储 0。

```
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {     
     count: 0    
};  
}
```

然后我们可以比较一下函数库 react hook 组件和类库 react 组件的区别。在我们使用 **useState** 钩子之前，我们应该像这样导入 useState 依赖项。

```
import React, { useState } from 'react';

function Example() {
       [count, setCount] = useState(0);
}
```

# 为什么我们在 useState 函数中传递一个参数

它是变量当前值的初始值。如果我们像这样编码，

```
[count, setCount] = useState(0);
```

初始值为 0，(计数=0)。

另一个例子，

```
[name, setName] = useState("vickey");
```

它也是 name 变量的初始值。

“vickey”是名为 name 的变量的初始值。

# **为什么 count & setCount** 有两个变量

通常当我们调用 useState 函数时，它返回一对值*。*因此，我们为存储当前值(计数)和更新值(设置计数)声明两个变量。

# 更新状态

在基于类的组件中，这是更新变量值的方法(图一)。

```
count: this.state.count + 1,//it's like count=count + 1
```

接下来是如何使用 react hook 更新基于函数的组件中的值。

举个例子，如果我们想在计数上加 1。那么代码应该是这样的(图二)。

```
setCount(count + 1)
```

如果计数值的初始值是 0，那么在该代码段之后，计数值是 1。

另一个例子，

```
setName("john")
```

如果名字的初始值是“vickey”，那么在代码段之后，名字的值就是“john”。

为了实现完美和可读的编码，在我的示例中，我通过单独的函数**increment handler**和**increment handler**来减少和增加 count 变量的值。

我认为你对讨论的内容有更好的理解。

> 我们讨论过的帽子。

→在不使用任何特殊技术的情况下编写简单的 familer 示例。

→使用 react useState 挂钩开发相同的代码

→比较主义

React 中的类与函数

2)声明两个图的状态变量

3)使用使用状态初始化变量

4)使用钩子更新 react 中的变量

在我的下一篇博客中，我将讲述另一个叫做“useEffect”的 react 钩子。与我的博客保持联系。快乐记录……!！！！！

📝将这个故事保存在[日志](https://usejournal.com/?utm_source=medium.com&utm_medium=noteworthy_blog&utm_campaign=tech&utm_content=guest_post_read_later_text)中。