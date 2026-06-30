---
title: Modeling Dynamical Vision with Biologically Plausible Recurrent Convolutional Networks
title_zh: 利用生物合理递归卷积网络建模动态视觉
authors: "Gutzen, R., Lindsay, G. W."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.1101/2025.08.11.669756v2.full.pdf"
tags: ["query:agent-detect"]
score: 7.0
evidence: 用于视觉感知的生物合理递归卷积网络
tldr: "生物视觉系统依赖循环连接处理时空动态，但标准CNN缺乏此机制。本文提出DynVision工具箱，提供模块化、配置驱动的生物合理循环卷积网络（RCNN）构建与评估，支持多种循环类型和时延，并实现52%训练加速。通过参数空间探索发现，循环整合的目标位置和损失计算的时间窗口显著影响动态特性；连续时间循环可自然产生皮层适应现象，而不同循环配置可达到接近人类的噪声鲁棒性。该工作强调统一建模框架对研究循环视觉模型的重要性。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有CNN缺乏与视觉皮层相似的循环连接，难以模拟时空适应和噪声鲁棒性等生物现象，且缺乏系统比较不同循环结构的工具。
method: 开发DynVision开源工具箱，基于配置驱动设计实现多种局部循环类型（自连接到皮层组织），集成数值ODE求解器与异构时延，并分离科学与实现细节。
result: "训练加速52%；揭示循环目标位置和时间窗口对动态特性的敏感影响；连续时间循环自发产生皮层时间现象，特定循环配置使噪声鲁棒性接近人类水平。"
conclusion: 不同循环配置功能各异，创建完全真实模型困难，亟需统一建模框架辅助探索。
---

## 摘要
摘要：用于图像识别的卷积神经网络(CNN)显示出与灵长类腹侧视觉通路显著的概念相似性，但其标准前馈架构缺乏视觉皮层中普遍存在的递归连接。这种递归被认为支撑着包括适应、延迟归一化和对噪声输入的鲁棒性在内的时空现象。然而，将功能上有益的递归纳入能够捕捉生物视觉时空现象的CNN中仍然具有挑战性。尽管最近的进展融入了神经生物学约束，但该领域缺乏易于使用的工具来系统地比较不同的架构选择（如递归类型、时间延迟和连接模式）如何塑造神经动力学和行为。在这里，我们介绍了DynVision，一个模块化的开源工具箱，用于构建和评估生物合理的递归卷积神经网络(RCNN)。DynVision实现了具有异质延迟的数值ODE求解器，支持五种类型的侧向递归，从简单的自连接到皮层组织的局部递归，并通过配置驱动设计将科学建模决策与实现细节分离。训练计算效率高，相比参考实现实现了52%的加速。我们通过系统探索参数空间来展示该框架，揭示了时间动力学的定性差异对通常隐式的建模选择（如递归整合的目标位置和用于损失计算的时间窗口）高度敏感。重要的是，我们发现连续时间的递归动力学可以自然地产生皮层时间现象，而无需显式的除法归一化，而另一种递归配置产生的噪声鲁棒性接近人类水平的表现。这些发现表明了功能上不同的递归配置，并强调了创建完全现实模型的挑战，从而突出了需要一个全面且连贯的建模框架来辅助探索。代码和文档见https://github.com/Lindsay-Lab/DynVision/。

## Abstract
AO_SCPLOWBSTRACTC_SCPLOWConvolutional Neural Networks (CNNs) trained for image recognition have demonstrated remarkable conceptual similarities to the primate ventral visual pathway, but their standard feedforward architectures lack the recurrent connections that are ubiquitous in visual cortex. Such recurrence is thought to underlie spatiotemporal phenomena including adaptation, delayed normalization, and robustness to noisy input. However, incorporating functionally beneficial recurrence into CNNs that captures spatiotemporal phenomena of biological vision remains challenging. Although recent advances have incorporated neurobiological constraints, the field lacks accessible tools for systematically comparing how different architectural choices, such as recurrence type, temporal delays, and connectivity patterns, shape neural dynamics and behavior. Here, we introduce DynVision, a modular open-source toolbox for constructing and evaluating biologically plausible recurrent convolutional neural networks (RCNNs). DynVision implements numerical ODE solvers with heterogeneous delays, supports five types of lateral recurrence ranging from simple self-connections to cortically-organized local recurrence, and separates scientific modeling decisions from implementation details through a configuration-driven design. Training is computationally efficient, achieving a 52% speedup over reference implementations. We demonstrate the framework through systematic exploration of the parameter space, revealing that qualitative differences in temporal dynamics are highly sensitive to often-implicit modeling choices such as the target location of recurrent integration and the temporal window used for loss computation. Critically, we find that continuous-time recurrent dynamics can naturally give rise to cortical temporal phenomena without requiring explicit divisive normalization, while a different recurrent configuration produces noise robustness approaching human-level performance. These findings suggest functionally distinct configurations of recurrence and highlight the challenge of creating fully realistic models, thus emphasizing the need for a comprehensive and cohesive modeling framework to aid exploration. Code and documentation are available at https://github.com/Lindsay-Lab/DynVision/.