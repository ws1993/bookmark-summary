Title: UE、Unity、Cesium、Three.js四款3D引擎入门级对比分析

URL Source: https://mp.weixin.qq.com/s/R8rSxsTVhPi5IZK_eMqq3g

Markdown Content:
文/张新房（纽豪斯）

作为一名数字孪生校园系统平台提供商和解决方案供应商的一员，经常有学校老师咨询相关的技术问题，最基础的莫过于“你家数字孪生平台用了什么3D引擎？”。从客户的需求分析来看，有的学校需要三维GIS导航系统、有的学校需要全景照片漫游系统、有的学校需要数字孪生校园、有的学校需要数字人、有的学校需要元宇宙，也有的学校什么都想要。

有人说，全中国都没有自主知识产权的3D引擎，有人说我们家的3D引擎是国产自主知识产权的，莫衷一是。不管哪种需求，不管哪种情况，有四款引擎作为入门级知识是一定要了解的，分别是：UE（虚幻引擎）、Unity、Cesium和Three.js。有的公司直接使用以上四种引擎的一种或者多种进行数字孪生校园开发，有的公司用UE开发数字人，有的公司用开源的Cesium和Three.js打磨自己的3D引擎。

![Image 1](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlhKBqDk6FekKhDicVicVr0jdZgvt81ZNue2HxtJxicovnNqR3okjNaCzic2A/640?wx_fmt=png&from=appmsg)

**一、UNREAL ENGINE（虚幻引擎）part of EPIC GAMES**
-------------------------------------------

![Image 2](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlhxRDrIEnxorp5bMZO4weicdAiaw9OdQSr36hHKVtqO0gm8SqhU1YP9fRQ/640?wx_fmt=png&from=appmsg)

UE是一款功能强大的游戏引擎，拥有可视化脚本系统、高级渲染功能和广泛的工具集。它支持各种平台（如PC、主机和移动设备）的游戏开发，并且具有出色的图形效果和物理模拟能力。使用场景包括：在AAA级游戏制作（如黑神话悟空就用了UE5）中被广泛使用，可创建高品质、逼真的游戏体验。它还用于虚拟现实（VR）和增强现实（AR）应用开发。

UE是一个功能强大且复杂的引擎，需要学习其脚本语言（Blueprints或C++）以及各种编辑器和工具的使用。对于初学者来说，可能需要一定的时间和精力来熟悉其工作流程和开发概念。

UE对于大规模的模型和场景有良好的支持能力。它采用了基于网格的渲染和场景分级LOD（Level of Detail）系统，可以有效地处理复杂的几何体和大规模场景。UE还提供了高效的资源管理和流加载机制，可以优化大型模型的加载和渲染性能。

UE采用了先进的渲染技术，包括基于物理的渲染（PBR）、实时全局光照（Real-Time Global Illumination）、屏幕空间反射（Screen Space Reflections）等。它还支持动态天空、体积雾、后期处理效果等。UE的渲染引擎被广泛认为在视觉质量和逼真度方面表现出色。

UE在国内游戏开发领域非常受欢迎，并且已经被广泛采用。很多国内游戏开发公司和独立开发者使用UE进行高质量游戏的制作。除游戏之外，UE还在国内的虚拟现实（VR）、增强现实（AR）、数字人领域得到应用，包括教育、设计等领域。国内某些厂家的数字孪生系统就是基于UE开发的（比如51World）。

UE4拥有庞大而活跃的开发者社区，全球范围内都有大量的用户和开发者共享经验、解答问题，并分享自己的项目和资源。UE4官方提供了广泛的文档、教程、示例项目和论坛等资源，为开发者提供全方位的支持和交流平台。

![Image 3](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlhHWDzxkhDthMpDZhDQvlT79CaFh87WwvzicYA5ia7R0cvricibYNw2z2CAw/640?wx_fmt=png&from=appmsg)

**二、UNITY（优三缔）**
----------------

![Image 4](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlhHkib3oiasZQbEibSPD8anD0Hicrj6z3MVOiczFuLppTdutlJfz7qIrwQZfw/640?wx_fmt=png&from=appmsg)

优三缔科技（上海）有限公司

Unity是一款跨平台的游戏引擎，由Unity Technologies开发和维护。它支持多种平台，包括Windows、Mac、iOS、Android等，并且可以用于开发2D和3D游戏、虚拟现实和增强现实应用等。Unity提供了丰富的工具和功能，包括场景编辑器、物理模拟、动画系统、碰撞检测、粒子效果等，方便开发者创建和管理游戏内容。同时，Unity还支持多种编程语言，如C#和JavaScript，使得开发者可以根据自己的喜好和需求进行开发。Unity是一个强大、灵活和易于上手的游戏引擎，被广泛应用于游戏开发和其他交互式应用的开发领域。

Unity的最新版本是Unity 6。

Unity是一款灵活易用的跨平台引擎，具有可视化编辑器和强大的脚本支持。它支持多个平台，包括PC、主机、移动设备和Web。Unity具有广泛的资源库和生态系统，可加快游戏开发进程。Unity在各种游戏类型和应用领域都有应用，包括游戏开发、AR/VR应用、模拟器、交互式应用等。它适合独立开发者和小团队，并且有强大的跨平台发布能力。  

Unity具有友好的可视化编辑器和强大的脚本支持，对于有编程经验的开发者来说相对容易上手。它有广泛的学习资源和社区支持，可以帮助初学者快速入门。

Unity在处理大模型方面的性能和效果因项目配置和开发实践而异。它提供了层级LOD系统和场景分割技术，以优化大型场景的渲染。Unity的性能也受到硬件和图形设置的影响。对于非常大型的模型和场景，可能需要使用额外的优化技术和工具。

Unity的渲染技术不断发展，最新版本引入了可编程渲染管线（Scriptable Render Pipeline），使开发者能够自定义渲染过程。Unity支持基于物理的渲染、实时光照、阴影和后期处理效果，但在某些高级渲染方面可能需要额外的插件或自定义开发。

Unity在国内的应用非常广泛，涵盖游戏、AR/VR应用、教育、建筑可视化、工业仿真等多个领域。国内许多游戏开发公司和独立开发者都选择Unity进行游戏开发。Unity还拥有庞大的中国开发者社区和资源库，提供了丰富的学习资源和技术支持。

Unity拥有非常庞大的开发者社区，全球范围内有大量的用户和开发者活跃于Unity社区中。Unity官方提供了详细的文档、教程、示例项目和论坛等资源，开发者可以在社区中交流、分享和寻求帮助。此外，Unity还有许多第三方社区和资源库，提供了丰富的扩展和插件。

Unity3D使用C#作为主要开发语言的游戏引擎。开发者可以使用C#编写游戏逻辑、脚本和插件等。此外，Unity3D还支持使用UnityScript（一种与JavaScript类似的脚本语言）进行开发。在使用Unity3D开发时，开发者可以使用Visual Studio等集成开发环境（IDE）进行代码编写和调试。  

![Image 5](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlhlIJt4gC7y5yquNicGPBDhUaNmRicJDKJeSApmJsbhicBRC7lrWFvAnO5g/640?wx_fmt=png&from=appmsg)

**三、CESIUM Part of Bentley Systems**
------------------------------------

![Image 6](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlhAddgr2o9VbZkuvjqv9snWfnhkibxqACxHOBFNJgPBK0XRnhAE17vljA/640?wx_fmt=png&from=appmsg)

Cesium是一个基于Web的地理信息系统（GIS）引擎，用于呈现地球表面的三维地图。它使用JavaScript进行开发，并支持高度可定制的地理数据可视化。Cesium还具有对地球表面进行高效渲染和交互的能力。Cesium主要用于地理信息系统、地球科学、遥感应用等领域。它被广泛应用于可视化地球数据、创建地球模拟和提供交互式地理可视化效果的应用。

Cesium是一个基于Web的GIS引擎，需要了解地理信息系统和地球科学的基础知识。对于熟悉JavaScript和地理数据可视化的开发者来说，学习曲线可能较为陡峭。

Cesium专注于地球表面的三维地图渲染，对于大规模地理数据集和模型有很好的支持能力。它采用了分片和地理空间索引技术，可以高效地呈现和交互大规模的地球表面数据。Cesium还提供了数据流式传输和级联LOD等功能，以优化大模型的加载和渲染性能。

Cesium主要用于地球表面的三维地图渲染，它采用了基于WebGL的渲染技术。Cesium支持大规模地理数据的可视化和渲染，包括地形渲染、纹理贴图、矢量数据渲染等。然而，相对于游戏引擎，Cesium的渲染技术在高级图形效果和逼真度方面可能较为有限。

Cesium在国内主要用于地理信息系统（GIS）、地球科学和遥感等领域。被用于可视化地球数据、展示地理信息、制作地球模拟等应用。国内的地理信息、测绘和GIS相关企业和研究机构使用Cesium进行地理可视化和空间数据展示。

Cesium拥有较小但专注的开发者社区，主要集中在地理信息系统（GIS）和地球科学领域。Cesium的官方网站提供了文档、示例和开发者论坛等资源，开发者可以在社区中分享和讨论相关话题。

Cesium是一个开源的JavaScript库，用于创建3D地球和2D地图。它专注于地理信息系统（GIS）和地球可视化应用，能够处理大量的地理空间数据。Cesium提供了高精度的地球模型，支持多种地理数据格式，并具备出色的性能优化。主要特点

•地球和地图渲染：提供高精度的3D地球和2D地图展示。

•地理空间数据支持：支持多种格式的地理数据，如KML、CZML、GeoJSON等。

•时间动态性：支持时间动态数据，可用于模拟和展示历史或未来的地理变化。

•高性能：使用WebGL进行渲染，具备良好的性能和可扩展性。

![Image 7](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlhfhl6EdKBnMZ6AHEicibv18QS6sotpLxXrVe0ZzosdvGJWRwFlUDia4SLg/640?wx_fmt=png&from=appmsg)

**四、Three.js r169**
-------------------

![Image 8](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlhcHI4LrCMTNib0aicaz1HWT84rtOhfcAia3GTvUK1weCgoCZxyp7kzX9bQ/640?wx_fmt=png&from=appmsg)

three.js是一款基于JavaScript的开源3D图形库，用于在Web浏览器中创建和展示交互式3D图形。Three.js是一个轻量的跨浏览器API库，通常用来在Web浏览器中创建并显示动态的3D图像。作者是图形编程工程师Ricardo Cabello。Ricardo（mrdoob）以前是一名图形设计师，后来成为了软件工程师。现在这两种身份兼而有之，同时还在做开源维护者，目前在Google工作。主要专注于提升开发者在Web端进行3D、AR以及VR开发时的体验。

three.js提供了一套简单易用的API，方便开发者在Web页面中使用WebGL技术进行3D渲染。通过three.js，开发者可以创建和管理3D场景、模型、灯光、材质等，并且可以应用动画、碰撞检测、阴影等效果。three.js 还支持多种导入格式，如JSON和OBJ，可以方便地导入和使用现有的3D模型。three.js 是一个功能强大、轻量级且跨浏览器的 3D图形库，适用于创建各种类型的 3D 可视化、游戏和交互式应用。

Three.js是一个轻量级的JavaScript库，用于在Web浏览器中创建和呈现三维图形。它提供了基础的3D渲染功能，包括几何体创建、材质和光照效果。Three.js易于上手，并具有丰富的社区资源。Three.js广泛应用于Web上的三维可视化和互动效果的创建。它适用于网页游戏、数据可视化、产品展示、AR/VR网页应用等领域。

Three.js是一个轻量级的JavaScript库，对于有基础的Web开发知识的开发者来说相对容易上手。它具有简洁的API和文档，并有活跃的社区支持。

Three.js是一个轻量级的引擎，对于大模型的支持能力较为有限。在处理大型模型和场景时，可能需要自行实现LOD系统和场景优化技术，以确保性能和渲染质量的平衡。由于Three.js运行在Web浏览器中，还需要考虑浏览器的性能限制和硬件要求。

Three.js是一个基于Web的轻量级渲染引擎，它利用WebGL技术进行渲染。Three.js提供了基本的3D渲染功能，包括几何体渲染、纹理贴图、光照和阴影等。它还支持一些后期处理效果和基于物理的渲染，但在高级渲染技术和逼真度方面相对较为有限。

Three.js在国内的应用也相当广泛。国内有很多大厂的3D引擎就是基于开源的Three.js进行封装的。被用于Web上的三维可视化、互动效果的创建。国内许多产品展示、数据可视化等项目都选择使用Three.js进行开发。Three.js具有简洁的API和易于上手的特点，适合广大开发者使用。

Three.js拥有活跃的开发者社区，全球范围内有大量的开发者和爱好者使用和贡献Three.js。官方网站提供了详细的文档、示例、教程和开发者论坛等资源。此外，Three.js还有许多第三方网站和社区，提供了更多的学习资源、教程和扩展。

three.js使用WebGL技术进行3D渲染。由于three.js可以直接在Web页面中嵌入和运行，因此适用于开发各种在线的3D可视化、模型展示、产品展示、数据可视化等应用。three.js提供了简单易用的API，使得开发者能够创建和管理3D场景、模型、灯光等，并应用动画、碰撞检测等效果。同时，由于它是基于Web技术的，可以与其他Web技术和工具进行集成，如HTML、CSS、JavaScript库等。

three.js是基于JavaScript的图形库，用于在Web浏览器中创建和展示3D图形。开发者使用JavaScript编写three.js的代码，进行3D场景的构建、模型的加载和动画的控制等。开发者可以使用任何支持JavaScript的文本编辑器进行代码编写，如Visual Studio Code、Sublime Text等。

Three.js是一个开源的JavaScript库，用于在Web上创建和显示3D图形。它是一个通用的3D图形引擎，广泛应用于游戏开发、数据可视化、动画和交互式3D应用。Three.js提供了丰富的3D图形渲染工具和灵活的API接口。主要特点

•多样化的3D渲染：支持各种3D图形和效果的渲染，包括模型、光照、材质、动画等。

•跨平台支持：可以在多种设备和浏览器上运行，兼容性好。

•丰富的工具集：提供多种实用的工具和辅助库，如加载器、控制器、效果器等。

•灵活性：可以根据需求自由组合和定制3D场景和效果。

**五、对比分析**
----------

UE和Cesium在处理大规模模型和场景方面具有较强的优势。Unity可以通过适当的配置和优化技术来应对大模型需求，而Three.js相对而言在大模型支持方面较为有限。对于需要处理大型模型的项目，综合考虑引擎的性能、工具和优化能力，选择最适合的引擎非常重要。

UE在渲染技术方面拥有先进的特性和逼真度。Unity的渲染技术不断发展，通过可编程渲染管线可以实现更高级的自定义渲染。Cesium主要注重地理数据的渲染和可视化，而Three.js是一个轻量级的Web渲染引擎，提供基本的渲染功能。选择合适的引擎应基于项目需求、图形质量要求和开发者的技术栈。

Unity和three.js在数字孪生中都经常用到，Unity是跨平台的，three.js是Web端的，而且Unity也不主要是用在web上或者数字孪生领域，这就好比拿个智能手机和功能手机比功能。

three.js是基于WebGL技术的图形库，在Web浏览器中进行3D渲染。由于受到Web浏览器的限制，three.js的性能可能受到一些限制。WebGL虽然是高性能的，但仍然受到浏览器和设备的硬件和软件限制。同时，由于three.js是通过JavaScript运行在Web环境中，因此在处理大量复杂的3D场景或动画时，可能会受到性能的影响。

Unity3D作为专业的游戏引擎，在游戏开发和复杂3D场景中通常能够提供更高的性能。而three.js作为基于Web的图形库，在Web浏览器中展示3D图形，受到浏览器和硬件的限制，性能可能相对较低。但是，性能的具体表现还取决于具体的应用场景、开发者的优化能力以及设备的硬件配置等因素。

Cesium和Three.js都是功能强大的Web 3D图形库，但它们在应用领域和技术实现上有显著差异。Cesium专注于地理信息系统和地球可视化，适合需要处理和展示地理空间数据的项目；而Three.js则是一个通用的3D图形引擎，适用于广泛的3D应用场景。开发者可以根据项目需求选择合适的工具，充分发挥它们的优势。

此为入门，非专业科普文章，大部分资料来源于互联网，如有错误，请指正，望见谅。

未完，待续...

参考文章：
-----

\[1\].AR大玩家.UE4、Unity、Cesium、Three.js三维引擎软件对比分析,https://baijiahao.baidu.com/s?id=1802350852478151677&wfr=spider&for=pc,2024-06-20 11:55

\[2\].方拓数字. UE4、Unity、Cesium、Three.js三维引擎软件对比分析, [https://mp.weixin.qq.com/s/yqGX28QtOQMCX-LaSG2sQA](https://mp.weixin.qq.com/s?__biz=MzU2Mzk3NzcxOQ==&mid=2247484177&idx=1&sn=69b81218fda1689858ab2623589bd3ac&scene=21#wechat_redirect),2023.6.20

\[3\].大象数据工场.数字孪生引擎：拿unity3D和three.js相比，有点羞辱前者了，https://blog.csdn.net/2401\_82881178/article/details/140880951，2024-08-02 21:49:17

\[4\].前端小助手.Cesium与Three.js的区别，https://blog.csdn.net/gz\_qiulinyong/article/details/140170832，2024-07-04 09:43:02

![Image 9](https://mmbiz.qpic.cn/sz_mmbiz_png/eAmE3pyVogia1ZT91aFnk55ozKHEiaAAlh7xELDrUdlpKic5qd8dS2zQLwEzvMZnchBHlibbsEt6vt8Ko5URaEt0EA/640?wx_fmt=png&from=appmsg)

UON孪生｜天行健数字孪生平台

时位即世界、即宇宙

天行健，君子以自强不息

天是指时，行是指位（空间和方位）

健是指在时空（位）的配合下永无止境地运行

文章编号：gh\_0e628d8c2d10..92
