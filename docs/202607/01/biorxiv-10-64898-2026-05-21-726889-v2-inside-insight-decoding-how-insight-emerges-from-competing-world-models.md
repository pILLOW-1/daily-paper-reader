---
title: "Inside insight: decoding how insight emerges from competing world models"
authors: "Inutsuka, K., Nishioka, T., Macpherson, T., Fujiwara, M., Hikida, T., Naoki, H."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.21.726889v2.full.pdf"
tags: ["query:agent-detect"]
score: 7.0
evidence: 从行为检测世界模型转变
tldr: 本文提出内部洞见动力学（IID）框架，从行为数据中估计世界模型转变的动态，包括转变时机和过程。应用于小鼠任务，成功解码了洞见涌现的时刻和机制。该方法为研究认知灵活性和世界模型转变提供了可量化的检测工具，对理解智能体内部检测过程有启示。
source: biorxiv
selection_source: fresh_fetch
motivation: 从行为检测世界模型转变。
method: 方法与实现细节请参考摘要与正文。
result: 结果与对比结论请参考摘要与正文。
conclusion: 总体而言，该工作在所述任务上展示了有效性，并提供了可复用的思路或工具。
---

## Abstract
When and how does insight emerge? We conceptualize insight as a sudden realization arising from restructuring a world model: an internal interpretation linking actions to outcomes. Yet these latent dynamics remain difficult to access, even with behavior and verbal report. Here we developed inside insight dynamics (IID), a machine-learning framework that estimates latent world-model dynamics from behavioral data. Using IID, we analyzed mouse behavior in indirect- and direct-rule tasks, each requiring a shift from an initial world model to a rule-consistent representation. IID inferred the "when" of insight-like shifts by estimating the timing of transitions between competing world models, and examined the "how" by comparing alternative learning processes underlying them. This analysis revealed distinct mechanisms of world-model learning: the indirect- and direct-rule tasks were better explained by gated learning and parallel learning, respectively. Thus, IID opens a route to quantifying latent insight dynamics from observable behavior alone.