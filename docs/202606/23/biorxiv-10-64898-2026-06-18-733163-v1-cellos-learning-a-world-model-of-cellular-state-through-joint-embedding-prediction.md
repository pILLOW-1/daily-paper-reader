---
title: "CellOS: Learning a World Model of Cellular State through Joint Embedding Prediction"
title_zh: CellOS：通过联合嵌入预测学习细胞状态的世界模型
authors: "Zhou, Q., Le, Y., Qi, X., Chang, S., Lu, H., Wu, Y., Wang, H., Ran, R., li, x."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733163v1.full.pdf"
tags: ["query:agent-detect"]
score: 6.0
evidence: 包含感知视图的世界模型
tldr: 现有单细胞基座模型仅基于单一表达视图，难以整合互补的细胞状态信息。CellOS提出多视图框架，通过因果语言建模、混合专家扩展与LLM-JEPA对齐三阶段训练，在3.905亿单细胞上训练120亿参数模型。在细胞状态注释和扰动响应预测基准上超越现有模型，同时保持鲁棒的批次整合能力。该工作为构建以表征为中心的细胞世界模型和可迁移AI虚拟细胞提供了可扩展方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞模型仅从单一基因表达视图学习，无法整合互补的感知视图以全面表征细胞状态。
method: 采用三阶段训练：因果细胞句子语言建模、密集到混合专家扩展、以及基于LLM-JEPA的潜在空间对齐。
result: 在3.905亿细胞上训练的120亿参数模型在细胞状态注释和扰动预测上超越现有SOTA，批次整合稳健。
conclusion: 互补视图的预测对齐为构建表征中心的细胞世界模型和可迁移AI虚拟细胞提供了可扩展路径。
---

## 摘要
从单细胞转录组学习的基础模型对于能够表示、查询和预测细胞状态的AI虚拟细胞的前景至关重要。然而，目前大多数单细胞基础模型仅从基因表达的单一视角学习，并主要通过重建或下一个标记预测进行优化。因此，它们捕捉表达丰度，但无法明确协调细胞状态的互补视图。在这里，我们提出CellOS，一个多视图基础模型，从配对的表达和感知视图中学习细胞表示。CellOS通过一个可扩展的三阶段训练策略整合互补视图，该策略结合了因果细胞句子语言建模、保持功能的稠密到混合专家扩展以及通过LLM-JEPA目标进行潜在空间对齐。利用这一框架，我们在3.905亿个单细胞转录组上训练了一个120亿参数的模型。在涵盖细胞状态注释、批次整合和扰动响应预测的多个基准测试中，CellOS在细胞状态注释和扰动响应预测方面持续优于最先进的单细胞基础模型，同时保持了稳健的批次整合。综上所述，这些结果表明，互补细胞视图之间的预测对齐为以表示为中心的细胞世界模型和可迁移的AI虚拟细胞提供了一条可扩展的路径。

## Abstract
Foundation models learned from single-cell transcriptomes are central to the prospect of AI virtual cell that can represent, query and predict cellular state. However, most current single-cell foundation models learn from a single view of gene expression and are optimized primarily through reconstruction or next-token prediction. As a result, they capture expression abundance but can-not explicitly reconcile complementary views of cellular state. Here we present CellOS, a multi-view foundation model that learns cellular representations from paired expression and perception views. CellOS integrates complementary views through a scalable three-stage training strategy that combines causal cell-sentence language modelling, function-preserving dense-to-mixture-of-experts expansion and latent-space alignment via an LLM-JEPA objective. Using this framework, we trained a 12-billion-parameter model on 390.5 million single-cell transcriptomes. Across diverse benchmarks spanning cell-state annotation, batch integration and perturbation-response prediction, CellOS consistently outperformed state-of-the-art single-cell foundation models in cell-state annotation and perturbation-response prediction while preserving robust batch integration. Together, these results suggest that predictive alignment between complementary cellular views provides a scalable path toward representation-centric cellular world models and transferable AI virtual cells.