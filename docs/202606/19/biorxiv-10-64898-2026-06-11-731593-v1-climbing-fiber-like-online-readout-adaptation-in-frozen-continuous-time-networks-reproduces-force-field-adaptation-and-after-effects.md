---
title: Climbing-fiber-like online readout adaptation in frozen continuous-time networks reproduces force-field adaptation and after-effects
title_zh: 冻结连续时间网络中的攀爬纤维样在线读出自适应再现力场适应与后效应
authors: "Kobayashi, J."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731593v1.full.pdf"
tags: ["query:self-improve"]
score: 6.0
evidence: 在线读出适应与任务兼容探测用于机器人校准，与自我改进相关
tldr: 机器人主动校准常因探索轨迹导致任务状态难以执行。本文提出有限步任务兼容探测方法，解决一阶退化的局限性。实验显示任务失败不能用参数误差或奇异度预测，但终端滚动风险完美区分。通过延长执行与零空间姿态正则化可消除剩余失败，从而建立可辨识性、任务兼容探索与后校准可控性的三层框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 主动校准中探索轨迹可能使机器人进入不利于下游任务的状态，需保证任务兼容性。
method: 提出有限步任务兼容探测作为高阶广义零空间信息梯度控制，突破一阶退化限制。
result: 有限步探测消除了校准失败，但仍有任务失败；终端滚动风险（AUC=1.0）完美预测失败，优于参数误差。
conclusion: 主动校准需三层策略：可辨识性创建、任务兼容探索、后校准有限视界可控性，从而消除任务失败。
---

## 摘要
在身体、工具或接触参数不确定的情况下运行的机器人通常必须在不停下手头任务的情况下完善其身体模型。本文表明，仅靠可辨识性并不能解决主动校准问题：探索性轨迹可以产生准确的参数，但同时将机器人置于难以完成后续任务的状态。我们研究了一个具有未知连杆长度的最小冗余平面机械臂中的这种失败模式，并采用了从校准到任务的两阶段协议。我们将有限步任务兼容探测定义为对一阶零空间信息梯度控制的高阶推广，允许机器人在限制任务漂移的同时逃逸一阶任务兼容退化。在50个随机种子中，有限步探测消除了校准失败，但如果没有终端可控性管理，仍然会留下大量的下游任务失败。这些失败不能用参数误差（AUC = 0.511）或静态奇异度度量（AUC = 0.490）来解释，但短视界终端滚动风险实现了完美分离（AUC = 1.000），包括使用先知参数。第二阶段实验表明，更长的执行时间和零空间姿态正则化共同消除了剩余的任务失败；后续检查表明，失败出现在退化和近退化起点，而非退化起点使用普通控制器成功。结果支持主动校准的三层观点：可辨识性创建、任务兼容探索和校准后的有限视界可控性。

## Abstract
Robots that operate with uncertain body, tool, or contact parameters must often refine their body models without abandoning the task at hand. This paper shows that active calibration is not solved by identifiability alone: an exploratory trajectory can yield accurate parameters while placing the robot in a state from which the downstream task is hard to complete. We study this failure mode in a minimal redundant planar manipulator with unknown link lengths and a two-phase calibration-to-task protocol. We formulate finite-step task-compatible probing as a higher-order generalization of first-order null-space information-gradient control, allowing the robot to escape first-order task-compatible degeneracy while limiting task drift. Across 50 seeds, finite-step probing eliminates calibration failures but still leaves substantial downstream task failure without terminal controllability management. These failures are not explained by parameter error (AUC = 0.511) or static singularity measures (AUC = 0.490), but short-horizon terminal rollout risk achieves perfect separation (AUC = 1.000), including with oracle parameters. Phase-2 experiments show that longer execution and null-space posture regularization together eliminate the remaining task failures; follow-up checks show that the failure appears in degenerate and near-degenerate starts, while non-degenerate starts succeed with the plain controller. The results support a three-layer view of active calibration: identifiability creation, task-compatible exploration, and post-calibration finite-horizon controllability.