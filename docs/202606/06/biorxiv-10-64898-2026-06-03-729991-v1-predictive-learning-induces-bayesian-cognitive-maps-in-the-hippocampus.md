---
title: Predictive learning induces Bayesian cognitive maps in the hippocampus
title_zh: 预测学习诱导海马体中的贝叶斯认知地图
authors: "Kim, Y., Kang, Y. H."
date: 2026-06-05
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729991v1.full.pdf"
tags: ["query:agent-detect"]
score: 7.0
evidence: 通过贝叶斯推理进行世界模型中的感知与检测
tldr: 经典空间表征模型忽视感知不确定性，假设位置直接可观测。本文引入贝叶斯理想观察者，发现其对位置的信念更准确复现位置细胞活动特性。通过预测下一时刻自我中心输入的循环神经网络，学习到类似贝叶斯信念的表征，在熟悉与陌生环境均产生位置细胞样活动。结果表明海马回路可能通过预测性学习从经验中构建贝叶斯认知地图。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型认为异我中心位置可直接观测，忽略感知不确定性，无法解释位置细胞特性。
method: 对比经典模型与贝叶斯理想观察者；训练RNN预测下一时刻自我中心输入。
result: 贝叶斯信念准确复现位置野宽度、面积和密度；RNN性能优于自编码器。
conclusion: 海马可能通过预测性感知学习构建贝叶斯认知地图。
---

## 摘要
导航需要感知：位置必须从嘈杂和模糊的自我中心感觉输入中推断出来，如同在距离的视觉估计中一样。然而，许多经典的空间表征模型隐含地假设异中心位置是直接可观察的，从而忽略了感知不确定性。在这里，我们将这种模型与明确包含感知推断的贝叶斯理想观察者进行比较。我们发现，贝叶斯观察者对位置的信念更准确地再现了位置细胞活动的关键属性，包括位置场宽度、面积和密度，无论是在环境内部还是跨环境。通过解析论证和数值模拟，我们表明，被训练预测下一个自我中心感觉输入的循环神经网络学习到的表征类似于贝叶斯信念，并在熟悉和不熟悉的环境中产生类似位置细胞的活动，优于被训练再现当前输入的自编码器。总之，这些结果表明，海马回路可能通过预测性的感知学习从经验中构建贝叶斯认知地图。

## Abstract
Navigation requires perception: location must be inferred from noisy and ambiguous egocentric sensory inputs, as in visual estimation of distance. However, many classical models of spatial representation implicitly assume that allocentric location is directly observable, thereby neglecting perceptual uncertainty. Here, we compare such a model with a Bayesian ideal observer that explicitly incorporates perceptual inference. We find that the Bayesian observer's beliefs over location more accurately reproduce key properties of place cell activity, including place field width, area, and density, within and across environments. Using analytic arguments and numerical simulations, we show that recurrent neural networks trained to predict the next egocentric sensory input learn representations resembling Bayesian beliefs and yield place cell-like activity in both familiar and unfamiliar environments, outperforming autoencoders trained to reproduce the current input. Together, these results suggest that hippocampal circuits may construct Bayesian cognitive maps from experience through predictive perceptual learning.