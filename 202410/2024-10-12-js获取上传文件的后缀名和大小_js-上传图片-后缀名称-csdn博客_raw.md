Title: js获取上传文件的后缀名和大小_js 上传图片 后缀名称-CSDN博客

URL Source: https://blog.csdn.net/qq_33988065/article/details/56841587

Markdown Content:
最新推荐文章于 2024-08-28 12:34:01 发布

![Image 1](https://csdnimg.cn/release/blogv2/dist/pc/img/original.png)

[东都花神](https://blog.csdn.net/qq_33988065 "东都花神") ![Image 2](https://csdnimg.cn/release/blogv2/dist/pc/img/newCurrentTime2.png) 最新推荐文章于 2024-08-28 12:34:01 发布

版权声明：本文为博主原创文章，遵循 [CC 4.0 BY-SA](http://creativecommons.org/licenses/by-sa/4.0/) 版权协议，转载请附上原文出处链接和本声明。

利用H5的新特性我们可以十分方便的获取上传文件的后缀名和大小，对于上传文件的校验十分方便，下面是具体的实现代码：

在线体验： [https://nk5qy2lwvj.codesandbox.io/](https://nk5qy2lwvj.codesandbox.io/)

源码：

```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
    <title>Document</title>
    <script src="https://cdn.bootcss.com/jquery/3.1.1/jquery.min.js"></script>
</head>
<body>
    <input type="file"  id="file"/>
    <button>清空</button>
    <script type="text/javascript">
       $('input').on('change', function () {
          alert('上传文件后缀名为：' + this.value.toLowerCase().split('.').splice(-1));
          alert('上传文件大小为：' + this.files[0].size/1024 + 'kb');
       });
       
       $('button').on('click', function () {
        	var objFile = document.getElementById("file")
           	objFile.outerHTML=objFile.outerHTML.replace(/(value=\").+\"/i,"$1\"");  
       });
    </script>
</body>
</html>


```
