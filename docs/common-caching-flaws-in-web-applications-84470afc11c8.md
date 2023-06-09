# web 应用程序中常见的缓存缺陷。

> 原文：<https://medium.com/nerd-for-tech/common-caching-flaws-in-web-applications-84470afc11c8?source=collection_archive---------7----------------------->

web 应用程序中的缓存策略对于性能提高和许多其他事情来说确实是一种非常有用的机制，但是如果没有经过衡量或深思熟虑，也可能是非常有害的。

这听起来可能有点傻，你可能会问，鸭子在缓存时怎么可能出错呢？但事实是，缓存操作被 web 开发人员低估了，因为它通常用于网站资产、样式和一堆图像。

但是缓存可能会导致敏感数据暴露在世人面前，并可能因谷歌黑客查询或被网络蜘蛛跟踪而被访问。这些错误可能发生在缓存普通 HTTP 响应、信用卡数字、密码和其他任何敏感信息时。

本讲座的目的是简要介绍几个错误应用缓存的案例，这不是实际操作，而是如何避免常见情况的概述。

## URL 中的敏感数据

让我们从最常见的一个开始，即在 URL 中传递敏感数据，问题是可以在 URL 中发送数据的开发人员没有意识到安全问题，这对安全不利，因为可以在多个地方公开，但如果应用加密，这可能是一件好事。

这样做的问题是，URL 中的敏感数据可能会在服务器日志或浏览历史中泄露。一个愚蠢的问题是当密码通过`GET`请求发送时，如果以纯文本格式发送就更愚蠢了。

另一个奇怪的情况是，当密码重置过程正在进行中，您收到一个 URL，在该 URL 中为该特定用户提供了一个静态令牌，如果聪明的黑客检测到该模式，可以轻松模仿密码重置 URL 并更改您的访问凭据。

所以，请不要在 URL 中发送敏感数据，如果需要，使用`POST`方法(POST 参数)。

## HTML 数据缓存

让我们想象一下，你正在从一个电子商务网站购物，你在一个结账页面前，没有使用 HTTPS 加密。

它可以出现在 HTML 元素中，而不是在 URL 中发送数据，因此，经常会发现对用户以 HTML 形式输入的敏感数据进行不安全的处理。

不要误解我的意思，在某种程度上使用 HTTPS 是可以的，也是安全的，但是在缓存的时候，事情可以有所不同。

一个好的实践是在敏感的表单元素中实现`autocomplete=off` HTML 属性，使用`POST`请求，当然还有加密。

## HTTPS

有时加密并不是你真正安全的答案。HTTPS 是一种用于保护 web 和客户端之间通信的协议，它保证机密性、完整性和身份验证。

如果你没看错，我写的是:通信。

请再次假设我们在一个完全 HTTPS 加密的网站中，敏感数据也通过 HTTPS 返回，并且您成功地缓存了请求，但是(总是但是)，当使用像`Cache-Control`或`Pragma`这样的 HTTPS 报头时，就像反缓存报头一样。如果您的响应头没有实现它们，您可以缓存该响应，并且您的密码可以以纯文本的形式出现。

是的，我们有安全的通信，但是缓存的密码可能是纯文本的，当然，这对安全性不好。

这可以通过避免在 HTTPS 响应中发送敏感数据，并在响应头中实现`cache-control: no-store`和`pragma: no-cache`来解决。

## 谷歌呢？

谷歌引擎的主要任务是缓存和收集来自互联网的数据，通过收集我们是一个目标，而且不仅仅是一个人，而是数十亿人。

谷歌的索引活动都是为了找到互联网上的一切，敏感数据也从索引和缓存。攻击者可以执行 Google hacking 请求，以便找到某些模式，这些模式可以导致可能的攻击载体的敏感数据。

简而言之，谷歌缓存会导致敏感数据的泄露。

如何在 Google 中查找数据？仅仅通过使用谷歌呆子。检查[该](https://www.exploit-db.com/google-hacking-database)列表。

这里有三个例子:

1.  去 google.com，直接输入类似`reset.php?token=`的东西
2.  像这样使用`site:`dork:`site:example.com`它将查找特定于列出的域的所有内容。
3.  一种“高级”的方法是使用 extend dork functionality:`site:example.com inurl:token`，这将评估 URL 结构中是否存在任何从特定站点缓存的令牌。

你可以通过控制 google 缓存的数据来解决这个问题，你可以用`noindex,nofollow`指令添加一个`robots.txt`文件，或者使用`<meta name="robots" content="noindex,nofollow">`标签来避免 Google 缓存那个特定的站点

# 对此能得出什么结论？

安全反措施可能非常简单，但却非常有害，您需要认真对待安全问题，实施简明的软件架构、设计和威胁建模。检查您的身份验证和会话方法。此外，在需要时执行错误处理和日志记录，并设置数据保护机制，因为缓存问题就在那里。

您可以随时在您的站点上执行笔测试，或者适应任何安全标准，即使在缓存的情况下也能实现真正的保护。

快乐编码:)