# Cognyte 云数据泄露—50 亿条记录泄露

> 原文：<https://medium.com/nerd-for-tech/the-cognyte-cloud-data-breach-5-billion-records-leaked-86a7114cef06?source=collection_archive---------0----------------------->

![](img/c408c7e4217538bab34b70cf308ddcaa.png)

Cognyte 是一家网络安全数据分析公司，提供各种服务，包括他们的分析平台、网络和运营情报分析以及开源和威胁情报分析。(Cognyte，2022)确保组织的安全性变得越来越困难，随着组织向云的过渡，它增加了他们的攻击面，使他们更容易受到攻击。Cognyte 通过研究过去的数据泄露数据，为组织生成可操作的情报，以更好地防范威胁参与者。该公司成立于 1998 年，拥有约 2，100 名员工。其总部设在以色列，并在世界各地设有办事处。(克拉夫特，2022)

2021 年 5 月，Cognyte 遭遇了一次数据泄露。由于不安全的配置，包含 50 亿条用户记录的数据库被暴露。该数据库包含用于执行比较分析的数据。该分析使他们能够在面临第三方数据泄露时向客户发出警报。(Siyal，2022)包括姓名、电子邮件地址、密码和漏洞数据点在内的信息被泄露。数据泄露表明，网络安全公司也不能幸免于数据泄露。Cognyte 花了 3 天时间保护数据并重新配置数据库。由于缺乏认证或授权安全机制，该数据库对公共互联网开放。与之前的数据泄露相关的 20 多个高知名度客户数据集被曝光。暴露数据的 Cognyte 的一些知名客户包括 Tumbler、Myspace、Canva、Verification.io、MGM 和 Zoosk。(拉希德，2021 年)

Cognyte 利用第三方软件即服务(SaaS)来帮助他们进行名为 Elasticsearch 的数据分析。Elasticsearch 是一个强大的搜索和分析引擎，它使用数据节点来提高性能和稳定性，以帮助分析大型数据集。(Speiser，2022)众所周知，该服务很容易被错误配置，并且缺乏自动化来使服务在默认情况下更加安全。随着越来越多的数据添加到服务中以及集群数量的增加，配置过程会变得更加复杂，从而导致数据泄露。这种情况发生了，一个错误配置的数据库被公开了 4 天，直到一名安全研究员发现了这个公共数据库并将其报告给 Cognyte。(比肖夫，2021 年)

![](img/9509ee8c1147a77df316231cf53c2eef.png)

没有证据表明数据是在发现之前从 Elasticsearch 泄露的。面向公众的数据库可以很快被机器人和自动化机制发现。安全研究员利用蜜罐找到暴露的数据库，并很快找到了它。如果威胁参与者获得了访问数据的权限，他们将可以访问来自 20 个组织的数据集。这些数据来自以前的数据泄露，值得注意的是，这些数据以前已经暴露过。威胁参与者可能已经收集了这些数据，通过凭据填充、密码喷洒和网络钓鱼活动，根据薄弱点对这些组织发动更多攻击。这将使他们能够轻松访问已经清理和部分分析过的 50 亿个记录数据集。(Bischoff，2021)这些信息可以为威胁参与者提供手段，使其能够获得 20 多个组织的相关威胁情报。Elasticsearch 的控件支持权限，使认证的身份能够提交对另一个身份行为的访问控制。这意味着外部人员可以通过使用“Elasticsearch 的‘运行方式’机制在组织中‘许可链’渗透企业的云，并找到其他服务和数据”(Speiser，2022)。

薄弱的身份验证和授权控制允许威胁参与者通过侦察、枚举渗透到云中，并根据他们的发现创建可预测的角色名称列表。如果他们找到一个角色的匹配项，例如“data_admin”，并且在多个数据库中有一个匹配项，那么他们就可以访问跨不同集群或数据库与该所有者共享的所有数据。(Speiser，2022)幸运的是，Cognyte 很快发现并修复了错误配置。Elasticsearch 需要通过在默认情况下提高安全性来提高安全性，这表明即使是网络安全组织也可以改进他们的流程、程序和服务。

共享责任模型概述了在云环境中谁负责什么。它概述了如果发生什么事，谁应该负责。在 Cognyte 的数据泄露事件中，责任不能只归咎于一方。默认情况下，Elasticsearch 没有适当的机制和控制来使服务更加安全。错误配置集群的能力太容易了。

![](img/dda321499cd4b857998d4628d3a8f74a.png)

通常，在共享责任模型中，客户负责在云中配置他们的服务。云提供商应该提供适当的控制和安全机制，以确保服务的安全性。如果没有适当的身份验证和授权，例如启用了强密码和多因素身份验证(MFA ),就不应该允许公开数据库。用户，在本例中是 Cognyte，没有正确配置他们的数据库，并允许数据库公开可用。应该进行适当的测试和尽职调查，以确保数据库得到适当的保护。有人会说，根据共享合理性模型，Cognyte 应该承担责任，因为它错误地配置了 Elasticsearch 服务。我认为他们都有责任，双方都需要做出改进。在这种情况下，受到数据泄露公开影响的是 Cognyte，而不是 Elasticsearch。结果，Cognyte 的声誉受到了最大的负面影响以及其他后果。

由于几个原因，分担责任模式是一项艰巨的任务。每个云提供商，如亚马逊网络服务(AWS)或微软 Azure，都提供了一个概述云服务提供商(CSP)和客户责任的模型。所有云服务提供商的模式都相似，但可能略有不同。像 AWS 或 Azure 这样的大型组织发生数据相关事件的可能性比客户错误配置服务的可能性要小。大型云提供商要熟练得多，有足够的资金分配给安全性，而中小型公司没有资源和知识。每个云平台都有自己的默认配置，并不断发布新功能。通常很难区分每个云架构之间的细微差异，也很难培训人才来正确掌握必要的知识和技能。

![](img/ce1ef7b1bb5797e95c791b107c541c4f.png)

大多数组织都使用多云策略。根据 Flexera 的云状态报告，“80%的组织利用多个云平台，并保持事实上的标准”(Adler，2022)。在云环境中承担客户责任的能力越来越困难。据估计，到 2022 年，95%的云安全故障将是客户的过错。(CIS，2022)随着攻击媒介的扩大和威胁参与者变得更加复杂，客户在保护其云资源和基础架构方面面临着更多挑战。为了应对这些挑战，组织在其云决策中采用风险管理策略至关重要。

客户和电信运营商都有自己的责任，但有些责任往往不明确。物理安全是 CSP 责任的主要组成部分。仅该组件就需要大量资源、知识和经验来确保区域、可用性区域和边缘位置是可用的、可靠的和高效的。如果发生物理安全事故，AWS 和客户都会受到影响。如果客户遇到安全事故，对客户的影响很可能远远超过 CSP。我认为这种模式有利于供应商而不是消费者。Cognyte 的数据泄露事件表明，通信服务提供商提供的服务很容易被错误配置，而客户是受影响最大的一方。“在 VMware 的《2021 年云安全状况报告》中，六分之一的受访公司在过去一年中因配置不当而遭遇过云数据泄露”(Cozens，2022)。组织在将数据和服务迁移到云的过程中面临着各种变化。每个公司在部署云时都会面临的主要安全挑战是(Puzas，2022):

1.缺乏云安全和技能

2.身份和访问管理

3.跟踪它

4.云中的合规性

云资源的使用很容易不受管理，从而增加了他们的攻击面。云在不断变化，组织无法跟上已知的安全威胁，也无法为安全威胁和挑战做好准备。

我认为该模式中有可以改进的地方。提供商应该为其提供的服务提供更安全的默认配置。例如，如果没有适当的授权和认证机制，Elasticsearch 上的集群就不应该是可配置的。一个集群中的所有者不应该自动访问另一个集群中的所有数据。提供商应该提供更熟练的自动化安全工具来帮助消费者验证配置。例如，可以检查所有云存储，如 S3 存储桶、数据库、实例和用户帐户，以确保它们没有配置错误，并提供正确配置它们的指导。客户需要一种自主意识来创建和使用他们认为合适的云，但是提供商可以在其服务中改进他们的安全机制。电信运营商应该更多地关注通过自动化和安全的默认配置来限制人为错误的空间，而不是过多地关注新功能和服务。

客户从 CSP 的使用中获得了价值，但他们也失去了对数据的控制，并面临新的困难，因为他们的数据可能位于多个区域和可用性区域。创建应用程序、确保适当的访问控制、正确的数据加密和配置的细微差别应该是 CSP 的主要关注点，以便更好地帮助他们的客户，并确保不会发生 Cognyte 之类的数据泄露事件。如果一个简单的错误配置就能导致 50 亿条记录如此轻易地被泄露，CSP 应该承担部分责任。很难在控制和自治之间找到正确的平衡，但客户需要在获得 CSP 支持的同时进行适当的尽职调查，以确保云更加安全。

干杯！

**参考文献**

阿德勒，B. (2022，4 月 13 日)。*云计算趋势:2022 年云状况报告*。Flexera 博客。2022 年 11 月 20 日检索，来自[https://www . flexera . com/blog/cloud/cloud-computing-trends-2022-state-of-the-cloud-report/](https://www.flexera.com/blog/cloud/cloud-computing-trends-2022-state-of-the-cloud-report/)

比肖夫，P. (2021，6 月 14 日)。网络安全公司此前泄露的 50 亿条数据记录。Comparitech。检索于 2022 年 11 月 20 日，来自[https://www . comparitech . com/blog/information-security/breach-database-leak/](https://www.comparitech.com/blog/information-security/breach-database-leak/)

独联体(2021 年 2 月 22 日)。*云安全和共享责任模式*。互联网安全中心。2022 年 11 月 20 日检索，来自[https://www . cisecurity . org/insights/white-papers/cloud-security-and-the-shared-respons ibility-model](https://www.cisecurity.org/insights/white-papers/cloud-security-and-the-shared-responsibility-model)

考尼特考尼特。(2022 年 4 月 3 日)。*关于我们*。科尼特。检索于 2022 年 11 月 20 日，来自[https://www.cognyte.com/about/](https://www.cognyte.com/about/)

工艺(2022)。 *Cognyte (CGNT)股票价格、收入和财务——craft.co*。科尼特。检索于 2022 年 11 月 21 日，来自[https://craft.co/cognyte/metrics](https://craft.co/cognyte/metrics)

Cozens，B. (2022 年 6 月 9 日)。*云数据泄露:云存储安全的 4 大威胁*。Malwarebytes。2022 年 11 月 20 日检索，来自[https://www . malwarebytes . com/blog/business/2022/06/cloud-data-breakes-4-maximum-threats-to-cloud-storage-security](https://www.malwarebytes.com/blog/business/2022/06/cloud-data-breaches-4-biggest-threats-to-cloud-storage-security)

普扎斯，D. (2022，10 月 18 日)。 *12 云安全问题:风险、威胁&挑战:众筹*。crowdstrike.com。2022 年 11 月 20 日检索，来自[https://www . crowd strike . com/cyber security-101/cloud-security/cloud-security-risks-threats-challenges/](https://www.crowdstrike.com/cybersecurity-101/cloud-security/cloud-security-risks-threats-challenges/)

拉希德 h .，&艾哈迈德 D. (2021 年 6 月 20 日)。*网络安全公司曝光 50 亿条数据泄露记录*。黑客攻击。检索于 2022 年 11 月 20 日，来自[https://www . hack read . com/cyber security-firm-expose-data-breach-records/](https://www.hackread.com/cybersecurity-firm-expose-data-breach-records/)

Siyal，G. (2022 年 1 月 23 日)。*近年来排名前五的云安全数据泄露*。MUO。检索于 2022 年 11 月 20 日，来自[https://www . makeuseof . com/top-recent-cloud-security-breakes/](https://www.makeuseof.com/top-recent-cloud-security-breaches/)

斯佩瑟，K. (2022 年 6 月 1 日)。*漏洞数据库暴露 5B 记录*。桑莱。检索于 2022 年 11 月 20 日，来自[https://sonraisecurity . com/blog/leaky-database-exposes-5b-records/](https://sonraisecurity.com/blog/leaky-database-exposes-5b-records/)