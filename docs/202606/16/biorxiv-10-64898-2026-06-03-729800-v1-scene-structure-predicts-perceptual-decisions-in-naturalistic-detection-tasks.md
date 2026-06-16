---
title: Scene Structure Predicts Perceptual Decisions in Naturalistic Detection Tasks
title_zh: 场景结构预测自然主义检测任务中的感知决策
authors: "Yang, J., Vercillo, T., Cutrona, T. E., Azeglio, S., Iannetti, G., Neri, P."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729800v1.full.pdf"
tags: ["query:agent-detect"]
score: 8.0
evidence: 研究自然场景结构如何影响检测任务中的感知决策
tldr: 自然场景中的知觉决策不仅取决于目标本身，还受背景统计结构的显著影响。本研究结合心理物理学、增强现实、深度神经网络、图像特征分析和脑电图，发现背景结构能预测人类在近阈值检测任务中的正确或错误反应，且在空间不确定时效应更强。低层图像特征如纹理熵和边缘密度是关键预测因子，同时脑电图在刺激前窗口即显示出与决策准确性相关的神经活动。该工作揭示了环境结构与神经动态如何共同支撑知觉决策。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究自然场景统计结构如何影响知觉证据形成和近阈值刺激的感知正确性。
method: 结合心理物理学、增强现实、深度神经网络、图像特征分析和脑电图，分析背景对检测任务的影响。
result: 背景结构预测行为结果，纹理熵和边缘密度等特征有效，脑电图刺激前窗口区分正确/错误试次。
conclusion: 自然场景中的感知由目标与周围背景统计结构共同决定。
---

## 摘要
人类视觉系统能够识别复杂自然场景中的物体，但在这种多变条件下支持稳健感知的机制仍不完全清楚。这里，我们研究了自然场景的统计结构如何塑造感知证据形成，并决定近阈值刺激是否被正确或错误地感知。我们结合控制心理物理学、户外增强现实（AR）、深度神经网络（DNN）、图像特征分析和脑电图（EEG），考察背景环境如何调节感知决策。在多个检测任务中，人类表现系统地受到无探针背景结构的影响。仅基于背景图像训练的DNN预测了正确和错误的行为结果，在后线索条件下效果更强，表明当空间不确定性较高时，全局场景上下文有助于局部感知决策。AR实验进一步表明，这些上下文驱动效应在自然观察环境中持续存在。为识别这些效应背后的视觉信息，我们分析了低级图像统计量。纹理熵和边缘密度成为信息丰富的特征，基于这些测量的传统机器学习模型实现了有意义的正确/错误分类。最后，EEG分析揭示了图像驱动感知变异性的神经标志物：无探针预图像窗口期间的活动区分了后来的正确和错误试验，将EEG与图像衍生特征结合提高了解码性能。总之，这些发现表明自然场景中的感知并非仅由目标决定，而是由周围上下文的统计结构塑造。通过连接心理物理学、AR、DNN建模、图像统计和EEG，这项工作提供了一个统一框架，用于理解环境结构和神经动力学如何共同支持感知决策。

## Abstract
The human visual system can identify objects in complex natural scenes, yet the mechanisms supporting robust perception under such variable conditions remain incompletely understood. Here, we investigate how the statistical structure of natural scenes shapes perceptual evidence formation and determines whether near-threshold stimuli are perceived correctly or incorrectly. We combine controlled psychophysics, outdoor augmented reality (AR), deep neural networks (DNNs), image-feature analysis, and EEG to examine how background context modulates perceptual decisions. Across multiple detection tasks, human performance was systematically influenced by probe-free background structure. DNNs trained on background images alone predicted correct and incorrect behavioral outcomes, with stronger effects in postcue conditions, suggesting that global scene context contributes to local perceptual decisions when spatial uncertainty is higher. AR experiments further showed that these context-driven effects persist in naturalistic viewing environments. To identify the visual information underlying these effects, we analyzed low-level image statistics. Texture entropy and edge density emerged as informative features, and conventional machine-learning models trained on these measures achieved meaningful correct/incorrect classification. Finally, EEG analyses revealed neural signatures of image-driven perceptual variability: activity during the probe-free preimage window distinguished later correct from incorrect trials, and combining EEG with image-derived features improved decoding performance. Together, these findings show that perception in natural scenes is not determined solely by the target, but is shaped by the statistical structure of the surrounding context. By linking psychophysics, AR, DNN modeling, image statistics, and EEG, this work provides a unified framework for understanding how environmental structure and neural dynamics jointly support perceptual decision-making.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：自然场景的统计结构如何影响近阈值刺激的感知决策？即背景环境是否以及如何调节人脑对微弱目标的正确或错误感知。
- **整体含义**：传统视觉研究多关注目标本身，但现实世界中的感知常依赖于周围上下文。本文旨在揭示自然场景背景结构如何塑造感知证据形成，并解释在复杂自然条件下稳健感知的机制。
- **动机**：人类视觉系统能在多变自然场景中识别物体，但支持这种稳健感知的机制尚不完全清楚。理解背景统计结构的作用有助于统一框架解释感知决策。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：感知决策并非仅由目标决定，而是由周围上下文的统计结构塑造。背景图像可预测人类的正确或错误反应。
- **关键技术细节**：
  - **心理物理学**：控制实验，测量人类在近阈值检测任务中的表现，系统操作有无探针背景。
  - **增强现实（AR）**：户外自然观察环境下验证上下文效应的生态效度。
  - **深度神经网络（DNN）**：仅用背景图像训练DNN，预测人类行为结果（正确/错误）。特别在后线索条件下预测效果更强，说明空间不确定性高时全局场景上下文贡献增大。
  - **图像特征分析**：提取低级图像统计量（如纹理熵、边缘密度），基于这些特征训练传统机器学习模型，实现有意义的正误分类。
  - **脑电图（EEG）**：采集无探针预图像窗口期间的神经活动，区分后续正确与错误试验；将EEG特征与图像衍生特征结合可提高解码性能。
- **公式/算法流程**：原文未提供具体数学公式，流程可概括为：
  1. 设计多个检测任务，记录人类行为反应。
  2. 收集“无探针”背景图像。
  3. 训练DNN（如卷积网络）以背景图像为输入，预测人类正确/错误标签。
  4. 计算背景图像的纹理熵、边缘密度等统计量，作为传统分类器输入。
  5. 同步记录EEG，分析刺激前基线窗口的神经活动，进行单试次解码。
  6. 比较不同条件（如前线索 vs 后线索、实验室 vs AR）下的效应强度。

## 3. 实验设计：数据集/场景、Benchmark、对比方法

- **数据集/场景**：
  - 控制心理物理学实验：室内实验室，受控视觉刺激（自然场景图像嵌入近阈值目标）。
  - 户外AR实验：自然观察环境，通过增强现实设备呈现检测任务。
  - 图像来源：未明确说明具体图像数据集名称，但使用大量自然场景背景。
- **Benchmark**：未明确设置传统基准测试。文中通过对比不同线索条件（前线索 vs 后线索）、实验室 vs AR环境来评估上下文效应。
- **对比方法**：
  - DNN模型 vs 传统机器学习模型（基于纹理熵、边缘密度等）。
  - DNN预测 vs 人类实际行为。
  - EEG单独解码 vs EEG+图像特征联合解码。
  - 心理物理学结果与AR结果对比，验证生态效度。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。
- 仅提及训练了深度神经网络和传统机器学习模型，推测需要一定计算资源，但未提供细节。

## 5. 实验数量与充分性

- **实验组数**：包含心理物理学实验、AR实验、DNN建模、图像统计分析和EEG实验，至少4大类实验。每个类别内可能包含多个子条件（如线索类型、任务难度）。
- **充分性评价**：实验设计较为全面，覆盖行为、计算建模、神经生理三个层面，并在实验室和自然场景进行验证，增强了结论的可推广性。但未报告样本量（被试数量）、试次次数、统计检验力等信息，难以判断统计可靠性。未进行跨数据集验证或消融分析（如去除某些特征的影响）。整体充分性中等，能支持主要结论，但细节透明性不足。

## 6. 论文的主要结论与发现

- **主要结论**：自然场景中的感知由目标与周围背景统计结构共同决定。背景结构能预测近阈值检测任务中的正确或错误反应，且效应在空间不确定时（后线索条件）更强。
- **具体发现**：
  - 仅基于背景图像训练的DNN可预测人类行为结果。
  - 户外AR实验确认上下文驱动效应在自然观察环境中持续存在。
  - 低级图像统计量（纹理熵、边缘密度）是信息丰富的预测特征。
  - EEG刺激前窗口的神经活动能区分后续正确与错误试验，且与图像特征结合提升解码性能。

## 7. 优点：方法或实验设计上的亮点

- **多模态融合**：同时整合心理物理学、增强现实、深度学习、图像分析和脑电图，提供从行为到神经机制的完整链路。
- **生态效度高**：引入户外AR实验，突破实验室限制，验证结论在真实自然环境中的适用性。
- **预测方向新颖**：用无目标背景本身预测感知结果，强调上下文而非单纯目标特征的作用。
- **神经与行为关联**：EEG预刺激窗口发现神经活动与后续行为准确性的关系，揭示决策前的潜在神经机制。

## 8. 不足与局限

- **实验细节缺失**：未报告被试数量、试次次数、刺激参数、统计检验量，影响可复现性和结论可靠性。
- **计算资源信息缺失**：未提供训练模型的具体算力需求，不利于其他研究者复现计算部分。
- **低级特征解释局限**：仅关注纹理熵和边缘密度等简单统计量，可能忽略更高阶的场景语义信息，解释力有限。
- **EEG空间分辨率有限**：未采用源定位等方法，无法精确定位参与决策的脑区。
- **未进行因果验证**：相关性不等于因果性，未通过扰动（如经颅磁刺激）验证背景结构是否真正决定感知。
- **应用限制**：结论可能局限于近阈值检测任务，对于强信号或搜索任务是否适用未知。

（完）
