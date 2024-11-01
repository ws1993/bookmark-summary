Title: iPhone 加入游戏，但 USB-C 的乱纪元还没有完结 - 少数派

URL Source: https://sspai.com/post/84508

Published Time: 2023-11-20T07:00:00.000Z

Markdown Content:
**tl;dr:**

*   USB-C 只是一个接口的形状；
*   USB-C 和具体支持什么特性无关；
*   USB-C、支持的协议、支持的速率和充电功率，这四者可以互相混搭；
*   带出门的充电线优先选择柔软易弯折的，其他需要根据用途、看准参数按需购买；
*   雷电 5 线缆是目前协议支持最全面的线缆，但价格也是最贵的。

消歧义：若无特别所指，本文中的 USB-C 包含如 Type-C 、C 口、华为口、乐视口、扁圆口等等所有概念。

* * *

伴随着 2023 年 9 月 13 日 iPhone 15 系列机型的发布，iPhone 上陪伴我们走过整整十一年、让人爱恨交加的 Lightning 接口终于正式退休，补齐了 2023 年科技春晚中「5G 大战 USB-C」的右二分之一。

![Image 1: JCfkbCMe4oz3MBxlVAxc8damn7B](https://cdnfile.sspai.com/editor/u_/cldc3cdb34taeapqr2qg?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

也算是实现了 2012 年 iPhone 5 发布会中对于 Lightning 接口的十年之约

按理说 iPhone 苦等十年终于加入 USB-C 大家庭应该是一件众望所归的好事，但是发布至今过去一个多月，大家也很快发现了换接口背后的隐性问题：统一到 USB-C 只是解决了线缆能不能插进去的问题，而插进去究竟能不能正常工作就另说了

重要的事情要重复三遍：「**USB-C 只是形状，其他特性可以自由组合**」。

其实，现如今有关于各家 USB-C 相互兼容与否的所有乱象，归根结底都是 USB 设备「接口」与「协议」之间的矛盾——简单来说，USB 设备的接口规格决定了它们的外形是什么样的、设备之间能否（物理）连接，而设别所使用的传输协议才是让两边协同工作的基础。

### USB-C 接口的好：统一的接口形状

在过去设备之间能不能连接起来，主要是看的是接口的脸色，只有接口形状和线缆相匹配才能连起来。USB 作为一种通用的设备连接标准，在经过多次升级演变后也有各种各样的接口，但看形状总是最方便的。

![Image 2: ChKcbPpu8oRBcex535vcN2g7nth](https://cdnfile.sspai.com/editor/u_/cldc3clb34taeen1qa5g?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

图源 Wiki 百科

这张维基百科列出的 USB 接口规格表所有的存在过的接口，在 Type-C 这个接口出现以前，每一种 USB 接口的物理样式通常只对应一种（至多两种）USB 传输协议。而且用起来一定要找到两头都对应的线缆才行，所以常常会遇到一抽屉的线材没能用的情况；好处也有，只需要买到接口形状对应的线材或者设备，就可以保证它们之间是可以正常工作——并且是以最大效率、最高兼容性在工作的。

记不住没关系，反正最近几年新出的设备能用上 Type-C 都上 Type-C 了。这听起来可以达成一个美好的愿望：「统一接口以后随便找根两头都是 USB-C 的线缆就能连接两个设备了」。

但是，出于包括兼容性等种种原因， USB 开发者论坛（USB Implementers Forum，一作 USB 联盟，以下统称 USB-IF）并没有要求 Type-C 需要完整地拥有正反各 12 根共计 24 根金属针脚，也就是说 Type-C 接口里的那些针脚并不需要全部工作，甚至少几根都没关系。然后就遇到了 Type-C 线缆插上去了但是不起作用。

![Image 3: AJ7pb3kacoWcSfxDTkmcgVOEnab](https://cdnfile.sspai.com/editor/u_/cldc3d5b34tae8ka146g?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

统一的接口形状

这时你可能就意识到，Type-C 接口的唯一好处就只剩下了**统一的接口形状**这唯一优势。

### USB-C 接口的坏：能插≠能用

![Image 4: OVNVb7Z3Moby7fxfUXqcvr47nae](https://cdnfile.sspai.com/editor/u_/cldc3d5b34tae2qbfa80?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

经历过这个弹窗的各位肯定清楚，「能插」和「能用」很明显是不一样的

上面我们提到过 Type-C 接口里的那些针脚并不需要全部工作，甚至少几根都没关系。而针脚会直接影响到 Type-C 这个接口的功能，USB 协议下各种子协议所需要的针脚又各不相同，这样我们就遇到了「能插≠能用」这一难题。

从技术层面来说，USB 作为一个已经陪伴了个人计算机快三十年的技术标准，经历过各种大跨度的迭代之后分支众多，但由于各种历史原因和技术细节，不同版本之间的兼容性并不完全一致。

![Image 5: LPO7b53dNofpHqxbi7lc77ZWn3d](https://cdnfile.sspai.com/editor/u_/cldc3ddb34taeen1qa60?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

每个针脚都有自己的用途

举个简单的例子而言，其实 USB 3.x 和 USB4 并不兼容 USB 2.0 的设备，因为 USB 2.0 的信号通过 USB 线材的里的 D+、D- 针脚传输，而 USB 3.x 和 USB4 的高速数据使用 SSTX/SSRX 针脚传输， 二者是完全独立的。除非推倒 USB 相关的协议重来，不然 USB 主机控制器总是需要同时支持 USB 2.0 和 USB 3.x 这两种速率。

当然，也可以选择偷懒，像普通版的 iPhone SoC 中没有独立的 USB 3.x 控制器就只能实现 USB 2.0 的速率；又比如大多数的充电线也没有 SSTX/SSRX 相关的针脚，这样他们被用来传输数据的时候也只有 USB 2.0 的速度。

![Image 6: iPhone 15 and iPhone 15 Pro: Everything you need to know about its new USB-C  port - SoyaCincau](https://cdnfile.sspai.com/2023/11/20/article/931a49ba68748498b56fa1aa25a4bb00?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

另一个例子则是 USB4 兼容 USB 3.2 则是通过 USB 隧道完成的，而 USB4 本身支持 USB 隧道、DP 隧道和可选 PCIe 隧道，当然这一点我们后面还会提到。

因此你可以看到，单 Type-C 这一个接口样式实际上包含了两部分，一个是它的的形状（接口样式），另一个则是它所具备的针脚（所支持的协议），它们共同组成如今我们口中比较笼统的 USB-C 概念。

而**如果你只想指代这个接口的外形的话，「Type-C」才是更准确的名字。**

揭秘 USB-C 接口线缆的兼容逻辑：全针脚≠全支持
--------------------------

这时你一定在想，以后买线买全针脚的线缆不就好了。但我必须戳穿你的「幻想」，针脚并非影响线缆性能的唯一因素。线缆两端1的控制器芯片，是决定线缆支持哪种协议的另一重要因素，不过好在和控制芯片在一起的电子芯片 eMarker 可以帮助其他电子硬件正确识别线缆支持的具体协议。

![Image 7: CGYnbX4TvozL0MxLpwXcos0Tnjf](https://cdnfile.sspai.com/editor/u_/cldc3dlb34taeapqr2r0?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

这个 eMarker 支持 USB4、Thunderbolt 3 和 Power Deliver 3.0

eMarker 是一种特殊的电子元器件，它主要功能是保存线缆的有关信息，例如支持的最大电流、电压、数据传输速率和协议等。eMarker 芯片中的信息在线缆连接到设备时被设备读取，根据这些信息设备会调整自身的运行参数，以适应线缆的性能。例如，如果 eMarker 告诉设备支持最大 5A 电流，设备会根据这个信息调整自己的供电电流，确保在使用过程中不会损坏设备或线缆；又比如 eMarker 告诉设备只支持 USB 2.0 的速度，那么设备就只会以最大 480Mbps 的速率传输数据。

从 2019 年开始 USB-IF 规定大多数的 USB 线缆都需要 eMarker，除了充电电流在 3A 及以下、数据传输的速度在 USB 2.0 或不支持数据传输的 USB 线缆才不需要 eMarker。

总的来说，USB-C 所支持的协议需要控制芯片、eMarker 芯片以及针脚三者共同组成。但线缆方面因为成本和用途，eMarker 电子芯片和针脚通常会完全匹配。但在线缆连接到设备时， 不仅要看线缆、也要看设备端支持的情况，不一定能以最大效率、最高兼容性连接，两者在不兼容时，会向下协商以达到相互兼容的最优运行状态。

### 主动线和被动线

也许你还听说过主动线和被动线的区别，不过以前这两个词往往会和前面提到的 eMarker 电子芯片相关，2019 年开始大多数的 USB 线缆都需要 eMarker 以后主动线和被动线又有什么区别呢？

![Image 8: LchTbJJAVoYLUGxba5KctUiPnhc](https://cdnfile.sspai.com/editor/u_/cldc3e5b34taeapqr2rg?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

USB-IF 关于主动线的定义

我们都知道日常生活中任何的物体都是有一定的电阻的。当数据线里的数据从一端传输到另一端时，会由于电阻等原因影响导致信号出现衰减。传输更大的带宽需要保证信号衰减更少、出错也更小，要不然另一端设备就不能获取正确的信息了。

所以当长度超过一定范围时，就需要利用主动线中的 eMarker 和独立的 ReTimer （可以理解为放大器）对信号进行整形和重新放大，来确保信号质量。而被动线自然就是指不需要对信号进行整形和放大的线缆。

不同协议的主动线和被动线所支持的长度和最高速度并不相同。举个例子，USB4 的被动线缆可以在长度小于 2m 时提供的最高传输速度为 20Gbps，而主动线可以在长度小于 5m 时提供这个速度。

目前，只能依靠厂家宣传和读取 eMarker 芯片了解一根线缆到底是主动线还是被动线。一般而言，长且高速的线缆都是主动线。

那些 USB-C 所支持的协议
---------------

聊清楚了 USB-C 本身和兼容逻辑以后，我们就不得不展开聊了 USB-C 目前最麻烦的协议部分了。不过在本段开始前，我们再要把重要的事情重复三遍：「**USB-C 只是形状，其他特性可以自由组合**」。

### 数据传输

而一旦讲起如今 USB 速度传输的这一锅粥，其中绕不开的话题就是 USB 技术背后的标准化组织。不客气的说，现在市场上鱼龙混杂的数据传输规格和数据线山头林立，USB-IF 自身的努力难辞其咎。

如果你尝试自己采买过 USB 设备，就一定不会对下面这张第一眼看上去不明所以的规格表感到陌生。这张表是 2022 年 9 月份 USB-IF 为各种 USB 数据传输规格作出的最新命名规范。而在此之前，与之相似的改名行为至少已经有过三四次了。

![Image 9: UnCmb3PTBouVgcxBQh0c7o4zn9l](https://cdnfile.sspai.com/editor/u_/cldc3edb34taeapqr2s0?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

目前 USB 图标、老名字、新名字和速度的对照表

考虑到各种历史原因和技术细节，不同版本之间的兼容性并不完全一致。有这样复杂的命名方式也无可厚非，但这些并不算直观且被 USB-IF 反复修改的名称就是在客观上导致了如今市场上 USB 设备鱼龙混杂、兼容性参差不齐。

即使是去年 9 月份的再次更名，以速度为名称，虽然有所缓解，但厂商跟进新的命名标准需要时间，并且消费者使用的老设备也不会就此停止使用，所以对于作为终端用户的我们来说，这些只不过是又一批需要强记的新名词罢了。

关于 USB4 相关的细节大家可以移步这篇文章《[科普 | USB4 和 Thunderbolt 4 都带来了什么新改变？](https://sspai.com/post/63932)》，其中比较重要的就是 USB4 将不使用传统的通用数据传输机制，而是采用了「隧道」的方式，在整条链路上划分出不同的「隧道」用来传输数据，隧道机制可以**充分利用带宽。**目前 USB4 支持如下三种隧道：

*   数据传输：USB 3.2 隧道
*   视频传输：DisplayPort 1.4a 隧道
*   可选隧道：PCI-E 隧道

另外就是 USB4 本质上只**强制要求 10Gbps 的数据传输带宽**，也可以选择 20Gbps 的数据传输带宽。如果加上显示传输所需要的带宽，**USB4 强制要求的带宽则是 20Gbps**，也可以选择 40Gbps 的高速版本（拓展坞强制需要），一切全部由厂商决定。

而 USB4 Ver2.0 版本2，物理层架构发生了变化，支持的最高速率为 80Gbps，但**强制要求的带宽则为 40Gbps**，**数据隧道强制最低要求 20 Gbps 的速率**，并更新了 DisplayPort 2.1 视频传输隧道和最新的 PCI-E 隧道。

### 视频输出

至此，当 USB 的接口规范在 2014 年更新到了 24 针脚的 Type-C 接口之后，得益于它超强的兼容性和越来越高的速度上限，整个 USB 技术的功能范围也得以扩展，在原本的基础上逐渐新增了（更高规格的）视频、音频和充电方面的许多新能力。

尽管在 USB 协议下进行视频和音频的传输在本质上仍然可以被称为「数据传输」，但这三者之间的工作模式其实是有区别的。当两端的 USB 设备均支持视频输入与输出——比如用一根 Type-C 线连接笔记本电脑与显示器——的时候，USB 接口会进入一个名为 Alternative Mode（备用模式，缩写为 Alt Mode）的状态，在备用模式下通过兼容已有的 DisplayPort (DP) 或 HDMI 协议来提供视频传输。

![Image 10: ROJYbVeVaoIGkIxFzMxcBHgWnK1](https://cdnfile.sspai.com/editor/u_/cldc3elb34tae8ka1470?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

有线版本的三星 DeX 就是一个 USB 视频输出的典型场景

换句话说，一个使用了 Type-C 接口的设备支持何种视频传输能力，实际上是与它支持的 USB 数据传输协议的版本**并不直接对等的，因为两者使用的是不同的标准**。

这也就是为什么在普通版的 USB-C iPhone 机型上，虽然只配备了速率上限 480Mbps 的 USB 2.0 接口，但依然可以有线连接显示器以最高 4K 60 帧的规格进行投屏。因为此时的 Type-C 接口是在以兼容 DP 或者 HDMI 的模式下工作，只要线缆针脚齐全、 控制芯片支持，就能传输相应规格的视频，**无关数据传输带宽**。

![Image 11: E7uZbcDuwoUVv4xwFRecirBDnDc](https://cdnfile.sspai.com/editor/u_/cldc3f5b34tae8ka147g?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

Apple 官网上对于 iPhone 有线视频输出能力的描述

### 音频输出

除了视频输出，自从 2017 年各大手机厂商开始竞相模仿 iPhone 7 去除手机上的 3.5mm 耳机孔之后，USB 接口的音频传输能力也逐渐走进了普通用户的视野，比如现在市面上偶尔还能见到的外置 USB 声卡利用的就是 USB 音频协议（USB Audio Class, UAC）进行模拟音频信号的输出：

![Image 12](https://cdnfile.sspai.com/2023/11/20/fafe4710bca20e6cd4071109d5682ee6.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1/format/webp)

这类免驱动的 USB 声卡大多使用的都是 UAC 1.0 协议

而从 Type-A 逐步进化到 Type-C 之后，面对音频信号中「模拟」和「数字」两大类的区分，越来越多的 Type-C 设备开始直接以数字音频信号作为唯一的输出规格，其中比较具有代表性的就是一些手机会出现所谓「挑耳机」的情况，因为这些手机的 Type-C 接口仅支持数字音频信号输出，而并不是所有的 Type-C 耳机都支持纯数字信号输入——为了对接这些纯数字音频，播放端（要么是耳机，要么是转接头上）必须要有一个数模转换器（DAC）先将数字信号翻译成模拟信号，再通过耳机中的放大器播出。

![Image 13: YYumbaqaKoWejLxVYmRcy3qEnwb](https://cdnfile.sspai.com/editor/u_/cldc3flb34tae8ka148g?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

比如 Type-C 接口的 EarPods 就内置了 DAC ，可以给只支持输出数字音频信号的 Pixel 用

### 电力传输

那么基于 USB 技术的充电技术呢？和协议一样，USB 技术也有着一整套配套的供电标准，抛开我们现在已经很熟悉的 USB-PD 协议，USB 其实一直支持以 5V 的电压进行不同功率（0.5～15W）的电源传输。比如这次 iPhone 15 系列支持最高支持 4.5W 的功率为其他设备充电，本质上就是 USB 电源标准的一部分。

![Image 14: M1s0bfZTsocEGixLv3Ac7c1Enbg](https://cdnfile.sspai.com/editor/u_/cldc3g5b34tae2qbfa90?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

iPhone 给配件充电时采用的不是 PD 协议

随着 2012 年 USB-PD 协议的正式出台，以及 Type-C 接口在针脚数量上面的提升，USB 设备上越来越高功率的充电得以成为现实。但标准的 Type-C 接口即使在没有专门协议的情况下也应该支持最高 15W 的充电，获得了当下最新的 USB-PD 3.1 认证之后更是应该最高支持到 240W（5A\*48V），不过想要达到这样的功率线缆也需要通过认证。

不过随着功率的提升，受到物理定律的制约，功率越高、规格越高的线材必然会比低功率的线材「粗壮」许多：

![Image 15: GT2HbSo2HoLPxTx5I79c5pnNnob](https://cdnfile.sspai.com/editor/u_/cldc3gdb34taeapqr2sg?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

从左到右：硬到能自己站起来的戴尔 5A 线、立讯代工的 3A 线和罗技鼠标赠送的 1A 充电线

值得注意的一点是，有些小家电虽然使用 USB-C 接口供电，但仔细查看这些电源适配器，你会发现许多小家电并未遵循标准的 USB 电力传输协议（比如输出 10V 2A 的 USB-C 插头）。因此，不建议任意将小家电的充电器用于其他设备，这可能会导致设备损坏。

息息相关但各有特点：雷电协议
--------------

而每次说起 USB-C ，还有一个总会跳出来的话题就是近几年多见于 MacBook 上面的「雷雳」。实际上，虽然 Apple 是目前主要推广雷雳规范的厂商，但雷雳背后的技术标准—— Thunderbolt ——其实是由同为 USB-IF 成员的英特尔发起的，最初的设想是一种更高规格的基于光纤而非铜线的传输标准，随后 Apple 才加入了雷电3的开发。

在 2011 年公布的第一代雷电标准中，其使用的物理接口是 Apple 在 2008 年推出的 miniDP 接口，也就是 2016 年之前 MacBook Pro 机身上那两个标志性的倒梯形接口：

![Image 16: UEXhbfMWuoBp3rxW18ScKEuWnMg](https://cdnfile.sspai.com/editor/u_/cldc3glb34taeen1qa6g?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

miniDP 的形式被一直沿用到了 2013 年的雷电 2 协议上。而在 2015 年发布的雷电 3 标准中，其使用的物理接口被更换成了 Type-C 并保持至今，伴随着 2023 年九月「雷电 5」技术标准的发布，这个长得和 USB-C 一模一样的家伙也毫不奇怪的再次引起了一波混淆。

雷电技术本身也是一个不止数据传输、多用的协议，加之 USB4 对 Thunderbolt 3 & 4 都是**可选兼容**的，所以我们也不得不把它单独拿出来说说。

### 什么是雷电协议

对于我们这样的终端消费者来说，如果想要快速理解当下「雷电」与「USB」的关系，可以用集合的逻辑来看：USB-IF 为 USB 传输协议制定了很多标准，但这些标准中有很多并不是强制性的。

英特尔作为 USB-IF 的主要成员之一**将其中一些非强制的标准的提取出来变成强制的，用这个更严苛的标准整合成了雷电。**换句话说，雷电比较类似 USB 标准的一个子集，对技术的要求更高、更超前一些。

前文说过，USB4 其实分为 20Gbps 和 40Gbps 两种速率，不满足后者的也可以被叫做 USB4 设备，但是同期的雷电 4 是强制要求设备必须可以达到 40Gbps 速率的，因此才会出现需要将两者分别列出的情况。就拿最新发布的 M4 SoC 的 MacBook Pro 为例，Apple 在技术规格页面是把它们俩分别列了出来的：

![Image 17](https://cdnfile.sspai.com/2024/10/31/d0bb753ec38a0dc9a74c1364815c2697.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1/format/webp)

### 目前尚为主流的雷电 4 协议

![Image 18: AnMObSIUaow3nXxFWhNcXBxrncd](https://cdnfile.sspai.com/editor/u_/cldc3h5b34tae2qbfaa0?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

雷电 4 和其他协议的直观对比，图片来自 Intel 中国

目前主流的雷电 4 协议相比 2015 年面世的雷电 3 虽然在最大速率上没有提升、依然维持在 40Gbps ，但是包含了不少对菊花链设备连接的能力的改进，其中比较显著的就包括支持了双 4K 或单 8K 显示器，并且新增了显示器的透传功能，让支持雷电 4 的显示器不再必须处于菊花链的末尾了。

![Image 19: FUe6b4GVyoTSstxYXfmcT3cIn8d](https://cdnfile.sspai.com/editor/u_/cldc3hdb34tae8ka1490?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

英特尔雷电技术官网的区别列表

### 已经到来的雷电 5 协议新在哪里

随着搭载 M4 Pro、M4 Max 系列的 Mac 上市，搭载雷电 5 的终端也终于登场了。相比雷电 4，雷电 5 比较主要的改动体现在它的动态带宽上。

雷电 5 首先支持了双向 80 Gbps 对等传输，为日后更高要求的传输速度打下基础；其次，雷电 5 还可以利用新的可变带宽机制将一路接收信号改为传送，从而实现单向最高 120Gbps 的数据传输速率的同时，还能向另一个方向提供 40Gbps 的带宽。

![Image 20: 雷雳5](https://cdnfile.sspai.com/2024/10/31/article/95f8a9a9ef7b1f8e2caad0fe2b785f42.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1/format/webp)

得益于更大的带宽，雷电 5 可以只用一根线就可以连接到三个 4K 144Hz的显示器，或者两个 6K 或 8K 显示器，甚至是一台 540Hz 刷新率的显示器，充分满足「一线牵」的需求。

此外雷电 5 还新增了看齐 USB-PD 3.1 标准的 240W 充电功率4，且线缆至少能传输 140W 的功率5；而雷电网桥也从原先的 32Gbps 翻倍到了 64Gbps，理论上支持更快的雷电局域网等等。

![Image 21](https://cdnfile.sspai.com/2024/10/31/ac1240e56f11daf15396a90359f4792c.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1/format/webp)

可以看到，雷电 5 整个设计明显更未来，但随着搭载雷电 5 的终端登场，相信相关生态也会逐渐丰富起来，配合 USB4 80Gbps 版本高速传输将不是梦。

### 雷电协议的特色功能

除了单纯传输速率上的区别之外，雷电协议还支持自己独特的菊花链（Daisy Chain）连接模式，即允许通过支持雷电协议的数据线将至多六台雷电设备串联起来，从而显著节省主设备——比如接口有限的笔记本电脑——被占用的接口数量，这也是 USB 标准无法向上涵盖的区别性功能之一：

![Image 22: CA2hbbUhHo1DEWxXulhcqp7Sngh](https://cdnfile.sspai.com/editor/u_/cldc3i5b34taeapqr2tg?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

即单根菊花链上最多可以支持一台雷电主机与 5 台雷电外设

不过，虽然现行的雷电 4 协议提供了非常丰富的多功能使用场景，但是想要用一台雷电设备像交换机那样给多台设备之间架网桥从而省下万兆网卡的钱目前仍然是不可行的，其根本原因是雷电协议中的每个主机端口只能建立一个合法网桥，因此使用雷电网桥的设备组成局域网在拓扑结构上依然需要保持为一条菊花链，而不能是交换机那样的星形结构。

对于最近几代基于 Type-C 接口的雷电和 USB 协议，我们可以概括地认为：**拥有雷电认证的设备或者线材通常都可以兼容 USB ，但并不是所有的 USB 设备都能向上满足雷电的需求。**

USB-C 线究竟怎么选
------------

在绕了这么大一圈之后，我们还是需要回到自己手中正在使用的设备上。前面曾经提到，从去年 9 月开始 USB-IF 引入了又一套新的命名标准，去掉了此前 USB 2、3、4 的版本数字，而是统一以最大传输速率来命名。抛开比较古早的 USB 1.0 和 2.0 ，我们正在使用的 USB 设备以后会被全部归属到 USB 5Gbps、10Gbps、20Gbps、40Gbps 和 80Gbps 这五个分类下——比如按照最新的叫法，iPhone 15 Pro 使用的传输协议就是 USB 10Gbps 接口，但 iPhone 15 依然只能叫 USB 2.0 。

这样单纯使用速率命名有帮助厘清混乱吗？有，但不多，因为它依然没有解决我们需要记住新旧两种命名方式之间的换算关系，只能说如果 USB-IF 此后可以坚持用速率命名的话几年之后或许才能真正起到拨乱反正的效果。因此在之后很长的一段时间内，我们依然是需要牢记这张 USB 换算表的：

![Image 23: TLI2boMzMoU2T6xpMIKcVn2Mnoe](https://cdnfile.sspai.com/editor/u_/cldc3idb34tae8ka149g?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

与此同时，对于 USB 的充电功能来说，上述的介绍全部是基于规范的 USB-PD 协议，而非国内主流手机厂商山头林立的私有快充协议。对于你手里只支持 USB-PD 的电子设备来说，这些使用私有快充协议的线缆或者电源大多只能提供 15W 乃至 7.5W 的最低兼容性，在最坏的情况下则可能出现无法工作乃至烧坏电子产品的潜在问题。

因此从最大兼容性的角度考虑，如果你希望找到一根能够同时兼任高功率充电、高速数据传输、音视频传输的数据线的话，高规格的双 Type-C 口 USB 协议线缆是最好的选择。至于是否需要规格更高的雷电线，则主要取决于你手中支持雷电协议的设备有多少。

### 单纯的充电

因此，如果你只是单纯在寻找一根使用 Type-C 接口的充电线，不要求它有什么数据传输能力的话，那么市面上绝大多数正规品牌生产销售的充电线都可以满足这样的需求，此时你只需要关注它们支持的是何种充电协议即可，比如是品牌的私有快充还是 USB-PD ，是 3A 线还是 5A 线等等。以闪极 67W 充电器附赠的这根充电线为例，可以看到它使用的并非 24 针脚 Type-C 接口，而是 16 针脚，因此数据传输速度只有 USB 2.0 的 480 Mbps ，但充电功率就是标定的 67W 了。

因此从实用角度出发，如果不是必须要用到 5A 的电流，那么现在比较常见的 3A 60W 数据线基本上就可以满足 USB-PD 框架下绝大多数我们日常会使用到的设备了，因为线材会柔软和便携许多。不过随着工艺的进步，市面上也有了一些高规格且便携的 5A 100W 线，差不多达成了便携性、功能性与兼容性的完美统一。另外需要注意的是**从 2021 年 12 月开始，USB-IF 其实就不再为 C-C 数据线提供 100W 的充电认证了，原本的 100W 认证会被 USB-PD 3.1 标准下的 240W 认证所取代。**

![Image 24: UYqLbYikaomctdx9chlc1tqXnzd](https://cdnfile.sspai.com/editor/u_/cldc3ilb34taeapqr2u0?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

只不过对于你手中兼容标准 USB-PD 协议的电子设备来说，最好不要轻易选择带「私有快充协议」的 A-C 充电线，因为 Type-A 接口在 USB-IF 给出的设计标准中最大也只能提供 7.5W 的充电功率，所有明显高出这个功率的充电协议大多都是对接口的针脚作出了修改的，使用不当就有可能会导致其他设备的故障。

![Image 25: CfZ0bCQ6RoLNaZxxHujcxegWnYb](https://cdnfile.sspai.com/editor/u_/cldc3j5b34taeapqr2ug?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

比如某品牌的 33W 和 22.5W A-C 快充线，其两侧的触点就明显宽于标准的 USB Type-A（最左）

纯充电线的另一种选择就是看准 USB-PD 协议中最高的 PD 3.1 240W 功率入手，可选的比如贝尔金的 5A 240W 编织线，可以喂饱手中任何支持 PD 充电协议的电子设备（前提是有适配的高功率充电头），并且这些符合 PD 3.1 认证的充电线同时也都兼容最高 USB 2.0 480Mbps 的数据传输能力，应急当一下数据线也未尝不可。

![Image 26: VtSgbwW9OoRpwhxUT9bc8yfgn9e](https://cdnfile.sspai.com/editor/u_/cldc3jdb34taeen1qa7g?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

### 兼顾充电和数据传输

假如你手边有经常使用的 USB 数据存储设备，想要兼顾不同设备之间的高功率充电以及高速数据传输，甚至是偶尔想要用这根线来连接一些 USB-C 显示器什么的，那么一根至少达到 USB 5Gbps 速率、60W 以上 PD 充电、支持 DP 或 HDMI 备用模式的所谓「全功能数据线」就是你应该考虑的了。

对于这样的需求，我个人使用的性价比最高的方案就是这两款来自立讯的 22 脚全功能数据线了，其中白色的 3A 线支持 60W PD 充电，最高传输速率为 USB 10Gbps，黑色的 5A 线则支持到了 100W 与 USB 20Gbps ，也都可以进行 4K 60 帧的视频传输。两者目前都可以直接在电商平台以「立讯代工」等关键词查询到，每根的价格普遍在 20 元以下，完全足以涵盖给设备充电、连接移动硬盘和连接显示器三种最主要使用场景。

![Image 27](https://cdnfile.sspai.com/2023/11/20/3264c0e7d0325a8d3a11854fc153afe5.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1/format/webp)

重要的是无论是 3A 还是 5A 款都足够柔软，便携带出门是足够的

如果还是倾向于购买具有明确品牌的线材，那么奥睿科这根全功能的 USB-C 编织线也是我目前在使用的产品之一。它同样支持最高 USB 20Gbps 的数据传输、5A 100W PD 充电以及 4K 60 帧的投屏，1 米的版本电商售价为 50 元左右，最主要的是编织线会比上面立讯两款塑胶线更加耐用一些。

![Image 28: NZpBb6mGhoKC2WxMfekcionpnqb](https://cdnfile.sspai.com/editor/u_/cldc3l5b34tae8ka14a0?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

此外，2024 年的今天现在市面上还出现了一些 USB 3.2/USB4 20Gbps、支持 240W PD 3.1 功率的**细直径**高规格数据线。相比于之前的版本更易弯折和携带，有喜欢的读者也可以关注下。

### 雷电 USB 我全都要

随着 [Apple Thunderbolt 5 (USB‑C) Pro 连接线](https://www.apple.com/hk-zh/shop/product/MC9C4FE/A/thunderbolt-5-usb%E2%80%91c-pro-%E9%80%A3%E6%8E%A5%E7%B7%9A-1-%E7%B1%B3)上架，眼下可以满足雷电 + USB 连接需求的线缆不再只有速率上限 40Gbps 的雷电 4 数据线了。在财力允许的情况下，那么来自 Apple 官方的雷雳 5 Pro 连接线也的确是一个可行的选择，应该是兼容性较好、适用于大多数场景的全功能线缆；截止本文更新时只有被动版 1m 长度可选，最高可达 120Gb/s、USB 4 数据传输最快 80Gb/s，支持 DP 2.1 UHBR20 传输模式，还支持 240W 电力传输。

![Image 29: Thunderbolt 5 Pro 連接線 (1 米) 採用捲起時不易纏繞的黑色編織設計，支援快達每秒 40 gigabyte 的數據傳輸。](https://cdnfile.sspai.com/2024/10/31/article/384a8465b485731fa11efafe20d7adde.jpeg?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1/format/webp)

如果你考虑雷电 4 协议的话，贝尔金的 INZ 系列雷电线可能也是个不错的选择，虽然充电功率依然是 100W PD ，但是 1 米的雷电 4 被动线（INZ003）仅需 300 块钱左右，2 米的主动线（INZ002）则为 550 元。

![Image 30: N9CGbuXnKojMrLxOIipcuJYknTg](https://cdnfile.sspai.com/editor/u_/cldc3ldb34tae2qbfaag?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

总之当一切都尘埃落定，你可以看到手中的数据线与它两边的设备都在以最大效率工作的时候，依然要记住：Type-C 只不过是一个形状，它背后的数据、音视频或电源协议才是决定其工作方式的本源，选择数据线绝非只是「看形状」。

\> 下载 [少数派 2.0 客户端](https://sspai.com/page/client)、关注 [少数派公众号](https://sspai.com/s/J71e)，解锁全新阅读体验 📰

\> 实用、好用的 [正版软件](https://sspai.com/mall)，少数派为你呈现 🚀
