# 在 dart 类中索引资产，就像 R.java| Flutter 一样

> 原文：<https://medium.com/nerd-for-tech/indexing-assets-in-a-dart-class-just-like-r-java-flutter-3febf558a2bb?source=collection_archive---------19----------------------->

![](img/6361ee7441b8bbc74b255dde1a11045e.png)

自从我开始研究 **#flutter** 以来，我喜欢它的每一个方面，并深入研究它提供的架构和 API，以便用漂亮的 **#dart 扩展它的功能。**

由于我对 android 生态系统及其开发工具非常感兴趣，所以我在 flutter 中非常想念 R.java 的概念。因此，我过去常常只需将资产图像或任何其他文件放在 drawable、mipmap 或 values DIR 中，它就会立即与 R.java 同步。R.java 包含一组子类，如 drawable、mipmap 等，其中包含静态变量来引用资产&值。

这使得事情变得非常简单，就像从 drawable 调用图像一样简单明了

```
myImageView.setBackgroundResource(R.drawable.thumbs_down); 
```

因为在 flutter 中我们必须这样写

```
Image.asset(‘assets/images/thumbs_down.png’); 
```

这使得事情变得有点混乱，难以管理。因为路径是字符串值，你总是需要重新检查你是否应该正确的输入它，而不是像我们在 R.java 那样只使用静态变量。所以我设法创建了一个用于在 dart 中生成该文件的 CLI 工具，但问题是 CLI 工具并不那么方便，新开发人员大多只熟悉他们项目的 **pubspec.yaml** 。

因此，飞镖的妙处就在这里。Dart 有一个工具包叫做**build _ runner**(https://dart . dev/tools/build _ runner)。用它我植入了这个叫做 assets_indexer 的包！[https://pub.dev/packages/assets_indexer](https://pub.dev/packages/assets_indexer)它生成带有各自目录名的类，这些目录名包含静态字段到它们的封装文件中🤩 😍

假设你有一个目录**资产/图像** &它包含了 **thumbs_down.png** 文件，现在可以这样调用它

```
import ‘package:my_awesome_app/generated/images.asset.dart’ Image.asset(Images.thumbsDown); 
```

就这样，🥳！

它对我来说非常有效，我希望它也能帮助社区。请随意报告问题和功能建议😁