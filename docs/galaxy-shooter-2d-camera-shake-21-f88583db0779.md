# 银河射手 2D——相机抖动

> 原文：<https://medium.com/nerd-for-tech/galaxy-shooter-2d-camera-shake-21-f88583db0779?source=collection_archive---------38----------------------->

## 增加伤害反应的冲击力和强度！

![](img/08be1d594e7659701961cbbe157496fd.png)

视频游戏中经常使用相机抖动来增加游戏的感觉，强化某些动作，增加沉浸感。这是一个混乱的细节，但却是一个改善玩家体验的微妙细节(当它没有被过度使用或处理不当时)。

当玩家被击中时，我使用相机抖动，随着 VFX 伤害增加强度。

# 设置

要摇动相机，我需要修改相机的变换位置，但这样做会阻止我移动它(它会不断地将相机的位置覆盖回摇动的值)。

为了解决这个问题，相机将是一个空游戏对象的子游戏对象，我将它命名为 CameraContainer，在那里将发生抖动。这样，相机将能够自由移动，并保持从父游戏对象的抖动。

![](img/36b90d6435faeb1a3371880ddb31df29.png)![](img/8c6168e1c576789580e81b308e8580d7.png)

# 震动

为了正确地摇动相机，我至少需要两个变量或值:摇动相机的随机方向和摇动的强度。

为了在任何方向随机移动相机，我首先使用了 Random。返回-1 和 1 之间的随机值。

![](img/146a8cd87dc6172b3ec1d054ebcaa69b.png)

这种方法的问题是运动不平稳。在较高的值，这很容易被注意到，它是混乱的，有点令人不快。

![](img/d91b9e43273aa8cda94ff3e93ad9cb99.png)

# **平稳摇动**

> [**Unity API:** Mathf。柏林噪声](https://docs.unity3d.com/ScriptReference/Mathf.PerlinNoise.html)

通过使用柏林噪声，它可以生成一个保持连续性的随机值，它非常适合我试图实现的目标:平滑的抖动。

PerlinNoise 接受两个参数:X 和 Y 值。它所做的是生成一个 2D 柏林噪声纹理，寻找给定坐标的灰度值，并返回该值，范围在 0 和 1 之间(纯黑、所有灰色阴影和纯白)。

![](img/71ad261e208a8119580aa61c22bddd87.png)

我将使用 X 参数设置一个“随机”的固定种子，使用 Y 参数使用 ***Time.time*** 在纹理中不断移动。在轴之间设置不同的 X 值非常重要，否则整个运动将在同一方向同步。

![](img/98ad7ec83154eea151e96b760ab18af7.png)

此外，该数值范围并不理想，因为这意味着它不会向轴的负方向移动。为了解决这个问题，我们将 PerlinNoise 的值乘以 2，然后减去 1，将其转换为-1…1。

![](img/3abf8e70f5945f65e1e5307c9fca7af9.png)

如果我们在 X，Y，Z 柏林噪声中设置相同的 X 值，就会发生这种情况

![](img/c86a1aff452388c7f2d62141403f0b13.png)

这样好多了，但是移动相当慢，而且是因为 Y 参数( ***Time.time*** )滚动太慢。添加一个新的变量“shakeFrequency”并将其乘以 Y 参数将解决这个问题。

![](img/813352459242b9749565911a1985c6ed.png)![](img/ab705e781550b5a3c77f86df50365ff2.png)

频率设置为 8。这样不是感觉好多了吗？

# 更多改进

这篇文章有点长，所以，我把我做的其他改进列在这里(你也可以做):

*   脚本还可以抖动相机的旋转。
*   从更新切换到协程，以避免每帧执行代码。
*   设置最大平移/旋转量，以避免相机过度抖动。
*   添加创伤和创伤衰减(这是介于 0 和 1 之间的相机抖动量)。
*   通过动画曲线修改创伤值，使抖动更加平滑。

![](img/31f535eccc62ca13f3e29e714d0bc4bf.png)![](img/edc7cb68ab5b255081cb0c256aa89ef1.png)