# Web 开发的良方

> 原文：<https://medium.com/nerd-for-tech/cure-for-web-development-65003afb701f?source=collection_archive---------3----------------------->

![](img/e1df140f9c15b37c930de52fda630a3e.png)

我想你有一个小生意。你在你的实体店卖花。一切都很顺利，但你想吸引更多的顾客，并提供一些额外的服务-例如，将鲜花送到指定的地址。

所以你需要一个网站。只是一些基本的东西-一个主页，花卉目录，订单，也许是一个简单的聊天和博客。

你没有足够的钱聘请专业的开发人员。找不到合适的建站商。幸运的是，你对电脑有所了解，所以你决定自己创建网站。

地狱之门已经打开。

你不知道从哪里开始，但互联网知道一切。过了一会儿，你找到一些[复杂得离谱的图表](https://github.com/kamranahmedse/developer-roadmap)的必要知识。

然后折磨继续，但是你发现你至少需要学习这些事情:

*   超文本标记语言
*   半铸钢ˌ钢性铸铁(Cast Semi-Steel)
*   java 描述语言
*   JSON
*   饭桶
*   域名服务器(Domain Name Server)
*   超文本传送协议
*   休息
*   WebSockets
*   结构化查询语言
*   饼干/ JWT

…了解如何选择正确的语言、库、框架和主机。

你掉进兔子洞，然后分析麻痹开始。你应该使用:

*   Javascript 还是 Typescript？
*   自举还是顺风？
*   React 还是 Vue？
*   Mongo 还是 Postgre？
*   无服务器还是 VPS？
*   整体服务还是微观服务？
*   网袋还是包裹？
*   少还是顶嘴？
*   …

谁知道呢？没人。火焰战争在网络开发者中非常流行。

> 它是有效的，直到你尝试进行第一次主要的重构——你会感觉像是在穿越一个雷区。

当你看着大多数前端或后端框架，稍微眯起眼睛，你会看到一堆 HTML / CSS / JSON 操作和 HTTP 包装器的助手。

但是 HTML 和 CSS 不适合 web apps 怎么办？它们是很久以前为简单的网页设计的，由于向后兼容，基本上无法改进。结果，CSS 和 HTML 功能的数量不断增长，几乎没有人能够正确地使用它们。

然后将 HTML 与 CSS 和一种为编写简短脚本而设计的语言(如 Javascript)结合起来，编写一个 web 应用程序。它是有效的，直到你尝试进行第一次主要的重构——你会感觉像是在穿越一个雷区。你碰到的任何东西都可能在运行时爆炸。没有人有足够的勇气进入 CSS 雷区并删除旧的 CSS 代码。

所以也许有这么多的框架，因为他们做了太聪明的 HTML 操作，并希望尽可能地可组合、灵活和通用，但他们未能实现最重要的目标——使 web 开发更容易。

> 我可以想象许多开发者为一小部分用户祈祷

一整天的另一个乐趣是选择数据库和消除单点故障。基本上有两种流行的方法:

1.  在容器中使用一个数据库(理想情况下是一个托管集群)和一个或多个无状态应用程序。然后希望它不会成为一个随机数据库死锁的 DevOps 噩梦。
2.  使用无服务器功能和数据库，希望你不会冷启动，不会收到令人惊讶的发票，也不需要实时通信(例如 WebSockets 或服务器发送的事件)。

我可以想象许多开发人员会为少量用户祈祷，这样基础设施就不会像纸牌搭的房子一样倒塌，或者烧掉所有的钱。

这种疯狂有一种治疗方法:

*   一种静态类型的语言，没有像 *null* 、 *undefined* 或继承这样的脚注。快速务实。[锈](https://www.rust-lang.org/)。
*   一个前端框架，为页面元素(HTML 和 CSS 抽象)提供了良好的 API。它应该激励你写容易理解和搜索引擎优化的内容。你不应该需要处理底层的东西(比如通信协议)。
*   一个直接管理数据而不需要数据库的后端框架。它可以自动将多个服务器节点加入一个集群，并将它们作为一个大型服务器透明地使用。内置认证。
*   价格合理且可预测的托管/云。具有监控、日志记录、自动扩展和一个命令部署功能。

给大家介绍一下 Rust fullstack 框架: [**MoonZoon**](https://moonzoon.rs) 。

![](img/5c636b33fc4f25aeccf98d724f1e3ad9.png)

图像:

*   马库斯·斯皮斯克的[代码](https://unsplash.com/photos/MI9-PY5cyNs)
*   Kate Hliznitsova 的药丸