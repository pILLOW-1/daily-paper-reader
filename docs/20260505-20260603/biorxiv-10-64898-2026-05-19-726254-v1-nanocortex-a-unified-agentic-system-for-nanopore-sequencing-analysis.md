---
title: "NanoCortex: A Unified Agentic System for Nanopore Sequencing Analysis"
title_zh: NanoCortex：用于纳米孔测序分析的统一代理系统
authors: "Xia, Q., Wang, Z., Shokoufandeh, M., Rouhanifard, S. H., Wanunu, M."
date: 2026-05-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.19.726254v1.full.pdf"
tags: ["query:self-improve"]
score: 6.0
evidence: 具有迭代代码级自校正的多智能体纳米孔分析系统
tldr: 纳米孔测序工具分散，用户面临分析挑战。NanoCortex提出统一自主智能体框架，基于Gemini API和ADK实现多智能体协作，自动完成从原始信号碱基识别到生物学解释的端到端流程。系统可生成离线可用代码，并通过迭代自纠错提升分析可靠性。基准测试表明，其复杂任务可用性显著优于通用大语言模型，有效降低计算门槛，赋能生物学发现。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有纳米孔分析工具分散，用户难以整合多步骤流程，亟需统一自动化框架。
method: 基于Gemini API和ADK构建多智能体系统，自主执行任务解析、代码生成、迭代自纠错及科学解释。
result: 在复杂分析任务中，NanoCortex可用性显著高于通用大语言模型，代码可离线复用。
conclusion: NanoCortex无缝整合实验与公共数据库元分析，实现无繁琐计算的生物学解释。
---

## 摘要
纳米孔测序已经实现了关于DNA和RNA序列同种型及化学修饰的多个层次的信息。然而，零散的纳米孔分析工具群岛使得在它们之间导航对纳米孔用户来说是一个重大挑战。我们提出了NanoCortex，一个统一的自主代理框架，旨在通过提供从原始信号碱基识别到生物学解释的端到端数据处理来弥补这一不足。该系统基于Gemini API服务（产生基于使用的API成本）并通过Gemini代理开发工具包（ADK）编排，利用多代理架构自主执行任务解析、代码生成、代码级别的迭代自纠错以及科学解释。代码生成后，代码可离线使用。基准测试表明，与通用大型语言模型相比，NanoCortex在复杂分析任务上实现了显著更高的可用性。该框架将实验数据与公开可用的生物数据库的元分析无缝集成，有助于从测序数据中提取生物学上有意义的见解，而无需繁琐的计算步骤。

## Abstract
Nanopore sequencing has enabled various layers of information about DNA and RNA sequence isoforms and chemical modifications. Yet, the archipelago of disjoint nanopore analysis tools makes navigating among these a significant challenge for the nanopore user. We present NanoCortex, a unified autonomous agentic framework designed to bridge this shortcoming by providing end-to-end data processing which ranges from raw signal basecalling to biological interpretation. Built upon Gemini API services that incur usage-based API costs and orchestrated through the Gemini Agent Development Kit (ADK), the system utilizes a multi-agent architecture to autonomously perform task parsing, code generation, iterative code-level self-correction of code, and scientific interpretation. Following code generation, the code can be used offline. Benchmarking reveals that NanoCortex achieves significantly higher usability across complex analytical tasks compared to general-purpose large language models. The framework seamlessly integrates experimental data with meta-analysis of publicly available, biological databases to facilitate the extraction of biologically meaningful insights from sequencing data without cumbersome computational steps.