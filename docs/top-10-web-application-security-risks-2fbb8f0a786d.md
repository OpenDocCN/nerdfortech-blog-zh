# 十大 Web 应用程序安全风险

> 原文：<https://medium.com/nerd-for-tech/top-10-web-application-security-risks-2fbb8f0a786d?source=collection_archive---------6----------------------->

![](img/e42b53c6a256ba2f7b8040a0763b25b3.png)

[来源](https://owasp.org/www-project-top-ten/)

1.  **注入:**当不可信数据作为命令或查询的一部分被发送到解释器时，会出现注入缺陷，如 SQL、NoSQL、OS 和 LDAP 注入。攻击者的恶意数据可以欺骗解释器执行非预期的命令或在没有适当授权的情况下访问数据。
2.  **被破坏的认证:**与认证和会话管理相关的应用程序功能经常被错误地实现，使得攻击者能够泄露密码、密钥或会话令牌，或者利用其他实现缺陷来临时或永久地冒充其他用户的身份。
3.  **敏感数据暴露:**许多 web 应用程序和 API 不能很好地保护敏感数据，例如金融、医疗保健和 PII。攻击者可能窃取或修改这种保护薄弱的数据，以进行信用卡欺诈、身份盗窃或其他犯罪。敏感数据可能会在没有额外保护(如静态加密或传输加密)的情况下遭到破坏，并且在与浏览器交换时需要采取特殊的预防措施。
4.  **XML 外部实体:**许多旧的或配置不佳的 XML 处理器评估 XML 文档中的外部实体引用。外部实体可通过文件 URI 处理程序、内部文件共享、内部端口扫描、远程代码执行和拒绝服务攻击来泄露内部文件。
5.  **中断的访问控制:**对经过身份验证的用户所允许做的事情的限制经常没有得到适当的实施。攻击者可以利用这些缺陷来访问未经授权的功能和/或数据，例如访问其他用户的帐户、查看敏感文件、修改其他用户的数据、更改访问权限等。
6.  **安全错误配置:**安全错误配置是最常见的问题。这通常是由不安全的默认配置、不完整或临时配置、开放式云存储、错误配置的 HTTP 头以及包含敏感信息的详细错误消息造成的。不仅必须安全地配置所有操作系统、框架、库和应用程序，而且必须及时地对它们进行修补/升级。
7.  **跨站点脚本:**每当应用程序在没有适当验证或转义的情况下在新网页中包含不受信任的数据，或者使用可以创建 HTML 或 JavaScript 的浏览器 API 使用用户提供的数据更新现有网页时，就会出现 XSS 漏洞。XSS 允许攻击者在受害者的浏览器中执行脚本，从而劫持用户会话、篡改网站或将用户重定向到恶意网站。
8.  **不安全的反序列化:**经常导致远程代码执行。即使反序列化缺陷不会导致远程代码执行，它们也可用于执行攻击，包括重放攻击、注入攻击和权限提升攻击。
9.  **使用具有已知漏洞的组件:**组件，如库、框架和其他软件模块，以与应用程序相同的权限运行。如果易受攻击的组件被利用，这种攻击会导致严重的数据丢失或服务器接管。使用具有已知漏洞的组件的应用程序和 API 可能会破坏应用程序防御，并导致各种攻击和影响。
10.  **日志记录和监控不足:**加上与事件响应的集成缺失或无效，使得攻击者能够进一步攻击系统，保持持久性，转向更多系统，以及篡改、提取或破坏数据。大多数违规研究显示，检测违规的时间超过 200 天，通常是由外部方检测到的，而不是内部流程或监控。