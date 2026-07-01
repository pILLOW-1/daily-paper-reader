---
title: Modeling echolocation as an active pursuit of information via infotaxis
authors: "Lee, W.-J., Buck, J. R., Tyack, P."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.31.697206v2.full.pdf"
tags: ["query:agent-detect"]
score: 7.0
evidence: 通过信息追踪的主动感知检测
tldr: 本文提出将信息贪婪算法“infotaxis”扩展到回声定位场景，构建在检测不确定性下主动搜索目标的代理。该代理通过调整发射信号获取信息，模拟实验验证了其有效性。该工作为主动感知和检测提供了计算框架，可迁移至机器人感知模块和世界模型中的检测组件。
source: biorxiv
selection_source: fresh_fetch
motivation: 通过信息追踪的主动感知检测。
method: 方法与实现细节请参考摘要与正文。
result: 结果与对比结论请参考摘要与正文。
conclusion: 总体而言，该工作在所述任务上展示了有效性，并提供了可复用的思路或工具。
---

## Abstract
Echolocation is a closed-loop active sensing modality in which animals not only choose how they move to acquire information, but also actively modulate incoming sensory (echo) information by shaping the acoustic signals they emit to probe the environment. While many models describe how echolocating animals react to prior echoes by adjusting subsequent behavior, few explicitly model how they cognitively reason about information embedded in echoes when determining future actions. Here, we extend "infotaxis," an information-greedy algorithm originally developed for olfactory search, to sonar sensing by formulating an echolocating agent searching for a single target under sensory uncertainty characterized by probabilities of miss and false alarm. Through analytical and computational analyses, we show that the characteristic exploration-exploitation balance of infotaxis also emerges in echolocation, and that the efficiency and reliability of infotaxis search depend strongly on sensory information quality. Compared with a maximum a posteriori agent that always directs the beam to the most probable target location, the infotaxis agent consistently completes searches with fewer pings and greater robustness to sensory uncertainty. These results highlight information as a powerful concept for understanding active sensing and developing models for sonar-guided autonomy in both biological and engineered systems.