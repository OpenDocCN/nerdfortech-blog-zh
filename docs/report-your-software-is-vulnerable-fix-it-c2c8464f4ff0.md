# 报告:您的软件易受攻击。修好它！

> 原文：<https://medium.com/nerd-for-tech/report-your-software-is-vulnerable-fix-it-c2c8464f4ff0?source=collection_archive---------4----------------------->

![](img/f71a05f1161c45be025e147ae02d1058.png)

软件不完美不是什么新闻——毕竟它是由不完美的人制造的。

但是，数百万行代码中的缺陷数量，它们是什么种类，它们在哪里，以及它们可能造成多大的损害，都是不那么明显的细节。

因此，为了提供更多关于软件漏洞的细节和背景，新思网络安全研究中心(CyRC)的安全顾问分析了 2020 年对大约 2600 个商业网络和移动应用程序进行的 3900 多次测试的匿名数据。

他们的发现发表在最近一份名为[“2021 年软件漏洞快照”](https://www.synopsys.com/software-integrity/resources/analyst-reports/software-vulnerability-trends.html?intcmp=sig-blog-SVS1?cmp=pr-sig&utm_medium=referral)的报告中，既有启发性又有不祥之兆。几乎所有的目标应用程序(97%)都有漏洞。近三分之一(30%)存在高风险漏洞，6%存在严重风险漏洞。

“很明显，仍然存在各种各样的软件弱点，从简单的实施和配置错误到更基本的系统设计缺陷，”Synopsys CyRC 的高级首席顾问 Aravind Venkataraman 说。

事实上，将这样的统计数据应用到汽车等物理世界的产品上——想象一下道路上超过三分之一的汽车的安全带、安全气囊、刹车或大灯出现故障——你就会感受到问题的规模和严重性。

**诱人的攻击面**

可以预见，这些漏洞对犯罪黑客来说是一个有吸引力的攻击面。有时他们可以在伦理世界发现他们之前利用软件缺陷。或者，更常见的是，他们利用已知的缺陷和可用的补丁，但他们的攻击成功了，因为成千上万的用户没有跟踪他们正在使用的软件的所有组件，因此不知道他们需要修补什么。

信用报告巨头 Equifax2017 年的违规事件是该问题最臭名昭著的例子之一。该公司未能修补 Apache Struts(一种流行的开源 web 应用程序框架)中的一个已知漏洞，尽管该修补程序已经发布了几个月。这次入侵泄露了超过 1.43 亿人的重要个人数据。

因此，虽然软件是数字世界的一部分，但企业及其客户在现实世界中依赖于它。十多年来，专家们一直在说，每家公司都是软件公司——它要么构建软件，要么用软件来运营业务。

正如该报告所言，“软件驱动着大多数工资单、账单、应收账款、销售跟踪和客户记录的管理系统。软件控制生产，管理库存，指导仓储，并运行分销系统这也是“大多数企业与客户互动和支持客户的主要方式。”

换句话说，软件的质量和安全性对组织有着生存性的影响。不安全的软件是一种商业风险。正如 CyRC 团队发现的那样，那里有很多风险。

CyRC 分析的几乎所有测试——所谓的“不透明盒子”或“半不透明盒子”测试——都是为了模拟真实世界的攻击。测试包括[渗透测试](https://www.synopsys.com/software-integrity/application-security-testing-services/penetration-testing.html?cmp=pr-sig&utm_medium=referral)、[动态应用安全测试](https://www.synopsys.com/software-integrity/application-security-testing-services/dynamic-analysis-dast.html?cmp=pr-sig&utm_medium=referral)、[移动应用安全分析](https://www.synopsys.com/software-integrity/application-security-testing-services/mobile-application-security-testing.html?cmp=pr-sig&utm_medium=referral)。不透明模拟来自外部黑客的攻击，而半不透明旨在显示具有凭证的经过身份验证的用户可以做什么。

测试覆盖了一系列行业，包括软件和互联网、金融服务、商业服务、制造、媒体和娱乐以及医疗保健。

最常见的高风险漏洞是跨站脚本(XSS)，在 28%的应用程序中发现。这是一种将恶意脚本注入可信网站的攻击。

开放网络应用安全项目(OWASP)在对 XSS 的[描述中称，目标用户的浏览器“无法知道该脚本不应该被信任，并将执行该脚本。”这使得恶意脚本(以及黑客)能够访问“浏览器保留并用于该站点的 cookies、会话令牌或其他敏感信息”](https://owasp.org/www-community/attacks/xss/)

OWASP 因维护 web 应用程序漏洞的前 10 名列表而闻名——这是今年早些时候更新的[列表。CyRC 报告更重要的发现之一是，更新列表中的漏洞在 76%的目标中被发现。](https://armerding.medium.com/owasps-new-top-10-help-for-securing-your-web-applications-856bdd7a1217)

应用程序和服务器错误配置在 OWASP 列表中排名第五，占测试中发现的全部漏洞的 21%。在发现的所有漏洞中，有 19%与列表中排名第一的漏洞(破坏访问控制)有关。

其他报告重点包括:

*   不安全的数据存储和通信漏洞困扰着大多数(80%)移动应用程序。这些漏洞可能允许攻击者以物理方式(即访问被盗设备)或通过恶意软件获得对移动设备的访问权。超过一半(53%)的移动测试发现了与不安全通信相关的漏洞。
*   甚至风险较低的漏洞也可能被利用来促进攻击。发现的漏洞中有 64%被认为是最低、低或中等风险，这意味着它们不会被攻击者直接利用来获得对系统或敏感数据的访问权限。尽管如此，它们仍可能被利用来进行攻击。例如，在 49%的测试中发现的详细服务器横幅提供了诸如服务器名称、类型和版本号等信息，这可能允许攻击者对特定的技术堆栈进行有针对性的攻击。

面对这种情况，消息并不都是暗淡的。越来越意识到风险的许多公司正在努力提高他们的软件安全性。然而，这变得更加困难，因为网络安全人才的需求和供应之间存在巨大差距。

据网络安全风险投资公司(Cybersecurity Ventures)称，目前世界上网络安全职位的空缺数量超过 350 万——比芝加哥的人口还多近 100 万。据估计，美国网络安全职位的空缺数量[接近 60 万。](https://www.cyberseek.org/heatmap.html)

值得称赞的是，当企业没有内部资源来加强应用程序安全测试时，他们越来越多地转向第三方提供商。但是无论谁来做安全测试，都必须有针对性和有效性，不能拖软件开发人员的后腿。

**全套工具**

该报告提出了几项建议。

首先，单一的安全工具是不够的。寻找软件中的漏洞“需要多种评估技术，如[半透明]测试、静态分析、成分分析、设计评审等。在持续的基础上应用于你的软件库存，”文卡塔拉曼说。

[静态应用安全测试](https://www.synopsys.com/software-integrity/security-testing/static-analysis-sast.html?cmp=pr-sig&utm_medium=referral)有助于在编写代码时发现代码缺陷，但在运行时则不然。那需要[动态](https://www.synopsys.com/software-integrity/application-security-testing-services/dynamic-analysis-dast.html?cmp=pr-sig&utm_medium=referral)和[互动](https://www.synopsys.com/software-integrity/security-testing/interactive-application-security-testing.html?cmp=pr-sig&utm_medium=referral)安全测试。还应该强制使用[软件组成分析，](https://www.synopsys.com/software-integrity/security-testing/software-composition-analysis.html?cmp=pr-sig&utm_medium=referral)一种可以帮助发现已知漏洞和潜在许可冲突的测试工具。

但是如果配置不当，多种工具可能会成为问题而不是解决方案。正在构建软件的组织需要为他们的开发人员提供一个自动化的工具系统，不会因为太多的发现——其中许多都是琐碎的——而减慢他们的速度，以至于他们变成了白噪音的等价物，开发人员会将他们拒之门外。

最新的自动化工具是[应用安全协调和关联](https://www.synopsys.com/glossary/what-is-application-security-orchestration-and-correlation.html?cmp=pr-sig&utm_medium=referral) (ASOC)，尽管它已经存在好几年了。它不仅可以配置为在正确的时间进行正确的测试(协调部分)，ASOC 还可以消除重复，根据组织设置的优先级按严重性汇总结果，并跟踪它们是否已得到修复。

第二，鉴于软件开发的速度，自动化测试工具是必不可少的，在某些情况下，人必须直接参与。

Synopsys 的产品管理经理 Debrup Ghosh 表示:“从报告中，我们清楚地看到，尽管应用安全专业人员多年来一直专注于跨站点脚本，但在超过 28%的测试中发现它是一个高风险漏洞。“这证明，即使许多开发团队可能已经进行了自动化应用程序安全测试，让人工智能补充自动化测试以获得风险的整体视图也是至关重要的。”

手动和自动测试的结合使得该报告鼓励使用“全方位的安全工具”

最后，如果你不创建和维护一个准确的、最新的[软件材料清单](https://www.synopsys.com/blogs/software-security/software-bill-of-materials-bom/)，你就是在自找麻烦，比如，跟踪你正在使用的所有东西。几十年来，专家们一直在说，你不能保护你不知道自己拥有的东西。你所拥有的可能比表面上看起来要复杂得多。

事实上，今天所有的应用程序都是由专有的、商业的和开源的软件组件组合而成的。这些组件可以依赖于其他组件或库，这些组件或库可以深入到多个级别，并且可以添加数百甚至数千个依赖项。

如果一个或多个你不知道的依赖项有漏洞，即使有补丁，你也不太可能去应用。这将使您成为下一个版本的 Equifax。

CyRC 团队在 18%的渗透测试中发现了易受攻击的第三方库。这意味着您的组织有五分之一的机会依赖其中一个。

所以要积极主动。假设您的软件易受攻击，因为它确实如此。测试它，跟踪它，并修复它。那你可以相信它。