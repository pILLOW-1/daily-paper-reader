---
title: Efficient Learning of Predictive Maps for Flexible Planning
title_zh: 高效学习预测地图以支持灵活规划
authors: "Bazarjani, A., Piray, P."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.11.705395v2.full.pdf"
tags: ["query:self-improve"]
score: 6.0
evidence: 提出SR-IS模型高效学习预测地图，通过灵活规划实现智能体自我改进
tldr: 针对传统预测地图依赖决策策略而限制灵活规划的问题，本文提出结合时序差分学习与重要性采样的SR-IS模型，学习策略无关的预测地图。该模型能在环境变化时高效更新，实现快速行为适应。实验表明SR-IS在规划任务中优于现有模型，并解释了人类重规划中的等级偏差。该工作桥接了预测地图理论与规划行为。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有预测地图（如继承表示）因策略依赖而无法灵活规划，亟需策略无关且能快速适应环境变化的表示方法。
method: 提出SR-IS模型，通过时序差分学习与重要性采样结合，学习独立于当前策略的预测地图，并支持环境变化时的高效更新。
result: 在规划任务中优于现有模型，并成功解释了人类重规划中的等级偏差，这是以往模型无法实现的。
conclusion: SR-IS提供了策略无关的预测地图学习框架，有效支持灵活规划，为理解大脑灵活决策提供了新视角。
---

## 摘要
认知地图通过提供任务结构的可重用内部表征来实现灵活行为。后继表征作为一种预测地图，编码期望的未来状态占据，已被提出作为大脑中可能计算此类地图的一种方式，但其策略依赖性严重限制了灵活规划。我们引入了一个新模型，即带有重要性采样的后继表征（SR-IS），它将时序差分学习与重要性采样相结合，以构建策略无关的预测地图。SR-IS在不被智能体当前决策策略约束的情况下学习环境结构。当环境发生变化时，这些表征可以被高效更新，从而实现快速的行为适应。我们表明，SR-IS在规划任务中优于现有模型，并更好地解释了以前模型无法解释的人类重新规划中的分级偏差。这项工作将预测地图理论与观察到的规划行为联系起来，为大脑中的灵活决策提供了新见解。

## Abstract
Cognitive maps enable flexible behavior by providing reusable internal representations of task structure. The successor representation, a predictive map that encodes expected future state occupancy, has been proposed as one way such maps might be computed in the brain, but its policy dependence severely limits flexible planning. We introduce a new model, the successor representation with importance sampling (SR-IS), which combines temporal-difference learning with importance sampling to construct policy-independent predictive maps. SR-IS learns the structure of the environment without being constrained by the agents current decision policy. These representations can be efficiently updated when the environment changes, enabling rapid behavioral adaptation. We show that SR-IS outperforms existing models in planning tasks and provides a better account of the graded biases in human replanning that previous models could not explain. This work bridges theories of predictive maps with observed planning behavior and offers new insights into flexible decision-making in the brain.