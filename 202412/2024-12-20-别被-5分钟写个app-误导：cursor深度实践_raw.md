Title: 别被"5分钟写个App"误导：Cursor深度实践

URL Source: https://mp.weixin.qq.com/s/JVb7-4a2XOFhfeJusaxvFg

Markdown Content:
今年 8 月份时试用了下 Cursor，发现非常惊艳，顺带写了一篇介绍 Cursor 的文章\[1\]。之后我很快就把日常工作环境从 GitHub Copilot + JetBrains 全面转向了付费版 Cursor，几个月使用下来感觉非常丝滑。

在自己使用的同时，我也经常向同事和朋友推荐 Cursor，不过发现不少同学还是经常会有疑问，比如：

*   它比起原生的 ChatGPT, Claude 有什么优势吗？或者说 Cursor 的强大主要就是因为 Sonnet 3.5？
    
*   它与 GitHub Copilot 相比有什么不同之处？为什么价格贵了一倍。
    
*   Cursor 是不是只适用于从零开始快速写一个小 demo？
    
*   Codeium 新推出了 Windsurf，看博主的视频好像更加丝滑，是不是应该切换？
    
*   Coding Copilot 是不是只对于新手比较有用？
    
*   在 AI Copilot 浪潮中，我们应该如何精进代码能力？还是说终将被 Agent 完全取代？
    

这里有不少问题，我发现最好的方式还是通过 live coding 来展示，所以 1024 程序员节那天我也在公司内部做了个分享，尽可能通过边操作演示边讲解的方式来展现 Cursor 的优点和使用技巧。不过当时用的是公司内部的代码项目，不好直接分享，所以这里就略微改动下，希望能通过这篇文章揭示一些 Cursor/Coding Copilot 的魅力与实践心得。

Cursor 简介与定位
------------

Cursor 是几位非常年轻的 MIT 学生在 2022 年创立的一家公司，当时其实 GitHub Copilot 已经有非常大的体量了。在产品刚推出时我也简单试用了下，当时感觉非常简单，好像就是把跟 ChatGPT/Claude 对话，生成代码的流程放到了 VSCode 里，没啥特别的……

但后来的发展出乎了几乎所有人的意料，我们来看下当时的格局：

*   针对专业开发者来说，GitHub Copilot 无疑是最有优势的，几乎凭一己之力真正跑通了 Coding Copilot 的 PMF，达到了 1 亿美金的 ARR。GitHub，VSCode 都是微软旗下的，当时最强的代码大模型来自于 OpenAI 的 GPT-3.5，Codex，也与微软有着最紧密的合作。
    
*   针对不懂编程的普通人来说，ChatGPT, Claude 或者 Replit 等占据了最大的流量入口，而且大多数一次性的需求或者 demo 项目，使用这些产品基本也能够很好地完成了，也完全看不出把这个搬到 VSCode 里会有什么优势。
    

![Image 27](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKlWKhD9qZeFuSwu4CXuYrarUibxRZA1glpM7RVFOeoA2H8IZiaNEP1BlQ/640?wx_fmt=png&from=appmsg)

用 bolt.new 一句话生成网站

所以 Cursor 为什么有勇气拿着微软的 IDE 进行“魔改”，调用的也是跟微软合作最紧密的 OpenAI 的模型，来跟上面这些大玩家竞争呢？

经过我个人的体验，包括也看了Cursor 主创团队的访谈\[2\]，发现他们还是找准了几个非常犀利的点进行切入：

*   Cursor 的定位非常明确，还是**专业开发者**。所以他们不会与 ChatGPT，v0，bolt 等竞争，甚至两者背后的愿景可能也是很不一样的（程序员还会存在吗？）。如果一个用户区分不出两者的区别，那肯定不是他们的目标用户。
    
*   他们当时最独特的 insights 可能是：**写代码不仅仅是“补全”，而是“编辑”，也就是需要包含删除+补全**。这看起来是不是显而易见？但当时所有的 Coding Copilot 都只有单纯的补全。直到今天，Cursor Tab 的体验也是独一档的，当然 Windsurf 也已经开始模仿了。
    
*   这个对编辑的思考也进一步推广到在 chat 中生成代码后，再**通过 apply 的方式生成整个文件甚至多个文件的编辑 diff**。体验流程，也体现出他们对程序员 workflow 的深入理解。
    
*   大模型的智力从 GPT 的 3，3.5 到 4 在不断地提升，但是 GitHub Copilot 的体验好像并没有很大变化。所以**大公司的产品迭代缓慢**的问题是真实存在的，Cursor 团队感觉他们可以更快地探索一些有趣的想法，真正把模型能力的提升释放出来。
    

这背后的思考还是非常值得我们学习的，**明确定位、深入理解“工作流”、快速迭代**，使得如此小的一个团队也能撼动 GitHub Copilot 这样的庞然大物。

Cursor 工作流
----------

前面提到 Cursor 的定位是专业开发者，这里可以再明确一下它产生价值最大的场景以及和其他产品的区别：

*   **无论你是新手程序员还是资深开发者，Cursor 都会很有帮助**，这里要特别提醒资深开发者，不要因为对自己能力的自信而放弃尝试这种编程新范式。
    
*   对于专业开发者来说，一般**大多数的时间都是在维护已有的中大型项目**，而不是每天从零开始写新项目。所以网上很多“从零写个 App”的教程，其实一点都不典型，也没有体现出 Cursor 与 Claude Canvas 等产品的区别。
    
*   当前模型的能力还不足以在大型项目中直接通过几句指令就完成一整个 feature 的开发，因此如果你过于依赖 Chat 来做开发，可能成功率不会太高。更好的做法可能是**把 Cursor 当成一个结对编程中的“Copilot 程序员”**，而不是一个“实习生程序员”。
    

接下来我们就结合 Cursor 的功能来实际看下真实日常工作中是怎么使用它来提效的。

Cursor Tab
----------

这是 Cursor 目前最核心的优势功能，简单来说，就是它可以预测你下一个想要编辑的代码，并自动帮你完成。我们来看几个场景。

### 场景 1：把 print 改成 logger

一个阳光明媚的早晨，你跟你的结对编程伙伴一起修改一段代码。你可能会跟伙伴说，当时在做原型开发时，这个文件用了很多 print 语句，现在要正式上线了，我们应该把它们都改成 logger 输出。可能还要注意一下，不同的信息在输出时应该选择不同的 logging level。

这个需求，你当然可以在 Cursor 里通过"CMD + L"唤出 chat 窗口，然后把整句话打进去，等待 Cursor 生成整个文件的 diff。但这个意图同样也可以通过“写代码”的方式来隐性表达，比如你直接在文件里写：

```
import logginglogger = logging.getLogger(__name__)# 已有代码略。..
```

然后你只需要改动第一个 print 语句，你的编程伙伴 Cursor 就能懂得你的意思了。接下来只需要 tab tab tab，你会惊奇地发现 Cursor 能“猜到”你想修改的所有地方，并且还很智能地把不同的 logging level 设置正确。

请注意打出上面这段代码的时间，跟你用 chat 窗口打整个需求的时间相比，可能更短，而且省去了后面 apply+review+accept 的时间。所以很多时候我们都可以想一下，是不是某些意图的表达用写示例代码/简单注释的方法来说会更快。

### 场景 2：增加函数入参

这也是一个很常见的场景，与其用自然语言说我想给某个函数加个参数，这个参数是干嘛用的，需要同时把使用这个参数以及调用这个函数的地方进行修改等，有时候你直接编辑这个函数，把参数写上，Cursor 就会明白你的意图。以 Cursor 官网的一个例子来看：

![Image 28](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKdiaHkFVGPZxgOzHWBBd5Ypt3zvRicSEP6PhR8yhc4CYqLNCsLZIYEthA/640?wx_fmt=png&from=appmsg)

自动理解参数变更意图

你只要在`__init__`方法里加上`dropout`这个参数，Cursor 就会自动帮你把需要使用的地方也都补全上。如果文件里还有调用`LSTMModel`的地方，Cursor 也会根据情况做初始化时的修改。

许多这种无法直接用 IDE 完成的小重构，都可以用 Cursor Tab 很好地进行理解和快速完成。

### 与 GitHub Copilot 的区别

其实上面的**通过写代码来表达意图**的做法，很可能你在用其他补全类产品时也在不自觉使用了。比如有时候 Copilot 补全的不对，你可能会：

*   再多打几个字，把 Copilot 引导到正确的方向上来。
    
*   把之前的代码删掉一点，让 Copilot 忘掉后面的内容重新生成。
    
*   改变一下光标的位置，hey Copilot，从这里开始补全！
    

你会发现 Cursor Tab 其实就是把“删掉一点”和“改个光标位置”这两件事情也自动化了。所以上手体验会比 GitHub Copilot 等更加“智能”。

Inline Chat
-----------

在编辑中使用"CMD + K"就能在光标位置/选中代码上唤出 inline chat 浮窗，相比侧边栏 chat，主要提供了 2 个好处：

*   Inline chat 提供了光标位置在哪里的意图信息，且专注于“编辑”任务。
    
*   **浮窗可以同时打开多处做“并行”**，不用等前一个生成完成再做下一个。
    

个人比较喜欢用 inline chat 来做以下任务：

*   模板类代码生成，比如参考这个文件里的其他部分，写一个新的 API、DB 操作、数据模型等。这类 low entropy 的代码生成一般 Cursor 都能完成的很好，节省不少时间。
    
*   选中一段代码后让 Cursor 帮我加一些注释，看看是否有不清晰的地方。
    
*   选中某个函数/变量的名字，让 Cursor 帮我想个更好的名字。
    
*   **在 terminal 里也可以调用它**，让它帮忙写一些复杂的命令行指令，比如 docker，git 等一些复杂指令。所以是不是也不需要 Warp 了？
    

![Image 29](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKXKN4RDsNWMWT3cpZgxrGjv0Idza2yDyvnl6qDaJl4ME0YoQ9sZvpsg/640?wx_fmt=png&from=appmsg)

在 terminal 中生成指令

Chat
----

标准的侧边栏 chat，也是大家最熟悉的形态，很容易拿它来跟 ChatGPT/Claude 这类产品对比。作为一个专业 IDE，在开发已有项目时这里的区别还是比较明显的，尤其是在 context 的获取上。我们来看几个典型场景。

### 场景 1：重构/功能修改

比如我们需要跟编程伙伴一起做一个重构，在`model`层修改了一个模型，需要在调用这个模型的文件里做多处对应的修改，包括一些复杂的控制流判断等。如果使用 ChatGPT 来解决，你需要把模型的改动，当前的文件，加上指令本身，全部打进去，然后等待 ChatGPT 生成新代码，拷贝回来，再看看有没有改错的地方。这里就体现出了用原生 ChatGPT 的工作流的不顺畅之处：

*   Prompt 中的 context 需要人工查找整理，做多次复制粘贴。
    
*   生成代码后需要手工拷贝回来。
    
*   需要再通过 diff 工具来查看拷贝回来的代码有没有少改、多改、改错。
    
*   如果有问题，要复制错误信息，继续重复上面的过程。
    

而在 Cursor 里，你可以非常丝滑地解决以上痛点：

*   想告诉 Cursor 参考哪个文件，用`@`可以非常灵活制定文件夹、文件、某个代码定义等。
    
*   生成代码后，可以一键`apply`，Cursor 会直接应用到当前文件上，**生成一个“pull request”形式的 diff，供你 review**。
    
*   如果有问题，可以提 follow up question，继续迭代。当然这里跟其它 AI 工具一样，有时候要注意“session 污染”问题，可以考虑重开一个 session 把所有信息再描述一下。
    
*   Accept 改动之后，我们可能会发现 lint 错误或者自动化测试失败，你不需要再手动拷贝错误信息，可以直接使用**AI Fix in Chat** (for lint) 或者**Debug with AI** (for terminal)，虽然是个很小的功能，但这个体验提升真的很爽。
    

![Image 30](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKerUxW5opGgep8Yvn1hV3cXeOIOMfoIMkjvTLPPVWCZcFTKvQ9Pe0zg/640?wx_fmt=png&from=appmsg)

把错误自动发给 Cursor 进行修复

以上图为例，我在命令行中运行了`mypy`做代码检查，出现了两个错误。然后只需要点击那个**Debug with AI** 的小按钮，**错误就自动发送给了 Cursor Chat，生成了代码 diff**，接受之后就一切正常了。这个效率非常之高。

### 场景 2：单元测试生成

无论你是 TDD 流派，还是先写功能，再补测试，都可以跟 Cursor 来交流，让其帮助快速构建测试的模板代码（各种依赖、mock 等），并不断迭代覆盖更多的场景。

![Image 31](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKYicnpZZVX2LIXeXEn6iaibAEqMP3Uf0pQaqXqVjtKpncVpIhS4fDRKn5A/640?wx_fmt=png&from=appmsg)

生成单元测试

写完之后直接运行，如果有报错，可以结合上面的 Debug with AI 功能，让 Cursor 来帮忙快速修复。

### 场景 3：性能优化

这是来自官网的一个案例，看起来应该是在做一些 Rust 代码的优化工作。我们日常也可以通过 chat 让 Cursor 来帮忙快速 review 整个文件，并对例如性能、稳定性、安全等方面提出检查与优化需求。

![Image 32](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKHkXvFXbU3Usib4Nf3tHyYNB0HN3O7MdGBPQE8OGBmMuicV0licpDLNxsQ/640?wx_fmt=png&from=appmsg)

Rust 性能优化

### 场景 4：结合网络搜索

平时在 debug 一些问题和学习一些新框架时，我们也会经常使用devv\[3\]，phind\[4\] 这类代码领域的perplexity\[5\]。我们同样也可以用`@Web`指令来让 Cursor 去做一些网络搜索，**获取更加全面和 up to date 的知识信息，然后结合我们的代码库给出更具有针对性的解决方案**。比如我们可以尝试下让 Cursor 来帮我们从`poetry`迁移到`uv`：

![Image 33](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKiaCuJ2NvAluuyIUFib2jU6VC0LvibnxQ1jSIAcVgGHtUSmH9rCrHkZNjw/640?wx_fmt=png&from=appmsg)

结合网络搜索

可见这种传统的需要高频使用网络搜索的场景都可以尝试用 Cursor 解决，包括很多环境配置，依赖安装，疑难报错解决等等。

此外还有个类似的功能是`@Docs`，尤其适合**一些非常流行的 library 有不兼容的大版本变更情况**。比如 Pydantic 1.x 版本存在了很久，模型训练中可能已经对其形成了比较牢固的记忆了。但是项目中实际使用的是 Pydantic 2.x 版本，这时候将新版文档的网址引入进来，提供给模型参考就会非常有必要，能大大提升生成代码的准确性。

![Image 34](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyK5ZcLWBCnbWCFMlYjWspBfD1LV7bUdbxvTTd6o81IuoujRWOJiclK9PA/640?wx_fmt=png&from=appmsg)

有内置文档，也可以导入

### 场景 5：Code Review

这个在旧版本中是一个单独的 tab，但是新版本中好像升级成了“Bug Finder”，且需要按使用次数收费……不过没关系，我们仍然可以在 chat 中使用`@Git`来让 Cursor 帮助我们 review 代码，还是能发现一些潜在 bug 的。如果为了效果好，可能需要做一些 prompt 的优化。

![Image 35](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKH0oPic8HCpvBuRc4EqLcqjs4iaEc1zFX6Dic7JunNCDFde1Zr6epxEFAA/640?wx_fmt=png&from=appmsg)

AI Code Review

所以相比 inline chat，**在 chat 窗口中可以进行的任务种类更多样化**，不一定是代码编辑，也可以是纯聊天，主打一个情感陪伴。

### 其他的 Context 生成

可以看到在 chat 里通过`@`操作符可以非常自由地控制当前聊天的 context，跟与真人程序员交流非常相似。除了上面提到的之外，还可以：

*   `@Recommended`来自动推荐带入的 context。
    
*   `@Codebase`引入整个 codebase，比如阅读理解整个项目代码或者查找一些特定功能的实现。
    
*   `@Notepad`这个功能我比较少用，常见的用法是开一个 notepad，让 AI 来生成一些功能开发的计划，然后再在具体的代码文件里去引用参考这些计划。
    
*   `@Lint errors`自动修复 lsp 检测到的代码问题。
    

这种灵活控制 context 的能力，体现了 Cursor 团队对于程序员日常工作流程的深入理解，也明显与通用的 chatbot 拉开了差距。

另外像在 chat 里上传设计图让 Cursor 实现这种基本功能也都是具备的。只不过目前大模型结合图片的推理能力还是略微弱了些，这个功能实用性还不强。

Composer
--------

很多博主都推荐过这个功能，我理解其主要是**在 chat 单文件编辑的基础上，进一步拓展到了多文件的编辑与创建**。事实上在 0.43 版本之前，我用这个功能比较少，因为**当前模型能力在复杂项目中其实还挺难准确生成跨多个文件的编辑**的（有不同意见的同学欢迎提供案例指正）。

所以简单理解来说，**编辑复杂度从低到高的任务，可以基本对应到 tab -\> inline chat -\> chat -\> composer**，形成一个逐渐递进关系。

有意思的是，随着Windsurf\[6\] 的推出，大家发现可能是之前 composer 的 agent workflow 写得太简单了才导致效果不好？Windsurf 的 Cascade 虽然需要花上更多的时间“思考”，但是用同样模型能达到的效果还经常比 composer 更好。于是 Cursor 也很快在 0.43 版本中推出了 composer 的 agent 模式。

![Image 36](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyKTOH5MBzqaDbFCEu9PhScxdUibDvQ4V9AiaTqTelicpoKXSTpd7cyicdlyg/640?wx_fmt=png&from=appmsg)

使用 composer 来阅读开源代码

可以看到现在 Cursor 也会在过程中去**进行多步的 context 检索，阅读，执行命令 (terminal)，获取返回信息，判断下一步操作等**，终于有点 ReAct agent 的模样了。其实前面我们已经看到 Cursor 在各个环节都做了 AI 能力的嵌入，利用一个 agent 把这些能力串联起来，还是挺自然的一个演进。

之前也有一些演示将 composer 用于代码之外的领域，例如将个人知识库存在 Obsidian 这类本地 markdown 文件中，再用 composer 进行“AI 检索问答”。不过新版本里好像 composer 更加聚焦在了代码场景，我尝试了几次都没有触发文档检索。倒是 chat 里可以通过`@Codebase`来实现这个效果。

其它技巧
----

另外值得一提的是`cursorrules`这个文件，可以把它简单理解成针对当前项目的一个通用知识说明。比如可以包括：

*   当前项目使用技术栈的一些规定，比如特定框架版本等。
    
*   项目约定的代码规范，如命名、注释、错误处理、日志规范、性能与安全考量等。
    

你可以从cursor.directory\[7\] 中找到一些项目模板，根据自己的项目进行修改和使用。

AI 辅助编程思考
---------

从上面的介绍中，我们可以看出 Cursor 已经能够在我们的很多日常工作中帮助完成一些“低熵”的任务，例如：

*   各种编程语言、框架中的习惯性写法，即使是你不熟悉的框架，Cursor 也能帮你快速入门。
    
*   项目库本身的一些常见写法和表达，**如果你的项目架构越清晰，代码越易读，那么这部分的比例也会随之增大**。
    
*   运行代码，报错，搜索，尝试修复这类循环操作，也能借助 Cursor 来提效。
    

从“心流”理论来看，一方面通过自动补全和 chat，Cursor 很好地帮助我们完成了那些低难度的“无聊”打字工作；另一方面，大模型的丰富知识结合对代码库 context 的深入解析（借助 RAG），也能够很好地提升程序员的知识面，降低了未知技术和不熟悉代码带来的挑战和焦虑感。日常使用就像真的在与一位虚拟程序员伙伴持续结对编程，能持续保持专注度和创造力。

![Image 37](https://mmbiz.qpic.cn/mmbiz_png/mTa1FM1vx1Df2DOU899V1rjapXLPmhyK0et5GzibUgQFbSLBGjZCNNmGIU4PBFC7x02ncK5C4icerk4Aa9dylInQ/640?wx_fmt=png&from=appmsg)

Cursor 帮你进入心流

要在 AI 时代更好地利用这些工具来提升生产力，我们的精力会更多往**设计和验证**这两个环节倾斜。

*   Cursor 作为一个虚拟的编程伙伴，也跟人类一样需要能理解我们写的代码，才能更好地给出建议。所以**在 AI 时代，编写清晰易读代码的重要性进一步提高了**。
    
*   足够清晰的代码组织会让我们在使用`@`指令时更容易找到合适的 context，这在深入使用 Cursor 过程中会有比较深的体会。像好的命名，单一职责等原则都很有帮助。
    
*   **AI 与人类程序员也有显著的智力模式的区别**，如果你从事 LLM 相关应用的开发，可能会更加注意 AI 在阅读代码时的一些区别，比如在注释中写更多的案例和思考过程，避免复杂的“多跳检索”逻辑，时不时也可以问问 AI 是怎么理解这段代码的，或者让它尝试使用你的代码完成一些任务，以便针对其思考逻辑进行优化（跟优化 prompt 的一些技术差不多）。
    
*   由于 AI 生成代码的能力会越来越强，速度越来越快，如何**高效地 review 和验证这些内容会很快成为一个瓶颈**。一方面可能自动化测试会越来越重要，另一方面 Cursor 这类产品应该也会在 code review 上逐渐开始提供一些辅助手段。
    

当然这块个人的思考还不是很多，欢迎大家一起提供想法，交流探讨。

其它产品简评
------

这里我们也简单对比一下 AI 辅助编程的一些其它产品：

*   **OpenAI Canvas, Claude Artifacts** 更面向大众群体，主要还是针对“一次性”代码或者 MVP 构建。他们基本都不会像 Cursor 那样提供与已有代码库的 context 集成，以及复杂的 IDE 开发流程适配。
    
*   **GitHub Copilot，Codeium，Supermaven** 等 IDE 插件产品，在补全本身的体验上的确还有不小的差距。Cursor Tab 应该是一个专门训练的模型，不过技术壁垒可能不会很高，也不知道为啥 GitHub Copilot 一直没有跟进。Chat 方面也同理，之前看 GitHub Copilot 并没有灵活控制 context 的能力。
    
*   “Agent”类产品，如之前很火的**devin，replit，bolt，v0** 等。如果定位很通用的话，这块的产品目前很难达到一个好的效果。如果专注于某个领域，例如前端代码生成，可能会稍微好一些，但也基本局限于小 demo 生成。这里可能涉及到大家对于 AI 编程未来的设想，未来程序员职业会不会消失？
    
*   **Windsurf**，目前最大的问题还是自动补全差了不少，还有因为比较新，很多功能（比如 Python lsp）和稳定性上不如 Cursor。但价格便宜，值得关注。
    
*   Cursor 的开源平替，如aider\[8\]，cline\[9\] 等。总体来说优势在于可以 pay as you go，但是体验上还是不如 Cursor 整体打磨的那么细致。
    
*   **JetBrains AI**，其实相比 VSCode，在 Java 生态 JetBrains 应该还是有很多忠实用户的，光凭这一点就阻止了很多人转向 Cursor。不过 JetBrains AI 的市场评价看起来很糟糕，包括在 JetBrains 上装 GitHub Copilot 插件的功能也要弱不少……
    

总结来说，在 2024 年 12 月这个时间点，如果不折腾的话，用 Cursor 就挺好。如果从 JetBrains 迁移，问题也不大：

*   搜索一下特定语言的推荐插件安装一下，VSCode 对于前端，Python，Rust，Go 这类支持感觉都不错。
    
*   最好重新背一下快捷键，当然也可以安装 IntelliJ IDEA Keybindings 插件。
    
*   Double shift 全局搜索没了，需要结合着用 CMD + P, CMD + T, SHIFT + CMD + F……
    
*   Git 图形化操作好像也弱了些，不过基本够用。
    
*   可玩性可配置性很高，但也带来不少小细节问题，好坏各半吧。
    

更详细的介绍也可以上网搜一下这方面的迁移指南。

展望未来
----

从 Cursor 产品角度看，我们可以从 Agent 框架和程序员 workflow 两个角度来思考未来的提升方向。不过这篇文章也比较长了，这里也不做太多展开。有几个前面提到的点可以简单汇总一下：

*   如果把 Cursor 作为一个虚拟编程伙伴，那么**接入实时语音模态**应该会比较有意思，真的可以做到边描述代码就边生成出来了。
    
*   如何高效 review AI 生成的代码是一个重要方向，包括我们现在的 code review 的产品，其实也有很大改进空间，review 内容的组织非常的死板。
    
*   能否在代码架构设计的层面也提供一些帮助？第一步或许是让 Cursor 对于代码的理解形成一些“层次性”，而不是平铺的 context。
    

另外一个值得探讨的问题是，程序员这个职业群体会有什么变化吗？

*   Cursor 显然是想做一个专业程序员的“高级工具”的思路，看好程序员职业会长期存在，无法被 AI 完全替代。Cursor 的使用方式来说门槛还是比较高的，更多是根据当前程序员的工作方式来设计的。
    
*   而像 devin，magic.dev 等产品更像是走向通用 Coding Agent，可以全面替代程序员的思路。未来会不会是“人人都可以自己开发应用”，或者是“只要产品经理就够了”的场景？
    

去年试用 MidJourney，Suno 的时候，也有种感觉是不是未来人人都会是数字艺术家了？但很快我就发现，我自己其实并没有这方面的“创作冲动”，即使给我看一堆别人创作的东西，很多时候也描述不出来自己想要画什么。最后我的需求基本上收敛到了每次写文章的时候，才会想着去生成一幅封面图。而这个功能或许未来会直接集成在很多自媒体的平台中。

目前我对于程序员未来的想法也是类似的，代码创作可能相比画画、写作、音乐、视频等覆盖的人群更少，**普通人日常中可能很少会想着我要开发一个自己的 app**。而一些可能需要利用代码生成来达到个性化的垂直场景，或许会作为一种功能包括在其它垂直场景的产品中。

你的想法是什么呢？也欢迎留言交流。

### 参考资料

\[1\]一篇介绍 Cursor 的文章:_https://zhuanlan.zhihu.com/p/716192597_

\[2\]Cursor 主创团队的访谈:_https://www.youtube.com/watch?v=oFfVt3S51T4_

\[3\]devv:_https://devv.ai/_

\[4\]phind:_https://www.phind.com/_

\[5\]perplexity:_https://www.perplexity.ai/_

\[6\]Windsurf:_https://codeium.com/windsurf_

\[7\]cursor.directory:_https://cursor.directory/_

\[8\]aider:_https://aider.chat/_

\[9\]cline:_https://github.com/cline/cline_
