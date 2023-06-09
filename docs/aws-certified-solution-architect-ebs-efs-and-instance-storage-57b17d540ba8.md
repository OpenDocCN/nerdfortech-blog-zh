# AWS 认证解决方案架构师— EBS、EFS 和实例存储

> 原文：<https://medium.com/nerd-for-tech/aws-certified-solution-architect-ebs-efs-and-instance-storage-57b17d540ba8?source=collection_archive---------4----------------------->

嗨，伙计们，在上一个教程中，我们谈到了 EC2。因此，每一个 EC2 都有一个可用的存储设施。作为一名架构师，你应该能够找到满足你需求的最佳解决方案。为此，让我们深入了解这些不同的存储机制提供了什么。

EBS 是一个网络驱动器，我们可以在它运行时将它附加到实例上。EC2 实例存储附加到 EC2 实例上，根据实例的大小，性能会有所不同。EFS 是托管网络文件系统(NFS ),我们将它挂载到一个或多个 EC2。

现在我们知道了这些存储技术的基本定义，接下来让我们看看使用案例。

当您有一个分布在 az(可用区域)中的 EC2 实例群来处理一个大型数据集并需要访问同一个数据集时，我们将不得不使用 EFS 而不是其他技术。这是因为只能为一个 AZ 创建 EBS。EFS 的另一个好处是可伸缩性。

当我们需要高性能的冗余安全数据存储时，EBS 是不错的选择。这就像一个普通的硬盘驱动器使用。

实例存储类似于 RAM，可用于高性能数据库存储类需求，但所有数据都应定期备份。当 EC2 实例终止时，存储被删除。实际上，实例存储被用作 EC2 实例上的应用程序的高性能本地缓存。