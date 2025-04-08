Title: 如何满足小众的录屏需求？自己配置 FFmpeg 解决问题 - 少数派

URL Source: https://sspai.com/post/76637

Published Time: 2022-11-05T03:00:00.000Z

Markdown Content:
如何满足小众的录屏需求？自己配置 FFmpeg 解决问题 - 少数派
===============

[](https://sspai.com/)

[共创](https://sspai.com/create)

[PRIME](https://sspai.com/prime)

[Matrix](https://sspai.com/matrix)

[栏目](https://sspai.com/series)

Pi Store

无需申请，自由写作

任何用户都可使用写作功能。成功发布 3 篇符合基本规则的内容，可成为正式作者。[了解更多](https://manual.sspai.com/guide/init/)

共创PRIMEMatrix栏目Pi Store

![Image 6](https://cdnfile.sspai.com/editor/u_/cdii80lb34tcpvhjl0lg?imageMogr2/auto-orient/quality/90/ignore-error/1)

如何满足小众的录屏需求？自己配置 FFmpeg 解决问题

主作者

[![Image 7: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!72x72r/gravity/center/crop/72x72/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 8](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

迷信新工具，热衷于研究开源软件、心理学理论，定期分享探索成果

[清顺 [![Image 9](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者 迷信新工具，热衷于研究开源软件、心理学理论，定期分享探索成果](https://sspai.com/u/zqj05i4v/updates)

联合作者

[![Image 10: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!72x72r/gravity/center/crop/72x72/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 11](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

迷信新工具，热衷于研究开源软件、心理学理论，定期分享探索成果

[清顺 [![Image 12](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者 迷信新工具，热衷于研究开源软件、心理学理论，定期分享探索成果](https://sspai.com/u/zqj05i4v/updates)

2022/11/05 03:00

开始自我监控后，录屏工具的重要性急速提升，我遇到的问题也越来越多。

疫情封控两个月后，我对自己开始 24 ...

经过几天的自我监控后，我对于自己的活动有了更清晰的认知，方...

[sspai.com](https://sspai.com/post/73362)

![Image 13](https://cdnfile.sspai.com/2022/05/22/9a850394d70ef92ba3c50d4274986908.jpg)

因为我录屏主要是为了自我监控，所以我需要的帧率并不用很高，甚至越低越好，分辨率同样不必和屏幕一致，能看清我在做什么即可。最初，我用了免费开源的 [VLC](https://sspai.com/link?target=https%3A%2F%2Fwww.videolan.org%2Fvlc%2F)，这也是我文章里采用的方案。它能调节输出视频的编码、帧率、格式，但操作麻烦不说，还不能同时录屏和摄像头，暂停录制容易程序崩溃。

然后，我试了 [OBS](https://sspai.com/link?target=https%3A%2F%2Fobsproject.com%2F)，它的录制功能极其强大，可以任意添加摄像头、文字、图像等，但输出限制多，生成的视频过大。同时，OBS 不支持录制画面与直播画面分开，而我平常习惯边开直播边工作，这令我只能放弃 OBS 录屏。

接着，我遇到 7.8k Star 的 [Capture](https://sspai.com/link?target=https%3A%2F%2Fgithub.com%2FMathewSachin%2FCaptura%2Freleases%2Ftag%2Fv8.0.0)，它的自由度较高，能自定义叠加元素，然而项目已于 2018 年停止更新，使用时经常碰到莫名其妙的报错，很不稳定。

免费的不行，那收费的会不会好点呢？

我用 [Bandicam](https://sspai.com/link?target=https%3A%2F%2Fwww.bandicam.cn%2F) 录了一周的视频。与 Capture 相比，Bandicam 的稳定性好了很多，不会突然崩溃，还能降噪，内录扬声器音频，但它时不时丢失摄像头，导致无法自动进行录屏。

再后，我测试了其他几款录屏应用：

*   相机：Windows 自带应用，录制方便，但输出选项少，限制多。
*   [FlashBack Express](https://sspai.com/link?target=https%3A%2F%2Fwww.flashbackrecorder.com%2Fzh%2Fexpress%2F)：能调节帧率，镜像，虚化背景，但免费版只支持 2 小时内的录制。
*   [Mirillis Action!](https://sspai.com/link?target=https%3A%2F%2Fmirillis.com%2Fzh%2Fproducts%2Faction.html)：高帧率录制游戏，自动分割视频，自定义叠加元素，但输入帧率不能自由调整，最低只能 15 帧，试用期 30 天。
*   [oCam](https://sspai.com/link?target=https%3A%2F%2Fohsoft.net%2Feng%2Focam%2Fintro.php%3Fcate%3D1002)：打着免费招牌但有弹窗广告，且输出视频偏大。
*   [ShareX](https://sspai.com/link?target=https%3A%2F%2Fgetsharex.com%2F)：免费开源强大的截图软件，具备录屏功能，能调节编码和帧率，但只能单一录屏或录像。

我一共试了 9 款录屏软件，体验都不算好，软件普遍存在无法自定义画面、不兼容、稳定性低的问题。再加上自我监控方案的单次录制时间在 12 小时以上，理想的帧率（0.02 帧）远超出应用最低 15-30 帧的下限。因此，我需要另找一款稳定能兼容自由度高，又能自由定制录屏方案的工具，最终找到的是这些录屏工具共同的父母：FFmpeg。

为什么 FFmpeg
----------

FFmpeg 是处理多媒体内容（如音频、视频、字幕和相关元数据）的库和工具的集合，支持在 Linux、macOS 和 Windows 全平台运行。它提供了录制、转换以及流化音视频的完整解决方案。

之前那些录屏、视频处理工具几乎都是基于 FFmpeg 而开发的。FFmpeg 能实现它们所有的功能，同时具备超高的稳定性和兼容性。现成的录屏应用与 FFmpeg 相比，优势只在于其美观的界面和简单易上手的录制方案。

如果你想跳出软件的限制，自由的定制录屏方案，避免莫名其妙的 bug，更加底层的 FFmpeg 反而是更稳定有效的方案。命令行录制看起来复杂，但实际上只需要熟悉十几个参数，你就能定制专属录屏方案，个人体验感觉比熟悉 Bandicam 的软件界面更简单。

下面以我的 Windows 桌面录制方案为例，从多屏幕中指定一个 2k 区域进行录制，并在画面右下角添加 360p 的摄像头录制角度，然后以帧率 0.02 输出监控视频。按 `q` 则停止录制。

![Image 14: boxcnOTvcNypfpA6wac40fLKKKd](https://cdnfile.sspai.com/editor/u_/cdii815b34tcqo565olg?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

输出画面如图例

录屏准备
----

### 配置 FFmpeg

1.  下载最新版 [FFmpeg](https://sspai.com/link?target=https%3A%2F%2Fgithub.com%2FBtbN%2FFFmpeg-Builds%2Freleases%2Ftag%2Flatest)，Windows 环境选择 `ffmpeg-master-latest-win64-gpl.zip`，GPL 版本包含了所有依赖项。
2.  将 FFmpeg 解压到任意文件夹，比如 `D:\Backup\Libraries\Documents\ffmpeg`。
3.  开始栏搜索「编辑系统环境变量」，点击进入「环境变量」。
4.  新建用户变量 `FFMPEG_HOME`，变量值设为刚才的解压路径 `D:\Backup\Libraries\Documents\ffmpeg`。

![Image 15: boxcn9Y5dfJbBiiuWteMoOB2xEe](https://cdnfile.sspai.com/editor/u_/cdii81db34tcqo565om0?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

配置完成后，在终端输入 ffmpeg 即可启动。

![Image 16: boxcnC51TlAjuqBGQ25WXQwChb3](https://cdnfile.sspai.com/editor/u_/cdii81lb34tcpvhjl0m0?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

### 配置视频/音频设备

FFmpeg 的录制命令 gdigrab 不支持音频录制，也不支持直接调用摄像头，此时需使用开源的 [screen-capture-recorder-to-video-windows-free](https://sspai.com/link?target=https%3A%2F%2Fgithub.com%2Frdp%2Fscreen-capture-recorder-to-video-windows-free%2Freleases) 增强 FFmpeg 的录制功能，其最新版本为 0.12.12。

通过命令 `ffmpeg -list_devices true -f dshow -i dummy` 查看支持的 Windows DirectShow 输入设备，采集视频和音频设备，包含设备名称，设备类型等信息1

ffmpeg 录屏命令，参考 [https://blog.csdn.net/m0\_60352504/article/details/126762161](https://sspai.com/link?target=https%3A%2F%2Fblog.csdn.net%2Fm0_60352504%2Farticle%2Fdetails%2F126762161)

。比如我这里得到了视频设备「V380 FHD Camera」和音频设备「Analogue 1/2 (Audient iD4)」，之后会用到。

![Image 17: boxcn6Roa6QiY7xhrKVdXdnxxjg](https://cdnfile.sspai.com/editor/u_/cdii81tb34tcqo565omg?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

录制屏幕
----

从坐标 0:0 开始圈定出一个 2560x1440 的屏幕范围，然后以每 50 秒截图 1 帧，输出为 mp4 格式的视频，录制命令为： `ffmpeg -f gdigrab -r 20/1001 -draw_mouse 1 -offset_x 0 -offset_y 0 -video_size 2560x1440 -i desktop -s 1280x720 output.mp4`

以下是录制命令的说明：

*   `-f gdigrab` 使用 FFmpeg 内置屏幕录制命令 [gdigrab](https://sspai.com/link?target=https%3A%2F%2Fffmpeg.org%2Fffmpeg-all.html%23gdigrab)，录制对象可为全屏、指定范围和指定程序。
*   `-r 20/1001` 帧率为 0.02，每 50 秒录制 1 帧。主流大家喜欢用 `-r 30` 录制，我这因为是每日监测视频，用了超低帧率。
*   `-c:v libx264` 是用于设置视频编解码器，一般可不填使用默认配置，`-c:a` 为音频编码。2
    
    libx265 编码说明 [https://ffmpeg.org/ffmpeg-codecs.html#libx265](https://sspai.com/link?target=https%3A%2F%2Fffmpeg.org%2Fffmpeg-codecs.html%23libx265)
    
*   `-draw_mouse 1` 在 gdigrab 录制的视频中显示鼠标。
*   `-offset_x 0 -offset_y 0 -video_size 2560x1440` 为起始坐标和选定录制范围。坐标可使用截图软件获取，比如我用 Snipaste，点击 F1 后进入截图界面，鼠标经过当前区域就会显示坐标。
*   `-s 1280x720` 用 scale 方法，设置视频分辨率为 720p。
*   `-i desktop` 为输入设备，指代显示屏。
*   `out.mp4` 为输出视频的名字与格式。默认保存在命令运行文件夹，可以在此处设置输出位置，如 `D:\Backup\Libraries\Desktop\out.mp4`。

除上方命令外，FFmpeg 还有许多参数可以设置，比如 `-pix_fmt yuv420p -preset ultrafast` 提升编码速度，`-filter:v "setpts=0.1*PTS"` 减少视频抽样，但 setpts 不是视频加速，对于低帧率的视频影响很小。3

x265 的 preset 与编码速度、视频画质以及比特率的关联 [https://magiclen.org/x265-preset/](https://sspai.com/link?target=https%3A%2F%2Fmagiclen.org%2Fx265-preset%2F) FFmpeg 音视频倍速控制 [https://blog.csdn.net/zhying719/article/details/123059209](https://sspai.com/link?target=https%3A%2F%2Fblog.csdn.net%2Fzhying719%2Farticle%2Fdetails%2F123059209)

录制摄像头
-----

然后，我们使用上方获取的视频设备，即可用摄像头进行录制，如： `ffmpeg -f dshow -i video="V380 FHD Camera" output.mp4`

如果录屏的同时需要录制音频，则在命令中加入之前获取的音频设备，命令变为： `ffmpeg -f dshow -i audio="Analogue 1/2 (Audient iD4)" -f dshow -i video="V380 FHD Camera" output.mp4`

输出视频：画中画
--------

清楚如何用 FFmpeg 录制屏幕、摄像头和音频后，我需要将他们放置于同一画面中，将摄像头画面放在录制画面的右下侧，并用 overlay 方法将其置于屏幕画面的上方，遮挡对应区域。4

FFmpeg 中 overlay 滤镜用法 - 水印及画中画 [https://www.cnblogs.com/leisure\_chn/p/10434209.html](https://sspai.com/link?target=https%3A%2F%2Fwww.cnblogs.com%2Fleisure_chn%2Fp%2F10434209.html) ffmpeg 调整缩放裁剪视频的基础知识 [https://blog.csdn.net/guanyijun123/article/details/121270650](https://sspai.com/link?target=https%3A%2F%2Fblog.csdn.net%2Fguanyijun123%2Farticle%2Fdetails%2F121270650)

综合了以上三步，最终的录制命令为： `ffmpeg -f gdigrab -r 1 -draw_mouse 1 -offset_x 0 -offset_y 0 -video_size 2560x1440 -i desktop -s 1280x720 -b:v 0 -crf 32 output.mp4 -f dshow -i audio="Analogue 1/2 (Audient iD4)" -f dshow -s 640x360 -i video="V380 FHD Camera" -filter_complex "overlay=W-w-1:H-h-1" -y`

*   `-b:v 0 -crf 32` 是将视频比特率设置为最小，同时使用恒定质量，CRF5
    
    固定码率因子
    
     的范围可以从 0（最佳质量）到 63（最小文件大小）。
*   `overlay=W-w-1:H-h-1` 这是一个坐标，指浮层放在右下角，距离边缘 1px。
*   `-y` 遇到选项时，默认执行 yes 命令，比如覆盖同名的视频文件。

命令中的录制帧率较低，但不会影响同时录制的音频。之后的录屏只需在终端中运行这段命令，就会自动录制屏幕，按 `q` 即可停止录制。使用 FFmpeg 后，我的录屏再也没有莫名其妙的崩溃了。

常见问题
----

### Could not set video options

报错 `Could not set video options`，多是由于录制设置的帧率、分辨率超出设备范围造成的。使用命令 `ffmpeg -f dshow -list_options true -i video="V380 FHD Camera" -loglevel debug` 检查设备的输出属性，调整录制属性。

### real-time buffer

报错 `real-time buffer [xxxxxx] [video input] too full or near too full (181% of size: 3041280 [rtbufsize parameter])! frame dropped!`，解决方案参考 [issue 136](https://sspai.com/link?target=https%3A%2F%2Fgithub.com%2Frdp%2Fscreen-capture-recorder-to-video-windows-free%2Fissues%2F136)。我未修复成功，不过也未影响视频录制。

### 摄像头分辨率错误

如果摄像头画面出现裁切，分辨率与预想不同，则检查摄像头录制属性和摄像头应用输出分辨率。例如部分版本的 SplitCam Video Driver 对外场景尺寸被固定为 4:3，导致输出画面被裁剪，只能更换其他视频输入源。

### 录制画面偏移

录制画面比例异常或画幅偏移，这是 Windows 的屏幕缩放造成的，勾选 ffmpeg.exe 的属性「高 DPI 缩放替代」即可解决。

后续
--

如果读了 FFmpeg 的文档，就会发现这个工具异常强大，很多采用 FFmpeg 的工具都没有将它的功能性发挥到极致，用比较普适的功能尽可能地换取了软件操作的易用性。而相应地，如果和我一样，有一个比较小众，甚至特殊的需求，已经打包好的图形界面应用就很有可能力有不逮。这时，FFmpeg 这种底层的命令行工具可能就是唯一选择，而且用了就会发现，它在功能强大的同时还更加稳定，自定义能力也更强。而且如果跨过了起初对于命令行的恐惧，理解和上手其实也不算多难。

而且，FFmpeg 的功能不止录屏，它还有诸如连续截图、视频转帧率改大小等多种玩法，非常强大。

前几天，群里有人分享了快速生成 FFmpeg 命令的工具 [FFmpeg.guide](https://sspai.com/link?target=https%3A%2F%2Fffmpeg.guide%2F)。本以为能帮新手快速入门，使用后却感觉完全不实用。FFmpeg 最快入门的方法还是得看[官方文档](https://sspai.com/link?target=https%3A%2F%2Fffmpeg.org%2Fffmpeg.html)，也有一些爱好者整理翻译了相关的中文/视频教程。前期会耗费些时间，但只要定制好自己要的代码，之后能一直用，需求不变命令也就不会变。

当然，这篇文章的目的是分享我监控自己的延伸，分享使用 FFmpeg 录屏的入门方法，而非完全掌握，因此只介绍了录屏相关的核心代码。如果有需要，还是推荐研究一下官方文档，或者跟着我做的试一试，说不定就有新收获。

#### 关联阅读

*   [闭关家中，我将监控摄像对准了自己](https://sspai.com/post/73362)
*   [Zoom 会议摸鱼学](https://sspai.com/post/71404)
*   [一日一技 | 妙用 Keynote 实现数据可视化](https://sspai.com/post/76001)

\> 下载 [少数派 2.0 客户端](https://sspai.com/page/client)、关注 [少数派公众号](https://sspai.com/s/J71e)，解锁全新阅读体验 📰

\> 实用、好用的 [正版软件](https://sspai.com/mall)，少数派为你呈现 🚀

*   1ffmpeg 录屏命令，参考 https://blog.csdn.net/m0\_60352504/article/details/126762161
*   2libx265 编码说明 https://ffmpeg.org/ffmpeg-codecs.html#libx265
*   3x265 的 preset 与编码速度、视频画质以及比特率的关联 https://magiclen.org/x265-preset/ FFmpeg 音视频倍速控制 https://blog.csdn.net/zhying719/article/details/123059209
*   4FFmpeg 中 overlay 滤镜用法 - 水印及画中画 https://www.cnblogs.com/leisure\_chn/p/10434209.html ffmpeg 调整缩放裁剪视频的基础知识 https://blog.csdn.net/guanyijun123/article/details/121270650
*   5固定码率因子

[](https://sspai.com/s/JYjP)

105

41

[](https://service.weibo.com/share/share.php?url=https%3A%2F%2Fsspai.com%2Fpost%2F76637?ref=weibo&title=%E3%80%90%E5%A6%82%E4%BD%95%E6%BB%A1%E8%B6%B3%E5%B0%8F%E4%BC%97%E7%9A%84%E5%BD%95%E5%B1%8F%E9%9C%80%E6%B1%82%EF%BC%9F%E8%87%AA%E5%B7%B1%E9%85%8D%E7%BD%AE%20FFmpeg%20%E8%A7%A3%E5%86%B3%E9%97%AE%E9%A2%98%E3%80%91%E5%BD%93%E6%89%80%E6%9C%89%E7%9A%84%E5%BD%95%E5%B1%8F%E5%BA%94%E7%94%A8%E9%83%BD%E6%97%A0%E6%B3%95%E6%BB%A1%E8%B6%B3%E6%88%91%E6%97%B6%EF%BC%8C%E6%88%91%E7%9A%84%E7%9B%AE%E5%85%89%E6%8A%95%E5%90%91%E4%BA%86%E9%82%A3%E4%B8%AA%E6%9C%80%E7%BB%88%E6%9E%81%E7%9A%84%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%EF%BC%8CFFmpeg%E3%80%82%EF%BC%88%E6%9D%A5%E8%87%AA%20%40%E5%B0%91%E6%95%B0%E6%B4%BEsspai%EF%BC%89%E5%85%A8%E6%96%87%EF%BC%9A&pic=https%3A%2F%2Fcdnfile.sspai.com%2Feditor%2Fu_%2Fcdii80lb34tcpvhjl0lg%3FimageMogr2%2Fauto-orient%2Fquality%2F90%2Fignore-error%2F1&appkey=3196502474#)

扫码分享

本文责编：@[北鸮](https://sspai.com/u/thebaldingken)

© 本文著作权归作者所有，并授权少数派独家使用，未经少数派许可，不得转载使用。

[#热门文章](https://sspai.com/tag/%E7%83%AD%E9%97%A8%E6%96%87%E7%AB%A0)

[#效率工具](https://sspai.com/tag/%E6%95%88%E7%8E%87%E5%B7%A5%E5%85%B7)

105

[![Image 18: Fergie](https://cdnfile.sspai.com/2022/04/05/avatar/264c8b5944ceb14206e8d8f02ad7044d.png?imageMogr2/auto-orient/thumbnail/!32x32r/gravity/center/crop/32x32/format/webp/ignore-error/1)](https://sspai.com/u/Fergie/updates)

[![Image 19: Mosaic](https://cdnfile.sspai.com/2022/04/02/d1b0caf6026a84e7c2235a2c8fdfd9b5.jpeg?imageMogr2/auto-orient/thumbnail/!32x32r/gravity/center/crop/32x32/format/webp/ignore-error/1)](https://sspai.com/u/yarcpteh/updates)

[![Image 20: Chessboard](https://cdnfile.sspai.com/2025/02/27/avatar/b50bed44513bc2ca21b01aea59dd4400.png?imageMogr2/auto-orient/thumbnail/!32x32r/gravity/center/crop/32x32/format/webp/ignore-error/1)](https://sspai.com/u/td6a1kto/updates)

[![Image 21: 奕哦](https://cdnfile.sspai.com/2022/07/04/73617dc52e1508e72a186aec23ed0c32.jpeg?imageMogr2/auto-orient/thumbnail/!32x32r/gravity/center/crop/32x32/format/webp/ignore-error/1)](https://sspai.com/u/r1oq6j9n/updates)

[![Image 22: Force647](https://cdnfile.sspai.com/2022/12/06/17f54c60b31eea2371434acd3d7ad2c2.jpg?imageMogr2/auto-orient/thumbnail/!32x32r/gravity/center/crop/32x32/format/webp/ignore-error/1)](https://sspai.com/u/timnv0gq/updates)

[Fergie](https://sspai.com/u/Fergie/updates)、[Mosaic](https://sspai.com/u/yarcpteh/updates)、[Chessboard](https://sspai.com/u/td6a1kto/updates) 等 105 人为本文章充电

[](https://service.weibo.com/share/share.php?url=https%3A%2F%2Fsspai.com%2Fpost%2F76637?ref=weibo&title=%E3%80%90%E5%A6%82%E4%BD%95%E6%BB%A1%E8%B6%B3%E5%B0%8F%E4%BC%97%E7%9A%84%E5%BD%95%E5%B1%8F%E9%9C%80%E6%B1%82%EF%BC%9F%E8%87%AA%E5%B7%B1%E9%85%8D%E7%BD%AE%20FFmpeg%20%E8%A7%A3%E5%86%B3%E9%97%AE%E9%A2%98%E3%80%91%E5%BD%93%E6%89%80%E6%9C%89%E7%9A%84%E5%BD%95%E5%B1%8F%E5%BA%94%E7%94%A8%E9%83%BD%E6%97%A0%E6%B3%95%E6%BB%A1%E8%B6%B3%E6%88%91%E6%97%B6%EF%BC%8C%E6%88%91%E7%9A%84%E7%9B%AE%E5%85%89%E6%8A%95%E5%90%91%E4%BA%86%E9%82%A3%E4%B8%AA%E6%9C%80%E7%BB%88%E6%9E%81%E7%9A%84%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%EF%BC%8CFFmpeg%E3%80%82%EF%BC%88%E6%9D%A5%E8%87%AA%20%40%E5%B0%91%E6%95%B0%E6%B4%BEsspai%EF%BC%89%E5%85%A8%E6%96%87%EF%BC%9A&pic=https%3A%2F%2Fcdnfile.sspai.com%2Feditor%2Fu_%2Fcdii80lb34tcpvhjl0lg%3FimageMogr2%2Fauto-orient%2Fquality%2F90%2Fignore-error%2F1&appkey=3196502474#)

扫码分享

[](https://getpocket.com/edit?url=https%3A%2F%2Fsspai.com%2Fpost%2F76637)[](http://www.instapaper.com/hello2?url=https%3A%2F%2Fsspai.com%2Fpost%2F76637&title=%E5%A6%82%E4%BD%95%E6%BB%A1%E8%B6%B3%E5%B0%8F%E4%BC%97%E7%9A%84%E5%BD%95%E5%B1%8F%E9%9C%80%E6%B1%82%EF%BC%9F%E8%87%AA%E5%B7%B1%E9%85%8D%E7%BD%AE%20FFmpeg%20%E8%A7%A3%E5%86%B3%E9%97%AE%E9%A2%98&description=%E5%BD%93%E6%89%80%E6%9C%89%E7%9A%84%E5%BD%95%E5%B1%8F%E5%BA%94%E7%94%A8%E9%83%BD%E6%97%A0%E6%B3%95%E6%BB%A1%E8%B6%B3%E6%88%91%E6%97%B6%EF%BC%8C%E6%88%91%E7%9A%84%E7%9B%AE%E5%85%89%E6%8A%95%E5%90%91%E4%BA%86%E9%82%A3%E4%B8%AA%E6%9C%80%E7%BB%88%E6%9E%81%E7%9A%84%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%EF%BC%8CFFmpeg%E3%80%82)

举报本文章

举报

[![Image 23: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!84x84r/gravity/center/crop/84x84/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[清顺](https://sspai.com/u/zqj05i4v/updates)

迷信新工具，热衷于研究开源软件、心理学理论，定期分享探索成果

关注

全部评论(41)

热门排序

![Image 24](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)

请在登录后评论...

[![Image 25: 不高山神](https://cdnfile.sspai.com/2022/04/13/f19fde401d36c21c57553f51f81e3a3d.jpg?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/ayz19x2z/updates)

[![Image 26](https://cdnfile.sspai.com/2022/04/13/f19fde401d36c21c57553f51f81e3a3d.jpg?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/ayz19x2z)关注

不高山神

[不高山神 [![Image 27](https://cdnfile.sspai.com/2022/04/13/f19fde401d36c21c57553f51f81e3a3d.jpg?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/ayz19x2z)关注 不高山神](https://sspai.com/u/ayz19x2z/updates)

2022/11/05 03:45

楼主写的很棒，这个需求也挺普遍。之前看有些人就用quicker来封装ffmpeg的命令，来实现自己个性化的需求，不用自己去写GUI，调用起来就更方便了。

161举报2022/11/05 03:45

[![Image 28: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 29](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 30](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/05 04:28

这个不错，简化了 FFmpeg 视频剪辑的难度

00举报2022/11/05 04:28

[![Image 31: 小燕子](https://cdnfile.sspai.com/2023/01/04/0216d80fce772297e40ac63c6ca65d66.jpg?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/rz4llyqs/updates)

[![Image 32](https://cdnfile.sspai.com/2023/01/04/0216d80fce772297e40ac63c6ca65d66.jpg?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/rz4llyqs)关注

小燕子

少数派作者

[小燕子 [![Image 33](https://cdnfile.sspai.com/2023/01/04/0216d80fce772297e40ac63c6ca65d66.jpg?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/rz4llyqs)关注 小燕子 少数派作者](https://sspai.com/u/rz4llyqs/updates)

2022/11/05 03:56

我之前用这个来批量转格式来着。。。因为是直接看的教程，没想到功能这么强大

120举报2022/11/05 03:56

[![Image 34: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 35](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 36](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/05 04:26

真正的 All in one，市面上音视频、流媒体处理的底层基本都是它。FFmpeg 唯一的缺点就是有门槛，需要花些时间入门参数命令。

30举报2022/11/05 04:26

[![Image 37: 小小白201302](https://cdnfile.sspai.com/2022/12/01/83b361aa443cb6d30870cf3346ec4b8f.gif?imageMogr2/auto-orient/quality/90/ignore-error/1)](https://sspai.com/u/esv91bt0/updates)

[![Image 38](https://cdnfile.sspai.com/2022/12/01/83b361aa443cb6d30870cf3346ec4b8f.gif?imageMogr2/auto-orient/quality/90/ignore-error/1)](https://sspai.com/u/esv91bt0)关注

小小白201302

少数派作者

[小小白201302 [![Image 39](https://cdnfile.sspai.com/2022/12/01/83b361aa443cb6d30870cf3346ec4b8f.gif?imageMogr2/auto-orient/quality/90/ignore-error/1)](https://sspai.com/u/esv91bt0)关注 小小白201302 少数派作者](https://sspai.com/u/esv91bt0/updates)

2022/11/07 06:00

是Captura不是Capture哦

110举报2022/11/07 06:00

[![Image 40: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 41](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 42](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/07 06:16

多谢除虫，我一直看成 e 了

10举报2022/11/07 06:16

[![Image 43: 圆子](https://cdnfile.sspai.com/2022/05/05/a2d64758f943b97a03d44b2e618b52cb.jpeg?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/i3mcnh5s/updates)

[![Image 44](https://cdnfile.sspai.com/2022/05/05/a2d64758f943b97a03d44b2e618b52cb.jpeg?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/i3mcnh5s)关注

圆子

[圆子 [![Image 45](https://cdnfile.sspai.com/2022/05/05/a2d64758f943b97a03d44b2e618b52cb.jpeg?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/i3mcnh5s)关注 圆子](https://sspai.com/u/i3mcnh5s/updates)

2022/11/05 05:34

有木有mac版的录屏软件推荐

110举报2022/11/05 05:34

[![Image 46: 朱小强](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl/updates)

[![Image 47](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl)关注

朱小强

[朱小强 [![Image 48](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl)关注 朱小强](https://sspai.com/u/l4p99oxl/updates)

2022/11/05 15:15

[https://apps.apple.com/cn/app/%E5%BD%95%E5%B1%8F%E4%B8%93%E5%AE%B6omi-%E5%B1%8F%E5%B9%95%E5%BD%95%E5%88%B6%E8%BD%AF%E4%BB%B6/id1592987853?mt=12](https://apps.apple.com/cn/app/%E5%BD%95%E5%B1%8F%E4%B8%93%E5%AE%B6omi-%E5%B1%8F%E5%B9%95%E5%BD%95%E5%88%B6%E8%BD%AF%E4%BB%B6/id1592987853?mt=12)

00举报2022/11/05 15:15

[![Image 49: Zerocat7](https://cdnfile.sspai.com/2023/07/28/avatar/738fd8195bf2eb4a7f14e20667b8fcd2.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zerocat7/updates)

[![Image 50](https://cdnfile.sspai.com/2023/07/28/avatar/738fd8195bf2eb4a7f14e20667b8fcd2.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zerocat7)关注

Zerocat7

[Zerocat7 [![Image 51](https://cdnfile.sspai.com/2023/07/28/avatar/738fd8195bf2eb4a7f14e20667b8fcd2.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zerocat7)关注 Zerocat7](https://sspai.com/u/zerocat7/updates)

2023/05/24 13:17

您好，请问一下您文章中那个配置系统变量的折线标注是使用什么软件做的呢

200举报2023/05/24 13:17

[![Image 52: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 53](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 54](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2023/05/24 13:46

figma

00举报2023/05/24 13:46

[![Image 55: Zerocat7](https://cdnfile.sspai.com/2023/07/28/avatar/738fd8195bf2eb4a7f14e20667b8fcd2.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zerocat7/updates)

[![Image 56](https://cdnfile.sspai.com/2023/07/28/avatar/738fd8195bf2eb4a7f14e20667b8fcd2.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zerocat7)关注

Zerocat7

[Zerocat7 [![Image 57](https://cdnfile.sspai.com/2023/07/28/avatar/738fd8195bf2eb4a7f14e20667b8fcd2.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zerocat7)关注 Zerocat7](https://sspai.com/u/zerocat7/updates)

2023/05/26 14:49

好的哈 ，感谢回复

00举报2023/05/26 14:49

[![Image 58: 少数派18450235](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/8hwefjt2/updates)

[![Image 59](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/8hwefjt2)关注

少数派18450235

[少数派18450235 [![Image 60](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/8hwefjt2)关注 少数派18450235](https://sspai.com/u/8hwefjt2/updates)

2023/03/23 17:05

Windows 相机你确定可以录屏吗？我到相机设置里面看了半天都没有看到。

顶多 Win+G Xbox Bar 录屏

100举报2023/03/23 17:05

[![Image 61: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 62](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 63](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2023/03/23 22:35

是的，录制按钮在右侧

00举报2023/03/23 22:35

[![Image 64: 少数派23540197](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/24jt8cm2/updates)

[![Image 65](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/24jt8cm2)关注

少数派23540197

[少数派23540197 [![Image 66](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/24jt8cm2)关注 少数派23540197](https://sspai.com/u/24jt8cm2/updates)

2023/01/02 12:52

上篇不是说还担心别人云服务有问题, 这来个180大转变啊还直播上了

100举报2023/01/02 12:52

[![Image 67: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 68](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 69](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2023/01/02 22:50

直播是用来监督的，不会显示桌面内容；录屏给自己看的，能看到实际桌面内容和个人行为，要保证 100% 本地化

00举报2023/01/02 22:50

[![Image 70: planarians](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/4vpubtie/updates)

[![Image 71](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/4vpubtie)关注

planarians

[planarians [![Image 72](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/4vpubtie)关注 planarians](https://sspai.com/u/4vpubtie/updates)

2022/11/10 00:56

obs本来就是用ffmpeg做的 没他功能多不是很正常

000举报2022/11/10 00:56

[![Image 73: Cccczzz007](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/Cccczzz007/updates)

[![Image 74](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/Cccczzz007)关注

Cccczzz007

[Cccczzz007 [![Image 75](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/Cccczzz007)关注 Cccczzz007](https://sspai.com/u/Cccczzz007/updates)

2022/11/09 05:59

楼主动手能力真的强

000举报2022/11/09 05:59

[![Image 76: 一只迷羊](https://cdnfile.sspai.com/2022/06/20/c49bfad4910cf708cb7bf7756a1be259.jpg?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/kbiscool/updates)

[![Image 77](https://cdnfile.sspai.com/2022/06/20/c49bfad4910cf708cb7bf7756a1be259.jpg?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/kbiscool)关注

一只迷羊

少数派作者

[一只迷羊 [![Image 78](https://cdnfile.sspai.com/2022/06/20/c49bfad4910cf708cb7bf7756a1be259.jpg?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/kbiscool)关注 一只迷羊 少数派作者](https://sspai.com/u/kbiscool/updates)

2022/11/07 14:14

确定是50秒录一帧？50毫秒吧。

300举报2022/11/07 14:14

[![Image 79: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 80](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 81](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/07 14:18

是的，用 -r 20/1001 是 50 秒录一帧。

长时间录屏不需要录那么细节，所以我得用低帧率，这样录多久不怕，不会爆硬盘，也方便后期检查。

00举报2022/11/07 14:18

[![Image 82: 少数派18450235](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/8hwefjt2/updates)

[![Image 83](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/8hwefjt2)关注

少数派18450235

[少数派18450235 [![Image 84](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/8hwefjt2)关注 少数派18450235](https://sspai.com/u/8hwefjt2/updates)

回复

[清顺 [![Image 85](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2023/03/23 17:14

我主要是作为类似视频型日志那样的目的来使用，因而得保证能够捕捉到程序安装时那些日志文件闪过时的最短时间==

00举报2023/03/23 17:14

[![Image 86: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 87](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 88](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

回复

[少数派18450235 [![Image 89](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/8hwefjt2)关注 少数派18450235](https://sspai.com/u/8hwefjt2/updates)

2023/03/23 22:31

那可能只能设为一秒了，不过需要每个画面都保存吗？日志会比较大的。

00举报2023/03/23 22:31

[![Image 90: 布衣少](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09/updates)

[![Image 91](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09)关注

布衣少

[布衣少 [![Image 92](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09)关注 布衣少](https://sspai.com/u/2t7cgq09/updates)

2022/11/05 17:44

Windows 下的文件名如何保存为 2022-11-06\_01-44-17.mp4 这样的格式呢?

200举报2022/11/05 17:44

[![Image 93: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 94](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 95](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/06 02:54

output.mp4 替换为 -f segment -segment\_time 2 -strftime 1 %Y-%m-%d\_%H-%M-%S.mp4

00举报2022/11/06 02:54

[![Image 96: 布衣少](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09/updates)

[![Image 97](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09)关注

布衣少

[布衣少 [![Image 98](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09)关注 布衣少](https://sspai.com/u/2t7cgq09/updates)

回复

[清顺 [![Image 99](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/11 06:46

ffmpeg -f gdigrab -r 20/1001 -draw\_mouse 1 -offset\_x 0 -offset\_y 0 -video\_size 3840x2400 -i desktop -s 1920x1200 -f segment -segment\_time 2 -strftime 1 % Y-% m-...展开

00举报2022/11/11 06:46

[![Image 100: 布衣少](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09/updates)

[![Image 101](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09)关注

布衣少

[布衣少 [![Image 102](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09)关注 布衣少](https://sspai.com/u/2t7cgq09/updates)

2022/11/05 16:49

和作者有同样的需求,苦于没有技术实现. 感谢作者 🙏

M2 Macbook Air MacOS 13 运行命令:

ffmpeg 是使用 brew 安装.

ffmpeg version 5.1.2 Copyright (c) 2000-2022 the FFmpeg developers

built with Apple ...展开

300举报2022/11/05 16:49

[![Image 103: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 104](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 105](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/06 00:41

单个屏幕无指定区域，不需要加坐标的

00举报2022/11/06 00:41

[![Image 106: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 107](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 108](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/06 00:50

gdigrab 是 windows 的，MacOS 使用 avfoundation 方法，[https://ffmpeg.org/ffmpeg-devices.html#avfoundation](https://sspai.com/link?target=https%3A%2F%2Fffmpeg.org%2Fffmpeg-devices.html%23avfoundation)

00举报2022/11/06 00:50

[![Image 109: 布衣少](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09/updates)

[![Image 110](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09)关注

布衣少

[布衣少 [![Image 111](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/2t7cgq09)关注 布衣少](https://sspai.com/u/2t7cgq09/updates)

回复

[清顺 [![Image 112](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/11 06:47

感谢

按照作者命令修改了一下,成功了.

00举报2022/11/11 06:47

[![Image 113: 朱小强](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl/updates)

[![Image 114](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl)关注

朱小强

[朱小强 [![Image 115](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl)关注 朱小强](https://sspai.com/u/l4p99oxl/updates)

2022/11/05 15:19

[https://www.rewind.ai/](https://sspai.com/link?target=https%3A%2F%2Fwww.rewind.ai%2F)

这款产品正好可以解决你的需求

000举报2022/11/05 15:19

[![Image 116: renkehuai](https://cdnfile.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/tv6n9ist/updates)

[![Image 117](https://cdnfile.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/tv6n9ist)关注

renkehuai

[renkehuai [![Image 118](https://cdnfile.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/tv6n9ist)关注 renkehuai](https://sspai.com/u/tv6n9ist/updates)

2022/11/05 07:56

Mac版录屏软件不能内录扬声器声音，大家如何解决的？

300举报2022/11/05 07:56

[![Image 119: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 120](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 121](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/05 07:59

FFmpeg 同样使用于 Mac，你可以测试下

00举报2022/11/05 07:59

[![Image 122: 朱小强](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl/updates)

[![Image 123](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl)关注

朱小强

[朱小强 [![Image 124](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/l4p99oxl)关注 朱小强](https://sspai.com/u/l4p99oxl/updates)

2022/11/05 15:15

[https://apps.apple.com/cn/app/%E5%BD%95%E5%B1%8F%E4%B8%93%E5%AE%B6omi-%E5%B1%8F%E5%B9%95%E5%BD%95%E5%88%B6%E8%BD%AF%E4%BB%B6/id1592987853?mt=12](https://apps.apple.com/cn/app/%E5%BD%95%E5%B1%8F%E4%B8%93%E5%AE%B6omi-%E5%B1%8F%E5%B9%95%E5%BD%95%E5%88%B6%E8%BD%AF%E4%BB%B6/id1592987853?mt=12)

这个可以，但需要额外加装程序

10举报2022/11/05 15:15

[![Image 125: Shems](https://cdnfile.sspai.com/2022/09/22/avatar/4dc27829ccf7ec85ca81dd5587919dd6.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/3uf0tx03/updates)

[![Image 126](https://cdnfile.sspai.com/2022/09/22/avatar/4dc27829ccf7ec85ca81dd5587919dd6.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/3uf0tx03)关注

Shems

[Shems [![Image 127](https://cdnfile.sspai.com/2022/09/22/avatar/4dc27829ccf7ec85ca81dd5587919dd6.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/3uf0tx03)关注 Shems](https://sspai.com/u/3uf0tx03/updates)

2022/11/05 23:56

OBS从MacOS 13开始可以录声音了

10举报2022/11/05 23:56

[![Image 128: 临光黎明](https://cdnfile.sspai.com/2022/06/24/003dee3343e82f369bae1ed804e48e1f.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/NearlNawd/updates)

[![Image 129](https://cdnfile.sspai.com/2022/06/24/003dee3343e82f369bae1ed804e48e1f.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/NearlNawd)关注

临光黎明

少数派作者

[临光黎明 [![Image 130](https://cdnfile.sspai.com/2022/06/24/003dee3343e82f369bae1ed804e48e1f.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/NearlNawd)关注 临光黎明 少数派作者](https://sspai.com/u/NearlNawd/updates)

2022/11/05 07:55

OBS其实也能用推流机的方式来达到同时直播+录制的效果

100举报2022/11/05 07:55

[![Image 131: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 132](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 133](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/05 07:58

OBS 里录播必须与直播画面一致的吧。录屏我不会加模糊滤镜

00举报2022/11/05 07:58

[![Image 134: b3721](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/vuxe47ii/updates)

[![Image 135](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/vuxe47ii)关注

b3721

[b3721 [![Image 136](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/vuxe47ii)关注 b3721](https://sspai.com/u/vuxe47ii/updates)

2022/11/05 05:20

可以用Captura，同样可以自定义ffmpeg配置，GUI界面还挺好看，就是不维护了……

100举报2022/11/05 05:20

[![Image 137: 清顺](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v/updates)

[![Image 138](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注

清顺

少数派作者

[清顺 [![Image 139](https://cdnfile.sspai.com/2022/07/17/8cfa2f6076ba12e3e03e1609a0e9a5d1.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/zqj05i4v)关注 清顺 少数派作者](https://sspai.com/u/zqj05i4v/updates)

2022/11/05 05:22

是的，不过它的帧率还是有限制，bug 也很多。我用的时候，经常崩溃

00举报2022/11/05 05:22

[![Image 140: hillni](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/owycs16t/updates)

[![Image 141](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/owycs16t)关注

hillni

[hillni [![Image 142](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/owycs16t)关注 hillni](https://sspai.com/u/owycs16t/updates)

2022/11/05 05:06

搞不懂ffmpeg这么简单的工具为什么都没人写个wrapper，我自己就用一下剪切，自己写个小GUI够用了

100举报2022/11/05 05:06

[![Image 143: LordYang](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/LordYang/updates)

[![Image 144](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/LordYang)关注

LordYang

[LordYang [![Image 145](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/LordYang)关注 LordYang](https://sspai.com/u/LordYang/updates)

2022/11/05 05:51

ffmpeg也不简单啊，常用命令的话alias一下就好了

00举报2022/11/05 05:51

[![Image 146: DejavuMoe](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/5wxnj9k1/updates)

[![Image 147](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/5wxnj9k1)关注

DejavuMoe

[DejavuMoe [![Image 148](https://cdn-static.sspai.com/ui/otter_avatar_placeholder_240511.png)](https://sspai.com/u/5wxnj9k1)关注 DejavuMoe](https://sspai.com/u/5wxnj9k1/updates)

2022/11/05 03:19

硬核🤔

000举报2022/11/05 03:19

[![Image 149: ChenSean](https://cdnfile.sspai.com/2022/02/17/00409e880cf20f20bd8abfceeb32cad7.png?imageMogr2/auto-orient/thumbnail/!80x80r/gravity/center/crop/80x80/format/webp/ignore-error/1)](https://sspai.com/u/flosean/updates)

[![Image 150](https://cdnfile.sspai.com/2022/02/17/00409e880cf20f20bd8abfceeb32cad7.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/flosean)关注

ChenSean

[ChenSean [![Image 151](https://cdnfile.sspai.com/2022/02/17/00409e880cf20f20bd8abfceeb32cad7.png?imageMogr2/auto-orient/thumbnail/!100x100r/gravity/center/crop/100x100/format/webp/ignore-error/1)](https://sspai.com/u/flosean)关注 ChenSean](https://sspai.com/u/flosean/updates)

2022/11/05 11:30

學習了, 原來ffmpeg還可以這樣用, 一直以為只能用來轉碼

001举报2022/11/05 11:30

没有更多评论了哦

推荐阅读

[![Image 152](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](https://sspai.com/post/96663)[![Image 153](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](javascript:;)

[![Image 154](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)米斯特软的](https://sspai.com/u/djyde)

02/24 04:27

[Apple Notes 中的 PARA 笔记法实践](https://sspai.com/post/96663)

[![Image 155](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)米斯特软的](https://sspai.com/u/djyde)

135

[![Image 156](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](https://sspai.com/post/95775)[![Image 157](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](javascript:;)

[![Image 158](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)张奕源Nick](https://sspai.com/u/nicholaszhang)

01/22 09:00

[深入《无边记》：一种革命性的知识管理体系](https://sspai.com/post/95775)

[![Image 159](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)张奕源Nick](https://sspai.com/u/nicholaszhang)

76

[![Image 160](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](https://sspai.com/post/95147)[![Image 161](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](javascript:;)

[![Image 162](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)愚人哲](https://sspai.com/u/yrzhe)

2024/12/28 06:52

[从被动接收到主动参与：我的 AI 辅助学习方法论](https://sspai.com/post/95147)

[![Image 163](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)愚人哲](https://sspai.com/u/yrzhe)

129

[![Image 164](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](https://sspai.com/post/95005)[![Image 165](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](javascript:;)

[![Image 166](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)Blushyes](https://sspai.com/u/e5836i8d)

2024/12/23 00:47

[App+1 | 简约、轻快、中文友好，更好用的 Windows 启动器：如快](https://sspai.com/post/95005)

[![Image 167](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)Blushyes](https://sspai.com/u/e5836i8d)

91

[![Image 168](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](https://sspai.com/post/92610)

[![Image 169](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)海拉鲁](https://sspai.com/u/c2vngcyw)

2024/09/29 13:36

[一日一技 | 用 iOS 快捷指令和 AI，DIY 一个更好用的「闪念笔记」](https://sspai.com/post/92610)

[![Image 170](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)海拉鲁](https://sspai.com/u/c2vngcyw)

74

[![Image 171](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](https://sspai.com/post/91848)[![Image 172](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)](javascript:;)

[![Image 173](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)CG艺术实验室](https://sspai.com/u/cgartlab)

2024/10/08 03:30

[从三维设计师入坑三年，我是这样使用 Mac 的](https://sspai.com/post/91848)

[![Image 174](blob:http://localhost/b9a31d3949b1882a09ed2f8508d538f3)CG艺术实验室](https://sspai.com/u/cgartlab)

111

![Image 175](https://cdn-static.sspai.com/ui/logo/logo_sspai_icon.png)

App 内打开

请绑定手机号码

取消

前往绑定

[](https://sspai.com/)

[](https://weibo.com/sspaime?is_hot=1)[关注公众号 sspaime ![Image 176](https://cdn-static.sspai.com/ui/gzh_qrcode_home.png)](https://mp.weixin.qq.com/mp/profile_ext?action=home&__biz=MzU4Mjg3MDAyMQ==&subscene=0#wechat_redirect)[](https://www.xiaohongshu.com/user/profile/63f5d65d000000001001d8d4)[](https://sspai.com/feed)

[下载 App](https://sspai.com/page/client) [联系我们](mailto:contact@sspai.com) [商务合作](https://sspai.com/page/bussiness) [关于我们](https://sspai.com/page/about-us) [用户协议](https://sspai.com/page/agreement)

© 2013-2025 少数派[粤ICP备09128966号-4](https://beian.miit.gov.cn/) | [粤B2-20211534](https://dxzhgl.miit.gov.cn/)

确定

*   联系客服
*   [发送邮件](mailto:contact@sspai.com)
*   [商务合作](https://sspai.com/page/bussiness)
*   [少数派 App](https://sspai.com/page/client)

请用微信手机端扫码咨询客服

![Image 177](https://cdn-static.sspai.com/ui/qrcode_service.png)
