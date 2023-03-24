# 熊猫的描述性统计

> 原文：<https://medium.com/nerd-for-tech/summarizing-and-computing-descriptive-statistics-in-pandas-7320a1fec371?source=collection_archive---------4----------------------->

## 大熊猫描述性统计数据计算指南。

![](img/bb2cbbd6051bdbc0b49c80fc50dd5822.png)

[斯科特·格雷厄姆](https://unsplash.com/@homajob?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍照

# 加载数据

首先，让我们导入库。

![](img/6f147bb48d863a08298211af113c61ae.png)

让我们创建一个名为 df 的数据框，该数据集包含缺失数据。

![](img/16e3493fccc9a26ef642ac1440c32784.png)

您可以使用 sum 方法计算列的总和。

![](img/337e426256f08d42cff5800c1c217e58.png)

对于行的总和，可以使用 axis = "columns "或 axis = 1。

![](img/15bff7cf804a70b544e047a25e461768.png)

您可以使用 mean 方法计算行的平均值。

![](img/5d1f59eca9aefdbe20593b421b3ea70a.png)

请注意，默认情况下，缺失数据不包括在平均值中。如果要考虑缺失的数据，可以使用 skipna = False。

![](img/2aba82e987cd13cbbc2e9e7088e85cbb.png)

让我们看看行和列中的最大值。

![](img/a2a0a84b39521c766a6c6092002155f6.png)

让我们看看行和列中的最小值。

![](img/9e26d7f622692ba226003f3d09617cd4.png)

让我们来计算累计的总数。

![](img/0e064415e9f695947f0c2e8541ca6890.png)

您可以使用所描述的方法来查看数据集的汇总统计信息。

![](img/ca3c4531d3596066079a31456357f446.png)

为了找到相关系数，我们先导入著名的 iris 数据集。你可以从[这里](https://archive.ics.uci.edu/ml/datasets/iris)下载虹膜数据集。

![](img/19c2ead0d1d071a906b386ae313dd22e.png)

让我们看看 iris 数据集的前五行。

![](img/5eea480f0742cd8992a42baf07dda64f.png)

如您所见，iris 数据集中没有列名。让我们给出列名。

![](img/c912f3748b5068f615e5b7ce16162961.png)

让我们再看一下 iris 数据集的前五行。

![](img/86d46fab5e9a5bab8c956f2b5a836376.png)

我们来计算一下萼片长度和萼片宽度的相关性。

![](img/7253e4a98cd996bdd1cf794622ff5354.png)

您可以使用 corr 方法查看数据框中所有变量的二进制相关性。

![](img/74c56d66d4f06c091810cc979178aa61.png)

您可以使用 cov 方法来查看所有变量的二元协方差。

![](img/d4864ebefa30cac9ec8a339b4c10137e.png)

使用 corrwith 方法，可以获得数据集中某个变量与其他变量之间的二进制比较。

![](img/316cdd86154d3c3df8863145a3f6ca80.png)

您可以使用 unique 方法来查看唯一值。为了说明这一点，让我们创建一个名为 s 的系列。

![](img/c59666593b56e7fc428a0c497701139a.png)

让我们使用独特的方法。

![](img/19b7ad4f25b29abd3e8879eb63b2ddd2.png)

您可以使用 value_counts 方法来查看值的频率。

![](img/13ee5219a3eef6dc68b9ed0f5d86937a.png)

若要控制值是否在数据集中，可以使用 is in 方法。

![](img/5d4f13bf06b1ef590674088bd373cb58.png)

让我们看看有这些值的行。

![](img/361e144736e3a7471786ae56c55a4f98.png)

就是这样。我希望你喜欢这篇文章。你可以在这里访问笔记本[。](https://github.com/TirendazAcademy/PANDAS-TUTORIAL/blob/main/09-Summary%20Statistics.ipynb)

别忘了关注我们的视频，YouTube，T2，Twitter，GitHub，Linkedin，Kaggle 和 T9

[](/codex/python-pandas-tutorial-42be3e827e2a) [## Python 熊猫教程

### Pandas 是 Python 最重要的库之一。在这篇博文中，我将谈论熊猫图书馆并展示…

medium.com](/codex/python-pandas-tutorial-42be3e827e2a) [](https://levelup.gitconnected.com/practical-data-analysis-with-pandas-c40fbd2955fa) [## 熊猫的实用数据分析

### 在我的上一篇文章中，我提到了在熊猫图书馆使用数据。Python 最重要的库之一是熊猫…

levelup.gitconnected.com](https://levelup.gitconnected.com/practical-data-analysis-with-pandas-c40fbd2955fa) 

如果这篇文章有帮助，请点击拍手👏按钮几下，以示支持👇