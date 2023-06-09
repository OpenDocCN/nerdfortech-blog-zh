# 吉他捕捉技术综述

> 原文：<https://medium.com/nerd-for-tech/review-of-guitar-capture-technology-6fc3c15d99fa?source=collection_archive---------6----------------------->

![](img/69198c9e9e7d943ae5a4e9674bdcddc4.png)

**什么是吉他采集/分析？**

吉他采集或仿形使用数字技术来采集模拟硬件的一个方面。它捕捉放大器/踏板/吉他声音的单一“快照”。这可以是从均衡器到电子管放大器的实际动态响应的任何内容。

建立电子电路模型并不是一件容易的事情，尤其是当涉及到真空管这样的非线性元件时。真空管放大器通常被认为比基于晶体管的放大器具有更好的声音和数字模型。但是随着最近数字技术的进步，也许这种看法正在改变。

以下是使用吉他捕捉技术的四款产品的简要概述:Kemper Profiler、Moore 音调捕捉踏板、Neural DSP Quad Cortex 和 GuitarML SmartAmp 插件。

**免责声明**:虽然我试图在这场关于吉他采集/分析技术的讨论中保持公正，但我是 GuitarML 的创造者，所以我有推广它的既得利益。

**肯珀剖面仪**

Kemper 的剖面仪可能是最熟悉的吉他剖面/采集硬件。它使用专有的捕捉技术来“捕捉”任何放大器的声音 DNA。零售价为 1799 美元，这是一个录音和表演的一体化解决方案。随之而来的是 Kemper 的真实放大器的数据库。人们甚至把他们自己的高端放大器的配置文件做成生意，并出售这些配置文件。(“剖析”在本文中实际上是 Kemper 的商标)

Profiler 将一系列测试音发送到放大器中，并从带麦克风的扬声器电缆或线路输入接收它们。确切的过程是严格保密的，但它使用输入/输出信号来创建硬件动态响应的轮廓。有趣的是，Kemper 会进行初始配置，然后进行“优化配置”功能，以获得更好的声音。

以下是使用 Kemper Profiler 的 profile 功能的 YouTube 演示:

**摩尔语气捕捉 GTR**

这是一个独特的产品，因为它捕捉你的吉他的音调，而不是放大器/效果硬件。官方的描述是这样的:

“音调捕捉吉他踏板基于 MOOER 独特的 EQ 匹配技术——音调捕捉。此踏板允许您通过采样目标吉他的独特音调特征来捕捉任何吉他的音调。拖着多把吉他的日子已经一去不复返了。”

所以你可以让 Fender Telecaster 听起来像 Strat，或者 Strat 听起来像莱斯·保罗。80 美元绝对是这个列表中最便宜的硬件，尽管它没有做适当的动态响应建模，只有 EQ 匹配。话虽如此，捕捉过程似乎非常快，下面是 YouTube 上的踏板演示:

**神经 DSP 四核皮层**

Neural DSP 的 Quad Cortex 是该领域最新的硬件产品。Neural DSP 是一家来自芬兰的初创公司，最初是开发高端吉他插件。我个人试用过他们的大部分插件，听起来确实不错。Quad Cortex 更进了一步，提供了一个一体化的硬件解决方案，非常像 Kemper，并具有“神经捕捉”功能，用于捕捉放大器和踏板的动态响应。零售价为 1600 美元，与肯珀剖面仪属于同一级别。

神经 DSP 为我们提供了这种工作方式的线索，因为它使用了神经网络/机器学习技术。整个捕获过程大约需要 10 分钟，捕获质量的初步评论非常好，一些人声称它的声音和感觉比 Kemper Profiler 更好。

以下是几个吉他踏板上的四皮层神经采集功能的演示:

**GuitarML**

GuitarML 是一个开源的免费项目，它使用机器学习来捕捉放大器和踏板的动态响应。它的独特之处在于代码是开源的，这意味着任何人都可以随心所欲地使用代码。修改它，改进它，贡献给 GuitarML 或者用于他们自己的项目。GuitarML 开发了吉他插件和工具来进行实际的放大器/踏板捕捉。用户对音质的评价是积极的，但鉴于它的 DIY 性质，这是一项正在进行中的工作。

GuitarML 网站:

[](https://guitarml.com/) [## 吉他 ML

### 记录放大器或踏板的输入/输出样本，用于创建数字模型。训练机器学习…

guitarml.com](https://guitarml.com/) 

目前，GuitarML 有两个主要插件，第三个将于 2021 年夏天推出。GuitarML 产品包括 SmartAmp 和 SmartAmpPro，以及用于创建捕获的代码工具。捕捉的工作原理是获取目标放大器/踏板的输入/输出记录，然后使用人工智能框架来优化/训练模型。Ai 框架要么是 Pytorch，要么是 Tensorflow(由 Google 提供)，这些也是开源工具。

这是一个用户创建的视频，比较了 Kemper 配置文件的 SmartAmp 捕获与原始 Kemper 配置文件。

以及 SmartAmpPro 采集功能的实际演示:

**奖励:分形音频系统——Axe FX III**

Fractal 的 Axe FX III 音频处理器也是一款高端吉他放大器建模器，但它为用户提供了模拟脉冲响应或“IR”的能力。这不会捕捉过度驱动的放大器或踏板的失真质量，而是捕捉扬声器和音箱对声音的影响。它的效果不如混响那么强，但给声音带来了更多的质感和真实感，就像是通过真正的放大器播放一样。这种产品的零售价约为 2000 美元。还应注意的是，有许多捕捉红外的软件选项，实际上唯一需要的硬件是麦克风和目标放大器。

**下一步是什么？**

我希望这篇评论有助于更多地了解这一令人兴奋的音乐技术及其发展方向。虽然数字建模和电子管放大器之间的争论很激烈，但不可否认的是，捕捉技术正使成为音乐家变得非常有趣。