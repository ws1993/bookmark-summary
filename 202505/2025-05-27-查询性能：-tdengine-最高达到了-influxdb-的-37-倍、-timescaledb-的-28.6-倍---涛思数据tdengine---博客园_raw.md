Title: 查询性能： TDengine 最高达到了 InfluxDB 的 37 倍、 TimescaleDB 的 28.6 倍

URL Source: https://www.cnblogs.com/taosdata/p/17199193.html

Published Time: 2023-03-09T17:02:00.0000000+08:00

Markdown Content:
查询性能： TDengine 最高达到了 InfluxDB 的 37 倍、 TimescaleDB 的 28.6 倍 - 涛思数据TDengine - 博客园

===============

[![Image 12](https://img2024.cnblogs.com/blog/35695/202412/35695-20241201073014811-1847930772.jpg)](https://www.doubao.com/?channel=cnblogs&source=hw_db_cnblogs&type=lunt&theme=bianc)

*   [![Image 13: 博客园logo](https://assets.cnblogs.com/logo.svg)](https://www.cnblogs.com/ "开发者的网上家园")
*   [会员](https://cnblogs.vip/)
*   [周边](https://cnblogs.vip/store)
*   [新闻](https://news.cnblogs.com/)
*   [博问](https://q.cnblogs.com/)
*   [闪存](https://ing.cnblogs.com/)
*   [赞助商](https://www.cnblogs.com/cmt/p/18341478)
*   [Chat2DB](https://chat2db-ai.com/)

*   ![Image 14: 搜索](https://assets.cnblogs.com/icons/search.svg)![Image 15: 搜索](https://assets.cnblogs.com/icons/enter.svg)
    *   ![Image 16: 搜索](https://assets.cnblogs.com/icons/search.svg)  所有博客
    *   ![Image 17: 搜索](https://assets.cnblogs.com/icons/search.svg)  当前博客

*   [![Image 18: 写随笔](https://assets.cnblogs.com/icons/newpost.svg)](https://i.cnblogs.com/EditPosts.aspx?opt=1 "写随笔")[![Image 19: 我的博客](https://assets.cnblogs.com/icons/myblog.svg)](https://passport.cnblogs.com/GetBlogApplyStatus.aspx "我的博客")[![Image 20: 短消息](https://assets.cnblogs.com/icons/message.svg)](https://msg.cnblogs.com/ "短消息")[![Image 21: 简洁模式](https://assets.cnblogs.com/icons/lite-mode-on.svg)](javascript:void(0) "简洁模式启用，您在访问他人博客时会使用简洁款皮肤展示")[![Image 22: 用户头像](https://assets.cnblogs.com/icons/avatar-default.svg)](https://home.cnblogs.com/)[我的博客](https://passport.cnblogs.com/GetBlogApplyStatus.aspx)[我的园子](https://home.cnblogs.com/)[账号设置](https://account.cnblogs.com/settings/account)[会员中心](https://vip.cnblogs.com/my)[简洁模式 ...](javascript:void(0) "简洁模式会使用简洁款皮肤显示所有博客")[退出登录](javascript:void(0))  [注册](https://account.cnblogs.com/signup)[登录](javascript:void(0);)

[![Image 23: 返回主页](https://www.cnblogs.com/skins/custom/images/logo.gif)](https://www.cnblogs.com/taosdata/)
[涛思数据TDengine](https://www.cnblogs.com/taosdata)
================================================

*   [博客园](https://www.cnblogs.com/)
*   [首页](https://www.cnblogs.com/taosdata/)
*   [新随笔](https://i.cnblogs.com/EditPosts.aspx?opt=1)
*   [联系](https://msg.cnblogs.com/send/%E6%B6%9B%E6%80%9D%E6%95%B0%E6%8D%AETDengine)
*   [订阅](javascript:void(0))
*   [管理](https://i.cnblogs.com/)

[查询性能： TDengine 最高达到了 InfluxDB 的 37 倍、 TimescaleDB 的 28.6 倍](https://www.cnblogs.com/taosdata/p/17199193.html "发布于 2023-03-09 17:02")
=====================================================================================================================================

![Image 24: 查询性能： TDengine 最高达到了 InfluxDB 的 37 倍、 TimescaleDB 的 28.6 倍](https://img2023.cnblogs.com/blog/2141580/202303/2141580-20230309170147969-29542214.png) 5大类15小类查询类型全面对比！ 

在上一篇文章[《写入性能：TDengine 最高达到 InfluxDB 的 10.3 倍，TimeScaleDB 的 6.74 倍》](https://www.taosdata.com/engineering/16739.html)中，我们基于 TSBS[时序数据库](https://www.taosdata.com/ "时序数据库")（[Time Series Database](https://www.taosdata.com/time-series-database "Time Series DataBase")）性能基准测试报告对三大数据库写入性能进行了相关解读，较为直观地展现出了[TDengine](https://www.taosdata.com/ "TDengine")的众多写入优势。本篇文章将以查询性能作为主题，给正在为数据分析痛点而头疼的朋友们带来一些帮助。

在查询性能评估部分，我们使用场景一（只包含 4 天数据）和场景二作为基准数据集，关于基础数据集的具体特点，请点击进入[《TSBS 是什么？为什么 TDengine 会选择它作为性能对比测试平台？》](https://www.taosdata.com/engineering/16710.html)一文中查看。在查询性能评估之前，为确保两大数据库充分发挥查询性能，对于 TimescaleDB，我们采用了《TimescaleDB vs. InfluxDB》（见下方链接）中的推荐配置，设置为 8 个 Chunk；对于 InfluxDB，我们开启 InfluxDB 的 TSI (time series index)。在整个查询对比中，TDengine 数据库的虚拟节点数量（vnodes）保持为默认的 6 个，其他的数据库参数配置为默认值。

TimescaleDB vs. InfluxDB: Purpose Built Differently for Time-Series Data：

[https://www.timescale.com/blog/timescaledb-vs-influxdb-for-time-series-data-timescale-influx-sql-nosql-36489299877/](https://www.timescale.com/blog/timescaledb-vs-influxdb-for-time-series-data-timescale-influx-sql-nosql-36489299877/)

4,000 devices × 10 metrics 查询性能对比：最高达到 InfluxDB 的 34.2 倍
--------------------------------------------------------

由于部分类型（分类标准参见上方《TimescaleDB vs. InfluxDB》 一文）单次查询响应时间非常短，为了更加准确地测量每个查询场景下较为稳定的响应时间，我们将单个查询运行次数提升到 5000 次，然后使用 TSBS 自动统计并输出结果，最后结果是 5000 次查询的算数平均值，使用并发客户端 Workers 数量为 8。下表是场景二 （4000设备）的查询性能对比结果。

![Image 25: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/%E6%88%AA%E5%B1%8F2023-03-03-%E4%B8%8B%E5%8D%881.22.12-1024x576.png)

4,000 devices × 10 metrics（场景二）查询性能对比表（单位：ms）

下面我们对每个查询结果做一定的分析说明：

![Image 26: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-7.jpg)

4000 devices × 10 metrics Simple Rollups 查询响应时间 (数值越小越好)

由于 Simple Rollups 的整体查询响应时间非常短，因此制约查询响应时间的主体因素并不是查询所涉及的数据规模，即这一类型查询的瓶颈并非数据规模。但从结果上看，TDengine 仍然在所有类型的查询响应时间上优于 InfluxDB 和 TimescaleDB，具体的数值对比请参见上表。

![Image 27: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-8.jpg)

4000 devices × 10 metrics Aggregates 查询响应时间 (数值越小越好)

在 Aggregates 类型的查询中，TDengine 的查询性能相比于 TimescaleDB 和 InfluxDB 优势更为明显，其在 cpu-max-all-8 中的查询性能是 InfluxDB 的 7 倍，是 TimescaleDB 的 6 倍。

![Image 28: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-9.jpg)

4000 devices × 10 metrics Double rollups 查询响应时间 (数值越小越好)

从上表可见，在 Double-rollups 类型查询中， TDengine 展现出了巨大的性能优势。以查询响应时间来度量，其在 double-groupby-5 和 double-groupby-all 的查询性能均是 TimescaleDB 的 24 倍；在 double-groupby-5 查询上是 InfluxDB 的 26 倍，double-groupby-all 上是其 34 倍。

![Image 29: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-10.jpg)

4000 devices × 10 metrics Thresholds 查询 high-cpu-1 响应时间 (数值越小越好)![Image 30: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-11.jpg)

4000 devices × 10 metrics Thresholds 查询 high-cpu-all 响应时间 (数值越小越好)

如上面两图所示，threshold 类型的查询中，high-cpu-1 中 TDengine 的查询响应时间均显著低于 TimescaleDB 和 InfluxDB。在 high-cpu-all 的查询中，TDengine 的性能是 InfluxDB 的 15 倍，是 TimescaleDB 的 1.23 倍。

![Image 31: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-12.jpg)

4000 devices × 10 metrics Complex queries 查询响应时间 (数值越小越好)

对于 Complex-queries 类型的查询，TDengine 两个查询均大幅领先 TimescaleDB 和 InfluxDB——在 lastpoint 查询中，其性能是 TimescaleDB 的 5 倍， InfluxDB 的 21 倍；在 groupby-orderby-limit 场景中其查询性能是TimescaleDB的 8 倍，是 InfluxDB 的 15 倍。在时间窗口聚合的查询过程中，TimescaleDB 针对规模较大的数据集查询性能不佳（double rollups 类型查询），对于 groupby-orderby-limit 的查询，其性能上表现同样不是太好。

资源开销对比：整体 CPU 计算时间消耗是 InfluxDB 的 1/10
-------------------------------------

由于部分查询持续时间特别短，因此并不能凭借以上信息完整地看到查询过程中服务器的 IO/CPU/网络情况。为此，我们以场景二的数据为模拟数据，以 Double rollups 类别中的 double-groupby-5 查询为例，执行 1000 次查询，记录整个过程中三个软件系统在查询执行的整个过程中服务器 CPU、内存、网络的开销并进行对比。

### 服务器 CPU 开销

![Image 32: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-13.jpg)

查询过程中服务器 CPU 开销

从上图可以看到，三个系统在整个查询过程中 CPU 的使用均较为平稳。TDengine 在查询过程中整体 CPU 占用约 80%, 在三个系统中使用的 CPU 资源最高；TimescaleDB 在查询过程中瞬时 CPU 占用次之，约 38%；InfluxDB 的 CPU 占用的最小，约 27 %（但是有较多的瞬时冲高）。从整体 CPU 开销上来看，虽然 InfluxDB 瞬时 CPU 开销最低，但是其完成查询持续时间也最长，所以整体 CPU 资源消耗最多。由于 TDengine 完成全部查询的时间仅为 TimescaleDB 或 InfluxDB 的 1/20，因此虽然其 CPU 稳定值是 TimescaleDB 与 InfluxDB 的 2 倍多，但整体的 CPU 计算时间消耗却只有其 1/10 。

### 服务器内存状况

![Image 33: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-14.png)

查询过程中服务器内存情况

如上图所示，在整个查询过程中，TDengine 内存维持了一个相对平稳的状态。TimescaleDB 在整个查询过程中内存呈现增加的状态，查询完成后即恢复到初始状态，InfluxDB 内存占用呈现相对稳定的状态。

### 服务器网络带宽

![Image 34: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/image-15.jpg)

查询过程中网络占用情况

上图展示了查询过程中服务器端上行和下行的网络带宽情况，负载状况基本上和 CPU 状况相似。TDengine 网络带宽开销最高，因为在最短的时间内就完成了全部查询，需要将查询结果返回给客户端。InfluxDB 网络带宽开销最低，TimescaleDB 介于两者之间。

100 devices × 10 metrics 查询性能对比：最高达到 TimescaleDB 的 28.6 倍
---------------------------------------------------------

对于场景一(100 devices x 10 metrics)来说，TSBS 的 15 个查询对比结果如下：

![Image 35: TDengine Database](https://www.taosdata.com/wp-content/uploads/2023/03/%E6%88%AA%E5%B1%8F2023-03-03-%E4%B8%8A%E5%8D%8811.12.59-1-1024x574.png)

InfluxDB 与 Timescale 相对于 TDengine 的查询响应时间比率 (单位：ms)

如上表所示，在更小规模的数据集（100 设备）上的查询对比可以看到，整体来说 TDengine 同样展现出极好的性能，在全部查询语句中均优于 TimescaleDB 和 InfluxDB，部分查询性能超过 TimescaleDB 28 倍，超过 InfluxDB 37 倍。

写在最后
----

基于上文可以做出总结，整体来讲，在场景一（只包含 4 天的数据）与场景二的 15 个不同类型的查询中，TDengine 的查询平均响应时间全面优于 InfluxDB 和 TimescaleDB，在复杂查询上优势更为明显，同时具有最小的计算资源开销。相对于 InfluxDB，场景一中 TDengine 查询性能是其 1.9 ～ 37 倍，场景二中 TDengine 查询性能是其 1.8 ～ 34.2 倍；相对于 TimeScaleDB，场景一中TDengine 查询性能是其 1.1 ～ 28.6 倍，场景二中 TDengine 查询性能是其 1.2 ～ 24.6 倍。

事实上，TDengine 高效的查询性能此前在很多企业客户的实践中就已经展示出来了，以广东省环境科学研究院生态环境数据治理服务项目为例，对于 76 亿行的超级表，TDengine 运行分组 TOP 查询仅用了 0.2 秒；基于 TDengine 返回 2,968 行，仅用了 0.06 秒；返回 5,280 行数据，仅用了 0.1 秒。

* * *

如果你也面临着数据处理难题或想要进行数据架构升级，欢迎添加**小T vx：tdengine1**，加入 TDengine 用户交流群，和更多志同道合的开发者一起攻克难关。

[好文要顶](javascript:void(0);)[关注我](javascript:void(0);)[收藏该文](javascript:void(0);)[微信分享](javascript:void(0);)

[![Image 36](https://pic.cnblogs.com/face/2141580/20200831144642.png)](https://home.cnblogs.com/u/taosdata/)

[涛思数据TDengine](https://home.cnblogs.com/u/taosdata/)

[粉丝 - 30](https://home.cnblogs.com/u/taosdata/followers/)[关注 - 0](https://home.cnblogs.com/u/taosdata/followees/)

[+加关注](javascript:void(0);)

0

0

[升级成为会员](https://cnblogs.vip/)

[«](https://www.cnblogs.com/taosdata/p/17175809.html) 上一篇： [写入性能：TDengine 最高达到 InfluxDB 的 10.3 倍，TimeScaleDB 的 6.74 倍](https://www.cnblogs.com/taosdata/p/17175809.html "发布于 2023-03-06 14:50")

[»](https://www.cnblogs.com/taosdata/p/17214629.html) 下一篇： [OPPO、京东云 loT 项目数据架构改造，数据处理痛点这样破解](https://www.cnblogs.com/taosdata/p/17214629.html "发布于 2023-03-14 13:22")

posted @ 2023-03-09 17:02[涛思数据TDengine](https://www.cnblogs.com/taosdata) 阅读(86) 评论(0)[收藏](javascript:void(0))[举报](javascript:void(0))

[刷新页面](https://www.cnblogs.com/taosdata/p/17199193.html#)[返回顶部](https://www.cnblogs.com/taosdata/p/17199193.html#top)

 登录后才能查看或发表评论，立即 [登录](javascript:void(0);) 或者 [逛逛](https://www.cnblogs.com/) 博客园首页 

[【推荐】新一代 Linux 服务器运维管理面板 1Panel V2 开放公测！](https://mp.weixin.qq.com/s/G8nkXzkagGWavP6jWnPxfg)

[【推荐】100%开源！大型工业跨平台软件C++源码提供，建模，组态！](http://www.uccpsoft.com/index.htm)

[【推荐】国内首个AI IDE，深度理解中文开发场景，立即下载体验Trae](https://www.trae.com.cn/?utm_source=advertising&utm_medium=cnblogs_ug_cpa&utm_term=hw_trae_cnblogs)

[【推荐】Flutter适配HarmonyOS 5知识地图，实战解析+高频避坑指南](https://www.cnblogs.com/HarmonyOS5/p/18867837)

[【推荐】轻量又高性能的 SSH 工具 IShell：AI 加持，快人一步](http://ishell.cc/)

[![Image 37](https://img2024.cnblogs.com/blog/35695/202412/35695-20241201072501456-2052907165.jpg)](https://www.doubao.com/?channel=cnblogs&source=hw_db_cnblogs&type=lunt&theme=bianc)

**相关博文：**

·[TimescaleDB VS TDengine：写入性能和查询性能是 TDengine 的 1/6、1/28](https://www.cnblogs.com/taosdata/p/17411559.html "TimescaleDB VS TDengine：写入性能和查询性能是 TDengine 的 1/6、1/28")

·[TDengine 的查询性能与老牌时序数据库相比如何？来看看](https://www.cnblogs.com/taosdata/p/17562374.html "TDengine 的查询性能与老牌时序数据库相比如何？来看看")

·[时序数据库 InfluxDB、TimeScaleDB和TDengine 对比](https://www.cnblogs.com/miracle-luna/p/17973749 "时序数据库 InfluxDB、TimeScaleDB和TDengine 对比")

·[时序数据库](https://www.cnblogs.com/edclol/p/17282559.html "时序数据库")

·[【数据库】时序数据库InfluxDB 性能测试和为什么时序数据库更快、时序数据库应用场景](https://www.cnblogs.com/bandaoyu/p/16752591.html "【数据库】时序数据库InfluxDB 性能测试和为什么时序数据库更快、时序数据库应用场景")

**阅读排行：**

 · [.NET 10 进展之 CoreCLR Interpreter](https://www.cnblogs.com/shanyou/p/18895698)

 · [全网最全！1500+ 免费、美观的前端网页模板，建站神器（包括HTML、Vue、Angular、Re](https://www.cnblogs.com/Can-daydayup/p/18895094)

 · [SharpIco：用纯C#打造零依赖的.ico图标生成器，支持.NET9与AOT编译](https://www.cnblogs.com/deali/p/18896645)

 · [杂七杂八系列----浅谈.NET微服务架构的演变](https://www.cnblogs.com/lmy5215006/p/18894045)

 · [AI工程师跑路了-SpringAi来帮忙](https://www.cnblogs.com/jijunjian/p/18896403)

### 公告

 昵称： [涛思数据TDengine](https://home.cnblogs.com/u/taosdata/)

 园龄： [4年8个月](https://home.cnblogs.com/u/taosdata/ "入园时间：2020-08-31")

 粉丝： [30](https://home.cnblogs.com/u/taosdata/followers/)

 关注： [0](https://home.cnblogs.com/u/taosdata/followees/)

[+加关注](javascript:void(0))

[<](javascript:void(0);)2025年5月[>](javascript:void(0);)
日 一 二 三 四 五 六
27 28 29 30 1 2 3
4 5 6[7](https://www.cnblogs.com/taosdata/p/archive/2025/05/07)8 9 10
11 12 13 14 15[16](https://www.cnblogs.com/taosdata/p/archive/2025/05/16)17
18 19 20 21 22 23 24
25 26 27 28 29 30 31
1 2 3 4 5 6 7

### 搜索

### 常用链接

*   [我的随笔](https://www.cnblogs.com/taosdata/p/ "我的博客的随笔列表")
*   [我的评论](https://www.cnblogs.com/taosdata/MyComments.html "我的发表过的评论列表")
*   [我的参与](https://www.cnblogs.com/taosdata/OtherPosts.html "我评论过的随笔列表")
*   [最新评论](https://www.cnblogs.com/taosdata/comments "我的博客的评论列表")
*   [我的标签](https://www.cnblogs.com/taosdata/tag/ "我的博客的标签列表")

### [我的标签](https://www.cnblogs.com/taosdata/tag/)

*   [时序数据库(332)](https://www.cnblogs.com/taosdata/tag/%E6%97%B6%E5%BA%8F%E6%95%B0%E6%8D%AE%E5%BA%93/)
*   [tdengine(330)](https://www.cnblogs.com/taosdata/tag/tdengine/)
*   [数据库(174)](https://www.cnblogs.com/taosdata/tag/%E6%95%B0%E6%8D%AE%E5%BA%93/)
*   [物联网(153)](https://www.cnblogs.com/taosdata/tag/%E7%89%A9%E8%81%94%E7%BD%91/)
*   [开源(101)](https://www.cnblogs.com/taosdata/tag/%E5%BC%80%E6%BA%90/)
*   [涛思数据(87)](https://www.cnblogs.com/taosdata/tag/%E6%B6%9B%E6%80%9D%E6%95%B0%E6%8D%AE/)
*   [大数据(87)](https://www.cnblogs.com/taosdata/tag/%E5%A4%A7%E6%95%B0%E6%8D%AE/)
*   [物联网大数据平台(65)](https://www.cnblogs.com/taosdata/tag/%E7%89%A9%E8%81%94%E7%BD%91%E5%A4%A7%E6%95%B0%E6%8D%AE%E5%B9%B3%E5%8F%B0/)
*   [taosdata(25)](https://www.cnblogs.com/taosdata/tag/taosdata/)
*   [后端(5)](https://www.cnblogs.com/taosdata/tag/%E5%90%8E%E7%AB%AF/)
*   [更多](https://www.cnblogs.com/taosdata/tag/)

### [随笔分类](https://www.cnblogs.com/taosdata/post-categories)

*   [TDengine 爱好者贡献的小工具(1)](https://www.cnblogs.com/taosdata/category/1848653.html)
*   [TDengine官方文档解读(10)](https://www.cnblogs.com/taosdata/category/1845761.html)
*   [TDengine技术博客(109)](https://www.cnblogs.com/taosdata/category/1946077.html)
*   [TDengine用户案例(81)](https://www.cnblogs.com/taosdata/category/1845762.html)
*   [人物(8)](https://www.cnblogs.com/taosdata/category/2171389.html)
*   [社区活动(13)](https://www.cnblogs.com/taosdata/category/2180616.html)
*   [新闻(71)](https://www.cnblogs.com/taosdata/category/2137365.html)

### 随笔档案

*   [2025年5月(2)](https://www.cnblogs.com/taosdata/p/archive/2025/05)
*   [2025年4月(15)](https://www.cnblogs.com/taosdata/p/archive/2025/04)
*   [2025年3月(11)](https://www.cnblogs.com/taosdata/p/archive/2025/03)
*   [2025年2月(5)](https://www.cnblogs.com/taosdata/p/archive/2025/02)
*   [2025年1月(9)](https://www.cnblogs.com/taosdata/p/archive/2025/01)
*   [2024年12月(14)](https://www.cnblogs.com/taosdata/p/archive/2024/12)
*   [2024年11月(13)](https://www.cnblogs.com/taosdata/p/archive/2024/11)
*   [2024年10月(6)](https://www.cnblogs.com/taosdata/p/archive/2024/10)
*   [2024年9月(18)](https://www.cnblogs.com/taosdata/p/archive/2024/09)
*   [2024年7月(6)](https://www.cnblogs.com/taosdata/p/archive/2024/07)
*   [2024年6月(34)](https://www.cnblogs.com/taosdata/p/archive/2024/06)
*   [2024年3月(9)](https://www.cnblogs.com/taosdata/p/archive/2024/03)
*   [2024年2月(4)](https://www.cnblogs.com/taosdata/p/archive/2024/02)
*   [2024年1月(13)](https://www.cnblogs.com/taosdata/p/archive/2024/01)
*   [2023年12月(14)](https://www.cnblogs.com/taosdata/p/archive/2023/12)
*   [2023年11月(12)](https://www.cnblogs.com/taosdata/p/archive/2023/11)
*   [2023年10月(13)](https://www.cnblogs.com/taosdata/p/archive/2023/10)
*   [2023年9月(11)](https://www.cnblogs.com/taosdata/p/archive/2023/09)
*   [2023年8月(10)](https://www.cnblogs.com/taosdata/p/archive/2023/08)
*   [2023年7月(15)](https://www.cnblogs.com/taosdata/p/archive/2023/07)
*   [2023年6月(12)](https://www.cnblogs.com/taosdata/p/archive/2023/06)
*   [2023年5月(9)](https://www.cnblogs.com/taosdata/p/archive/2023/05)
*   [2023年4月(9)](https://www.cnblogs.com/taosdata/p/archive/2023/04)
*   [2023年3月(12)](https://www.cnblogs.com/taosdata/p/archive/2023/03)
*   [2023年2月(9)](https://www.cnblogs.com/taosdata/p/archive/2023/02)
*   [2023年1月(10)](https://www.cnblogs.com/taosdata/p/archive/2023/01)
*   [2022年12月(10)](https://www.cnblogs.com/taosdata/p/archive/2022/12)
*   [2022年11月(6)](https://www.cnblogs.com/taosdata/p/archive/2022/11)
*   [2022年10月(6)](https://www.cnblogs.com/taosdata/p/archive/2022/10)
*   [2022年9月(11)](https://www.cnblogs.com/taosdata/p/archive/2022/09)
*   [2022年8月(14)](https://www.cnblogs.com/taosdata/p/archive/2022/08)
*   [2022年7月(13)](https://www.cnblogs.com/taosdata/p/archive/2022/07)
*   [2022年6月(19)](https://www.cnblogs.com/taosdata/p/archive/2022/06)
*   [2022年5月(17)](https://www.cnblogs.com/taosdata/p/archive/2022/05)
*   [2022年4月(8)](https://www.cnblogs.com/taosdata/p/archive/2022/04)
*   [2022年3月(10)](https://www.cnblogs.com/taosdata/p/archive/2022/03)
*   [2022年2月(6)](https://www.cnblogs.com/taosdata/p/archive/2022/02)
*   [2022年1月(7)](https://www.cnblogs.com/taosdata/p/archive/2022/01)
*   [2021年12月(14)](https://www.cnblogs.com/taosdata/p/archive/2021/12)
*   [2021年11月(14)](https://www.cnblogs.com/taosdata/p/archive/2021/11)
*   [2021年10月(2)](https://www.cnblogs.com/taosdata/p/archive/2021/10)
*   [2021年9月(4)](https://www.cnblogs.com/taosdata/p/archive/2021/09)
*   [2021年8月(2)](https://www.cnblogs.com/taosdata/p/archive/2021/08)
*   [2021年7月(7)](https://www.cnblogs.com/taosdata/p/archive/2021/07)
*   [2021年6月(4)](https://www.cnblogs.com/taosdata/p/archive/2021/06)
*   [2021年5月(2)](https://www.cnblogs.com/taosdata/p/archive/2021/05)
*   [2021年4月(2)](https://www.cnblogs.com/taosdata/p/archive/2021/04)
*   [2021年3月(2)](https://www.cnblogs.com/taosdata/p/archive/2021/03)
*   [2021年1月(2)](https://www.cnblogs.com/taosdata/p/archive/2021/01)
*   [2020年11月(5)](https://www.cnblogs.com/taosdata/p/archive/2020/11)
*   [2020年9月(7)](https://www.cnblogs.com/taosdata/p/archive/2020/09)
*   [更多](javascript:void(0))

### [文章分类](https://www.cnblogs.com/taosdata/article-categories)

*   [TDengine官方文档详解(1)](https://www.cnblogs.com/taosdata/category/1845771.html)

### [阅读排行榜](https://www.cnblogs.com/taosdata/most-viewed)

*   [1. TDengine常见问题解答（FAQ）(3696)](https://www.cnblogs.com/taosdata/p/13653055.html)
*   [2. 双汇大数据方案选型：从棘手的InfluxDB+Redis到毫秒级查询的TDengine(3259)](https://www.cnblogs.com/taosdata/p/13999606.html)
*   [3. 万字详解TDengine 2.0整体架构设计思路(2938)](https://www.cnblogs.com/taosdata/p/13652919.html)
*   [4. 保姆级演示一分钟搞定TDengine的下载安装(2598)](https://www.cnblogs.com/taosdata/p/14009957.html)
*   [5. 一篇文章说清楚TDengine的FQDN(2351)](https://www.cnblogs.com/taosdata/p/13690374.html)

### [评论排行榜](https://www.cnblogs.com/taosdata/most-commented)

*   [1. TDengine 的用户如何优化数据的写入速度？(2)](https://www.cnblogs.com/taosdata/p/14793551.html)
*   [2. 60秒定位问题，十倍程序员的Debug日常(2)](https://www.cnblogs.com/taosdata/p/14522371.html)
*   [3. 有梦想、赢未来—— 涛思数据 TDengine 校园招聘(1)](https://www.cnblogs.com/taosdata/p/18251909)
*   [4. TDengine 3.3.0.0 引入图形化管理工具、复合主键等 13 项关键更新(1)](https://www.cnblogs.com/taosdata/p/18247291)
*   [5. TDengine Open Day 成功举办：洞察技术革新与职场策略！(1)](https://www.cnblogs.com/taosdata/p/18246139)

### [推荐排行榜](https://www.cnblogs.com/taosdata/most-liked)

*   [1. 60秒定位问题，十倍程序员的Debug日常(3)](https://www.cnblogs.com/taosdata/p/14522371.html)
*   [2. 创新灵感来源于用户实践，TDengine 首次公开四项专利申请(1)](https://www.cnblogs.com/taosdata/p/17415735.html)
*   [3. 从社区贡献者到加入核心团队，开源给他带来了这些变化(1)](https://www.cnblogs.com/taosdata/p/15619193.html)
*   [4. 三分钟梳理TDengine安装部署的逻辑(1)](https://www.cnblogs.com/taosdata/p/15118672.html)
*   [5. TDengine和InfluxDB的性能对比报告(1)](https://www.cnblogs.com/taosdata/p/15044708.html)

### [最新评论](https://www.cnblogs.com/taosdata/comments)

*   [1. Re:有梦想、赢未来—— 涛思数据 TDengine 校园招聘](https://www.cnblogs.com/taosdata/p/18251909)
*   欢迎移步至官网 www.taosdata.com，免费试用。也欢迎添加小T（VX：tdengine），加入技术讨论群，第一时间了解 TDengine 官方信息，与关注前沿技术的同学们共同探讨新技术、新...
*   --涛思数据TDengine
*   [2. Re:TDengine Open Day 成功举办：洞察技术革新与职场策略！](https://www.cnblogs.com/taosdata/p/18246139)
*   欢迎移步至官网 www.taosdata.com，免费试用。也欢迎添加小T（VX：tdengine），加入技术讨论群，第一时间了解 TDengine 官方信息，与关注前沿技术的同学们共同探讨新技术、新...
*   --涛思数据TDengine
*   [3. Re:TDengine 3.3.0.0 引入图形化管理工具、复合主键等 13 项关键更新](https://www.cnblogs.com/taosdata/p/18247291)
*   欢迎移步至官网 www.taosdata.com，免费试用。也欢迎添加小T（VX：tdengine），加入技术讨论群，第一时间了解 TDengine 官方信息，与关注前沿技术的同学们共同探讨新技术、新...
*   --涛思数据TDengine
*   [4. Re:新渠道+1！TDengine Cloud 入驻 Azure Marketplace](https://www.cnblogs.com/taosdata/p/18245566)
*   欢迎移步至官网 www.taosdata.com，免费试用。也欢迎添加小T（VX：tdengine），加入技术讨论群，第一时间了解 TDengine 官方信息，与关注前沿技术的同学们共同探讨新技术、新...
*   --涛思数据TDengine
*   [5. Re:借助Historian Connector + TDengine，打造工业创新底座](https://www.cnblogs.com/taosdata/p/18242316)
*   欢迎移步至官网 www.taosdata.com，免费试用。也欢迎添加小T（VX：tdengine），加入技术讨论群，第一时间了解 TDengine 官方信息，与关注前沿技术的同学们共同探讨新技术、新...
*   --涛思数据TDengine

[博客园](https://www.cnblogs.com/)© 2004-2025

[![Image 38](https://assets.cnblogs.com/images/ghs.png)浙公网安备 33010602011771号](http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=33010602011771)[浙ICP备2021040463号-3](https://beian.miit.gov.cn/)

点击右上角即可分享

![Image 39: 微信分享提示](https://img2023.cnblogs.com/blog/35695/202309/35695-20230906145857937-1471873834.gif)
