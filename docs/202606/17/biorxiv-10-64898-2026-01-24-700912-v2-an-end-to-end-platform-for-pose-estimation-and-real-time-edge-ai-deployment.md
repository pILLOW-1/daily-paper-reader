---
title: An end-to-end platform for pose estimation and real-time edge-AI deployment
title_zh: 一个用于姿态估计和实时边缘AI部署的端到端平台
authors: "Haggerty, D. L., Darden, C. B., Lovinger, D. M."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.01.24.700912v2.full.pdf"
tags: ["query:agent-detect"]
score: 7.0
evidence: 面向智能体姿态估计的检测技术平台
tldr: 现有姿态估计工具依赖离线工作流、工作站GPU和外部中间件，难以在边缘设备实时部署。本文提出集成软硬件生态系统，包括SqueakPose Studio（数据集创建、训练与推理）、SqueakView（实时部署）和MouseHouse（模块化笼盒）。平台利用现代目标检测架构实现端到端训练和推理，无需patch采样或多阶段后处理，支持CPU、GPU和Apple Silicon。统一数据格式和确定定时架构确保离线分析与实时实验的一致性，无需工作站硬件或外部中间件。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有姿态估计工具依赖离线工作流和碎片化软件管道，难以在边缘设备实时部署。
method: 构建包括SqueakPose Studio、SqueakView和MouseHouse的集成软硬件平台，利用现代目标检测架构实现端到端训练和推理，统一数据格式与定时架构。
result: 平台支持CPU/GPU/Apple Silicon，无需patch采样或多阶段后处理，实现离线分析和嵌入式实时实验的一致性。
conclusion: 提供了无需工作站硬件或外部中间件的统一姿态估计平台，适用于离线分析和实时边缘AI部署。
---

## 摘要
精确的姿态估计支撑着行为的定量分析，然而许多基于深度学习的追踪工具仍然针对离线工作流程优化，这些工作流程依赖于碎片化的软件管线、工作站级GPU或外部中间件来实现实时部署。这里我们提出了一个用于姿态估计的集成软件-硬件生态系统，涵盖数据集创建、模型训练、离线分析以及在嵌入式边缘计算设备上的实时部署。SqueakPose Studio提供了一个用于基于深度学习的全帧姿态估计的软件套件，统一了数据集创建、手动和模型辅助标注、模型训练、验证以及大规模离线推理。该系统利用现代目标检测架构，无需基于块的采样或多阶段后处理即可实现高效的端到端训练和推理，并支持在CPU、GPU和Apple Silicon上执行。对于需要连续记录和同步数据采集的实验设置，SqueakView能够在嵌入式边缘计算硬件上实现实时模型部署、视频捕获和传感器记录，而MouseHouse提供了一个专为基于家庭笼的实验设计的紧凑模块化外壳，集成了嵌入式GPU计算、基于微控制器的定时和外围I/O。共享的数据格式和确定性时序架构确保了离线分析和实时部署之间的一致性。总之，SqueakPose Studio、SqueakView和MouseHouse为姿态估计提供了一个统一的平台，既支持传统的离线分析，也支持嵌入式实时实验，无需依赖工作站级硬件或外部中间件。

## Abstract
Accurate pose estimation underpins quantitative analysis of behavior, yet many deep learning-based tracking tools remain optimized for offline workflows that rely on fragmented software pipelines, workstation-grade GPUs, or external middleware to enable real-time deployment. Here we present an integrated software-hardware ecosystem for pose estimation that spans dataset creation, model training, offline analysis, and real-time deployment on embedded edge-computing devices. SqueakPose Studio provides a software suite for whole-frame, deep learning-based pose estimation that unifies dataset creation, manual and model-assisted labeling, model training, validation, and large-scale offline inference. The system leverages modern object-detection architectures to enable efficient end-to-end training and inference without patch-based sampling or multi-stage postprocessing, and supports execution on CPUs, GPUs, and Apple Silicon. For experimental settings requiring continuous recording and synchronized data acquisition, SqueakView enables real-time model deployment, video capture, and sensor logging on embedded edge-computing hardware, while MouseHouse provides a compact, modular enclosure designed for home cage-based experiments that integrates embedded GPU compute, microcontroller-based timing, and peripheral I/O. A shared data format and deterministic timing architecture ensure consistency across offline analysis and real-time deployment. Together, SqueakPose Studio, SqueakView, and MouseHouse provide a unified platform for pose estimation that supports both conventional offline analysis and embedded, real-time experimentation, without reliance on workstation-grade hardware or external middleware.