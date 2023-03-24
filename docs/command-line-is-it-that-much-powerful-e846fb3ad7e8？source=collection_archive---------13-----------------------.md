# 命令行，有那么强大吗？

> 原文：<https://medium.com/nerd-for-tech/command-line-is-it-that-much-powerful-e846fb3ad7e8?source=collection_archive---------13----------------------->

## 黑客用命令行，命令行有什么特别的？

![](img/44ca055a61a53d7311989533c31f5583.png)

[Bermix 工作室](https://unsplash.com/@bermixstudio?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](/s/photos/hacker?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 拍摄的照片

命令行(CLI)已经存在很长时间了，自 20 世纪 60 年代中期以来，它就一直是计算机的一个强大功能。是什么让命令行如此特别？黑客为什么爱它？嗯，归结起来就是几件事。但是在我们开始之前，让我们先讨论一下，命令行是什么？

# 命令行是什么？

命令行是一个基于文本的程序，用于向计算机传递命令。命令行的用户界面称为外壳，它充当操作系统和用户之间的一层，它让用户能够访问操作系统的核心组件，并且它充当翻译器，将人类可读的命令翻译成计算机理解的命令。世界上有两种使用最广泛的 shell，它们是 Windows shell 或命令提示符(Windows 中的默认 shell ),以及 bash shell 或 Bourne Again SHell(主要用于 Mac os 和 Linux)。

![](img/d0d83b55cd3d413dde71a0d2f158063f.png)

照片由[萨法尔·萨法罗夫](https://unsplash.com/@codestorm?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](/s/photos/coding?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 拍摄

# 命令行有什么特别之处？

我们计算机上的大多数程序都使用图形用户界面(GUI)。这只是日常执行任务的一种简单方式。但是命令行不像 GUI，它使用基于文本的 UI。虽然图形用户界面很吸引人，但它不如命令行界面强大，为什么？

![](img/e5d9c392c4d0dd1873a14e51418d7419.png)

马库斯·斯皮斯克在 [Unsplash](/s/photos/hacker?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄的照片

1.  今天的操作系统防止你弄乱核心系统进程。这导致操作系统阻止访问我们电脑上的某些文件和位置。例如，苹果公司有他们所谓的 [**系统完整性保护**](https://support.apple.com/en-us/HT204899) ，它限制对某些文件夹的访问，因此用户不能使用常规文件管理器访问它们。但是用命令行那只是小菜一碟。你所要做的就是用命令行禁用系统完整性保护[T5。没有其他 GUI 应用程序可以做到这一点。这显示了命令行的强大功能。](https://developer.apple.com/documentation/security/disabling_and_enabling_system_integrity_protection)
2.  与 GUI 相比，它使用的资源最少。GUI 很漂亮，但是引擎盖下很笨拙，但是命令行很精干，引擎盖下很快。这是由于 CLI 基于文本的特性，它执行任务的速度往往比 GUI 更快，GUI 可能会在其渲染中使用 GPU。这使得 CLI 在执行任务时速度非常快。
3.  命令行支持编码(脚本)。虽然 GUI 已经从过去走了很长的路，看起来也漂亮了很多，但是有些东西并不是为它们设计的。假设你被要求转换 500 个文件。wav 音频格式到. mp3 格式，你会一个接一个地点击它们，然后用 GUI 把它们的文件扩展名重命名为. mp3 吗？我打赌你会这么做。但是使用命令行，只需移动到文件所在的目录，然后 [**写一行简短的命令**](https://askubuntu.com/questions/919788/convert-mp3-file-to-wav-using-the-command-line) ，瞧，你所有的文件都会被转换。或者，如果您希望将。wav to .mp3 作为一项常规工作，你所要做的就是编写一个简单的 bash 脚本，并放入你的代码，每次你需要改变音乐文件的扩展名时，你就运行 bash 文件。

# 黑客为什么爱命令行？

由于上述原因，黑客们非常喜欢命令行，黑客们倾向于重复任务，命令行对他们来说是完美的工具，也因为命令行如此强大，它可能会使他们的工作比使用图形用户界面更容易。但你会感兴趣地知道，像我这样的人(我以前没有专业地黑过，嗯，黑游戏不算黑)也热爱命令行。

![](img/185f77aaa67f953cbc87a173d2d451e8.png)

照片由 [**萨克舍姆·乔杜里**](https://www.pexels.com/@saksham-choudhary-109710?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) 发自 [**像素**](https://www.pexels.com/photo/man-holding-laptop-computer-with-both-hands-2036656/?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels)

命令行是一个强大的工具，甚至可以带来毁灭，但是如果掌握得好，它可以成为您手中的强大工具。

# 命令行可以做得更好的事情。

[**命令提示符—高级磁盘管理命令**](https://www.digitalcitizen.life/command-prompt-advanced-disk-management-commands/) —命令提示符可以作为一个强大的磁盘管理器。

[**命令提示—系统信息高级命令&管理活动任务**](https://www.digitalcitizen.life/command-prompt-advanced-commands-system-information-managing-active-tasks/) —命令行可以作为系统管理器，你可以用它来杀 app，在任务管理器里杀不了的。

[**命令提示符—高级网络命令**](https://www.digitalcitizen.life/command-prompt-advanced-networking-commands/) —您可以使用命令提示符查看您的 mac 地址、IP 地址等等。

[**命令提示符—修复丢失或损坏的文件**](https://www.digitalcitizen.life/command-prompt-repair-missing-or-corrupt-files/) —命令提示符可以修复丢失或损坏的 Windows 文件。

[**命令提示符—修复您的引导记录问题**](https://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records/) —命令行可以修复您的引导加载程序、引导记录以及任何与引导相关的问题。

如果你喜欢这篇文章，你可以给我 50 次掌声👏👏👏，如果你对技术和软件开发感兴趣，也可以关注我的[](https://konaduakwasiakuoko.medium.com/)*和社交媒体。您可以在[***Twitter***](https://twitter.com/akuoko_konadu)上关注我，因为我们将讨论编码和一般的技术世界，我的 DM 永远是开放的。加入我的[***YouTube***](https://www.youtube.com/channel/UCYKFy3oPn2b6gbjAzmgNgJg)让我们一起做一些编码。祝你有愉快的一天。下一次快乐编码。*

*如果你希望有人为你写科技文章，我很乐意为你写一篇**低至 5 美元**[**【Fiverr**](https://www.fiverr.com/share/8Kq9Br)**。***

## *头条新闻*

*这些是我最喜欢的文章，请随意阅读*

*[](https://konaduakwasiakuoko.medium.com/apple-what-took-you-so-long-rumors-of-redesigned-14-inch-and-16-inch-macbook-pros-2021-59b8e89ff53f) [## 苹果，你怎么这么久才来。传闻重新设计的 14 英寸和 16 英寸 MacBook Pro，2021 年。

### 自 2016 年以来，MacBook Pro 没有重大的重新设计，这是五年前的事情。苹果你准备好听…

konaduakwasiakuoko.medium.com](https://konaduakwasiakuoko.medium.com/apple-what-took-you-so-long-rumors-of-redesigned-14-inch-and-16-inch-macbook-pros-2021-59b8e89ff53f) [](https://levelup.gitconnected.com/if-all-these-m1-macbook-rumors-are-true-then-other-laptops-are-in-for-hell-71a02eee9958) [## 如果所有这些关于 M1 MacBook 的传言都是真的，那么其他笔记本电脑就惨了。

### 一个 M1x 芯片出现在一个基准测试网站上，其多核性能是当前 M1 的两倍。

levelup.gitconnected.com](https://levelup.gitconnected.com/if-all-these-m1-macbook-rumors-are-true-then-other-laptops-are-in-for-hell-71a02eee9958) [](https://levelup.gitconnected.com/open-source-and-linux-makes-it-to-space-pushing-the-limits-of-human-imagination-a05e032aa884) [## 开源和 Linux 进入太空，推动了人类想象力的极限。

### 你可以获得在火星直升机上运行的软件框架，并将其用于你的项目。开源是多么的…

levelup.gitconnected.com](https://levelup.gitconnected.com/open-source-and-linux-makes-it-to-space-pushing-the-limits-of-human-imagination-a05e032aa884) [](https://levelup.gitconnected.com/programmers-dont-stay-in-your-comfort-zone-1b10e465b8cb) [## 程序员们，不要待在自己的舒适区里。

### 呆在我们的舒适区非常有趣，但后果是什么，我们如何才能阻止这种情况。

levelup.gitconnected.com](https://levelup.gitconnected.com/programmers-dont-stay-in-your-comfort-zone-1b10e465b8cb)*