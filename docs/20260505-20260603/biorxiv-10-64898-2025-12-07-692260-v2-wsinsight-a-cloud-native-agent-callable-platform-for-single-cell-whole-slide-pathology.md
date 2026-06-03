---
title: "WSInsight: a cloud-native, agent-callable platform for single-cell whole-slide pathology"
title_zh: WSInsight：一个云原生、可被智能体调用的全切片病理单细胞分析平台
authors: "Huang, C. H., Awosika, O. E., Fernandez, D."
date: 2026-05-10
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.07.692260v2.full.pdf"
tags: ["query:agent-detect"]
score: 6.0
evidence: 病理学中具有单细胞检测和分类的AI代理可调用平台
tldr: "针对大规模H&E全切片图像分析需求，WSInsight作为云原生开源平台，实现patch级推理与单细胞分割、表型分类。它利用可重训练的形态学与转录组监督细胞类型头，从云存储读取切片并输出至QuPath/OMERO。通过MCP接口支持AI代理调用，在TCGA队列中成功复现已知免疫与分子关联。该平台解决了现有工具可扩展性差和自动化程度低的问题，为计算病理学提供了高效、可复用的基础设施。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有病理图像分析平台缺乏云原生架构及AI代理调用能力，难以处理大规模单细胞解析。
method: 平台集成patch级推理与单细胞分割，支持可重训练的细胞类型头，基于云仓库数据读写并开放MCP接口。
result: 在TCGA队列上成功复现已知的免疫细胞浸润与分子亚型关联。
conclusion: WSInsight为大规模病理组学提供云原生、可代理调用的高效解决方案，促进可重复研究。
---

## 摘要
WSInsight是一个开源平台，用于队列规模的H&E全切片图像分析。它结合了斑块级推理、单细胞分割和表型分类，具有形态学和转录组监督的细胞类型头部，可从公开数据重新训练。切片从云存储库读取，每张切片的输出写入QuPath和OMERO。同一工作流可通过模型上下文协议端点被AI智能体调用。将其应用于TCGA队列，恢复了已知的免疫和分子关联。

## Abstract
WSInsight is an open-source platform for cohort-scale H&E whole-slide image analysis. It performs patch-level inference together with single-cell segmentation and phenotype classification, with morphology- and transcriptome-supervised cell-type heads retrainable from public data. Slides are read from cloud repositories and per-slide outputs are written to QuPath and OMERO. The same workflow is AI-agent callable through a Model Context Protocol endpoint. Applying it to TCGA cohorts recovered known immune and molecular associations.