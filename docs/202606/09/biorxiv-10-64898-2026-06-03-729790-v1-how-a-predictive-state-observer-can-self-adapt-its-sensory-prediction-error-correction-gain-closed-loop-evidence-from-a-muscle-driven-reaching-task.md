---
title: "How a Predictive State Observer Can Self-Adapt Its Sensory Prediction-Error Correction Gain: Closed-Loop Evidence from a Muscle-Driven Reaching Task"
title_zh: 预测状态观察器如何自适应地调整其感官预测误差校正增益：来自肌肉驱动到达任务的闭环证据
authors: "Kobayashi, J."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729790v1.full.pdf"
tags: ["query:self-improve"]
score: 7.0
evidence: 利用智能体可用信号自适应调整感觉预测误差修正增益
tldr: 在肌肉驱动到达任务中，前向模型预测状态观测器需根据感觉延迟调整修正增益。无延迟时中等增益（K=0.25-0.50）最优，有18步延迟时高增益（K=1.0）最优。基于可靠性的自适应观测器在延迟条件下改善1.9-2.5 cm，但仍有1.4-1.8 cm差距。该研究揭示了延迟依赖的修正结构和纯前向模型的失效模式。
source: biorxiv
selection_source: fresh_fetch
motivation: 探索前向模型预测状态观测器如何根据感觉延迟自适应调整修正增益，以提升肌肉驱动到达任务的闭环性能。
method: 在MyoSuite 34肌肉臂上部署残差MLP前向模型与稳定端点探针控制器，通过扫描固定增益和基于创新历史的可靠性自适应机制评估增益配置。
result: 无延迟时中等增益最优，18步延迟时高增益最优；可靠性自适应在延迟条件下改善1.9-2.5 cm，但仍低于固定增益最优1.4-1.8 cm。
conclusion: 感觉延迟决定了最优修正增益结构，纯前向模型（K=0）性能差，基于可用信号的自适应修正存在固有限制。
---

## 摘要
我们探究基于前向模型的预测状态观察器在肌肉驱动到达任务中应如何设置其感官预测误差校正增益，以及该增益是否可以基于智能体可用的信号（创新历史与每次试验的到达结果）进行自适应调整，而非依赖扫掠的基准标签。我们在一个34块肌肉的MyoSuite手臂模型中评估了一个残差-MLP前向模型，任务为IK可达的肩下目标，并与一个稳定的末端点探针控制器闭环部署，该控制器使用非负最小二乘肌肉路由和虚拟目标斜坡；该控制器是用于评估状态估计效应的稳定探针，而非生物运动规划器。扫掠固定增益的闭环基准揭示了依赖于延迟的校正结构：无感觉延迟时，中间校正增益最佳（K = 0.25-0.50），而具有18步延迟时，观察密集型校正占优（K = 1.0）。仅前向模型的K = 0消融并不等同于基准：其系统性地比最佳固定K值差1.9-6.1厘米，并且由于长时程自回归漂移导致NNLS控制器残差较大；因此我们将K = 0作为诊断指标。基于结果训练的可信度自适应观察器在延迟条件下改善了1.9-2.5厘米，相较于默认可信度，而在无延迟单元中保持中性（此时基准已为中间值）。一个特征条件的贝塔适配器将单元级创新统计量映射到场级增益参数，在5/6个单元中几乎匹配了每单元训练的诊断指标，但两者在18步延迟下仍比扫掠固定增益基准差1.4-1.8厘米。这些结果分离了依赖于延迟的校正结构、仅前向模型的K = 0失败模式，以及智能体可用自适应校正的剩余限制。

## Abstract
We ask how a forward-model-based predictive state observer should set its sensory prediction-error correction gain during muscle-driven reaching, and whether that gain can be adapted from agent-available signals - innovation history and per-episode reaching outcome - rather than from swept oracle labels. We evaluate a residual-MLP forward model in a 34-muscle MyoSuite arm on an IK-reachable below-shoulder task, deployed in closed loop with a stabilized endpoint probe controller that uses non-negative least-squares muscle routing and a virtual target ramp; the controller is a stabilized probe for evaluating state-estimation effects, not a biological motor planner. A swept fixed-gain closed-loop oracle reveals a delay-dependent correction structure: with no sensory delay, intermediate correction gains are best (K = 0.25-0.50), whereas with 18-step delay observation-heavy correction wins (K = 1.0). The forward-model-only K = 0 ablation is not the oracle: it is systematically worse than the best fixed K by 1.9-6.1 cm and shows large NNLS controller residuals caused by long-horizon autoregressive drift; we therefore report K = 0 as a diagnostic. Outcome-trained reliability-adaptive observers improve the delayed regime by 1.9-2.5 cm over default reliability while remaining neutral in no-delay cells, where the oracle is already intermediate. A feature-conditioned beta adapter that maps cell-level innovation statistics to per-field gain parameters nearly matches a per-cell trained diagnostic in 5/6 cells, but both remain 1.4-1.8 cm worse than the swept fixed-K oracle at 18-step delay. These results separate the delay-dependent correction structure, the forward-model-only failure mode of K = 0, and the remaining limits of agent-available adaptive correction.