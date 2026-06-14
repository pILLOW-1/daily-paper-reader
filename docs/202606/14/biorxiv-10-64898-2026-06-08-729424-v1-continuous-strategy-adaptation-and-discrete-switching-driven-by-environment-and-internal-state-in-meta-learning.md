---
title: Continuous Strategy Adaptation and Discrete Switching Driven by Environment and Internal State in Meta-Learning
title_zh: 元学习中由环境和内部状态驱动的持续策略适应与离散切换
authors: "Chen, J., Taira, M., Doya, K."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.729424v1.full.pdf"
tags: ["query:self-improve"]
score: 6.0
evidence: 研究元学习与策略适应，与自我改进智能体学习相关
tldr: 行为策略可根据环境和内部状态连续或离散变化，这是元学习的核心问题。本研究通过四种方法分析小鼠两步决策任务：stay-switch概率分析和GLMM揭示学习进程促使策略从随机探索转向模型导向的价值学习，并提升选择持续性；时变元参数强化学习模型的粒子滤波方法显示，随着学习进展，元参数表现出学习更快、模型贡献更大、随机性更高、选择持续性发展更快但对最终决策贡献更小的动态；有限内部状态模型发现最优价值学习状态与次优重复状态之间存在每试次离散切换。综合这些结果，揭示了策略适应中连续调整与离散切换在中时间尺度上的交互：当奖励设置变化时，小鼠持续处于重复状态，导致不完整的模型导向尝试。该研究为理解元学习中的策略动态提供了统一框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 研究行为策略如何根据内外状态连续或离散变化，揭示元学习中的策略适应机制。
method: 结合stay-switch概率分析、GLMM、时变元参数RL模型粒子滤波、有限内部状态模型四种方法分析小鼠行为。
result: 学习进展促使策略转向基于模型，提升选择持续性；不确定奖励引发探索；发现最优与次优状态的离散切换。
conclusion: 策略适应包含连续调整与离散切换的交互，不同时间尺度机制共存，为理解元学习提供统一框架。
---

## 摘要
行为策略可响应环境和内部状态而逐渐或突然改变，从而实现灵活适应。这种策略调节是元学习（学习如何学习）能力的核心。以往研究利用假设连续或离散变化的模型和理论，分析了时间依赖或条件依赖的策略变化。本文通过四种不同方法分析小鼠在两步决策任务中的行为：停留-切换选择概率分析；基于先前任务事件的选择与反应时间的广义线性混合模型（GLMM）；通过新颖的多步粒子滤波方法拟合具有时变元参数的强化学习（RL）模型；以及拟合基于离散状态转换产生选择和反应时间的有限内部状态（FIS）模型。综合来看，停留概率和GLMM分析表明，学习进程会促使向基于模型、基于价值的学习策略转变，并伴随选择持久性的增强。更不确定的奖励设置或奖励设置的变化会导致随机、探索性行为。元参数动态显示，随着学习推进，学习速度加快，基于模型的策略参与度更高，选择随机性增大，选择持久性发展更快但对最终决策的贡献减小。面对不确定的奖励设置或奖励设置变化时的探索性行为，由更慢的遗忘和更大的模型贡献所支撑。FIS模型发现，在试次层面存在从最优基于价值的学习状态到次优自我重复状态的切换。元参数动态反映了策略的持续变化，而状态转换则捕捉了突然的离散策略切换。在中间时间尺度上，当奖励设置变化时，两个过程相互作用：小鼠持续处于自我重复状态，导致尝试基于模型的策略但适应不完全。

## Abstract
Behavioral strategies can change in response to environmental and internal states, either gradually or abruptly, enabling flexible adaptation. Such strategy regulation is central to meta-learning, the ability to learn to learn. Previous studies analyzed temporal or condition-dependent strategy change using models and theories that assume continuous or discrete changes. Here, we analyze the mice's behavior in a two-step decision task using four different approaches: stay-switch choice probability analysis; generalized linear mixed model (GLMM) of choice and reaction time (RT) given preceding task events; fitting a reinforcement learning (RL) model with time-varying meta-parameter by a novel multiple-step particle filtering method; and fitting a finite internal state (FIS) model that produces choice and RT depending on discrete state transition. Together, the stay probability and GLMM analyses reveal that learning progress encourages a shift toward a model-based, value-based learning strategy, accompanied by elevated choice perseveration. More uncertain reward settings or changes in them lead to random, exploratory behavior. Meta-parameter dynamics show faster learning, greater involvement of a model-based strategy, higher choice stochasticity, and more rapid development of choice perseveration with less contribution to the final decision as learning progresses. Exploratory behavior in the face of uncertain reward settings or changes in those settings is underpinned by slower forgetting and greater model-based contribution. FIS modeling discovered a trial-level switch between an optimal value-based learning state and a suboptimal self-repeating state. Meta-parameter dynamics reflect continuous strategy changes, while state transitions capture abrupt, discrete strategy switches. At an intermediate timescale, when reward settings change, two processes interact: mice persist in a self-repeating state, leading to attempts at model-based strategy with incomplete adaptation.