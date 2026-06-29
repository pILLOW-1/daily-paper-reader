---
title: "CellOS: Learning a World Model of Cellular State through Joint Embedding Prediction"
title_zh: CellOS：通过联合嵌入预测学习细胞状态的世界模型
authors: "Zhou, Q., Le, Y., Qi, X., Chang, S., Lu, H., Wu, Y., Wang, H., Ran, R., li, x."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733163v2.full.pdf"
tags: ["query:agent-detect"]
score: 9.0
evidence: 通过学习带有感知视图的细胞状态世界模型
tldr: 现有单细胞基础模型仅从单一表达视图学习，无法整合互补信息。CellOS提出多视图框架，通过三阶段训练（因果语言建模、密集到MoE扩展、LLM-JEPA对齐）学习联合表征。在3.9亿个单细胞转录组上训练120亿参数模型，在细胞状态注释、批次整合和扰动响应预测任务上超越最先进方法。该工作为构建表征中心的细胞世界模型和可迁移AI虚拟细胞提供了可扩展方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞基础模型仅使用单一基因表达视图，无法显式协调补充的细胞状态视图。
method: CellOS采用三阶段训练：因果细胞句子语言建模、保留功能的密集到混合专家扩展、LLM-JEPA目标潜空间对齐。
result: 120亿参数模型在3.9亿单细胞转录组上训练，在细胞注释、批次整合、扰动预测等基准上全面超越现有模型。
conclusion: 通过互补视图的预测对齐，CellOS提供了构建可迁移AI虚拟细胞和细胞世界模型的可扩展路径。
---

## 摘要
基于单细胞转录组学习的基础模型对于能够表示、查询和预测细胞状态的AI虚拟细胞的前景至关重要。然而，目前大多数单细胞基础模型从单一基因表达视图学习，主要通过重建或下一个标记预测进行优化。因此，它们捕获了表达丰度，但无法明确协调细胞状态的互补视图。在这里，我们提出CellOS，一个多视图基础模型，从配对表达和感知视图学习细胞表示。CellOS通过一个可扩展的三阶段训练策略整合互补视图，该策略结合了因果细胞句子语言建模、保函数密转混合专家扩展以及通过LLM-JEPA目标进行潜在空间对齐。利用此框架，我们在3.905亿个单细胞转录组上训练了一个120亿参数模型。在涵盖细胞状态注释、批次整合和扰动响应预测的多个基准测试中，CellOS始终优于最先进的单细胞基础模型。总之，这些结果表明，互补细胞视图之间的预测对齐为以表征为中心的细胞世界模型和可迁移的AI虚拟细胞提供了一条可扩展的路径。

## Abstract
Foundation models learned from single-cell transcriptomes are central to the prospect of AI virtual cell that can represent, query and predict cellular state. However, most current single-cell foundation models learn from a single view of gene expression and are optimized primarily through reconstruction or next-token prediction. As a result, they capture expression abundance but cannot explicitly reconcile complementary views of cellular state. Here we present CellOS, a multi-view foundation model that learns cellular representations from paired expression and perception views. CellOS integrates complementary views through a scalable three-stage training strategy that combines causal cell-sentence language modelling, function-preserving dense-to-mixture-of-experts expansion and latent-space alignment via an LLM-JEPA objective. Using this framework, we trained a 12-billion-parameter model on 390.5 million single-cell transcriptomes. Across diverse benchmarks spanning cell-state annotation, batch integration and perturbation-response prediction, CellOS consistently outperformed state-of-the-art single-cell foundation models. Together, these results suggest that predictive alignment between complementary cellular views provides a scalable path toward representation-centric cellular world models and transferable AI virtual cells.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

当前的单细胞基础模型（如 Geneformer、scGPT、TranscriptFormer）大多从**单一的表达视图**学习，即仅基于基因表达丰度排序的“细胞句子”（cell sentence），并通过重建或下一个标记预测目标进行优化。这种设计存在两个根本局限：一是高表达的管家基因可能携带较少的状态特异性信息，而中等表达但处于群体分布尾部的基因（如转录因子、应激响应基因）可能更具诊断价值——但现有模型无法显式区分“丰度”与“信息含量”；二是输入空间的目标迫使模型将容量花费在低层重建上，而非学习鲁棒的细胞级表示。

CellOS 的动机是：**构建一个能够显式整合细胞状态互补视图的世界模型**。它提出让模型同时学习两种视图——表达视图（表达丰度排序）和感知视图（基于群体相对惊奇度排序），并通过联合嵌入预测（JEPA）在潜在空间中对齐它们。这样既能保留生成式的细胞句子建模，又能迫使模型捕获跨视图共享的语义结构，从而得到更通用、更可迁移的细胞表示。

---

### 方法论：核心思想、关键技术细节与算法流程

#### 核心思想
将每个单细胞转录组表示为**两个互补的基因序列**：
- **表达视图（Expression view）**：按归一化表达丰度降序排列的基因句子，捕获“细胞表达了什么”。
- **感知视图（Perception view）**：按**群体相对惊奇度**降序排列的基因句子，捕获“哪些基因的表达值在群体分布中最出乎意料”。

通过 LLM-JEPA 目标在潜在空间中对齐这两个视图，同时保留因果语言建模损失，使模型兼顾生成能力与表征抽象性。

#### 关键技术细节

1. **数据预处理与基因词汇构建**  
   - 原始计数矩阵经基因符号统一、库大小归一化（\( e_{cg} = 10^4 \cdot x_{cg} / \sum_g x_{cg} \)）。  
   - 对每个基因，从训练语料中计算非零归一化表达的经验分位数。

2. **感知视图的构造**  
   - 信息得分：\( I_{cg} = -\log(1 - q_g(e_{cg}) + \epsilon) \)，其中 \( q_g \) 是基因 g 的经验分位数函数。该得分衡量表达值处于群体分布上尾的“稀有度”。  
   - 按 \( I_{cg} \) 降序排列所有检测到的基因，得到感知句子。

3. **三阶段训练策略**
   - **Stage 1（密集因果语言建模）**：仅在表达视图上训练一个密集 Transformer（24层解码器），学习细胞表达语法。
   - **Stage 2（保留函数的密集到MoE扩展）**：将密集的前馈层转换为 MoE 层（1个共享专家 + 32个路由专家，top-1 路由）。共享专家由密集权重初始化，路由专家近零初始化，以保证初始行为接近原密集模型。继续预训练，加入 MoE 辅助损失。
   - **Stage 3（LLM-JEPA 对齐）**：引入感知视图，对每个细胞同时输入表达句子和感知句子。共享编码器分别获取两个视图的细胞表示（来自特殊表示 token 的最终隐藏状态）。一个预测器网络 \( q_\phi \) 将表达视图表示映射到感知视图表示空间。对齐损失为余弦距离：\( L_{\text{JEPA}} = 1 - \cos(\hat{z}_c^{\text{perc}}, z_c^{\text{perc}}) \)。

4. **总目标**  
   \[
   L = \lambda_{\text{LM}} L_{\text{LM}} + \lambda_{\text{JEPA}} L_{\text{JEPA}} + \lambda_{\text{MoE}} L_{\text{aux}}
   \]
   三阶段中权重逐步引入。

---

### 实验设计：数据集、基准与对比方法

#### 数据集
- **细胞状态注释基准**（6个数据集）：
  - PBMC 免疫衰老（13种细胞类型）
  - iPSC 细胞类型分化（25种状态）
  - iPSC 分化时间序列（day0–day3）
  - T 细胞亚群（16个精细亚型）
  - 人肺（16种细胞类型）
  - IFN-β 刺激的 PBMC（13个聚类）
- **批次整合基准**（2个数据集）：
  - 人肺（107个文库）
  - 嗅周皮层（2个样本）
- **扰动响应预测基准**：利用 STATE 框架，在5个 held-out 细胞环境（H1、HepG2、Jurkat、K562、RPE1）中评估嵌入质量，下游模型固定，仅替换嵌入。

#### 对比方法
UCE、State、scGPT、TranscriptFormer、STACK、C2S-2B（C2S-Scale 的 2B 变体）。

#### 评估指标
- 注释：调整兰德指数 (ARI)、归一化互信息 (NMI)、平均轮廓宽度 (ASW)。对每个指标进行数据集内归一化后平均，得到生物保守得分 (BioConserv)。
- 批次整合：轮廓批次得分 (sil_batch)、图连通性 (GC)、集成局部逆辛普森指数 (iLISI)，平均得到批次效应得分。

---

### 资源与算力

论文明确提到：CellOS 在 **3.905 亿个单细胞转录组**上训练，模型参数量为 **120 亿（12B）**。但**未详细说明使用的 GPU 型号、数量或训练时长**。文中仅提及使用“token-balanced data engine”在分布式训练中按估计的 token 负载分区。因此，具体算力开销无法从本文中获取。

---

### 实验数量与充分性

- 共覆盖 **8 个独特的数据集**（6 个注释 + 2 个批次），加上 **5 个 held-out 扰动环境**。
- 注释基准上对比了 6 种 SOTA 基础模型，批次整合对比了同样 6 种，扰动预测对比了 7 种（包括自身）。
- 进行了**消融实验**：在 T 细胞亚群上对比 0.2B 单视图、2B 单视图、12B MoE+JEPA 三个 checkpoint，验证了规模和 JEPA 对齐的贡献。
- 设计公平：扰动预测中下游模型和训练程序固定，仅更换原始嵌入；指标全面（ARI、NMI、ASW、各扰动指标）。
- 结论：实验数量充分，对比全面，消融设计合理，评估客观公平。

---

### 论文的主要结论与发现

1. **CellOS 在注释基准上全面领先**：归一化 ARI 0.751、NMI 0.797、ASW 0.828，生物保守得分 0.792，远超所有对比模型。
2. **批次整合中取得有利权衡**：图连通性最高（0.964），批次效应得分 0.771（仅次于 STACK 0.801，但 STACK 的生物保守得分仅 0.474，远低于 CellOS 的 0.792），说明 CellOS 在去除批次的同时保留了生物结构。
3. **扰动预测性能显著提升**：在 DE Spearman 相关系数（0.590）、Pearson edist（0.619）、聚类一致性（0.633）、DE 方向匹配（0.623）上均最优，表明 CellOS 表征捕获了状态变化信息，而不仅仅是静态细胞身份。
4. **规模与多视图对齐均有益**：消融显示从 0.2B 到 2B 提升明显（ARI +0.102），加入 JEPA 后进一步改善（+0.042），说明参数规模和对齐目标贡献互补。

---

### 优点：方法或实验设计上的亮点

- **提出感知视图**：将群体相对惊奇度作为独立视图，赋予模型显式的信息含量信号，而非隐式嵌入在单排名中。
- **首次将 JEPA 应用于单细胞转录组学**：在潜在空间中对齐多视图，避免了输入空间重建的局限，推动从“重建中心”向“表征中心”转变。
- **三阶段可扩展训练策略**：先用小规模密集模型学习语法，再通过函数保留扩展至 MoE，最后引入对齐目标，保证了训练稳定性和容量增长。
- **公平的扰动预测评估**：固定下游模型，仅变化嵌入，排除了架构差异的混淆。
- **大规模验证**：在 3.9 亿细胞、12B 参数尺度上证明了方法的可扩展性。

---

### 不足与局限

1. **感知视图的群体统计是全局的**：基于整个预训练语料估计，未考虑组织或谱系特异性背景，可能在某些条件下不够精确。论文也承认未来需要上下文感知的感知视图。
2. **仅使用转录组模态**：未纳入染色质可及性、蛋白丰度、空间信息或扰动读出，限制了多模态表征的潜力。
3. **无直接的因果动态建模**：CellOS 学习的是静态表征，虽然后续可用于扰动预测，但模型本身并未预训练在时间序列或扰动轨迹上。距离真正的“世界模型”仍有差距。
4. **资源细节缺失**：未披露训练所需具体硬件和时长，不利于可重复性和成本评估。
5. **评估中某些指标可能受数据分布影响**：例如扰动预测基准中 Pearson edist 的差异可能部分受嵌入维度或尺度影响，虽已固定下游模型，但仍需更多跨框架鲁棒性验证。

---

（完）
