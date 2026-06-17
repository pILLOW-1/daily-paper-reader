---
title: "AutoZyme: An Autonomous Agentic Framework to Optimize Bioinformatics Software"
title_zh: AutoZyme：一个用于优化生物信息学软件的自主代理框架
authors: "Xie, E., Cheng, L., Cai, Y., Shireman, J., Kendziorski, C."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731250v1.full.pdf"
tags: ["query:self-improve"]
score: 9.0
evidence: 自主智能体框架迭代优化软件，实现自我改进
tldr: "针对基因组学和生物信息学软件性能瓶颈依赖人工优化难以扩展的问题，提出AutoZyme自主代理框架。该框架自动构建基准测试、识别瓶颈并迭代优化代码，在不显著增加内存的前提下改进运行时。在45个函数评估中，超过95%获得提升；对Seurat等38个函数，运行时中位数降低8.52倍，最大降低676倍。优化函数作为即插即用替代品分发，框架可复用于其他软件。"
source: biorxiv
selection_source: fresh_fetch
motivation: 生物信息学软件性能瓶颈随数据增长日益严重，人工优化耗时且难以扩展，需要自动化方法。
method: 提出AutoZyme框架，自动构建基准测试、定位瓶颈，迭代测试代码更改并保留提升运行时且保持输出的修改。
result: "在45个函数中超过95%性能提升，对Seurat等38个函数运行时中位数降低8.52倍，最大降低676倍，内存未显著增加。"
conclusion: AutoZyme高效自动化优化生物信息学软件，优化函数即插即用，框架可复用，显著加速分析流程。
---

## 摘要
在广泛使用的基因组学和生物信息学软件中，性能瓶颈随着生物数据集规模和数量的持续增长而带来日益沉重的负担。缓解这些瓶颈主要依赖于专家手动优化，因此难以规模化。在此，我们提出AutoZyme，一个用于科学软件优化的代理框架。给定一个目标函数，AutoZyme构建基准测试、识别瓶颈并迭代测试代码更改，只保留那些能提高运行时间且保持输出不变的更改。我们在45个函数上评估了AutoZyme，在超过95%的情况下，运行时间得以改善，而内存没有显著增加。对于来自Seurat、Scanpy及基因组学和生物信息学相关包的38个函数，AutoZyme将运行时间中位数减少了8.52倍，最大的减少超过676倍。优化后的函数通过AutoZyme-Library分发，作为现有分析管道的直接替代品。我们还发布了AutoZyme作为一个可重用的框架，用于优化用户指定的其他包和函数。

## Abstract
Performance bottlenecks in widely used genomics and bioinformatics software present a substantial and growing burden as biological datasets continue to increase in size and number. Relieving these bottlenecks relies largely on expert manual optimization and therefore remains difficult to scale. Here we present AutoZyme, an agentic framework for scientific software optimization. Given a target function, AutoZyme builds benchmarks, identifies bottlenecks, and iteratively tests code changes, retaining only those that improve runtime while preserving output. We evaluated AutoZyme on 45 functions, improving runtime without substantial memory increases in over 95% of cases considered. Across 38 functions from Seurat, Scanpy and related packages in genomics and bioinformatics, AutoZyme reduced runtime by a median of 8.52-fold, with the largest reductions exceeding 676-fold. The optimized functions are distributed through AutoZyme-Library as drop-in replacements for existing analysis pipelines. We also release AutoZyme as a reusable framework for optimizing additional user-specified packages and functions.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：随着生物数据集规模和数量持续增长，广泛使用的基因组学和生物信息学软件（如 Seurat、Scanpy 等）中的性能瓶颈日益严重。手工优化依赖于专家经验，难以规模化，无法跟上数据增长的步伐。
- **研究动机**：开发一种自动化、可扩展的软件优化方法，以显著降低运行时间，而无需人工介入。
- **整体含义**：提出的 AutoZyme 框架能够自主识别瓶颈、迭代改进代码，并将优化函数作为即插即用组件分发，有望加速整个生物信息学分析流程，降低计算成本。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：构建一个自主代理框架，给定目标函数后，自动完成基准测试构建、瓶颈识别、代码修改迭代，只保留那些能提升运行时间且保持输出不变的修改。
- **关键技术细节**：
  - **基准测试构建**：自动生成测试用例以评估函数性能。
  - **瓶颈识别**：使用性能分析工具（如 profiler）定位耗时部分。
  - **迭代测试**：由智能体（agent）生成代码更改，通过运行基准测试验证效果，保留有效的改进。
  - **输出保真度检查**：确保优化后的函数输出与原始一致。
- **算法流程**（文字说明）：
  1. 用户指定目标函数以及依赖包。
  2. AutoZyme 构建性能基准测试（包含多种输入规模）。
  3. 识别当前函数的性能瓶颈（热点代码段）。
  4. 智能体（基于大型语言模型或程序合成）提出代码修改。
  5. 运行基准测试比较运行时间及输出——仅接受同时满足“运行时间减少”和“输出一致”的修改。
  6. 重复步骤 3-5 直至收敛或达到预设迭代次数。
  7. 输出优化后的函数，并通过 AutoZyme-Library 分发。

## 3. 实验设计：数据集/场景、benchmark、对比方法
- **数据集/场景**：
  - 从 **Seurat**、**Scanpy** 以及基因组学和生物信息学相关包中选取了 **38 个函数**。
  - 另外还评估了来自其他领域的 **45 个函数**（总计 45 个评估实例，但 38 个来自特定包，其他可能来自更广泛的生物信息学包）。
- **Benchmark**：使用自动构建的性能基准测试（包含典型输入数据与规模）。
- **对比方法**：论文未明确列出与其他自动化优化工具的对比。主要对比的是优化前后的函数运行时间和内存消耗，即自身前后对照。未提及对比其他自动化优化框架（如基于 LLM 的代码优化工具）。实验设计偏向于展示 AutoZyme 自身的能力，而非直接比较。

## 4. 资源与算力
- **未明确说明**：论文摘要和元数据中没有提及使用的 GPU 型号、数量、训练时长或推理算力。仅提到 AutoZyme 作为“代理框架”运行，可能依赖大语言模型（LLM）进行代码修改，但未给出 LLM 的具体配置或计算资源。因此无法量化资源消耗。

## 5. 实验数量与充分性
- **实验数量**：
  - 主要实验：在 **45 个函数**上评估，其中 **38 个函数**来自 Seurat、Scanpy 等包（报告了中位数降低 8.52 倍，最大降低 676 倍）。
  - 成功比例：超过 **95%** 的函数获得了运行时间改善且内存未显著增加。
- **充分性评价**：
  - **优点**：覆盖了多个流行生物信息学包，涉及不同复杂度的函数；结果统计指标（中位数、最值）较为清晰。
  - **不足**：
    - 未对每个函数进行多次重复实验以评估结果的稳定性。
    - 未提及消融实验（如不同代码生成策略、不同 LLM 的影响）。
    - 未与现有的自动化优化方法（如基于模板的优化、其他 LLM 驱动的工具）进行横向对比，难以判断其相对优势。
    - 实验数据集规模/多样性信息缺失（如函数输入数据的具体大小、类型）。
    - 未报告优化失败的具体案例及原因分析。

## 6. 论文的主要结论与发现
- AutoZyme 能大幅提升生物信息学软件性能：在 45 个函数中，**超过 95%** 的函数运行时间得到改善，内存无显著增加。
- 针对 38 个来自 Seurat、Scanpy 等包的函数，运行时间**中位数降低 8.52 倍**，最大降低 **超过 676 倍**。
- 优化后的函数通过 **AutoZyme-Library** 分发，可作为现有分析管道的直接替代（即插即用）。
- AutoZyme 作为一个可重用的框架，能够为用户指定的其他包和函数提供自动优化能力。

## 7. 优点：方法或实验设计上的亮点
- **自动化程度高**：无需人工干预，自动完成基准测试、瓶颈识别、代码修改和验证，解决了手工优化难以规模化的痛点。
- **保持输出正确性**：在优化过程中强制要求输出一致，避免因性能提升而牺牲功能正确性，这是科学软件优化的关键。
- **即插即用分发**：通过 AutoZyme-Library 提供优化函数，用户只需替换函数名即可加速现有分析流程，使用成本低。
- **通用框架设计**：不仅限用于给定包，还可扩展到用户指定的其他包和函数，具有良好的可复用性。
- **结果显著**：在多个流行包上取得了惊人的加速比（最大 676 倍），显示出实用价值。

## 8. 不足与局限
- **缺乏与同类方法对比**：没有与现有的自动化代码优化工具（如基于搜索的优化、其他 LLM 驱动方法）进行基准比较，无法证明 AutoZyme 的优越性。
- **实验覆盖范围有限**：尽管涉及 45 个函数，但这些函数是否具有代表性？未列出具体函数名称或功能类型，难以判断是否涵盖主要瓶颈模式。
- **未报告失败案例与局限性**：超过 95% 的成功率意味着存在约 5% 的失败，但未分析失败原因、失败函数的特征（如复杂度高、依赖外部库等）。
- **资源消耗分析缺失**：AutoZyme 本身运行需要多少计算资源（时间、成本）？与手工优化的专家时间成本相比是否有优势？论文未提及。
- **代码生成依赖的 LLM 信息不透明**：未说明使用了哪种语言模型、模型规模、采样策略等，降低了可复现性。
- **对内存影响的评估可能不足**：仅说明“内存没有显著增加”，但未给出具体数据或统计测试。
- **应用限制**：优化可能只适用于可重入、无副作用的函数；对于大规模并行或多线程复杂软件，框架的有效性未知。

（完）
