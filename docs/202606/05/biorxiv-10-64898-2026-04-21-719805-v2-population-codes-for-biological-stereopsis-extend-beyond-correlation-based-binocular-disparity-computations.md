---
title: Population codes for biological stereopsis extend beyond correlation-based binocular disparity computations
title_zh: 生物立体视觉的群体编码超越基于相关的双眼视差计算
authors: "Wundari, B. G., Fujita, I., Ban, H."
date: 2026-05-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.21.719805v2.full.pdf"
tags: ["query:agent-detect"]
score: 6.0
evidence: 立体视觉群体编码研究，与感知检测相关
tldr: 尽管基于相关的双眼差异模型能解释初级视皮层单个神经元响应，但其群体表征是否支撑深度感知尚不明确。本文通过心理物理、fMRI和神经网络建模，使用动态反相关刺激发现：人类可靠感知反转深度，但群体表征在V3A而非V1检测到。分析神经网络内部表征显示，受限于相关计算的模型产生更大表征重叠，而未显式约束相关交互的深度网络表征更分离且更符合人类行为。结果表明生物立体视觉可能依赖超越相关计算的群体编码。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究基于相关的双眼差异局部计算在群体水平能否支撑深度感知，特别是面对模糊输入时。
method: 结合心理物理实验、fMRI脑成像和神经网络建模，使用动态反相关刺激测试人类立体视觉。
result: 人类感知反转深度，群体表征在V3A而非V1与感知一致；未受限于相关计算的深度网络表征更分离且更拟合人类行为。
conclusion: 生物立体视觉可能依赖超越相关计算的群体编码机制，而非简单的局部相关运算。
---

## 摘要
双眼立体视觉依赖于比较两只眼睛所看到的图像。尽管基于相关的模型可以解释初级视觉皮层（V1）中单个双眼神经元的反应，但由局部相关活动模式形成的群体表征是否能在模糊输入下支持深度感知，仍然难以确定。通过心理物理学、fMRI和神经网络建模，我们测试了人类对动态反相关刺激（主要由双眼不匹配主导）的立体视觉。人类可靠地感知到了由基于相关计算预测的反转深度，但在V3A（而非V1）中检测到了与这种感知一致的群体表征。受限于类似相关的双眼相互作用的浅层和深层神经网络未能捕捉人类深度判断的完整模式。对其内部表征的分析显示，这些网络具有更大的表征重叠，而不受显式相关相互作用约束的深层架构则表现出更少纠缠的表征，并且与人类行为更一致。这些发现表明，生物立体视觉可能依赖于超越类似相关计算的群体编码。

意义声明：大脑必须从本质上模糊的双眼输入中推断深度。尽管基于相关的模型可以解释初级视觉皮层（V1）中单个神经元的视差调谐，但这些局部机制是否在群体水平上支持感知推断仍不清楚。通过心理物理学、fMRI和神经网络建模，我们发现在中背侧区域V3A（而非V1）中检测到了与模糊条件下感知深度一致的群体表征。对神经网络如何编码多个特征的分析表明，基于相关的计算将特征表征为重叠的活动模式，这可能限制下游读出并降低深度估计。相比之下，不受显式眼间相关约束的模型保持了更独特的群体编码，并与人类感知高度匹配。这些发现表明，受限于显式类似相关处理的架构可以形成群体表征，但这种表征在解释人类立体视觉方面是次优的，从而促使混合机制的发展。

## Abstract
Binocular stereopsis depends on comparing the images seen by the two eyes. Although correlation-based models explain responses of individual binocular neurons in primary visual cortex (V1), it remains elusive whether population representations formed by local correlation activity patterns can support depth perception under ambiguous inputs. Using psychophysics, fMRI, and neural network modeling, we tested human stereopsis with dynamic anticorrelated stimuli that were dominated by binocular mismatches. Humans reliably perceived reversed depth as predicted by correlation-based computations, yet population representations consistent with this percept were detected in V3A, not V1. Shallow and deep neural networks constrained by correlation-like binocular interactions did not capture the full pattern of human depth judgments. Analyses of their internal representations showed greater representational overlap, whereas deep architectures not constrained to explicit correlation interactions exhibited less entangled representations and better aligned with human behavior. These findings suggest that biological stereopsis may rely on population coding beyond correlation-like computations.

Significance StatementThe brain must infer depth from binocular inputs that are inherently ambiguous. Although correlation-based models explain disparity tuning of individual neurons in primary visual cortex (V1), whether these local mechanisms support perceptual inference at the population level remains unclear. Using psychophysics, fMRI, and neural network modeling, we show that population representations consistent with perceived depth under ambiguity were detected in mid-dorsal area V3A, not V1. Analyses of how neural networks encode multiple features showed that correlation-based computations represent features into overlapping activity patterns that may constrain downstream readout and degrade depth estimates. In contrast, models not constrained by explicit interocular correlation maintained more distinct population codes and closely matched human perception. These findings suggest that architectures constrained to explicit correlation-like processing can form population representations that are suboptimal to explain human stereopsis, motivating hybrid mechanisms.