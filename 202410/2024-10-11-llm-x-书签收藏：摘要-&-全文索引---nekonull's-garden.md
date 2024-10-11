# LLM x 书签收藏：摘要 & 全文索引 - Nekonull's Garden
- URL: https://nekonull.me/posts/llm_x_bookmark/
- Added At: 2024-10-11 07:25:01
- [Link To Text](2024-10-11-llm-x-书签收藏：摘要-&-全文索引---nekonull's-garden_raw.md)

## TL;DR
作者使用osmos::memo插件将书签记录到Github存储库，并建立bookmark-summary存储库生成全文、摘要和总结，通过Github Actions自动化流程，解决URL失效和查找困难问题，未来计划优化摘要质量、数据结构化和代码重构等。

## Summary
1. **背景**：
   - **书签收藏动机**：作者在网上冲浪时经常遇到有趣的文章或网站，希望收藏以备后用。
   - **工具选择**：自2021年5月起，作者使用名为[osmos::memo](https://github.com/osmoscraft/osmosmemo)的书签插件，将收藏记录到公开的[Github存储库](https://github.com/jerrylususu/bookmark-collection)。
   - **工作流程**：插件设置Github token，每次点击收藏按钮时，浏览器临时clone存储库，追加新条目，生成commit并提交，然后推送回Github。

2. **问题**：
   - **URL失效**：书签指向的URL可能不再存在，成为死链接。
   - **查找困难**：记录项仅包含URL、标题和可选标签，查找时若关键词记忆不清，难以找到。
   - **内容遗忘**：长文章时间久了可能忘记内容，临时查找和引用效率低。

3. **解决**：
   - **新存储库**：建立[bookmark-summary](https://github.com/jerrylususu/bookmark-summary)作为辅助数据，包含Markdown格式全文、列表摘要、一句话总结。
   - **工作原理**：
     1. 通过书签插件新增条目到现有书签存储库。
     2. 代码提交触发Github Actions（`summarize`）。
     3. Actions执行：
        - 解析书签README.md，找到新增条目。
        - 保存URL到Wayback Machine。
        - 使用[jina reader](https://jina.ai/reader/) API获取全文并保存。
        - 使用LLM生成列表摘要和一句话总结。
        - 保存摘要到摘要存储库，更新README.md。
     4. Actions提交变更到摘要存储库。

4. **未来优化**：
   - **摘要质量**：优化prompt或换用其他模型。
   - **数据结构化**：考虑在Markdown外维护JSON。
   - **代码重构**：重构Python文件，改进存储库交互方式。
   - **向量搜索**：接入embedding模型，生成嵌入并存储。
   - **自动周报**：自动生成每周摘要，放在Github Release。
   - **工具链更新**：考虑使用更现代的工具链。

5. **部署指南**：
   - **初始化书签存储库**：参考[osmos::memo](https://github.com/osmoscraft/osmosmemo)指引。
   - **新建摘要存储库**：添加[process_changes.py](https://github.com/jerrylususu/bookmark-summary/blob/main/process_changes.py)并调整参数。
   - **配置Github Actions**：添加[bookmark_summary.yml](https://github.com/jerrylususu/bookmark-collection/blob/main/.github/workflows/bookmark_summary.yml)。
   - **生成PAT**：创建Personal Access Token并添加到环境变量。
   - **测试**：添加书签，观察工作流是否正常运行。
