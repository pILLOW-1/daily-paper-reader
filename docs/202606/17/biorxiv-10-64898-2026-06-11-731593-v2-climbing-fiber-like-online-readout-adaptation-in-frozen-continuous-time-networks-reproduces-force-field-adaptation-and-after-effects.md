---
title: Climbing-fiber-like online readout adaptation in frozen continuous-time networks reproduces force-field adaptation and after-effects
title_zh: 冻结连续时间网络中的类爬行纤维在线读出适应再现力场适应与后效
authors: "Kobayashi, J."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731593v2.full.pdf"
tags: ["query:self-improve"]
score: 6.0
evidence: 在线读出自适应使智能体无需重训练即可改进性能
tldr: 连续时间神经网络（如CfC）通常离线训练后无法在线适应环境变化。本研究提出冻结核心网络，仅通过攀爬纤维样误差信号在线调整线性读出层。在平面两连杆臂的卷曲力场到达任务中，该方法能矫正轨迹，并在力场移除后产生镜像后效，体现出内部模型学习特征。研究表明，仅适应读出层即可实现低成本在线误差纠正，无需更新核心网络。
source: biorxiv
selection_source: fresh_fetch
motivation: 离线训练的连续时间网络缺乏在线校准机制，需要一种生物启发的低计算成本适应方法。
method: 冻结CfC/NCP核心，使用反馈误差学习（FEL）和LMS规则在线更新线性读出权重，以攀爬纤维样误差信号驱动。
result: 在卷曲力场中成功矫正到达轨迹，力场移除后产生镜像后效；RLS变体收敛快但慢去适应，协方差重置可改善。
conclusion: 仅适应读出层为离线训练的连续时间控制器提供了有效的在线误差适应方案，且对核心网络变化具有鲁棒性。
---

## 摘要
基于液态神经网络和相关连续时间模型（如LTC和CfC）的机器人运动控制通常通过时间反向传播进行离线训练，缺乏在植物动力学变化时在线重新校准的显式机制。我们研究了一个冻结的CfC核心（其液态状态跨越固定的连续时间基）是否可以通过仅使用类爬行纤维误差信号适应其线性读出，来支持小脑风格的在线适应。在一个具有速度依赖性卷曲力场的平面两连杆到达模拟中，我们在最小均方（LMS）规则下使用反馈误差学习（FEL）信号在线适应读出，而不触及核心。冻结核心的仅读出控制器重新矫直了受卷曲扰动的到达动作，并且在移除力场后产生了镜像后效，这是一种与内部模型学习一致的行为特征，而仅反馈控制器不会产生这种效果。当使用循环状态（而非投影的运动输出）作为读出基础时，该结果从密集的CfC推广到稀疏的神经电路策略（NCP）连接；它对力场强度和方向具有鲁棒性；递归最小二乘变体适应更快，但去适应缓慢，因为其协方差崩溃，而协方差重置的安全遗忘规则消除了这种僵化。在所探索的二维两连杆模拟范围内，我们没有发现仅读出失败的情况，即在测试条件下需要适应冻结核心。因此，在这项模拟研究中，仅适应读出为离线训练的连续时间控制器提供了一种生物启发的、低成本的在线误差适应层。

## Abstract
Robotic motor control built on liquid neural networks and related continuous-time models, such as LTC and CfC, is typically trained offline via backpropagation through time and lacks an explicit mechanism for recalibrating online as plant dynamics change. We ask whether a frozen CfC core, whose liquid state spans a fixed continuous-time basis, can support cerebellar-style online adaptation by adapting only its linear readout with a climbing-fiber-like error signal. In a planar two-link reaching simulation with a velocity-dependent curl force field, we adapt the readout online with a feedback-error-learning (FEL) signal under a least-mean-squares (LMS) rule, leaving the core untouched. The frozen-core readout-only controller re-straightens curl-perturbed reaches and, upon field removal, produces a mirror-image after-effect, a behavioral signature consistent with internal-model learning, which a feedback-only controller does not produce. The result generalizes from a dense CfC to a sparse Neural-Circuit-Policy (NCP) wiring when the recurrent state, rather than the projected motor output, is used as the readout basis; it is robust to force-field strength and direction; and a recursive-least-squares variant adapts faster but de-adapts slowly because its covariance collapses, a rigidity that a covariance-reset safe-forgetting rule removes. Within the explored two-link planar simulation range, we did not find a readout-only failure case that required adapting the frozen core in the tested conditions. In this simulation study, adapting only the readout therefore provides a biologically inspired, low-cost online error-adaptation layer for offline-trained continuous-time controllers.