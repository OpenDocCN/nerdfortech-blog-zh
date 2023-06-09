# 公开 Twitter 源代码有什么(或没有)安全风险？

> 原文：<https://medium.com/nerd-for-tech/what-are-the-security-risks-or-not-of-making-twitter-source-code-public-471ef434e15c?source=collection_archive---------4----------------------->

![](img/66427d6842d09bf0ae94bd7b35486a9f.png)

如今，在谈论特斯拉和 SpaceX 首席执行官、Twitter 未来主人、世界首富埃隆·马斯克(Elon Musk)时，很难说“抛开政治”，也很难严肃起来。

但说真的，除了对马斯克即将收购 Twitter 可能产生的政治影响的无休止的雪崩式评论之外，技术专家之间还在进行一些相当激烈的无党派讨论，讨论他对更大透明度的承诺是否会导致一些意想不到的安全风险，无论是对平台还是对用户。

具体来说，马斯克表示，为了增加透明度和信任，他打算公开 Twitter 内容监管算法的源代码。

这导致了一些声明，马斯克正在使 Twitter 成为一个开源平台。但这不会真正改变什么，因为它已经改变了，就像世界上的每个企业一样。

如今，每个行业都是软件行业，开源软件几乎出现在[他们的每一个代码库中](https://www.synopsys.com/software-integrity/resources/analyst-reports/open-source-security-risk-analysis.html?cmp=pr-sig&utm_medium=referral)。它也构成了这些代码库的绝大部分(将近 80%)。

云安全联盟的首席区块链官和特别项目主任 Kurt Seifried 指出，“你不能编写一个 web 服务器/客户端，你必须使用开源的。它们现在太复杂了，无法在内部构建。这适用于大多数软件。”

事实上，Twitter 本身[宣称](https://opensource.twitter.dev/)它“从一开始就建立在开源的基础上。开放是我们 DNA 的一部分。”

**打开信号源**

“开放”的另一种方式是马斯克公开其源代码的意图。

如果他这样做，看起来这将符合美国民主党参议员罗恩·怀登(俄勒冈州)和科里·布克(新泽西州)以及美国众议员伊薇特·克拉克(纽约州)在 2 月份提出的一项名为[2022 年算法问责法案](https://www.wyden.senate.gov/imo/media/doc/Algorithmic%20Accountability%20Act%20of%202022%20Bill%20Text.pdf)的法案，一份[怀登新闻稿](https://www.wyden.senate.gov/news/press-releases/wyden-booker-and-clarke-introduce-algorithmic-accountability-act-of-2022-to-require-new-transparency-and-accountability-for-automated-decision-systems#:~:text=Y.%2C%20today%20introduced%20the%20Algorithmic,every%20aspect%20of%20Americans'%20lives.)称，该法案将“为软件、算法和其他自动化系统带来新的透明度和监督，这些系统用于对美国人生活的几乎每个方面做出关键决策。"

但多位专家指出，对我们所有好人来说透明也意味着对坏人来说透明——那些想要利用代码中的弱点或出于恶意目的创建自己的修改版本的人。

开源软件不比私有或商业软件更安全，但它的无处不在使它成为一个非常大的、有吸引力的攻击面。事实上，2021 年 12 月公开的流行开源 Apache 日志库 [Log4j](https://www.synopsys.com/blogs/software-security/mitigating-impact-of-log4j-log4shell/?cmp=pr-sig&utm_medium=referral) 中的漏洞存在于数亿到数十亿个系统、服务、网站和设备中。

安全公司 ExtraHop 的高级技术经理 Jamie Moles[告诉 TechCrunch](https://techcrunch.com/2022/04/26/elon-musk-twitter-privacy/)Log4j 展示了“广泛使用的开源应用程序的价值是指数级的。将代码开源可能会增加 Twitter 用户的透明度，但也可能使 Twitter 成为攻击者更大的目标。”

Synopsys 网络安全研究中心的首席安全策略师 Tim Mackey 引用了另一个可能的、不受欢迎的结果。他说，如果源代码公开，它“为代码的分叉或分支创造了机会，从而将 Twitter 客户端从单一来源变为可从多个渠道获得。”

为了避免使用错误的应用程序，麦基说:“维护员工应用程序商店的 IT 部门应该确保员工只使用来自 Twitter 的 Twitter 移动客户端，并通过 Twitter 发布的认证。”

剑桥大学的博士后研究员 Jennifer Cobbe[告诉《技术评论》](https://www.technologyreview.com/2022/04/27/1051472/the-problems-with-elon-musks-plan-to-open-source-the-twitter-algorithm/)说，公开源代码的风险大于任何透明的好处，她同意其他人的观点，即让所有人都可以访问源代码将包括寻找漏洞的恶意黑客的访问。

英国德蒙特福特大学(De Montfort University)网络安全教授埃克·博伊滕(Eerke Boiten)表示，开源 Twitter 的算法可能会帮助坏人更好地利用系统，这可能会使马斯克的其他既定目标之一“击败所有垃圾邮件机器人”变得更加困难。

**更大的目标？**

当然，与任何主要的社交媒体平台一样，Twitter 自流行以来一直是网络犯罪分子的目标。哔哔声电脑[报道称，就在上周](https://www.bleepingcomputer.com/news/security/new-phishing-warns-your-verified-twitter-account-may-be-at-risk/)“哔哔声电脑的许多记者已经成为钓鱼邮件的目标，这些邮件伪装成来自 Twitter 认证的账户平台。”

如果帐户持有人被骗输入他们的凭据，这些帐户可能会被用来促进诈骗。该杂志指出，去年网络犯罪分子利用受损的 Twitter 账户推广一种假的加密货币赠品，据称来自马斯克，这使他们在一周内净赚了超过 58 万美元。

Lightstream Managed Services 副总裁兼首席战略官拉斐尔·洛斯(Rafal Los)表示，如果犯罪分子或敌对国家能够入侵该平台，并接管像美国总统这样的政治领导人的账户，那将是一个更大的危险。“想想如果总统的账户发出‘我们明天入侵俄罗斯’或类似的消息，会发生什么，”他说。“这可能会引起混乱。”

但他也认为，如果源代码公开，坏人利用算法的风险是值得的。“旨在保护我们的法律是透明和公开的，”他说。“当然，人们会找到创造性的方法来颠覆法律的精神，同时在技术上不违反它。但如果我们赖以生存的法律不透明，我们都不确定我们是如何被治理的，以及被什么规则治理的。”

“不确定性造成了偏执，滋生了你无法证明或反驳的阴谋论，”他补充道。“这造成了分裂，并最终将社会带入黑暗的境地。”

塞弗里德进一步指出，在 Twitter 上操纵系统并不新鲜。“他们(用户)已经在玩游戏了，”他说。“你不需要访问源代码就能知道源代码是做什么的。你可以做黑盒测试，输入信息，观察输出，就像人们做谷歌搜索引擎优化一样。”

他也没有看到修改代码的人“冒名顶替”推特的大风险。“我可以给你所有的 Twitter 源代码，”他说。“你打算如何大规模运营它？你从哪里找到有能力的人？就算有，怎么让几亿人转过去？”

Los 说，已经有“许多克隆或重做该平台的尝试——都悲惨地失败了，因为 Twitter 的采用是如此广泛和狂热。开源代码增加了这种可能性——我们这里说的是整个代码库——但我认为这不太可能。将算法公开和开源更有可能，也是一个好主意。”