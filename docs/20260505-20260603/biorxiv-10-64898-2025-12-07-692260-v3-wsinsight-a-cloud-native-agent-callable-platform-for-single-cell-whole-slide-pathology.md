---
title: "WSInsight: a cloud-native, agent-callable platform for single-cell whole-slide pathology"
title_zh: WSInsight：一个云原生、可被智能体调用的单细胞全玻片病理学平台
authors: "Huang, C. H., Awosika, O. E., Fernandez, D."
date: 2026-05-17
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.07.692260v3.full.pdf"
tags: ["query:agent-detect"]
score: 6.0
evidence: 可被智能体调用的病理图像检测平台
tldr: "全切片病理分析面临计算效率低和可重复性差的挑战。WSInsight是一个云原生开源平台，支持队列规模H&E全切片图像分析，通过补丁级推理实现单细胞分割和表型分类，并使用形态学和转录组监督的细胞类型头进行可重训练。它从云存储读取切片，将结果输出至QuPath和OMERO，同时通过MCP端点可被AI代理调用。在TCGA队列上应用，成功恢复了已知的免疫和分子关联，展示了其在数字病理学中的实用性和可扩展性。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有全切片病理分析工具难以处理队列规模数据，且缺乏与云存储和AI代理的集成，限制了可重复性和自动化。
method: 提出云原生平台WSInsight，执行补丁级推理结合单细胞分割和表型分类，细胞类型头可基于公共数据重训练，通过MCP支持AI代理调用。
result: 在TCGA队列上应用，准确恢复了已知的免疫细胞浸润模式和分子亚型关联，验证了平台的生物有效性。
conclusion: WSInsight通过云原生架构和AI代理接口，实现了可扩展、可重复的全切片分析，为计算病理学提供了新的基础设施。
---

## 摘要
WSInsight是一个用于队列规模H&E全玻片图像分析的开源平台。它执行补丁级推断以及单细胞分割和表型分类，具有形态学和转录组监督的细胞类型头部，可从公共数据重新训练。玻片从云端存储库读取，每张玻片的输出写入QuPath和OMERO。同一工作流通过模型上下文协议端点可被AI智能体调用。将其应用于TCGA队列恢复了已知的免疫和分子关联。

## Abstract
WSInsight is an open-source platform for cohort-scale H&E whole-slide image analysis. It performs patch-level inference together with single-cell segmentation and phenotype classification, with morphology- and transcriptome-supervised cell-type heads retrainable from public data. Slides are read from cloud repositories and per-slide outputs are written to QuPath and OMERO. The same workflow is AI-agent callable through a Model Context Protocol endpoint. Applying it to TCGA cohorts recovered known immune and molecular associations.