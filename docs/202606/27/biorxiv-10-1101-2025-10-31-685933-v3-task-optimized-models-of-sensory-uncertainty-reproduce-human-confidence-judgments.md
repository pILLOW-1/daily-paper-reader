---
title: Task-optimized models of sensory uncertainty reproduce human confidence judgments
title_zh: 任务优化的感觉不确定性模型再现了人类置信判断
authors: "Govindarajan, L. N., Alavilli, S., McDermott, J. H."
date: 2026-06-24
pdf: "https://www.biorxiv.org/content/10.1101/2025.10.31.685933v3.full.pdf"
tags: ["query:agent-detect"]
score: 6.0
evidence: 开发任务优化模型来估计感知不确定性，与世界模型中的感知和检测模块相关
tldr: 感官输入常存在歧义，导致感知不确定性，但人类在自然场景中是否明确表示不确定性且表示是否规范正确尚不清楚。本文开发了一类任务优化的模型，通过生成感知估计的概率分布来量化不确定性，填补了缺乏可计算模型的空白。在声音定位和音高感知实验中，比较人类置信判断与模型置信度，发现人类置信度随刺激变异性增大而降低，且与模型输出高度相关。结果表明人类不确定性表示准确反映了感知实际不确定性，该建模框架可扩展至其他感知领域。
source: biorxiv
selection_source: fresh_fetch
motivation: 为填补缺乏可计算模型的空白，探究人类在自然场景中是否准确表示感知不确定性，并检验表示是否规范正确。
method: 开发任务优化的生成概率分布的模型，在声音定位和音高感知实验中比较人类置信判断与模型置信度。
result: 人类置信度随刺激变异性增大而降低，且在不同条件下与模型置信度高度相关。
conclusion: 人类不确定性表示准确反映感知实际不确定性，所提出的建模框架可推广至其他感知领域。
---

## 摘要
感官输入常常是模糊的，导致对外部世界的不确定解释。对感知不确定性的估计可能有助于指导行为，但仍不清楚人类是否在自然场景中明确表示不确定性，以及任何此类表示是否在规范上是正确的。由于缺乏估计不确定性的刺激可计算模型，进展受到阻碍。我们开发了一类任务优化模型，生成感知估计的概率分布。为了评估人类不确定性表示是否与模型一致，我们将人类置信判断（可能间接反映不确定性表示）与从模型不确定性中提取的置信判断进行了比较。在声源定位和音高感知中，人类置信度系统性地变化，对于跨试验产生更可变估计的刺激，置信度更低。人类置信度在不同条件下跟踪模型置信度，表明人类不确定性表示准确地反映了感知估计的实际不确定性。该建模框架可扩展到其他感知领域。

## Abstract
Sensory input is often ambiguous, leading to uncertain interpretations of the external world. Estimates of perceptual uncertainty might be useful in guiding behavior, but it remains unclear whether humans explicitly represent uncertainty in naturalistic settings, and whether any such representations are normatively correct. Progress has been hindered by the absence of stimulus-computable models that estimate uncertainty. We developed a class of task-optimized models that generate probability distributions over perceptual estimates. To assess whether human uncertainty representations align with the models, we compared human confidence judgments, which might indirectly reflect uncertainty representations, to confidence judgments extracted from the models uncertainty. In both sound localization and pitch perception, human confidence varied systematically, being lower for stimuli that produced more variable estimates across trials. Human confidence tracked model confidence across conditions, suggesting that human uncertainty representations accurately reflect the actual uncertainty of perceptual estimation. The modeling framework is extensible to other perceptual domains.