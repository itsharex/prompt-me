<h1 align="center">
    promptulate
</h1>


<p align="center">
    <a target="_blank" href="">
        <img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg?label=license" />
    </a>
    <a target="_blank" href=''>
        <img src="https://img.shields.io/github/release/Undertone0809/promptulate/all.svg?style=flat-square"/>
    </a>
    <a target="_blank" href=''>
        <img src="https://bestpractices.coreinfrastructure.org/projects/3018/badge"/>
   </a>
    <a target="_blank" href=''>
        <img src="https://static.pepy.tech/personalized-badge/cushy-storage?period=month&units=international_system&left_color=grey&right_color=blue&left_text=Downloads/Week"/>
   </a>
</p>


<p align="center">
  <img src="https://zeeland-bucket.oss-cn-beijing.aliyuncs.com/images/promptulate_logo_new.png"/>
</p>



`promptulate` 是一个专为Prompt工程师设计的大语言模型自动化与应用开发框架，支持智能决策、消息持久化、外部工具调用、角色预设等功能，开箱即用。
通过 `promptulate`，你可以轻松构建起属于自己的LLM应用程序。

`promptulate`旨在构建为开发者提供一种强大而灵活的平台，以创建能够自动化各种任务和应用程序的自主代理。通过Core
AI Engine、Agent System、APIs and Tools Provider、Multimodal Processing、Knowledge Base和Task-specific Modules
6个组件实现自动化AI平台。 Core AI Engine是该框架的核心组件，负责处理和理解各种输入，生成输出和作出决策。Agent
System是提供高级指导和控制AI代理行为的模块；APIs and Tools Provider提供工具和服务交互的API和集成库；Multimodal
Processing是一组处理和理解不同数据类型（如文本、图像、音频和视频）的模块，使用深度学习模型从不同数据模式中提取有意义的信息；Knowledge
Base是一个存储和组织世界信息的大型结构化知识库，使AI代理能够访问和推理大量的知识；Task-specific
Modules是一组专门设计用于执行特定任务的模块，例如情感分析、机器翻译或目标检测等。通过这些组件的组合，框架提供了一个全面、灵活和强大的平台，能够实现各种复杂任务和应用程序的自动化。

# 特性

- 大语言模型支持：支持不同类型的大语言模型的扩展接口
- 对话终端：提供简易对话终端，直接体验与大语言模型的对话
- 角色预设：提供预设角色，以不同的角度调用GPT
- 长对话模式：支持长对话聊天，支持多种方式的对话持久化
- 外部工具：集成外部工具能力，可以进行网络搜索、执行Python代码等强大的功能
- KEY池：提供API key池，彻底解决key限速的问题
- 智能代理：集成ReAct，self-ask等高级Agent，结合外部工具赋能LLM
- 自治代理模式：支持调用API官方接口、自治代理或使用promptulate提供的代理
- 中文优化：针对中文语境进行特别优化，更适合中文场景
- 数据导出：支持markdowm等格式的对话导出
- 对话总结：提供API式的对话总结、翻译、标题生成
- 高级抽象，支持插件扩展、存储扩展、大语言模型扩展

# 快速开始

- [快速上手](get_started/quick_start.md#快速开始)
- [当前开发计划](other/plan.md#开发计划)
- [参与贡献/开发者手册](other/contribution.md#contribution)
- [常见问题](other/fqa.md#fqa)
- [pypi仓库](https://pypi.org/project/promptulate/)

# 基础架构

在本人深度阅读`langchain, Auto-GPT, django, django-rest-framework, gpt_academic...`
等项目的源码，参与pr之后，学习它们的架构、代码设计思路等内容，重构了两次，有了现在的版本，相较于之前的老版本`prompt-me`，`promptulate`
重新构建了 `llms, message, memory, framework, preset_roles, tools, provider`等模块，将`prompt`
的各个流程全部组件化，便有了现在的`promptualte`框架。当前`promptualte`仍有很多细节需要完善，也十分欢迎大家的讨论与参与。

`promptualte`作为一个为大语言模型设计的Prompt Layer框架，主要由以下几部分组成：

- `Agent` 更高级的执行器，负责复杂任务的调度和分发
- `framework` 框架层，实现不同类型的prompt框架，包括最基础的`Conversation`模型，还有`self-ask`和`ReAct`等模型。
- `llm` 大语言模型，负责生成回答，可以支持不同类型的大语言模型
- `memory` 负责对话的存储，支持不同的存储方式及其扩展，如文件存储、数据库存储等
- `tools` 提供外部工具扩展调用，如搜索引擎、计算器等
- `preset roles` 提供预设角色，进行定制化对话
- `provider` 为framework和agent提供tools和其他细粒度能力的集成

<img src="https://zeeland-bucket.oss-cn-beijing.aliyuncs.com/images/20230704180202.png"/>

# 设计原则

`promptulate`框架的设计原则包括：模块化、可扩展性、互操作性、鲁棒性、可维护性、安全性、效率和可用性。

- 模块化是指以模块为基本单位，允许方便地集成新的组件、模型和工具。
- 可扩展性是指框架能够处理大量数据、复杂任务和高并发的能力。
- 互操作性是指该框架与各种外部系统、工具和服务兼容，并且能够实现无缝集成和通信。
- 鲁棒性是指框架具备强大的错误处理、容错和恢复机制，以确保在各种条件下可靠地运行。
- 安全性是指框架采用了严格的安全措施，以保护框架、其数据和用户免受未经授权访问和恶意行为的侵害。
- 效率是指优化框架的性能、资源使用和响应时间，以确保流畅和敏锐的用户体验。
- 可用性是指该框架采用用户友好的界面和清晰的文档，使其易于使用和理解。

以上原则的遵循，以及最新的人工智能技术的应用，`promptulate`旨在为创建自动化代理提供强大而灵活的大语言模型应用开发框架。

# 交流群

欢迎加入群聊一起交流讨论有关LLM相关的话题，链接过期了可以issue或email提醒一下作者。

<div style="width: 250px;margin: 0 auto;">
  <img src="https://zeeland-bucket.oss-cn-beijing.aliyuncs.com/images/20230702132948.png"/>
</div>

# 贡献

本人正在尝试一些更加完善的抽象模式，以更好地兼容该框架，以及外部工具的扩展使用，如果你有更好的建议，欢迎一起讨论交流。
如果你想为这个项目做贡献，请先查看[当前开发计划](other/plan.md#开发计划)
和[参与贡献/开发者手册](other/contribution.md#contribution)。我很高兴看到更多的人参与并优化它。