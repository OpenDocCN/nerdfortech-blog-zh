# 实现 React 路由器背后的理念

> 原文：<https://medium.com/nerd-for-tech/implementing-the-ideas-behind-react-router-390b5f99307c?source=collection_archive---------11----------------------->

![](img/bbc7d773b9936fd18c68e7dfc2e427b7.png)

【https://unsplash.com/photos/1SAnrIxw5OY 

我正在建立我的 Next.js 网站。然后我偶然发现了这个简单的特性，由于忽略了组件生命周期的一个基本原则，我花了比预期更长的时间来实现它。我想在页面上创建路线之间的渐变过渡，但这让我陷入了兔子洞。稍微思考了一下谷歌，我还没有找到任何一个关于这一切是如何工作的深入解释，所以我决定跟进我自己的解释。

让我们从探索我们正在构建的东西开始。为了缩小这个练习的范围，我决定将`create-react-app`和`tailwindcss`以及我们信任的朋友[代码沙箱](https://codesandbox.io)一起使用。

我们正在构建的小玩具应用程序

既然我们已经想通了，让我们开始一步一步地做这个，并解释大致的想法。

如果您想跟进，您所要做的就是用 React 模板创建一个新的 CodeSandbox 项目，并通过 CDN 添加 Tailwinds。

(只需转到左边的外部资源部分，添加这个网址`https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css`)

**注意，在原型项目之外不建议这样做**

# 制作标记

让我们做一些标记！我们需要一个左侧导航栏和一些占位符内容来呈现。我们将通过创建两个额外的组件作为页面来实现这一点。

初始加价

注意，现在我们只是硬编码了`<Home />`组件。

接下来，我们想想办法将组件“切换”到正确的位置，这意味着我们需要**一个状态**来跟踪用户当前所在的 URL，并需要一个方法**在用户点击其中一个链接时更新状态**。

给定我们当前的标记，放置这种状态的唯一逻辑位置应该是在 App 组件内部，但是我们想更进一步！我们希望与路线相关的州与 VDOM 的其他州共享。

我们不知道用户会把他的导航放在哪里，或者他会在哪里改变它，我们需要这样的分散化。幸运的是，这种状态共享有一个 React 特性，那就是[上下文 API](https://reactjs.org/docs/context.html) 。

最终结果看起来会像这样:

上下文的示例

# 背景

为了定义上下文，我们需要一个`Provider` 和一个`Consumer` ，当然，还有上下文要传递的对象。

路由器上下文

我们还为这个上下文提供了默认值，主要是路线，并指出`push`将是一个函数。

现在，我们需要一个组件，它将**向上下文提供状态**，负责实际处理“路由”逻辑。让我们制作一个组件，并用它需要的正确值初始化它。

路由处理逻辑

需要注意的是，这必须**包装在**我们的应用程序中，并将路由状态提供给应用程序的其余部分。最后，我们需要创建一个组件，该组件将根据哪个路由是活动的来注入组件。

这里最有趣的一点是，我们还需要利用`useEffect` hook，以便在我们更改路由后让浏览器更新 URL **。**

动态显示子组件

简单地说，我们传递给它一个“路线”数组，并使用`||`操作符，我们计算出我们需要动态呈现哪个组件。

# 让我们回顾一下

以下是我们目前的情况:

简单看一下到目前为止的代码

到目前为止，我们已经创建了一个功能路由器的所有必要结构，现在我们只需将所有部分连接在一起。

值得注意的是，在这一点上，我们有一个部分工作的例子。如果您转到浏览器开发工具并手动切换`setState` 钩子的值，您可以看到页面呈现了适当的组件。

# 家政

在我们继续之前，我们需要做一些整理工作来保持代码库的整洁。
首先，注意`useContext` 函数是如何通过暴露上下文来泄露内部实现细节的。我们不需要这样做，我们应该用自定义的钩子把它包起来！这样，我们将有一个干净的 API 与外界进行交互。此外，我们应该将所有与路由器相关的功能从 App.js 模块中移出，放到一个单独的模块中。

接下来，让我们将所有的功能移到一个单独的`router/index.js`模块中，以保持代码的整洁。

经过一些内务路由器/索引. js

# 点击路线

让我们来测试一下！为了点击路由，我们需要在实际链接上设置事件监听器，并让它们实际导航。我们可以通过利用我们编写的`useRouter`钩子和一个简单的`onClick`事件监听器来做到这一点。

工作路线

请记住，我们必须在上下文中的某个地方声明`useRouter`**，否则它将无法工作。因为在内部它依赖于上下文。这正是我们将按钮移到`<Navigation>`组件内部的原因。**

就是这样！我们有一个全功能的小应用程序，它有**工作** **路线**。

# 临时演员

到目前为止，我认为 API **已经完成**。然而，我们可以改善一些位，因为它们只是生活质量的改善，我已经决定把它放在这里，所以请随意阅读结论。

React 路由器提供的一个东西是导航用的更优秀的 API，我们的实现只有**一个** **低级 API。为了让用户体验更干净，我们应该创建自己的`<Link>`组件，它应该自动处理点击逻辑，我们应该只提供一个`href`和一个子组件，要么是`<a>`，要么是`<button>`。**

```
<Link href='/some/path/1'>
  <a>My Link</a>
</Link>
```

另一件事，我们应该提供的是一种方式来设计**活动链接。最简单的方法是为一个活动类提供一个道具。**

链接组件

这里最独特的代码是`React.cloneElement`，我们在这里使用它是因为我们想要动态地读取**和修改**链接组件的子组件，并对它们应用一个事件监听器。代码与我们的 click listener 几乎相同，除了现在**它被封装在`<Link>`组件中**。

最后，我们应该为我们的`<RouterView>`处理**未找到**的情况

# 最后

非常感谢你能走到这一步！这是一次不可思议的经历，希望你能像我一样在这个过程中学到一些东西！

*免责声明:我认为* [*React 路由器*](https://reactrouter.com/) *是一个很棒的库，你应该经常使用它！问题是，大多数博客都专注于探索现有的 API 并解释它们，我想探索它们是如何在内部工作的，而不是实际使用它们。*