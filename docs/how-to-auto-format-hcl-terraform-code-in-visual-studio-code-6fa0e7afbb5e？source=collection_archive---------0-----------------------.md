# 如何在 Visual Studio 代码中自动格式化 HCL Terraform 代码

> 原文：<https://medium.com/nerd-for-tech/how-to-auto-format-hcl-terraform-code-in-visual-studio-code-6fa0e7afbb5e?source=collection_archive---------0----------------------->

![](img/27a18ad0ce9d00d4df8403c6f46603fb.png)

## 不要再使用“terraform fmt”

**在我们开始之前**

> *-你将需要 Visual Studio 代码编辑器。你可以在下面下载。* [*Visual Studio 代码*](https://code.visualstudio.com/)

安装哈希公司 Terraform

📝打开 Visual Studio 代码并导航到扩展。

![](img/530ecbf48240528ae2da1068e63c9f7c.png)

📝在搜索栏中，键入“HashiCorp ”,并在出现时选择 HashiCorp Terraform。

![](img/35315795556222b7efdadcbe92fcb5d1.png)

📝单击安装

![](img/9d83d5d18ddf34e205011a69729f9309.png)

安装完成后，它应该看起来像这样👇🏽

![](img/1a68b0348d5909764337e76843248498.png)

📝导航到文件->首选项->设置

![](img/1f445fe12cdb1c9bdc5c1a3a082e0946.png)

📝在搜索设置中键入“格式”。

![](img/c212867f21efbd4787de321065152005.png)

📝单击文本编辑器

![](img/556b1cb6b85b2b518c9f5f3f6a9931f9.png)

📝保存时启用格式

![](img/4137897058c463a391e686013dfda9ca.png)

📝在默认格式化程序下选择 HashiCorp Terraform

![](img/a36231285df695cbe1c372969b06a80a.png)

📝关闭设置和扩展窗口，然后单击资源管理器

![](img/30219b99b863f4a7de1c6ae84cbcf412.png)

**确认自动格式化工作。**

> 如果你已经有了你的 Terraform 代码，那么导入它，做一个小的改变，然后撤销它，然后点击保存，看看这个魔术。每当您保存更改时，自动套用格式将起作用。

> 请允许我演示一下

📝单击打开文件夹，然后选择一个空文件夹。(创建一个用于测试目的。)

![](img/21bd7bfb9a57193f3ff9903b8f9d22bd.png)

如果提示您信任文件夹中文件的作者，请单击“是”。

![](img/e164851a2ec137d707963b4cd6d75175.png)

📝通过右键单击“资源管理器”面板并选择“新建文件”来创建新文件

![](img/e064a3b98574584a5c300820a31b85a2.png)

📝键入以结尾的名称。法国南部（French Southern Territories 的缩写）

![](img/bd8fd280c4fba7591afb8846759b7519.png)

Sample.tf

![](img/d8516c83b18c569dd5effa672fb668bb.png)

> 请注意，文件现在有了 terraform 徽标，这表明扩展到目前为止工作正常。

📝将以下示例代码复制并粘贴到您的可视代码中。

![](img/a780a0c9f1e2a2832fd2c9dae80b3f9a.png)

> 粘贴这段代码被认为是对文件的更改，所以当我单击 Save…

![](img/e09a32d6ba74e6cbdc75f336b85b3435.png)

漂亮的 Terraform 代码！！😍😍不需要 fmt