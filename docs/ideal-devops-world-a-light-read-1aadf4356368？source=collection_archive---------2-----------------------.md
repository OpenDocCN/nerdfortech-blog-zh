# 理想的德沃普斯世界——light🕯️解读

> 原文：<https://medium.com/nerd-for-tech/ideal-devops-world-a-light-read-1aadf4356368?source=collection_archive---------2----------------------->

![](img/04b42328a545cf41fa345a3c5792ed51.png)

Dev♾️Ops 生命周期

快速阅读以了解一些情况🔦DevOps 应该是什么样的？

🚫我不会引用**纸上的定义**📚。

# — DevOps❓

## 简而言之就是——“组织和自动化”。

DevOps 不是一种技术、工具或角色。
这是一种意识形态。💡这是一种练习。高效的做事方式。

> “编码、运行、拥有”

它试图淡化界限，减少工程垂直领域(即开发、测试、架构、支持、监控和基础设施)之间的摩擦。

> 它是关于统一端到端的软件生命周期，而无需移交。

DevOps 补充了敏捷哲学— **尽早测试，经常发布**。

# —神话🦄

*   DevOps 不负责应用程序测试，可能只负责平台和框架。
*   DevOps 不专门维护应用服务器，它不是质量、运营或 SR(站点可靠性)团队的更名。
*   DevOps 不是一个单独的团队或角色。当然，基线设置需要一个专门的**小队**，其 TO-DEV 比率非常小。

> “我们使用 Jenkins、Ansible 和 Terraform，我们是 devo PS——不，这还不够！!"

# **—连续工作流程🔄**

**DevOps** 整体上是将**➗**分成以下几个部分。

**>持续集成** ✅

我们需要有人从源代码中构建、版本代码、收集依赖项、运行单元测试并手工保存二进制文件吗？

💡:管道即代码，集成构建系统

🛠️: [GitHub](https://guides.github.com/activities/hello-world/) ( [视频](https://www.youtube.com/watch?v=hwP7WQkmECE))，[詹金斯](https://www.jenkins.io/doc/book/pipeline-as-code/)， [Maven](https://maven.apache.org/what-is-maven.html) ， [GitHub 动作](https://github.com/features/actions) ( [视频](https://www.youtube.com/watch?v=scEDHsr3APg))

**>连续交货**🚀

我们需要有人来创建机器，处理配置和安装您的产品吗？

💡:基础设施即代码(IAC)

🛠️: [Ansible](https://docs.ansible.com/) ， [Terraform](https://www.terraform.io/intro/index.html) ( [Video](https://www.youtube.com/watch?v=tomUWcQ0P3k) )， [Heroku](https://www.heroku.com/about) ， [EC2](https://aws.amazon.com/ec2/)

**t44】持续质量** ✨

谁有时间每次手动测试、检查代码中的重复错误？*这主要集成到 CI 渠道中。*

💡:自动化测试、质量关、测试覆盖

🛠️: [单元测试](https://www.youtube.com/watch?v=u6QfIXgjwGQ)，[集成测试](https://docs.spring.io/spring-framework/docs/current/reference/html/testing.html)，[硒](https://www.selenium.dev/documentation/)，[sonar cube](https://www.sonarqube.org/)， [Jacoco](https://www.eclemma.org/jacoco/)

**>连续监控**📈📉

我们是否需要有人全天候跟踪资源使用情况，提醒您观察数千台服务器，您认为您的日志记录会随着分散的云原生部署而扩展吗？

💡:系统监控、应用程序监控、集中日志记录

🛠️: [格拉夫纳](https://grafana.com/grafana/)、[麋鹿栈](https://www.elastic.co/what-is/elk-stack)、[普罗米修斯](https://prometheus.io/)、[弗鲁恩特](https://www.fluentd.org/architecture)

**>云基础设施** ☁️

我们需要在全球范围内购买、维护和扩展您的数据中心吗？备份、灾难恢复和扩展呢？

💡:按需购买的基础架构、无服务器计算、托管服务

🛠️: [AWS](https://aws.amazon.com/what-is-aws/) 、 [Azure](https://azuredevopslabs.com/) 、 [Google Cloud](https://cloud.google.com/devops)

**>云原生**🐳

为什么我们不把产品做成云原生的、运输环境而不是包，并且按需扩展呢？

💡:容器化、水平自动扩展微服务、负载平衡、容错、分散部署

🛠️: [Docker](https://docs.docker.com/get-started/overview/) ( [视频](https://www.youtube.com/watch?v=Gjnup-PuquQ))， [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) ( [视频](https://www.youtube.com/watch?v=PziYflu8cB8))

# —最后…🚩

DevOps 是**在组织内被稀释**的东西，它从未打算成为一个单独的团队或角色——消除孤岛，而不是作为电灯泡集中职责。

> “在理想的 devops 世界中，我们不能只让专家编写管道脚本——他们在这里研究、指导、培训和授权团队；
> 所有权属于我们——开发团队。”

S 对于工作流程而言，一切都是为了正确的目的使用正确的工具✅，✅，以正确的方式✅
—最终节省人力💪优化释放速度🌊，并节省资金💰为了公司。

> 感兴趣吗？查看我关于 CI 和 CD 的文章:
> [Maven 带 Github 动作和包— A **CI** 阅读](/nerd-for-tech/maven-with-github-actions-and-packages-a-ci-read-b968173b018f)
> [Java Spring on Heroku cloud 带 **CD**](/nerd-for-tech/spring-app-on-heroku-cloud-with-continuous-deployment-328ff8fbfe7a)