# 我是如何从对 Spring Boot 一无所知开始用 Java 开发微服务编排服务的

> 原文：<https://medium.com/nerd-for-tech/how-i-developed-a-microservice-orchestrating-service-in-java-starting-from-zero-knowledge-of-spring-a7cea7f23547?source=collection_archive---------0----------------------->

作为对一家公司评估的一部分，我收到了一份类似这样的问题陈述

![](img/0cd28bdce85221920d04fb5680e837ca.png)

我收到的评估问题陈述

在此之前，我知道 Spring Boot 可以用于快速开发后端服务，但我从未参与过任何涉及它的项目。在与我的一些同行就 Spring Boot 进行了一些咨询和讨论，并阅读了关于如何使用 Spring Boot 开发生产就绪服务器的资料后，我开始征服 Spring 的世界来构建我的 API。

一周之后，经过大量疯狂的谷歌搜索，我的(几乎)生产就绪的 API 看起来不错，可以展示了。Spring 上丰富的可用资源被证明是一件好事也是一件坏事，考虑到一个人可能面临的几乎每一个错误都已经在 [stackoverflow](http://stackoverflow.com) (或一篇博客文章)上得到回答，但是由于所涉及的多种依赖关系的不断变化的版本，一个人必然会面临过多的选择来进行实验。这篇文章是我如何开发我的编排微服务的指南，以及我在这个过程中收集的所有链接和资源。我希望有一天它能对某个地方的人有所帮助。

**第一部分——学习春天的基本知识**

当我意识到我必须使用 Spring Boot 的时候，我就开始寻找一门课程，通过这门课程我可以理解 Spring 的全部功能。这里涉及到相当多复杂的概念，比如控制反转和依赖注入，如果你不理解的话，它们看起来很复杂，但是一旦你理解了，生活就会变得容易得多。我在 Udemy 上看到了这个课程来了解春天的基本知识-

[](https://www.udemy.com/course/spring-hibernate-tutorial) [## 学习 Hibernate 和 Spring(作为初学者)教程

### UDEMY 上最畅销的 1 门春季冬眠课程-超过 47，000 条评论- 5 颗星！

www.udemy.com](https://www.udemy.com/course/spring-hibernate-tutorial) 

这是一门很棒的课程，我肯定会推荐它来理解 Spring，并很好地实践所涉及的各种概念。参加这个课程有助于我了解谁将对象“自动连接”到我的类中:)

**第 2 部分——识别实体并弄清楚我的服务的架构和控制流**

我可以假设我有某些下游服务来验证我的支付方法，从数据库中获取产品价格，等等，所以我不需要实现任何这样的 DAO 层(或者我从需求中假设)。因此，基本需求可以归结为“开发一个微服务，以弹性和可伸缩的方式调用其他微服务来下订单”

我仔细考虑了我的用例需要什么样的实体，然后我想出了这些-

![](img/1dad425c0c30429f3571b7e71bd6a69c.png)

订单管理服务的实体

![](img/be3032798bae4b16fed9cd807bb725a6.png)

订单管理应用程序概览

我需要我的 Rest 控制器监听某些路由，并且我必须根据请求将请求重新路由到相应的服务。

第 3 部分-弄脏我的手-编码！

这些是我的 API 的样子

获取产品价格-Product get Product price(int Product id)

下订单-订单下单(订单)

首先，我创建了两个 Rest 控制器——分别用于产品和订单请求。我分别在 GET 和 POST 上创建了映射路由的方法(因为我的 API 分别用于获取和发布数据)。

然后，我创建了获取产品价格和下订单的服务。下订单的服务也调用了支付服务。因此，我的服务本质上是在产品价格服务、订单服务和支付服务之间进行协调。在每一个服务中，我都需要一个 REST API 来为相应的服务提供实际的下游服务。我在 Spring 中使用 RestTemplate 完成了这个任务。有关使用 RestTemplate 的更多信息，请访问以下链接

[](https://www.baeldung.com/rest-template) [## RestTemplate | Baeldung 指南

### 在本教程中，我们将举例说明 Spring REST 客户端- RestTemplate …

www.baeldung.com](https://www.baeldung.com/rest-template) [](https://www.tutorialspoint.com/spring_boot/spring_boot_rest_template.htm) [## Spring Boot 休息模板

### Rest 模板用于创建使用 RESTful Web 服务的应用程序。您可以使用 exchange()方法来…

www.tutorialspoint.com](https://www.tutorialspoint.com/spring_boot/spring_boot_rest_template.htm) 

一旦我的端到端基本流程完成，我就决定通过验证输入、以优雅的方式处理下游服务的故障等，使我的编排服务更有弹性。

为了验证输入，我在 Spring 中使用 javax 验证来确保我的 productID 不为空，我订单中的产品不为空，支付细节不为空，等等。如果您使用的对象有另一个需要验证的对象，请确保使用嵌套验证。

你可以在这里查看更多关于如何在 Spring 中验证任何成员变量的信息

[](https://www.baeldung.com/spring-boot-bean-validation) [## 在 Spring Boot 验证| Baeldung

### 当涉及到验证用户输入时，Spring Boot 为这一常见而关键的任务提供了强有力的支持…

www.baeldung.com](https://www.baeldung.com/spring-boot-bean-validation) [](https://www.baeldung.com/spring-validate-requestparam-pathvariable) [## 在 Spring | Baeldung 中验证 RequestParams 和 PathVariables

### 在本教程中，我们将看看如何在 Spring MVC 中验证 HTTP 请求参数和路径变量…

www.baeldung.com](https://www.baeldung.com/spring-validate-requestparam-pathvariable) 

如果我的下游服务出现任何故障，我希望向客户机返回一个通用的响应(INTERNAL_SERVER_ERROR)，而不是描述任何细节。为此，我在 Spring 中使用了控制器建议异常处理。控制器抛出的任何异常都会在这里被捕获，并返回适当的响应。为此，我还创建了自定义错误响应和自定义异常。

关于使用控制器建议创建和处理自定义异常的更多信息，请参见以下链接-

[](https://www.javatpoint.com/restful-web-services-404-not-found) [## 实现异常处理- 404 找不到资源-Java point

### 在上一节中，我们已经在创建资源时返回了正确的响应状态 CREATED。在这个…

www.javatpoint.com](https://www.javatpoint.com/restful-web-services-404-not-found) [](https://www.baeldung.com/global-error-handler-in-a-spring-rest-api) [## REST API | Baeldung 的自定义错误消息处理

### 在本教程中，我们将讨论如何为 Spring REST API 实现一个全局错误处理程序。我们将使用…

www.baeldung.com](https://www.baeldung.com/global-error-handler-in-a-spring-rest-api) 

**第 4 部分-测试**

由于实际下游端点不可用，我无法测试我的编排服务的端到端工作，因此我必须编写大量的单元测试，以确保我覆盖了特定功能的所有可能结果。我使用 JUnit 5(包含在*spring-boot-starter-test*dependency 中)进行测试。作为一个从未编写过测试的人，我发现理解单元测试如何工作，然后在 Spring Boot 编写它们是一个相当长的学习过程。经过大量的谷歌搜索，我找到了这些有用的链接，它们帮助我开始编写我的测试-

为了理解如何编写测试，如何在 Spring Boot 模仿你的数据

[](https://stackabuse.com/how-to-test-a-spring-boot-application/) [## 如何测试 Spring Boot 应用程序

### 请注意:下面的文章将致力于测试 Spring Boot 应用程序。据推测…

stackabuse.com](https://stackabuse.com/how-to-test-a-spring-boot-application/) 

使用 Mockito 来模仿你的控制器并向它们发送请求-

[](https://www.springboottutorial.com/unit-testing-for-spring-boot-rest-services) [## 用 Spring Boot 和 JUnit 对 Rest 服务进行单元测试

### 本指南将帮助您为您的 Spring Boot Rest 服务编写出色的单元测试。我们将使用一个简单的代码示例…

www.springboottutorial.com](https://www.springboottutorial.com/unit-testing-for-spring-boot-rest-services) 

经过大量的调试和找出为什么我的测试失败了，男孩不是我高兴地看到他们都是绿色的测试运行后。:)

**第五部分——伐木**

一旦我有了恢复能力，我想在任何失败的情况下使调试变得更容易。为此，我包含了 SLF4J 记录器，它包含在 *spring-boot-starter-web* 依赖项中。我在所有的课程中都包含了相关的跟踪、信息、调试和错误日志。

有关记录器和设置记录器属性的更多信息，您可以查看以下链接-

[](https://howtodoinjava.com/spring-boot2/logging/spring-boot-logging-configurations/) [## Spring Boot 伐木指南— HowToDoInJava

### 在 spring boot 中登录是非常灵活和容易配置的。Spring boot 支持各种日志提供程序，通过…

howtodoinjava.com](https://howtodoinjava.com/spring-boot2/logging/spring-boot-logging-configurations/) 

**第 6 部分-用致动器监控**

Spring Boot 可以方便快捷地构建您的 API，原因有很多，其中之一是它为您提供了一些开箱即用的端点来监控您的服务器，而且是免费的！您所需要做的就是包括执行器依赖性，并且您可以很好地监控您的应用程序的各种指标，比如它是否启动和运行、它收到了多少请求、返回的不同 HTTP 响应等等。还有谁觉得这个超级方便？

有关如何在应用程序中包含执行器以及如何保护端点的更详细文章，请查看此链接-

[](https://www.baeldung.com/spring-boot-actuators#:~:text=Actuator%20is%20mainly%20used%20to,us%20out%20of%20the%20box) [## Spring Boot 执行器| Baeldung

### 在这篇文章中，我们介绍 Spring Boot 致动器。我们将首先介绍基础知识，然后详细讨论什么是…

www.baeldung.com](https://www.baeldung.com/spring-boot-actuators#:~:text=Actuator%20is%20mainly%20used%20to,us%20out%20of%20the%20box) 

**奖励:用于测试的模拟 JSONs】**

在我做研究的时候，我发现一些 API 端点带有假数据，可以用来测试你的 API。虽然我不能在我的特定用例中使用它，但是我把它放在这里，希望它对将来的人有用。

 [## JSON 测试

### 编辑描述

www.jsontest.com](https://www.jsontest.com/) 

对于更广泛的数据，你可以使用这个-

[](https://jsonplaceholder.typicode.com/) [## JSONPlaceholder

### JSON}占位符由 JSON Server + LowDB 提供支持，截至 2020 年 12 月，每月处理约 18 亿次请求…

jsonplaceholder.typicode.com](https://jsonplaceholder.typicode.com/) 

**扩展-**

虽然我无法实现身份验证，但保护您的终端非常重要。因此，我在 Spring 中加入了一些关于身份验证和安全性的文章，我将把它们作为我当前项目的扩展:

[](https://www.baeldung.com/spring-security-basic-authentication) [## Spring 安全基本认证| Baeldung

### 本教程展示了如何使用 Spring 设置、配置和定制基本认证。我们将建立在…

www.baeldung.com](https://www.baeldung.com/spring-security-basic-authentication) [](https://www.marcobehler.com/guides/spring-security-oauth2#_preview) [## Spring Security & OAuth 2.0:深入

### 您可以使用本指南深入了解 OAuth 2.0 以及如何将 Spring Security 与它集成。

www.marcobehler.com](https://www.marcobehler.com/guides/spring-security-oauth2#_preview) [](https://www.marcobehler.com/guides/spring-security) [## Spring Security:深入验证和授权

### 2020-02-25 10:24:27.875 INFO 11116-[main]o . s . s . web . defaultsecurityfilterchain:正在创建过滤器链:any…

www.marcobehler.com](https://www.marcobehler.com/guides/spring-security) 

**最后一个音符**

在构建这个项目的过程中，我经历了一个完整的学习过程，我试图捕捉我的学习和研究，希望这篇文章能帮助一些人在 Spring Boot 从零开始构建 REST APIs。请在评论中告诉我你对我的项目的反馈和改进这篇文章的建议！

请随意检查我的这个项目的代码在这里-

[](https://github.com/Vaibhavi15/order-management/) [## vaibhavi 15/订单管理

### Spring Boot 微服务，用于协调管理订单的上游和下游服务 Spring Boot…

github.com](https://github.com/Vaibhavi15/order-management/)