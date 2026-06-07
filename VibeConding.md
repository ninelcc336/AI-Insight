个人简易Vibe流程，每一阶段成果沉淀为文档，下一阶段可以开新窗口执行
详细可使用 Superpowers / get-shit-done

### 确定需求
目标：阐述目标，并要求大模型来完成需求文档

输入：介绍当前目录，什么技术栈、有什么资料

输出：请在 doc 目录下生成需求文档

步骤(brainstorming)：使用提问的方式帮助我确认需求，不要猜测我的意图，不明确的地方必须提问。


### 设计
概要设计 -> 划分模块
详细设计 -> 实现细节
模型如果足够强大，上一步的需求文档会含盖部分设计

目标：根据上一步的需求文档生成概要设计文档

输入：需求文档的内容

输出：输出为 doc/xxxxxx.md

步骤：
根据需求文档的内容，划分出模块，识别模块与模块之间的关系生成概要设计文档。
模块之间尽量保持相互独立，可以独立进行测试。
不要猜测我的意图，任何不明确的地方必须提问。

### 划分任务
目标：为每个模块划分最小可执行任务

输入：
需求文档 doc/xxxx.md
详细设计 doc/xxxxxxx.md

输出：
任务列表
- doc/tasks/<module-name>.md （每个模块对应一个）
- doc/tasks/progress.md （总体进度）

步骤：
根据需求文档和详细设计。
为每一个模块生成Vibe Coding用的最小任务。
每个模块对应一个<module-name>.md
用check list表示子任务是否完成。
progress.md中，用check list表示模块是否已经完成


### 实现
根据任务列表写程序

目标：
生成Vibe Coding用的Prompt

输入：
需求文档 doc/xxxxx.md
详细设计 doc/xxxxxxx.md
任务划分 doc/tasks

输出：
doc/prompt.md

步骤：
阅读输入信息，了解当前要实现的工程
生成 doc/prompt.md 作为Vibe Coding的起始Prompt

主Agent，用来跟踪整体的进度
主Agent生成子Agent，用来实现每一个模块，并完成测试
整个过程不会有人工参与

代码必须有完整的单元测试，并且通过

生成prompt的过程中，如果有任何不明确的地方都必须想我提问。

