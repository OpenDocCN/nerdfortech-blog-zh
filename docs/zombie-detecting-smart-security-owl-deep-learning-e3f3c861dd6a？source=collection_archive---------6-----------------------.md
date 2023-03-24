# 🦉僵尸探测智能安全猫头鹰

> 原文：<https://medium.com/nerd-for-tech/zombie-detecting-smart-security-owl-deep-learning-e3f3c861dd6a?source=collection_archive---------6----------------------->

在这个万圣节教程中，我们将向你展示我们是如何给一个平凡的家庭经典:安全摄像头添加一个超级怪异的元素的。怎么会？！我们制造了一只夜视猫头鹰，它利用图像处理来跟踪人。哦，它发出呜呜声，就像真的一样！

![](img/9723d6d74b84fc2b1f901d4894dca0c3.png)

我们对这个项目非常兴奋，自从新的 Raspberry Pi 4 发布以来，我们一直在等待这个项目。它有 4GB 内存，这为大量真正令人兴奋的可能性打开了大门，包括实时使用深度学习模型进行一些图像处理。

如果你想在万圣节警惕僵尸的靠近，或者只是在一年中的其他时间检查你的花园，这就是适合你的。安全不一定要无聊才有效！

# 供应

对于这个版本，您需要:

*   树莓 Pi 4 (4GB 内存)[亚马逊](https://amzn.to/2MNkHyM)
*   夜视摄像头[亚马逊](https://amzn.to/2MMqXa1)
*   微伺服[亚马逊](https://amzn.to/2BLTlCR)
*   假猫头鹰[亚马逊](https://amzn.to/31S2qEO)
*   胶水[亚马逊](https://amzn.to/2NdoNiU)
*   油漆[亚马逊](https://amzn.to/2WiDaGQ)
*   螺丝[亚马逊](https://amzn.to/2JqCjyl)
*   USB 音箱[亚马逊](https://amzn.to/2BNuPBr)
*   大(5v+)便携式电源[亚马逊](https://amzn.to/2BLTlCR)
*   3D 打印机[亚马逊](https://amzn.to/31NpuES)

> [🔗在 Github 上获取智能 CCTV Owl 代码📔](https://github.com/sk-t3ch/cctv-owl)

# 建设🛠️

## 将…斩首

a.用力拉猫头鹰头上与弹簧相连的地方，把它的头拉下来(有时你不得不残忍一点)。

![](img/8a5544cf10a14d2d68028bb98610ce3c.png)

b.猫头鹰的头部通过一个圆柱体与身体相连，圆柱体位于一个大弹簧的顶部。通过取出螺钉拆下该气缸。

![](img/8fee50b5a41e519a7196c2d7ffa17319.png)![](img/74659940bd3793c6b067465faf8a42ef.png)

c.你刚刚拆下的气缸由两部分组成，一个塑料杯和一个位于其中的轴承。用螺丝刀(或类似工具)从气缸上拆下轴承。

![](img/1bb318317285908d1bc123bdf0cb947d.png)

d.拧开将弹簧固定在阀体上的三个螺丝，拆卸弹簧。

![](img/ead166321ed86380dde74e749bcbe1f1.png)

e.在猫头鹰的身体顶部打一个洞，这个洞足够大，可以放一些电线和摄像头电缆。我们用了一个钻头和一个螺丝刀的不雅组合来做这件事。

![](img/c7635dba13696aae9758ac2b0a7d9959.png)

## 添加智能🧠

a.3D 打印相机外壳，并绘制成与猫头鹰相匹配的颜色——我们使用了一些廉价的丙烯酸颜料。绘画不是至关重要的一步，但它确实极大地改善了整体外观！

[](https://www.thingiverse.com/thing:2755175/makes) [## 树莓 Pi 夜视摄像头安装红外削减迷你

### 与 Raspberry Pi 和夜视摄像头配合使用，使用自动红外切割+红外光斑:=>…

www.thingiverse.com](https://www.thingiverse.com/thing:2755175/makes) [](https://www.thingiverse.com/thing:2860717) [## olivermandic 的 GoPro 兼容遮阳板支架

### 下载文件，并使用 3D 打印机、激光切割机或 CNC 构建它们。Thingiverse 是一个事物的宇宙。

www.thingiverse.com](https://www.thingiverse.com/thing:2860717) ![](img/defbccd0ab8b41bd890cfbdb8ef586b3.png)

b.将猫头鹰的头倒置，将相机外壳的顶部拧入它的头部内侧，也就是鸟喙突出的地方。

![](img/21a27ab83ff1c336f059acfbf52c2800.png)

c.将相机放入机箱，连接相机电缆。

d.将伺服系统粘在弹簧的顶部。

![](img/0ba15aef9653cfbd23c36688ff800bf9.png)

e.将长导线连接到伺服引脚(5V，GND，信号)

f.通过弹簧和你在身体顶部做的孔给相机电缆和伺服电线，这样它们就在猫头鹰中空的身体里面了。

![](img/cf2d07fc498b5154d386c5af6710624f.png)

g.把脖子拧回去，把头推上去。

![](img/a09bbc8921a961021176017c9a5cce2b.png)![](img/bd6cd95cad1fde53be690b76c4d2d780.png)

## 给她加满油🤖

a.移除猫头鹰底部的塞子，并通过切割塑料来增加这个孔的尺寸。继续增加尺寸，直到树莓皮和扬声器可以进入猫头鹰的身体。

![](img/92a222e2f766486e736959d94367bb95.png)![](img/79f28b10bf8e42948365ecf8a03c723b.png)

b.一旦孔足够大，所有的组件都可以放进去，将你穿过猫头鹰顶部的摄像头电缆从底座中拉出，并将其插入树莓 Pi 中。

![](img/0fcc7a0df0ed4f4a5f5d469a65706826.png)

c.类似地，将伺服线穿过并插入树莓派:

> ***+5V 伺服= > +5V Pi
> GND 伺服= > GND Pi
> 信号伺服= >引脚 12 Pi***

![](img/58e2a361780c275fd0e3d372db46e030.png)

d.将 USB 扬声器插入 Pi。

![](img/6785f1a803a4f1c344537bed688fef76.png)

e.将 SD 卡插入 Pi。

f.使用便携式电源供电。

![](img/c28003d76b7fe42309a7448259722ca7.png)

g.通过底座上的孔将 Pi、电源和扬声器插入 owl。

![](img/072dbb5d6e3ece736a8f6870564d68be.png)

## 4.设置 Pi🥧

a.下载 [Raspian](https://www.raspberrypi.org/downloads/) 并使用 [Balena Etcher](https://www.balena.io/etcher) 将其上传至您的 SD 卡。

b.要远程访问您的 pi:

*   将名为 ssh 的文件添加到您的启动 sd 卡中
*   添加一个名为`wpa_supplicant.conf`的文件，并放入你的 wifi 凭证

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev update_config=1   
network={   
         ssid="MySSID"   
         psk="MyPassword"  
}
```

c.将 SD 卡插入 pi 并尝试通过 ssh 访问。

## ⚙️动了动脑袋

> **移动磁头的代码教程(用树莓派控制伺服)——**[**github**](https://github.com/sk-t3ch/cctv-owl/tree/master/tutorials/1_move_the_head)

为了控制在 Pi 上运行的伺服系统，我们将创建一个脚本来控制伺服系统所连接的 GPIO 管脚。

a.确保伺服机构与 Pi 之间的连接:

> ***+5V 伺服= > +5V Pi
> GND 伺服= > GND Pi
> 信号伺服= >引脚 12 Pi***

b.您必须首先设置 gpio 引脚，以便在伺服系统的信号引脚上使用 PWM。

c.然后，只需选择信号引脚的占空比(此处解释)即可将伺服从占空比为 7.5 的 90 度移动到占空比为 2.5 时的 0 度，再移动到占空比为 12.5 的 180 度

## 让它发出声音🔉

> **制作猫头鹰叫声的代码教程(用树莓派播放音频)——**[**github**](https://github.com/sk-t3ch/cctv-owl/tree/master/tutorials/2_hoot)

a.插入 USB 扬声器。

b.下载一个声音——我们选择了一个怪异的叫声。

c.运行以下命令播放声音:`omxplayer -o alsa:hw:1,0 owl_sound.mp3`

![](img/80216852b98e5e83f929296b78027fd6.png)![](img/3bf288cf3ac4cac89c46bffa9ff9ebcc.png)

[d .如果这不起作用，请使用 alsamixer 命令检查您的 Pi 正在使用什么输出以及音量是多少——您将看到混音器屏幕，您可以在其中更改音量并选择您的媒体设备。要增加声音的音量，执行如下命令`omgxplayer -o alsa:hw:1,0 owl_sound.mp3 -vol 500`要使用 Python 播放声音，请看我们的测试脚本。]

## 从 Pi 流视频🎦

> **代码教程创建 raspberry pi 相机流—**[**github**](https://github.com/sk-t3ch/cctv-owl/tree/master/tutorials/3_stream_video)

a.在`http://raspberrypi.local:5000`运行 python `app.py`并在本地网络上查看。

b.这段代码摘自 Miguel Grinberg 的博客文章，他很好地解释了这是如何完成的，他的教程也很棒——deffo 请查看！基本概念是，我们使用线程和生成器来提高流速度。

这架照相机在夜晚和黑暗中都可以工作。

![](img/4dc13dd0f14149b69da812028e93d3a7.png)![](img/4a4162dbf614ef31c9967fce3237c7a3.png)

## 人体检测🕵️‍♀️

> **人体检测代码(带有树莓 pi 的视频流上的 ImageNetSSD)——**[**github**](https://github.com/sk-t3ch/cctv-owl/tree/master/tutorials/4_object_detection)

![](img/707d5f8e5d0f4a365fe70c767b698bd7.png)

a.由于我们使用的是 Raspberry Pi 4，我们认为最好在它上面尝试一些深度学习模型，而不是我们迄今为止受限的基本[Haar scade](https://docs.opencv.org/3.4/db/d28/tutorial_cascade_classifier.html)方法。

b.我们看了一些预先训练好的模型，比如看起来超级酷的 YOLOv3。YOLOv3 很小的重量，这对于 Pi 来说是完美的，但我们无法让它运行:(

c.相反，我们选择了 MobileSSD 模型，我们可以使用 openCVs DNN(深度神经网络)模块运行该模型，正如我们从这个[代码](https://heartbeat.fritz.ai/real-time-object-detection-on-raspberry-pi-using-opencv-dnn-98827255fa60)以及图像处理教程的英雄[阿德里安·罗斯布鲁克](https://www.pyimagesearch.com/2017/09/11/object-detection-with-deep-learning-and-opencv/)中了解到的那样。

d.然而，当我们试图流式传输这些内容并在每一帧上运行模型时，这导致了滞后、支离破碎的视频。我们再次从 Adrian Rosebrock 那里学到了东西，使用 Python 多处理模块将我们的图像放入队列中，在那里它们可以被处理，而不会严重阻塞相机流。

e.尝试自己运行代码

## 发送僵尸通知

> **发送通知的代码(python to phone)——**[**github**](https://github.com/sk-t3ch/cctv-owl/tree/master/tutorials/5_send_notifications)

a.我们决定使用[https://pushed.co](https://pushed.co/)通知服务。

![](img/3e6357c5007d7aaec3c595818a480399.png)

b.你可以获得一个免费帐户，下载应用程序，并真正快速设置进行移动通知。我们使用这样的 python 脚本创建了通知。

![](img/770a70aaa6d1312545f6ad3398acf172.png)

## 多可笑啊！

我们希望你喜欢我们的智能安全猫头鹰项目！这是一个超级有趣的制作，知道我的房子被我们信任的猫头鹰守护着，我感觉安全多了。查看 [Youtube 视频](https://youtu.be/aLX4btGs_x8)。

![](img/404b98e8621467d25c5c7a295985af5f.png)

> [🔗在 Github 上获取智能 CCTV Owl 代码📔](https://github.com/sk-t3ch/cctv-owl)

# 感谢阅读

我希望你喜欢这篇文章。如果你喜欢这种风格，可以去看看[T3chFlicks.org](https://t3chflicks.org/)了解更多以科技为重点的教育内容( [YouTube](https://www.youtube.com/channel/UC0eSD-tdiJMI5GQTkMmZ-6w) 、 [Instagram](https://www.instagram.com/t3chflicks/) 、[脸书](https://www.facebook.com/t3chflicks)、 [Twitter](https://twitter.com/t3chflicks) )。