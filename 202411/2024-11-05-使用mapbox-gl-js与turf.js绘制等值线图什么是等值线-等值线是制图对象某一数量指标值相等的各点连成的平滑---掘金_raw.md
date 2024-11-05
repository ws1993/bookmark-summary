Title: 使用mapbox-gl-js与turf.js绘制等值线图什么是等值线 等值线是制图对象某一数量指标值相等的各点连成的平滑 - 掘金

URL Source: https://juejin.cn/post/7044797998177452040

Markdown Content:
### 什么是等值线

等值线是制图对象某一数量指标值相等的各点连成的平滑曲线，由地图上标出的表示制图对象数量的各点，采用内插法找出各整数点绘制而成的。等值线地图的编制，则通常是在地理底图上标出制图对象的相对点位（测站）的数值，然后把数值相等的点联成圆滑曲线，勾画出制图对象的空间结构特征。

如年平均气温图、年降水量图。它是专题地图的重要图型，最先用于描述地形。 常见的有表现地势起伏和地貌结构的等高线图与等深线图； 表现气温、水温、地温变化的等温线图；表现大气降水量变化的等降水量线图； 在水利方面常常用来展示降雨量大小分布情况；

![Image 1: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ba2604c6b92a4808ace308ab93fb3e6b~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 绘制过程

```
// 散点（Points）经过插值、等值线绘制、裁剪和渲染展示。
// 各个函数间传递GeoJSON 数据

// 添加图层
mapInstance.addLayer(
  // 计算交集，边界裁切
	turf.intersect(
	// 基于插值获得的格点绘制等值区域
		turf.isobands(
	  // 数据插值
			turf.interpolate(geojson)
		),boundaries
	)
)
```

#### 1\. 获取站点雨量数据、边界数据

```
const basinRes = await axios.get('static/json/边界.geojson');
const rainPointList = await getRainList();
```

#### 2\. 数据插值（耗时过程）

> [turf.interpolate()](https://link.juejin.cn/?target=https%3A%2F%2Fturfjs.fenxianglu.cn%2Fcategory%2Finterpolation%2Finterpolate.html "https://turfjs.fenxianglu.cn/category/interpolation/interpolate.html") 提供了基于 [IDW（反距离权重）](https://link.juejin.cn/?target=https%3A%2F%2Fbaike.baidu.com%2Fitem%2F%25E5%258F%258D%25E8%25B7%259D%25E7%25A6%25BB%25E5%258A%25A0%25E6%259D%2583%25E6%258F%2592%25E5%2580%25BC%2F3689866 "https://baike.baidu.com/item/%E5%8F%8D%E8%B7%9D%E7%A6%BB%E5%8A%A0%E6%9D%83%E6%8F%92%E5%80%BC/3689866")算法的将数据插值为格点的方法。插值的精度是由第二个参数与 interpolate\_options.units 共同决定的，单位支持 degrees, radians, miles, or kilometers，IDW 要为每个格点计算所有散点的权重，计算规模是 (散点数 \* 格点数)，所以要在精度与性能间做好平衡。 我们将之前的散点（points）代入

```
// interpolate 只接受FeatureCollection,先构造FeatureCollection 
const pointFeature = {
  type: 'FeatureCollection',
  features: rainPointList.map(i => {
    return {
      type: 'Feature',
      geometry: {
        type: 'Point',
        coordinates: [Number(i.lgtd), Number(i.lttd)],
      },
      properties: i,
    };
  }),
};
// 插值配置
const interpolate_options = {
  gridType: 'points',
  // 降雨值
  property: 'sdrp',
  units: 'degrees',
  weight: 10,
};
// 插值
// 第二个参数是插值精度，值越小，精度越大，插的值越多，也越耗时
const gridInterpolate = turf.interpolate(pointFeature, 0.01, interpolate_options)
```

#### 3\. 根据插值结构生成等值线

> 这一步基于插值获得的格点绘制等值区域，并为区域配置颜色。[turf.isobands()](https://link.juejin.cn/?target=https%3A%2F%2Fturfjs.fenxianglu.cn%2Fcategory%2Finterpolation%2Fisobands.html "https://turfjs.fenxianglu.cn/category/interpolation/isobands.html") 根据 zProperty 分段，形成一些 MultiPolygon。

```
// 等值线分割点，跟zProperty比较
const breaks = [0, 10, 25, 50, 100, 250, 10000];
// 配置
const isolines_options = {
  // rainPointList 降雨量字段的key sdrp
  zProperty: 'sdrp',
  commonProperties: {
    'fill-opacity': 0.6,
  },
  breaksProperties: [
    { fill: '#a5f38d' },
    { fill: '#39aa00' },
    { fill: '#63baff' },
    { fill: '#0000fe' },
    { fill: '#ff00fe' },
    { fill: '#ff0000' },
  ],
};
// gridIsobands是FeatureCollection <MultiPolygon>类型
let gridIsobands = turf.isobands(gridInterpolate, breaks, isolines_options);
```

#### 4\. 与边界数据进行裁切

> [turf.intersect()](https://link.juejin.cn/?target=https%3A%2F%2Fturfjs.fenxianglu.cn%2Fcategory%2Ftransformation%2Fintersect.html "https://turfjs.fenxianglu.cn/category/transformation/intersect.html") 函数：取两个多边形并找到它们的交点。如果它们共享一个边界，返回边界;如果它们不相交，返回undefined。 接收两个Feature 类型参数

```
// 先将gridIsobands需要先 flatten() 处理一下
const gridIsobands = turf.flatten(gridIsobands);
// 之后对每个 Polygon 做一次 intersect() 操作。
const features = [];
gridIsobands.features.forEach((layer1) => {
  basinRes.features.forEach((layer2) => {
    let intersection = turf.intersect(layer1, layer2);
    if (intersection != null) {
      intersection.properties = layer1.properties;
      intersection.id = Math.random() * 100000;
      features.push(intersection);
    }
  });
});
// 将裁切之后的数据转成FeatureCollection类型
const geojson = turf.featureCollection(features);
```

#### 5\. 添加等值线图层

```
mapInstance.addLayer({
  id: 'contourLayer',
  type: 'fill',
  source: {
    type: 'geojson',
    data: geojson,
  },
  paint: {
    'fill-color': ['get', 'fill'],
    'fill-opacity': 0.8,
    "fill-outline-color": "red"
  },
});
```

### 重难点分析（数据插值耗时操作）

#### 1\. 常规写法

```
// 数据插值
const gridInterpolate = turf.interpolate(pointFeature, 0.01, interpolate_options)
```

采用上述写法，如果站点值很多，且精度设置的较大，此时会造成js主线程阻塞，浏览器页面会直接卡住，无任何相应动作，严重影响体验。

#### 2\. 什么是web worker

Web Worker 的作用，就是为 JavaScript 创造多线程环境，允许主线程创建 Worker 线程，将一些任务分配给后者运行。在主线程运行的同时，Worker 线程在后台运行，两者互不干扰。等到 Worker 线程完成计算任务，再把结果返回给主线程。这样的好处是，一些计算密集型或高延迟的任务，被 Worker 线程负担了，主线程（通常负责 UI 交互）就会很流畅，不会被阻塞或拖慢。 Worker 线程一旦新建成功，就会始终运行，不会被主线程上的活动（比如用户点击按钮、提交表单）打断。这样有利于随时响应主线程的通信。但是，这也造成了 Worker 比较耗费资源，不应该过度使用，而且一旦使用完毕，就应该关闭。

#### 3\. 进阶写法

为了防止插值过程长时间占用主线程，造成进程阻塞，所以使用web worker。 在vue中直接使用原生web worker较为麻烦，这里使用 [vue-worker](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fisraelss%2Fvue-worker "https://github.com/israelss/vue-worker") 写法更简单。

```
// 安装
npm i vue-worker
// 在main.js 添加
import Vue from 'vue'
import VueWorker from 'vue-worker'
Vue.use(VueWorker)
// 在组件中采用 this.$worker 进行使用
```

```
const computeFunc = (...e) => {
  // Worker 内部如果要加载其他脚本，有一个专门的方法importScripts()
  // 引入 turf.js
  importScripts('https://cdn.bootcdn.net/ajax/libs/Turf.js/6.5.0/turf.min.js');
  // self代表子线程自身，即子线程的全局对象
  // 数据插值
  return self.turf.interpolate(e[0], e[1], e[2]);
};
// This method works like Promise.resolve(), but in another thread.
// 此方法创建一个一次性worker，运行并返回给定函数的结果并关闭。
const gridInterpolate = await this.$worker.run(computeFunc, [pointFeature, 0.01, interpolate_options]);
```

### 成果展示

![Image 2: 插值0.01.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a78f13aa3dcc472ba1ae15b2831b1060~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 插值精度 `0.05  VS  0.01`

![Image 3: 插值0.05vs0.01.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2ce0d5c2261f493ba5517d9eda93265c~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

### 相关链接

> [Web Worker 使用教程](https://link.juejin.cn/?target=https%3A%2F%2Fwww.ruanyifeng.com%2Fblog%2F2018%2F07%2Fweb-worker.html "https://www.ruanyifeng.com/blog/2018/07/web-worker.html")

> [vue-worker](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fisraelss%2Fvue-worker "https://github.com/israelss/vue-worker")​

> [Turf.js中文网](https://link.juejin.cn/?target=https%3A%2F%2Fturfjs.fenxianglu.cn%2F "https://turfjs.fenxianglu.cn/")​
