# 机器学习基础-异常值

> 原文：<https://medium.com/nerd-for-tech/machine-learning-fundamentals-outliers-f1dd8f8fdbd7?source=collection_archive---------7----------------------->

## 什么是离群值？，如何识别离群值？，如何克服离群值？，如何克服现实生活中的离群点。

![](img/093321f0ddcdc0a491e38ca67ab8c00e.png)

弗兰基·查马基在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

离群值可以是一组数据中偏离观察值的任何极值。此外，异常值是与大多数其他值不同的值。

例如，考虑学校数据集中学生的年龄。众所周知，学生接受教育是有年龄限制的。在这样的数据集中，不能考虑该范围的较大或较小值。数据集中出现这样的记录会导致异常值。但是在大学里，受教育没有年龄限制。但是，即使这样的数据集有一个关于超龄人的记录，在数据集中也是相当罕见的。这也是一个离群值的定义。

此外，在数据集中检查这样的异常值也是有原因的。由于数据集中存在极值，因此在进行预测时可能会产生一些混乱。正因为如此，预测模型可能会做出弱决策。这导致模型无法得出可接受的结果。此外，数据集中出现异常值还有一些原因。这些错误包括数据输入错误、采样错误以及分析数据时的操作错误。

作为具有异常值的解决方案，可以移除或处理这些异常值以建立预测模型。存在离群值的另一个缺点是。也就是说，异常值会扭曲数据分布，从而导致偏离正态分布。作为一种实践，我们知道拥有每个数据分布正态结果的最佳预测模型。因此，由于存在离群值，我们可能会遇到机器学习算法的误导性训练过程，具有更长的训练周期，更不准确的模型，以及在测量特定指标时的糟糕结果。

有两种异常值，称为单变量异常值和双变量异常值。单变量异常值超出了数据集中单个变量的正常值。单个变量中的异常值称为单变量异常值。当数据集中有一个以上的变量具有极值时，称为双变量异常值。

下面的 GitHub 库给出了分析 Jupiter 异常值的系统方法。请遵循下面给出的源代码。

[](https://github.com/HashanEranga/data-science-fundamentals-outliers/blob/main/bigmart-outliers-identification.ipynb) [## 数据-科学-基础-异常值/big mart-异常值-识别

### 在 GitHub 上创建一个帐户，为 HashanEranga/data-science-fundamentals-outliers 开发做出贡献。

github.com](https://github.com/HashanEranga/data-science-fundamentals-outliers/blob/main/bigmart-outliers-identification.ipynb) 

如上所述，有两种方法可以克服异常值。删除异常值变量或优化或最小化数据中异常值的影响，而不是删除极值。第二种方法称为 winsorization 方法。在这种方法中，基本方法是改变接近分布的极值的方式。换句话说，这是一种找出最不常见的观察值并以最合适的方式创建它们的方法。此外，winsorization 基于正态分布的概念。因此，winsorization 可以应用于分布的任何一侧。winsorization 的数量取决于数据集和所考虑的异常值的分布。一旦应用了 winsorization，应用 winsorization 之后外部的值可以被移除或者可以被处理以优化数据集中的记录。一旦识别出异常值，就可以通过删除或限制记录来处理异常值。如果记录由于错误输入并被正确替换，则对所选记录加帽。另一种方法是投标，即将数值转换为分类类型值。

最后，如何识别数据集市数据集中的异常值将在下面讨论。(与上面给出的存储库相同)。

[https://github . com/HashanEranga/data-science-fundamentals-outliers/blob/main/big mart-outliers-identificati on . ipynb](https://github.com/HashanEranga/data-science-fundamentals-outliers/blob/main/bigmart-outliers-identification.ipynb)