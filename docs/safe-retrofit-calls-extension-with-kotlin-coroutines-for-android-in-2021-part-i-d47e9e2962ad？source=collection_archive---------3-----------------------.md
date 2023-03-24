# 2021 年 Android 安全改造调用 kotlin 协同程序扩展—第一部分

> 原文：<https://medium.com/nerd-for-tech/safe-retrofit-calls-extension-with-kotlin-coroutines-for-android-in-2021-part-i-d47e9e2962ad?source=collection_archive---------3----------------------->

![](img/09009555fe6b4edbfcba051efa70e842.png)

照片由 [Fotis Fotopoulos](https://unsplash.com/@ffstop?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

你好👋，今天我将教你如何以一种安全和 kotlin 惯用的方式执行网络呼叫。在这个小系列的结尾，您可能会看到这样的内容:

从数据层到领域层和表示层，这里有一个清晰的架构结构。

以上要点是向您展示如何在您的 ViewModel / Presenter/ etc 中执行改造呼叫并处理失败或成功的结果。
如果你不明白要点的内容，不要担心，我会一步一步地做一个非常简单但具体的解释。

如果你想直接看代码，看看我做的这个关于电影的游乐场项目。

[](https://github.com/ChristopherME/movies-android) [## Christopher me/电影-android

### Movies 是一个简单的项目，可以学习和使用一些 android 组件、架构和 Android 工具…

github.com](https://github.com/ChristopherME/movies-android) 

# 有什么问题？

首先，为什么需要协程来执行网络调用(使用 retrofit 或任何其他 HTTP 客户端)？我的朋友，正如你已经知道的(或者可能不知道),当你启动你的 android 应用程序时，它会创建一个新的 Linux 进程，只有一个线程(主线程或者 UI 线程，如果你愿意的话)。这个线程负责绘制视图组件、小部件等。与 UI 相关的一切。完全禁止在这个线程上做其他事情，因为应用程序可能会崩溃。查看官方[文档](https://developer.android.com/guide/components/processes-and-threads#Threads)了解更多详细信息。

现在我们知道，我们不允许在 UI 线程上执行繁重的任务，如网络调用、数据库操作、读/写文件，因为它会变慢，我们可能会遇到 [ANR](https://developer.android.com/training/articles/perf-anr#anr) 异常，我们的应用程序会崩溃。

# 有什么解决办法吗？

在旧的 android 编码时代，人们习惯于创建自己的线程池，并自己管理线程的创建和维护🤯！相信我，孩子，这不是你想做的事。其他解决方案暗示 [AsyncTasks](https://developer.android.com/reference/android/os/AsyncTask) 不太灵活，现在已被弃用。那些真实的虽然岁月。我对那些开发 android 应用程序的开发者表示敬意。

然后，作为一个不断演变的平台，挑战和克服这些挑战的方法需要新的和更灵活的方法。那时 RxJava 是 Android 应用程序的新救世主。RxJava 对于异步任务来说是一个很好的解决方案，但是它也有自己的缺陷:

*   漫长的学习过程。第一次理解起来并不容易，因为你必须将你的思维模式转变为一种反应式编程，有很多操作符和马贝尔图😵。
*   它给你最终的 APK 尺寸增加了 2MB 以上
*   这就像用火箭筒打死一只虫子。您可能不会使用该库中 50%的实用程序，而只会将它用于一个问题，即异步任务。

# 救援协管员

2017 年，谷歌正式将 Kotlin 用于 Android 开发，此后事情发展得非常快。他们在该语言的 1.1 版本中为异步任务提供了一个集成的解决方案，即著名的协程。对于那些用 Kotlin 编码的人来说，这是一个开箱即用的解决方案！

> *协程*是可挂起计算的一个实例。它在概念上类似于一个线程，因为它需要一个代码块与其余代码同时运行。然而，协程并不绑定到任何特定的线程。它可以在一个线程中暂停执行，然后在另一个线程中继续执行。
> 
> 协程可以被认为是轻量级的线程，但是有许多重要的区别使得它们在现实生活中的用法与线程非常不同。
> 
> [科特林文件](https://kotlinlang.org/docs/coroutines-basics.html#your-first-coroutine)

# 让我们一起把它包起来

为了安全地执行网络呼叫，我们需要做以下事情:

*   **确保它没有在主线程**中执行——协程[调度程序](https://developer.android.com/kotlin/coroutines/coroutines-adv?hl=es-419)将成为我们这里的工具。
*   我们可能还需要**解析一些后端错误响应**——我们将使用 [Moshi](https://github.com/square/moshi) 解析 JSON。
*   如果我们愿意，我们可以添加某种中间件功能，以便**仅在所有这些中间件都满足条件的情况下执行我们的网络调用**。—这是可选的。

我们得到了对网络调用扩展包装器的要求，但是还有一个问题悬而未决……如何用协程处理异常🤔？

使用`try catch`块非常直接地处理异常。看看这篇来自 [Manuel Vivo](https://medium.com/u/3b5622dd813c?source=post_page-----d47e9e2962ad--------------------------------) 的[博客](/androiddevelopers/exceptions-in-coroutines-ce8da1ec060c)谈论它。事实上，我们还将使用一个 try catch 块来处理我们的异常🤫但是，我们不会通过应用程序的各个层传递异常。

相反，我们将传递包装在 awsome " [要么](https://github.com/ChristopherME/movies-android/blob/master/functional-programming/src/main/java/com/christopher_elias/functional_programming/Either.kt)"类中的自定义[故障](https://github.com/ChristopherME/movies-android/blob/master/functional-programming/src/main/java/com/christopher_elias/functional_programming/Failure.kt)(您甚至可以在 google 示例中找到类似的实现，就像这个[结果](https://github.com/google/iosched/blob/main/shared/src/main/java/com/google/samples/apps/iosched/shared/result/Result.kt)密封类)。

这两个类都是一个密封的类，在给定的时间里可以是一个错误或成功的对象。它还包含一些我实现的额外方法，用于基于[箭头](https://github.com/arrow-kt/arrow)函数编程库执行某种映射操作。这两种课都不是什么新鲜事，我是在阅读费尔南多·切哈斯的这篇令人惊叹的文章时发现的。

如果你不知道什么是密封类，看看弗洛里纳·芒特内斯库的视频

我们已经建立了基础，该编码了。查看第 2 部分👉[此处](https://christopher-elias.medium.com/safe-retrofit-calls-extension-with-kotlin-coroutines-for-android-in-2021-part-ii-fd55842951cf)。