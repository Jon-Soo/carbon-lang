# Carbon 语言：<br/> C++ 的实验性继承者

<!--
Carbon 语言项目的一部分，在带有 LLVM 的 Apache License v2.0 下
例外。有关许可证信息，请参阅 /LICENSE。
SPDX-License-Identifier：带有 LLVM 异常的 Apache-2.0
-->

<p align=“center”>
  <a href="#why-build-carbon">为什么？</a> |
  <a href="#language-goals">目标</a> |
  <a href="#getting-started">开始使用</a> |
  <a href="#join-us">加入我们</a>
</p>

<a href="docs/images/snippets.md#quicksort">
<!--
在 docs/images/snippets.md 中编辑片段，然后：
https://drive.google.com/drive/folders/1-rsUjiya7dSZ87L8kpZmu3MZghRVxzLA
-->
<img src="docs/images/quicksort_snippet.svg" align="right" width="575"
     alt="Carbon 中的快速排序代码。点击链接阅读更多内容。">
</a>

<!--
不要让文本在上图的左侧绕得太窄。
`div` 减少了垂直高度。
GitHub 会自动链接 `img`，但在 `href="#"` 时不会生成链接。
-->
<div><a href="#"><img src="docs/images/bumper.png"></a></div>

**快速且可与 C++ 一起使用**

- 性能与使用 LLVM 的 C++ 匹配，具有对位的低级访问和
    地址
- 与您现有的 C++ 代码互操作，从继承到模板
- 可与您现有的 C++ 构建系统一起使用的快速且可扩展的构建

**现代且不断发展**

- 易于学习的扎实语言基础，特别是如果你有
    使用 C++
- Carbon 版本之间基于工具的简单升级
- 更安全的基础，以及通往内存安全子集的增量路径

**欢迎开源社区**

- 明确的目标和优先事项，以及强有力的治理
- 致力于欢迎、包容和友好的社区
- 包含电池的方法：编译器、库、文档、工具、包
    经理等

## 为什么要构建碳？

C++ 仍然是性能关键型软件的主要编程语言，
拥有庞大且不断增长的代码库和投资。然而，它正在努力
改进和满足上述开发人员的需求，这在很大程度上是由于
积累了数十年的技术债务。逐步改进 C++ 是
[极其困难]（/docs/project/difficulties_improving_cpp.md），两者都是由于
技术债务本身及其演变过程中的挑战。最好的
解决这些问题的方法是避免继承 C 或 C++ 的遗留问题
直接，而是从坚实的语言基础开始，例如
【现代泛型系统】（#generics），模块化代码组织，一致，
简单的语法。

现有的现代语言已经提供了出色的开发者体验：Go、
Swift、Kotlin、Rust 等等。 **_可以_使用其中一种的开发者
现有语言_应该_。**不幸的是，这些语言的设计
对 C++ 的采用和迁移提出了重大障碍。这些障碍
范围从软件惯用设计的变化到性能开销。

Carbon 从根本上说是**一种后续的语言方法**，而不是一种
尝试逐步发展 C++。它是围绕与互操作性而设计的
C++ 以及现有 C++ 代码库的大规模采用和迁移
开发商。 C++ 的后继语言需要：

- **性能匹配 C++**，这是我们开发人员的基本属性。
- **与 C++ 的无缝、双向互操作性**，例如库
    现有 C++ 堆栈中的任何地方都可以采用 Carbon，而无需移植其余部分。
- **一个温和的学习曲线**，对 C++ 开发人员具有合理的熟悉度。
- **可比的表现力**和支持现有软件的设计和
    建筑学。
- **可扩展的迁移**，具有一定程度的源到源翻译
    惯用的 C++ 代码。

通过这种方法，我们可以在 C++ 现有的生态系统之上构建，并带来
沿着现有的投资、代码库和开发人员群体。有一个
很少有语言在其他生态系统中遵循这种模式，而 Carbon
旨在填补 C++ 的类似角色：

- JavaScript → 打字稿
- Java → Kotlin
- C++ → **_Carbon_**

## 语言目标

我们正在设计 Carbon 以支持：

- 性能关键型软件
- 软件和语言演变
- 易于阅读、理解和编写的代码
- 实用的安全和测试机制
- 快速且可扩展的开发
- 现代操作系统平台、硬件架构和环境
- 与现有 C++ 代码的互操作性和迁移

虽然许多语言共享这些目标的子集，但 Carbon 的不同之处在于
他们的组合。

对于 Carbon，我们也有明确的_非目标_，特别是包括：

- 适用于整个语言和库的稳定 ABI
- 完美的向后或向前兼容性

我们详细的 [目标](/docs/project/goals.md) 文档充实了这些想法
并更深入地了解我们对 Carbon 项目和语言的目标。

##项目状态

Carbon目前是一个实验项目。我们想更好地理解
我们是否可以建立一种符合我们后继语言标准的语言，以及
由此产生的语言是否可以在
更大的 C++ 行业和社区。

目前，我们已经充实了 Carbon 项目的几个核心方面
和语言：

- Carbon 语言和项目的战略。
- 开源项目结构、治理模型和演进过程。
- 由我们提供的语言设计的关键和基础方面
    使用 C++ 的经验以及我们预期的最​​困难的挑战。这个
    包括以下设计：
    - 泛型
    - 班级类型
    - 继承
    - 运算符重载
    - 词汇和句法结构
    - 代码组织和模块化结构
- 一个原型解释器演示，既可以运行独立的示例，也可以提供
    具体语义模型和抽象机的详细分析
    碳。我们称之为 [Carbon Explorer](/explorer/)。

我们目前专注于获得更广泛的反馈和参与
C++ 社区，
[完成 0.1 语言设计](/docs/project/roadmap.md#completing-the-language-design),
和
[完成此设计的 Carbon Explorer 实现](/docs/project/roadmap.md#demo-implementation-of-core-features-with-working-examples)。
除此之外，我们计划优先考虑 C++ 互操作性和现实
实现 0.1 语言的工具链，可用于评估 Carbon
更多详情。

您可以查看我们的 [完整路线图](/docs/project/roadmap.md) 了解更多详细信息。

## 泛型

碳提供了一个
**[现代泛型系统](/docs/design/generics/overview.md#what-are-generics)**
已检查定义，同时仍**支持选择加入
[模板](/docs/design/templates.md) 用于无缝 C++ 互操作**。已检查
与 C++ 模板相比，泛型提供了几个优点：

- **通用定义经过全面类型检查**，无需
    实例化以检查错误并增强对代码的信心。
    - 避免重新检查每个定义的编译时间成本
        实例化。
    - 当使用定义检查的泛型时，使用错误消息是
        更清晰，直接显示不满足哪些要求。
- **启用自动、选择加入类型的擦除和动态调度**，无需
    分开实施。这可以减少二进制大小并启用构造
    像异构容器。
- **强大的、经过检查的接口**意味着更少的意外依赖
    实施细节和更清晰的消费者合同。

在不牺牲这些优势的情况下，**支持碳仿制药
专业化**，确保它可以完全解决性能关键的用例
C++ 模板。有关 Carbon 泛型的更多详细信息，请参阅他们的
[设计]（/docs/design/generics）。

除了与 C++ 简单而强大的互操作之外，Carbon 模板还可以
以细粒度约束和增量迁移到检查的泛型
并具有平稳的进化路径。

##内存安全

安全，尤其是
[内存安全](https://en.wikipedia.org/wiki/Memory_safety)，保持关键
C++ 面临的挑战以及后续语言需要解决的问题。我们的
最初的优先事项和重点是立即解决重要的、低调的问题
安全空间中的水果：

- 更好地跟踪未初始化的状态，加强执行
    初始化，并系统地提供针对
    需要时初始化错误。
- 设计基本 API 和习惯用法以支持动态边界检查
    调试和强化构建。
- 拥有既便宜又更多的默认调试构建模式
    比现有的 C++ 构建模式更全面，即使与
    [地址消毒剂](https://github.com/google/sanitizers/wiki/AddressSanitizer)。

一旦我们可以将代码迁移到 Carbon 中，我们将拥有一种简化的语言
在设计空间中添加任何必要的注释或功能，以及
像 [generics](#generics) 这样的基础设施来支持更安全的设计模式。
从长远来看，我们将在此基础上引入**一个安全的碳子集**。这个
将是一项庞大而复杂的任务，不会出现在 0.1 设计中。
同时，我们正在密切关注和学习增加内存安全的努力
语义到 C++ 上，例如 Rust-inspired
[生命周期注释]（https://discourse.llvm.org/t/rfc-lifetime-annotations-for-c/61377）。

＃＃ 入门

您可以通过查看代码库并使用
碳探索者：

```外壳
# 使用 Homebrew 安装 bazelisk。
$ brew install bazelisk

# 使用 Homebrew 安装 Clang/LLVM。
# 许多 Clang/LLVM 版本不是使用我们依赖的选项构建的。
$ brew install llvm
$ export PATH="$(brew --prefix llvm)/bin:${PATH}"

# 下载 Carbon 的代码。
$ git clone https://github.com/carbon-language/carbon-lang
$ cd碳朗

# 构建并运行资源管理器。
$ bazel run //explorer -- ./explorer/testdata/print/format_only.carbon
```

这些说明假设 [Homebrew](https://brew.sh/);看我们的
[贡献工具文档](/docs/project/contribution_tools.md) 了解更多
广泛的工具说明。

了解有关碳项目的更多信息：

- [项目目标](/docs/project/goals.md)
- [语言设计概述](/docs/design)
- [碳探索者](/explorer)
- [常见问题](/docs/project/faq.md)

＃＃ 加入我们

Carbon 致力于营造一个欢迎和包容的环境，让每个人都可以
贡献。

- 要观看主要发布公告，请订阅
    [我们在 GitHub 上发布的 Carbon 帖子](https://github.com/carbon-language/carbon-lang/discussions/1020)
    和 [star carbon-lang](https://github.com/carbon-language/carbon-lang)。
- 加入设计讨论，加入我们的
    [我们的 Github 论坛](https://github.com/carbon-language/carbon-lang/discussions)。
- 请参阅我们的 [行为准则](CODE_OF_CONDUCT.md) 和
    [贡献指南](CONTRIBUTING.md) 获取有关碳的信息
    发展社区。
- 我们在 [Discord](https://discord.gg/ZjVdShJDAs) 上讨论 Carbon。
