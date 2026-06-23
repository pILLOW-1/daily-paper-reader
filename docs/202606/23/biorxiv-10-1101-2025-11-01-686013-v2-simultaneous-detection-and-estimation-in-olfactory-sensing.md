---
title: Simultaneous detection and estimation in olfactory sensing
title_zh: 嗅觉感知中的同时检测与估计
authors: "Jiang, C., He, M. Y., Murthy, V. N., Pehlevan, C., Zavatone-Veth, J. A., Masset, P."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.1101/2025.11.01.686013v2.full.pdf"
tags: ["query:agent-detect"]
score: 6.0
evidence: 基于压缩感知的嗅觉检测模型，受SLAM启发
tldr: 哺乳动物嗅觉系统能高效解码气味身份和浓度，但现有压缩感知模型局限于检测少量气味。本文借鉴同步定位与建图(SLAM)思想，分离推断气味存在性和浓度，通过镜像Langevin动力学实现生物合理的循环电路。该模型能在大规模场景中准确推断，其电路结构可映射至嗅球主要细胞类型，解释了僧帽细胞与簇状细胞的功能差异。工作为神经概率推理提供了通用算法框架，且预测可实验验证。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有嗅觉压缩感知模型无法处理自然场景的复杂性，只能检测少数气味。
method: 基于SLAM思想分离推断存在性与浓度，引入镜像Langevin动力学实现循环电路。
result: 模型能准确大规模推断，电路映射至嗅球细胞类型，解释功能差异。
conclusion: 提出可实验验证的神经概率推理算法，为嗅觉及更广领域提供框架。
---

## 摘要
哺乳动物的嗅觉系统展现出快速准确解码气味剂身份和浓度的卓越能力。先前的研究利用压缩感知理论阐明了这一能力的算法基础：由于任何特定感官场景中仅存在少数相关气味剂，因此从有限受体库的反应中解码气味信息是可行的。然而，现有的嗅觉解码电路模型仍难以应对自然嗅觉场景的复杂性；它们仅限于检测少量气味剂。在此，我们提出了一种受导航中同时定位与地图构建算法启发的嗅觉压缩感知模型，其中分别推断存在的气味集及其浓度。我们通过引入与存在和浓度不同性质相匹配的独立动力学，并借鉴镜像朗之万动力学框架，在生物合理的循环电路中实现了这种分离推断。该模型能够大规模准确推断存在和浓度。此外，其电路结构可映射到嗅球的主要细胞类型上，为僧帽细胞和丛状细胞之间的功能差异提供了可能的规范性解释。我们的方法为概率推理的电路算法提供了一条通用路径——在嗅觉感知及其他领域——该算法既能在自然环境中表现良好，又能为神经响应动力学做出可实验检验的预测。

## Abstract
The mammalian olfactory system shows an exceptional ability for rapid and accurate decoding of both the identity and concentration of odorants. Previous works have used the theory of compressed sensing to elucidate the algorithmic basis for this capability: decoding odor information from the responses of a restricted repertoire of receptors is possible because only a few relevant odorants are present in any given sensory scene. However, existing circuit models for olfactory decoding still cannot contend with the complexity of naturalistic olfactory scenes; they are limited to detection of a handful of odorants. Here, we propose a model for olfactory compressed sensing inspired by simultaneous localization and mapping algorithms in navigation, in which the set of present odors and their concentrations are inferred separately. We implement this split inference in a biologically-plausible recurrent circuit by introducing separate dynamics matched to the distinct nature of presence and concentration, and drawing on the framework of Mirrored Langevin Dynamics. This model can accurately infer presence and concentration at scale. Moreover, its circuit structure can be mapped onto the primary cell types of the olfactory bulb, giving a possible normative account for functional differences between mitral and tufted cells. Our approach offers a general path towards circuit algorithms for probabilistic inference--in olfactory sensing and beyond--that both perform well in naturalistic environments and make experimentally-testable predictions for neural response dynamics.