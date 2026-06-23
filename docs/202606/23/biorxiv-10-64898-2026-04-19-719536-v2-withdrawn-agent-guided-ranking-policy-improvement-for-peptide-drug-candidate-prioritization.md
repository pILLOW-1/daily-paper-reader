---
title: "WITHDRAWN: Agent-Guided Ranking Policy Improvement for Peptide Drug Candidate Prioritization"
title_zh: 撤回：基于智能体引导的排序策略改进用于肽类药物候选物优先排序
authors: "Wijaya, E."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.19.719536v2.full.pdf"
tags: ["query:self-improve"]
score: 9.0
evidence: 智能体引导的排序策略改进，自我改进的智能体
tldr: "肽类药物研发需从数千个虚拟筛选候选物中挑选少量进行湿实验验证，面临活性、毒性、稳定性和可开发性等多目标约束。本文提出一种自动化策略搜索智能体，在冻结评估框架上学习排名策略，以替代手动加权求和。在包含3554个抗菌肽的公共基准测试中，智能体策略在top-20短名单中捕获65%的最佳候选，显著优于NSGA-II（44%）和等权标量化（61%）。该排名策略已开源，可作为即插即用的筛选层，支持替换内部库和实验评估。"
source: biorxiv
selection_source: fresh_fetch
motivation: 手动加权求和排名难以平衡多目标约束，需要自动化学习更优排名策略以提高候选物筛选效率。
method: 使用策略搜索智能体在冻结评估框架上学习排名策略，直接从打分候选池中优化排序。
result: "在3554个抗菌肽基准上，智能体策略在top-20短名单中捕获65%最佳候选，显著优于NSGA-II（44%）和等权标量化（61%）。"
conclusion: 自动化排名策略有效提升肽类药物候选物筛选效率，开源工具可灵活替换候选池和评估指标。
---

## 摘要
肽类药物项目的成败取决于优先级排序：在竞争性的活性、毒性、稳定性和可开发性约束下，从数千个计算机筛选命中中挑选出少数值得昂贵湿实验验证的候选物。我们探究了，在给定冻结的评估框架和已评分的候选池的情况下，自动化策略搜索智能体能否学习到比人类团队手动编写的加权和得分更好的排序策略。在包含3,554个抗菌肽的公开基准测试中，所有四个端点均被评分，智能体衍生的策略在其前20名候选名单中捕获了65%的最佳候选物，而NSGA-II为44%，等权重标量化和最佳1000次随机权重搜索均为61%（Wilcoxon符号秩检验p=0.004，基于10个独立数据分割）。我们报告的是一个公开抗菌基准测试，而非临床声明。代码、预测模型和排序策略作为即插即用的优先级排序层发布：候选池可以替换为内部肽库和内部检测数据。

## Abstract
Peptide drug programs live or die on triage: picking the handful of candidates worth expensive wet-lab validation from thousands of in silico hits, under competing activity, toxicity, stability, and developability constraints. We asked whether an automated policy-search agent, given a frozen evaluation harness and a scored candidate pool, could learn a better ranking policy than the weighted-sum score a human team would write by hand. Across a public benchmark of 3,554 antimicrobial peptides scored on all four endpoints, the agent-derived policy captures 65% of the best candidates in its top-20 shortlist, compared to 44% for NSGA-II and 61% for both equal-weight scalarization and best-of-1,000 random weight search (Wilcoxon signed-rank p = 0.004 across 10 independent data splits). We report on a public antimicrobial benchmark, not a clinical claim. The code, oracles, and ranking policy are released as a drop-in triage layer: the candidate pool can be swapped with an internal peptide library and in-house assays.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：在肽类药物研发中，从数千个虚拟筛选候选物中挑选少数值得进行昂贵湿实验验证的候选物时，面临活性、毒性、稳定性和可开发性等多目标约束，传统的手动加权求和排序策略难以平衡这些相互竞争的目标。
- **研究动机**：探索能否利用自动化策略搜索智能体，在给定冻结的评估框架和已评分的候选池条件下，学习到比人类手工编写的加权和得分更优的排序策略，从而提高候选物筛选效率。
- **整体含义**：该研究旨在提供一个即插即用的优先级排序层，将候选池替换为内部肽库和内部检测数据即可使用，从而加速肽类药物研发流程。

## 2. 论文提出的方法论
- **核心思想**：使用自动化策略搜索智能体，在冻结的评估框架上直接学习排序策略，而非手动设计加权和公式。
- **关键技术细节**：
  - 策略搜索智能体从一个已评分的候选池出发，学习一个排名策略（ranking policy），该策略定义如何将多个端点分数（如活性、毒性、稳定性、可开发性）组合成最终排序。
  - 智能体在冻结的评估框架（包括评分函数和候选池）上进行优化，不改变底层评估模型。
  - 训练过程中，智能体通过某种搜索算法（文中未明确具体算法类型，但暗示是策略搜索）迭代改进排序策略，以最大化在top-k（如top-20）候选名单中捕获最佳候选的比例。
- **算法流程（文字说明）**：
  1. 输入：已评分的候选池（每个候选拥有四个端点的分数）。
  2. 智能体从随机或初始权重开始，生成一个排名策略。
  3. 在训练数据分割上，应用该策略对候选池排序，计算top-20中包含的最佳候选比例（作为奖励信号）。
  4. 通过策略优化（如强化学习或进化算法）更新策略参数。
  5. 重复步骤2-4直到收敛或达到预算。
  6. 输出最终排名策略，可用于新候选池的排序。
- **公式**：未提供具体公式，仅描述为“策略搜索”和“加权和得分”的替代方案。

## 3. 实验设计
- **数据集**：公开抗菌肽基准，包含3,554个抗菌肽，所有四个端点（活性、毒性、稳定性、可开发性）均有评分。
- **Benchmark**：以top-20候选名单中捕获的最佳候选比例作为评估指标。
- **对比方法**：
  - 智能体衍生策略（Agent-derived policy）
  - NSGA-II（多目标进化优化算法）
  - 等权重标量化（Equal-weight scalarization）
  - 最佳1000次随机权重搜索（Best-of-1,000 random weight search）
- **实验设置**：基于10个独立数据分割（10 independent data splits）进行交叉验证，使用Wilcoxon符号秩检验比较显著性。

## 4. 资源与算力
- **文中未明确说明**：论文没有提及使用的GPU型号、数量、训练时长或其他计算资源细节。仅提到代码、预言机和排名策略已开源，但未提供硬件需求。

## 5. 实验数量与充分性
- **实验数量**：主要在单一基准数据集（3554个抗菌肽）上，基于10个独立数据分割进行对比实验。没有提及其他数据集或消融实验。
- **充分性与客观性**：
  - 优点：使用了10折交叉验证和统计显著性检验（Wilcoxon p=0.004），增加了结果可靠性。
  - 不足：仅在一个数据集上验证，缺乏跨不同肽库或不同任务（如非抗菌肽）的泛化实验；没有消融实验分析智能体策略的各个组件；对比方法中NSGA-II表现明显较差（44%），但未说明其参数调优是否充分。

## 6. 论文的主要结论与发现
- 智能体衍生策略在top-20候选名单中捕获65%的最佳候选，显著优于NSGA-II（44%）、等权重标量化（61%）和最佳随机权重搜索（61%），Wilcoxon符号秩检验p=0.004。
- 表明自动化策略搜索可以学习到比手动加权和更好的排序策略。
- 该排名策略已开源，可作为即插即用的筛选层，支持替换内部候选池和实验评估指标。
- **注意**：作者声明这只是一个公开抗菌肽基准测试，而非临床声明。

## 7. 优点
- **方法创新**：首次将策略搜索智能体应用于肽类药物候选物多目标排序，替代手工加权和方法。
- **实用性强**：开源代码、预测模型和排名策略，可作为即插即用工具，便于其他研究者改编使用。
- **评估严谨**：采用10折交叉验证和统计显著性检验，对比了多种基线方法（包括多目标优化算法和随机搜索）。
- **问题定义清晰**：明确将“前20名中捕获最佳候选的比例”作为关键指标，贴近实际研发场景。

## 8. 不足与局限
- **数据集单一**：仅在一个公开抗菌肽基准上验证，缺乏多样性和跨领域泛化实验，结果可能不适用于其他肽类项目。
- **对比方法调优不明**：NSGA-II表现显著差（44%），但未说明其参数是否经过调优；最佳随机权重搜索仅做了1000次，未探索更多尝试次数。
- **消融实验缺失**：未分析智能体策略不同组件（如奖励设计、探索策略）的贡献，无法判断哪些因素最关键。
- **计算资源未报告**：无法评估方法的实际训练成本或可复现性。
- **临床声明限制**：作者明确表示这不是临床声明，意味着结果距离实际应用仍有距离。
- **潜在偏差风险**：智能体策略可能过度拟合该特定基准数据集中的评分分布，当替换为内部库和内部检测数据时，性能可能下降。

（完）
