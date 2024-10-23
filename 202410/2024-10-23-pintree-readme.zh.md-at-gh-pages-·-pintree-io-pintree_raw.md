Title: pintree/README.zh.md at gh-pages · Pintree-io/pintree

URL Source: https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md

Markdown Content:
[English](https://github.com/Pintree-io/pintree/blob/gh-pages/README.md) | [中文](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md)

Pintree 是一个开源项目，旨在将浏览器书签导出成导航网站。通过简单的几步操作，就可以将书签转换成一个美观且易用的导航页面。

[![Image 1](https://github.com/Pintree-io/pintree/raw/main/assets/preview.png)](https://github.com/Pintree-io/pintree/blob/main/assets/preview.png)

项目功能和目标
-------

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E9%A1%B9%E7%9B%AE%E5%8A%9F%E8%83%BD%E5%92%8C%E7%9B%AE%E6%A0%87)

*   导出浏览器书签
*   将书签文件转换成JSON格式
*   生成静态导航网站

安装和运行
-----

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E5%AE%89%E8%A3%85%E5%92%8C%E8%BF%90%E8%A1%8C)

### 步骤 1：下载浏览器书签

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E6%AD%A5%E9%AA%A4-1%E4%B8%8B%E8%BD%BD%E6%B5%8F%E8%A7%88%E5%99%A8%E4%B9%A6%E7%AD%BE)

1.  安装 [Pintree Bookmarks Exporter](https://chromewebstore.google.com/detail/pintree-bookmarks-exporte/mjcglnkikjidokobpfdcdmcnfdicojce) 插件。
2.  使用插件导出浏览器书签，并保存 JSON 文件到本地。

[![Image 2](https://github.com/Pintree-io/pintree/raw/main/assets/guide/step1.png)](https://github.com/Pintree-io/pintree/blob/main/assets/guide/step1.png)

### 步骤 2：Fork 项目

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E6%AD%A5%E9%AA%A4-2fork-%E9%A1%B9%E7%9B%AE)

1.  访问 [Pintree GitHub 仓库](https://github.com/Pintree-io/pintree)。
2.  点击页面右上角的 `Fork` 按钮，将项目 Fork 到您的 GitHub 账号中。

[![Image 3](https://github.com/Pintree-io/pintree/raw/main/assets/guide/step2.png)](https://github.com/Pintree-io/pintree/blob/main/assets/guide/step2.png)

### 步骤 3：替换 JSON 文件

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E6%AD%A5%E9%AA%A4-3%E6%9B%BF%E6%8D%A2-json-%E6%96%87%E4%BB%B6)

1.  打开您 GitHub 账号中的 `pintree` 仓库（即刚才 Fork 的项目）。
2.  点击仓库中的 `json` 文件夹。
3.  点击 `Upload files` 按钮，选择刚才下载的 JSON 文件，并上传。
4.  确保上传的文件命名为 `pintree.json`，并选择 `Commit changes`。

[![Image 4](https://github.com/Pintree-io/pintree/raw/main/assets/guide/step3.png)](https://github.com/Pintree-io/pintree/blob/main/assets/guide/step3.png)

### 步骤 4：启用 GitHub Pages

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E6%AD%A5%E9%AA%A4-4%E5%90%AF%E7%94%A8-github-pages)

1.  在您的 `pintree` 仓库页面，点击 `Settings`。
2.  找到 `Pages` 选项。
3.  在 `Source` 下拉菜单中，选择 `gh-pages` 分支，然后点击 `Save`。
4.  几分钟后，您的静态网站将会在 `https://yourusername.github.io/pintree` 上可用。记得替换 `yourusername`。

[![Image 5](https://github.com/Pintree-io/pintree/raw/main/assets/guide/step4.png)](https://github.com/Pintree-io/pintree/blob/main/assets/guide/step4.png)

* * *

通过以上步骤，您已经成功完成了 Pintree 项目的安装和运行。如果有任何问题，可以加群获取更多帮助，也可以添加我的微信: `Gift_wei` 我拉你进交流群

[![Image 6](https://github.com/Pintree-io/pintree/raw/main/assets/wechat_group.png)](https://github.com/Pintree-io/pintree/blob/main/assets/wechat_group.png)

使用技术
----

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E4%BD%BF%E7%94%A8%E6%8A%80%E6%9C%AF)

*   HTML/CSS/JavaScript
*   JSON格式处理
*   静态网站托管

贡献指南
----

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E8%B4%A1%E7%8C%AE%E6%8C%87%E5%8D%97)

欢迎贡献代码和提出建议！请遵循以下步骤参与项目：

1.  Fork 本仓库：[https://github.com/Pintree-io/pintree/tree/main](https://github.com/Pintree-io/pintree/tree/main)
2.  创建一个新的分支 (`git checkout -b feature/your-feature`)
3.  提交您的修改 (`git commit -am 'Add some feature'`)
4.  推送到分支 (`git push origin feature/your-feature`)
5.  提交一个 Pull Request

请注意，`main` 分支是项目的源代码分支，而 `gh-pages` 分支是打包出来的静态网站代码分支。请在 `main` 分支上进行开发和提交，然后我们会负责将代码打包并发布到 `gh-pages` 分支。

联系方式
----

[](https://github.com/Pintree-io/pintree/blob/gh-pages/README.zh.md#%E8%81%94%E7%B3%BB%E6%96%B9%E5%BC%8F)

如有任何问题或建议，请通过以下方式联系我们：

*   项目网站: [Pintree](https://pintree.io/)
*   Email: [viggo.zw@gmail.com](mailto:viggo.zw@gmail.com)
*   微信：`Gift_wei`

感谢使用和支持！
