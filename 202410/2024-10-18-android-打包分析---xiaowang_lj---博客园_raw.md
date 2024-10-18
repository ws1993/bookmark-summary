Title: Android 打包分析 - xiaowang_lj - 博客园

URL Source: https://www.cnblogs.com/wanglongjiang/p/17248365.html

Markdown Content:
问题：make project 项目生成的apk大小在15M左右

run 到设备里的apk 大小在5M左右

通过解包分析 ，主要差异在lib文件夹下

15M的包

![Image 1](https://img2023.cnblogs.com/blog/3068292/202303/3068292-20230323174159641-1468753487.png)

5M的包

![Image 2](https://img2023.cnblogs.com/blog/3068292/202303/3068292-20230323174232639-1212519215.png)

如需控制打包的内容，在app的build.gradle中配置即可

ndk{
            abiFilters 'armeabi-v7a'
}

1、apk为何要分包（32位安装包、32位64位兼容包和64位安装包）？
------------------------------------

安卓设备的核心是cpu（中央处理器），cpu常用架构有ARM架构和x86架构，cpu又分为32位和64位，因此不同架构也分为32位和64位。

apk为适配市面上不同安卓设备，apk运行在Android系统调用系统驱动时需要兼容不同的CPU架构，apk的应对策略是分包。

大部分手机使用的是ARM架构，ARM架构分为32位架构、兼容32位的64位架构，以及即将推出的只支持64位的架构。

因此apk包分为32位安装包、32位64位兼容包和64位安装包。

注意：32位架构只支持32位安卓应用，兼容32位的64位架构支持32和64位安卓应用，不兼容32位的64位架构只支持64位安卓应用。

2、影响apk适配的cpu架构的因素-原生代码（C/C++代码）
--------------------------------

为什么原生代码决定apk适配的架构？为什么java代码不影响？

安卓系统的内核是Linux，Linux是使用C语言和汇编语言编写的，Android系统是使用Java语言开发的，Java代码需要通过JNI调用原生代码才能实现对操作系统底层的调度。

而为适配不同的cpu架构，可能需要根据cpu架构的不同编写不同的原生代码。

3、如何判断apk支持的cpu架构？
------------------

3.1 查看apk支持的cpu架构
-----------------

通常apk中使用原生代码，基本都是将原生代码打包成so库供Java代码使用，因此判断apk支持的cpu架构只需要判断apk中包含的so库的架构即可。

构建apk时会将不同架构的so库分不同的文件夹放置在lib文件夹下，架构和文件夹名称的对应关系如下：

ARM架构：

32 位：lib/armeabi-v7a、lib/armeabi

64 位：lib/arm64-v8a

x86架构：

32 ：lib/x86

64 ：lib/x86\_64

判断apk支持的cpu架构的方法就是检测apk文件的结构即可，具体方法如下：

方法一：查看apk安装包中的lib文件夹下的库文件

使用Android Studio菜单Build-\>Analyze APK-\>选择需要检测的apk，查看检测结果lib文件夹下的文件夹，如果有 armeabi、armeabi-v7a 或 x86文件夹，则说明有 32 位库，如有x86\_64或arm64-v8a文件夹，则说明有64位库，如两种都有则说明即有32位库也有64位库。

将apk文件后缀改为.zip，然后解压查看lib文件夹下的内容也可以。

方法二：查看安卓引用代码中支持的so库的位数

查看app模块下build.gradle文件下的android标签下的defaultConfig标签下的ndk标签下的abiFilters包含的支持的so库的位数。

abiFilters 的值分别有以下几种，一个安卓应用可以兼容多种，用,分割

ARM架构：

32 位：'armeabi', 'armeabi-v7a'

64 位：'arm64-v8a'

x86架构：

32 位：'x86'

64 位： 'x86\_64'

如安卓应用没有使用任何so库，那么该安卓应用不存在主动去调度操作系统的功能，此安卓应用不管运行的手机是32位还是64位都不存在硬件调度的兼容问题，此安卓应用可以称之为32位和64位兼容包。

3.2 不同cpu架构之间的so库的兼容关系  
Android设备如何加载.so文件

arm64-v8a架构：

![Image 3](https://img2023.cnblogs.com/blog/3068292/202303/3068292-20230323174549893-2068929034.png)

armeabi-v7a架构：

![Image 4](https://img2023.cnblogs.com/blog/3068292/202303/3068292-20230323174602242-1564440027.png)

armeabi架构

![Image 5](https://img2023.cnblogs.com/blog/3068292/202303/3068292-20230323174608515-786350124.png)

x86架构

![Image 6](https://img2023.cnblogs.com/blog/3068292/202303/3068292-20230323174614613-1702838698.png)

一个应用安装在设备上，只有该设备支持的CPU架构对应的.so文件会被安装。不同CPU架构的Android手机加载时会在libs下找自己对应的目录，从对应的目录下寻找需要的.so文件；如果没有对应的目录，就会去armeabi下去寻找，如果已经有对应的目录，但是如果没有找到对应的.so文件，也不会去armeabi下去寻找了。

当在项目的build.gradle中设置了abiFilters时，要么对应的Filter的SO文件都有，要么都没有，那么应用程序就会直接向armeabi查找SO文件进行兼容处理。

ndk {

//APP的build.gradle设置支持的SO库架构
abiFilters 'armeabi', 'armeabi-v7a','arm64-v8a'

}

![Image 7](https://img2023.cnblogs.com/blog/3068292/202303/3068292-20230323174646289-1155306494.png)

适配不同的平台

目前主流的Android设备是armeabi-v7a架构的，然后就是x86和armeabi了。如果同时包含了 armeabi，armeabi-v7a和x86，所有设备都可以运行，程序在运行的时候去加载不同平台对应的so，这是较为完美的一种解决方案，但是同时也会导致包变大。

armeabi-v7a是可以兼容armeabi的，而v7a的CPU支持硬件浮点运算，目前绝大对数设备已经是armeabi-v7a了，所以为了性能上的更优，就不要为了兼容放到armeabi下了。x86也是可以兼容armeabi平台运行的，另外需要指出的是，打出包的x86的so，总会比armeabi平台的体积更小，对于性能有洁癖的童鞋们，还是建议在打包so的时候支持x86。

第三方平台的.so库怎么处理

第三方的类库只提供了armeabi下的.so文件，我们项目里适配了armeabi-v7a和x86，如果不在对应的文件下放对应的.so文件，就可能导致某些Android设备会出一些问题，我们可以复制armeabi下得.so文件到不同的文件夹下。如果第三方提供了不同平台的.so文件，则复制不同平台的.so文件到项目中对应的文件夹下即可

4、针对应用平台适配64位政策-让apk适配 64 位架构  
原因：

目前，Arm架构将逐步限制32位应用的运行。32位应用仅支持跑在小核之上，会导致纯32位应用在性能与功耗等方面出现明显的体验问题。预计2023底上市的旗舰机，Arm的IP架构将只支持64位应用。

政策解读：

Arm将推出只支持64位应用的架构，因此应用要适配64位架构，修改的目的是为了确保应用能够在仅支持 64 位架构的环境中正常运行。

针对政策的解决方案：

确保应用包含64位库即可，如包含不做修改，如未包含，需添加64位库即可。

应用不一定要支持所有 64 位架构，但对于支持的每种原生 32 位架构，应用都必须包含相应的 64 位架构。

5、Android Studio如何构建支持不同架构的apk  
修改build.gradle文件下的android标签下的defaultConfig标签下的ndk标签下的abiFilters值然后打包即可。

[(279条消息) 解读apk分包-32位安装包、32位64位兼容包和64位安装包\_android 64位安装包\_璐璐丫头的博客-CSDN博客](https://blog.csdn.net/li1500742101/article/details/127631236)

[(279条消息) Android生成Apk32位和64位问题\_android 如何打64位apk包\_inlooker的博客-CSDN博客](https://blog.csdn.net/K_Cobian/article/details/111895823?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-111895823-blog-127631236.235%5Ev27%5Epc_relevant_multi_platform_whitelistv3&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-111895823-blog-127631236.235%5Ev27%5Epc_relevant_multi_platform_whitelistv3&utm_relevant_index=1)
