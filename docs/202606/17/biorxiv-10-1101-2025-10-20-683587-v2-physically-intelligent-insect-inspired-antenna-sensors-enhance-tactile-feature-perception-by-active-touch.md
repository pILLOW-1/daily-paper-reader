---
title: Physically intelligent insect-inspired antenna sensors enhance tactile feature perception by active touch
title_zh: 受昆虫触角启发的物理智能传感器通过主动触觉增强触觉特征感知
authors: "Meng, L., McDonnell, P., Jayaram, K., Mongeau, J.-M."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.1101/2025.10.20.683587v2.full.pdf"
tags: ["query:agent-detect"]
score: 7.0
evidence: 通过触觉感知实现世界模型中的感知与检测
tldr: 软体传感器处理复杂触觉场景时计算成本高，受昆虫触角启发，本文提出具有柔性刚度梯度的天线传感器，通过主动触觉构建“触觉场”表示。实验表明，蟑螂触角启发的力学特性和主动触摸速度相比均匀刚度传感器提升了特征分类准确率，并增加了数据稀疏性和分散性。模拟到现实的转移验证了该物理智能框架的有效性，可降低计算负载并增强机器人触觉适应性。
source: biorxiv
selection_source: fresh_fetch
motivation: 克服软体传感器处理复杂触觉场景的高计算成本，借鉴昆虫触角物理智能实现高效触觉感知。
method: 设计蟑螂触角启发的多连杆软体天线，引入柔性刚度梯度与主动触觉速度，构建触觉场时空表示。
result: 相比均匀刚度传感器，触觉特征分类准确率显著提升，且数据稀疏性和分散性增加。
conclusion: 证实物理智能和主动触觉可简化触觉感知，降低计算需求，适用于机器人系统。
---

## 摘要
当前软体机器人传感器在解读复杂触觉场景时往往需要高昂的计算成本。受昆虫触角（一种通过物理智能高效处理触觉信息的柔性分布式传感器）启发，我们研究了机械设计与主动触觉感知策略能否增强机器人触觉特征感知能力。我们假设昆虫触角动力学（特别是弯曲刚度梯度与主动触摸速度）可简化触觉分类。通过搭建将仿生计算模型与多连杆软体机器人触角相连接的仿真-现实框架，我们引入了“触觉场”概念——由接触位置、特征类型和主动触摸速度共同塑造的触觉刺激时空表征。分析表明，与具有均匀弯曲刚度梯度的传统传感器相比，蟑螂启发式触角力学结合主动触摸速度可通过提升触觉数据稀疏性与分散性，提高特征分类准确率。对触角力学中刚度与阻尼的探索揭示了影响触觉辨识能力与结构稳定性的设计权衡。通过仿真-现实迁移，我们在微型分布式软体机器人触角上验证了刚度梯度与结构化主动触摸动作的有效性。综上，本研究提出了一种基于生物学的触觉传感器设计框架，可降低计算负载并增强适应性。

## Abstract
Soft robotic sensors today struggle to interpret complex tactile scenes without incurring significant computational costs. Inspired by insect antennae--compliant, distributed sensors that efficiently process tactile information through physical intelligence--we investigated whether mechanical design and active touch sensing strategies could enhance robotic tactile feature perception. We hypothesized that insect-inspired antenna dynamics, specifically flexural stiffness gradients and active touch speed, could simplify tactile classification. Using a sim-to-real framework that bridges bioinspired computational models with a multi-link soft robot antenna, we introduce the notion of tactile fields--spatiotemporal representations of tactile stimuli shaped by contact location, feature type, and active touch speed. Our analyses show that cockroach-inspired antenna mechanics jointly with active touch speeds improve feature classification accuracy compared to conventional sensors with uniform flexural stiffness gradient by increasing tactile data sparsity and dispersion. An exploration of stiffness and damping of antenna mechanics revealed design trade-offs that influence tactile discrimination and structural stability. Through sim-to-real transfer, stiffness gradients and structured active touch motions were demonstrated on a miniature distributed soft robotic antenna, validating their effectiveness in real-world robotic systems. Taken together, this work presents a biologically grounded framework for tactile sensor design that reduces computational load and enhances adaptability.