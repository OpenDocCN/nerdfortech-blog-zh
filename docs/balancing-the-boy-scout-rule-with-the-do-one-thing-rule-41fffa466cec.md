# 平衡童子军规则和“做一件事”规则

> 原文：<https://medium.com/nerd-for-tech/balancing-the-boy-scout-rule-with-the-do-one-thing-rule-41fffa466cec?source=collection_archive---------3----------------------->

![](img/26ba8f81e4a70f4eb1c2d4ab7fad2ee3.png)

来自 [Pexels](https://www.pexels.com/photo/interracial-kids-setting-in-wood-chunk-on-ground-9303542/) 的 [cottonbro](https://www.pexels.com/@cottonbro/) 摄影

# 童子军规则

鲍勃大叔(或畅销书作家罗伯特·c·马丁)是这样表述的:

> **童子军有一条规则**:“永远要让露营地比你发现的时候更干净。”如果你发现地上一片狼藉，不管是谁弄的，你都要清理干净。你有意为下一批营员改善环境。
> 
> 来自 Kevlin Henney 的《每个程序员都应该知道的 97 件事》

# “做一件事”法则

它跨越了许多领域，并可以转化为许多其他规则，如单一责任规则，单一来源的真理公约，或不要重复自己的原则。

# 冲突

当在产品的某个部分工作时，你将不可避免地遇到你可以改进或修正的事情。如果你想成为一名优秀的侦察兵，你会想要修理它们。问题是:它们与你的工作无关。你的公关不再只做一件事，在公关中发现这些离群点有一个名字:范围蔓延。最初是项目管理中的一个术语，它也适用于代码评审。

我们需要分而治之。

## 战略 1:多种减贫战略

这是最明显的，但也是开销最大的。工程师们倾向于选择最短的路径，花时间从多个分支创建多个 pr 是一个我们所有人都可能会跳过的头痛问题。修复越小，我们就越不可能为它创建一个完整的 PR(以及随之而来的所有开销——代码审查、CI 渠道、部署)。

## 策略 2:一个 PR，独立提交

当审查一个 PR 的工作量对我来说太大而无法将变更分成多个 PR 时，我会使用这个策略。

告诉你的代码评审员阅读这份 PR 的最佳方式:这种 PR 最好是逐个提交地评审，而不是一个巨大的变更列表。这个策略需要考虑您的提交，以便每个提交都有其上下文，并作为一个整体的“变更单元”

我发现这不仅有利于回顾本身，也有利于从更大的角度看待你的任务。它让你在逻辑相连的工作块中思考，谁不想要更紧的提交呢？