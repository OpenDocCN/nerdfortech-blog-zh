# 如何在 iPhone 上测试 Xcode 应用程序

> 原文：<https://medium.com/nerd-for-tech/how-to-run-xcode-on-your-iphone-irene-bosque-783a2975534a?source=collection_archive---------1----------------------->

## 本教程是在 Xcode 12 中完成的

![](img/6b47829ef1169bae2a0e73c76eea4b44.png)

你正在 Xcode 12 中构建一个应用程序，你想知道如何在你的 iPhone 上运行 Xcode 吗？然后，在这个简短的教程里和我呆在一起。

# 1.创建新的 iOS 应用程序(可选)

如果您已经开始构建应用程序，请跳过这第一步，否则，打开 Xcode 并为 iOS 创建一个新的应用程序:

![](img/36cba5828d01a6b41015d1ca8a10f1c6.png)

# 2.尝试在您的 iPhone 中运行该应用程序…

去点击你当前模拟器的图标…

![](img/d0f71ef789301c333a2c2ee579e187d9.png)

…将 iPhone 连接到 Mac，并从列表中选择它

![](img/cc854ebc836d183e9f2ffdd36a36c2b9.png)

现在，如果你点击运行按钮，你会看到一个红色的错误，告诉你需要一个开发团队:

![](img/d00d5969e74561f8749c7edc91118974.png)

# 3.解决方法:添加一个团队帐户

在左侧面板中，选择您的应用程序，然后选择名为*签名&功能*的选项卡。点击*添加账户……*

![](img/35371f620cb109058fec57eff7c45d60.png)

添加您的常规 icloud 电子邮件并输入您的密码:

![](img/68fdb251726f20df7e6c13a491e36ef5.png)

还没离开*签约&能力*标签；在*签名*部分，点击*团队*，而不是*无*，选择您最近添加的 Apple ID 账户:

![](img/9395393ab1f6242b9a8da56c3296fde0.png)

# 4.在你的 iPhone 上运行应用程序

就是这样，如果您再次运行它，您应该不会收到任何问题。现在转到你的 iPhone，你会看到你的应用程序。如果你点击它，很可能会出现一条关于不可信开发者的警告信息:

![](img/deb0b6b3e5f2f2b92ae3e5c99491713b.png)![](img/f2a7cf41da1847a16913b3cf506dd25a.png)

前往“设置”>“通用”>“设备管理”,并信任开发者:

![](img/6c308beda1f0ac1bf8439b29408407e2.png)![](img/ed29e687440b204425ba6d824e9de1dc.png)

就是这样！这就是如何在你的 iPhone 上运行 Xcode！🎉🥳

![](img/bae4c2498a53dcf6ca583edbb1c6c023.png)

感谢阅读😊！

# 参考资料:

[https://www . twilio . com/blog/2018/07/how-to-test-your-IOs-application-on-a-real-device . html](https://www.twilio.com/blog/2018/07/how-to-test-your-ios-application-on-a-real-device.html)

*原载于 2021 年 6 月 13 日 http://irenebosque.com*[](http://irenebosque.com/how-to-run-xcode-on-your-phone/)**。**