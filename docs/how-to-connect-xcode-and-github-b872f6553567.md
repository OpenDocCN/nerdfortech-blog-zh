# 如何连接 Xcode 和 GitHub

> 原文：<https://medium.com/nerd-for-tech/how-to-connect-xcode-and-github-b872f6553567?source=collection_archive---------28----------------------->

## 学习直接从 Xcode12 提交

![](img/d58caa6c425901aa983a97762966fa10.png)

图片由作者提供，背景来自[约书亚·阿拉贡](https://unsplash.com/@goshua13)在 [Unsplash](https://unsplash.com/photos/EaB4Ml7C7fE)

这个循序渐进的教程将教你如何连接 Xcode 和 GitHub，这样你就可以执行项目的控制版本。在继续之前，我假设你有一个 GitHub 账户，如果没有，不要再浪费一秒钟，[去创建一个](https://github.com/join)。

# 1.在 Mac 上配置 GitHub

打开一个新的终端( *cmd + space* ，然后编写 *terminal* ，使用您的 GitHub 用户名和电子邮件粘贴以下命令:

# 2.将您的 GitHub 帐户添加到 Xcode

打开 Xcode 并前往偏好设置:

![](img/08d19fddd9f049d50116cc24eba862bc.png)

导航到帐户，点击窗口底部的+并选择 GitHub:

![](img/de9b3192116ae9809bfb9e92f71a67fe.png)

写下你的 GitHub 用户名和令牌？是的，您不能使用您的普通密码，您需要生成一个令牌:

![](img/70fbff8b2f84be5c7f2352f411ab91a3.png)

转到 GitHub，点击您的图片>设置>开发者设置>个人访问令牌>生成新令牌:

![](img/620bd8202c48333ffa5e9976b282ad2f.png)

给你的令牌起一个一致的名字，比如 *Xcode* 并选择作用域。我选择: *repo，admin:public_key，notifications，user 和 delete_repo:*

![](img/5562048800e8a59aa157dc3bcff993fc.png)

复制剪贴板中的令牌…

![](img/fcd307c6494b7a04cc14287f0e0278e6.png)

…并将其粘贴到 Xcode 中:

![](img/1b166500a985401aa21b5af36d996523.png)

然后，您会看到您的 GitHub 帐户已经添加到 Xcode:

![](img/15c8176c28527ed502bb70f5b572be38.png)

# 3.创建新的 Xcode 项目

是时候创建一个新项目了。转到文件>新建>项目…

![](img/787fbd08a62d454ec30f27c0a6f954ef.png)

为您的项目选择一个模板，然后单击下一步。我选择了 iOS 应用程序:

![](img/77c5601ec0c80481a8ef6810c6beb2da.png)

填写您的应用程序的名称…

![](img/5fab3c35ac6a58c50a2c6951bfdaf3ce.png)

…而且，小心⚠️选择选项*“在我的 Mac 上创建 Git 存储库”:*

![](img/e927a9e2d385fe2e96b47b0cd0b57fa5.png)

# 4.创建新的 GitHub 存储库(从 Xcode)

我们快到了。显示源代码控制导航器，右键单击 *Remotes* ，然后单击*New“Your app”Remote…*

![](img/f11da014e27ee76286cc8b1cfab54c22.png)

我们可以直接在 Xcode 中完成这项工作，而不是从 GitHub 创建存储库。给你的库起一个好听的名字，添加一些描述，选择可见性，然后点击*创建*:

![](img/c0ef46e08d5001ebf7f6b24df37585ae.png)

如果你去 GitHub，你会看到你的新仓库在那里等着你，很好🤩！

![](img/6c6a8806ce3cb4c2143417cc1842d5ee.png)

# 5.从 Xcode 提交

在这最后一步，我将向你展示如何直接从 Xcode 提交，不需要打开终端。首先，对代码进行一些修改。我只是改变了默认的 *Hello，world！你好，世界！您可以在文件旁边看到一个小的 **m** ，表示您的存储库中的文件有一些修改。*

转到源代码管理>提交…

![](img/3ff039b4d7726b86bc606329859ba22b.png)

将出现一个新窗口，您可以在其中看到已修改的内容。添加您的提交消息，选择*推送至远程*，最后点击*提交并推送:*

![](img/042e9a4682cf788d40b6ea28c9f0f7f2.png)

终于！这是你第一次直接从 Xcode 🥳提交🎉

![](img/7aeee10676e4b5ebe2ccbb0fa8a7cd0c.png)

感谢阅读！

# 参考资料:

*   Youtube: [Xcode 教程:GitHub 集成、个人访问令牌和 Xcode 回购创建](https://www.youtube.com/watch?v=m9a6dkqYVS8)
*   中:[如何配合 Xcode11 使用 Github](/swlh/how-to-use-github-with-xcode11-8a93b64ff1bc)

*原载于 2021 年 6 月 11 日 http://irenebosque.com*[](http://irenebosque.com/how-to-xcode-and-github/)**。**