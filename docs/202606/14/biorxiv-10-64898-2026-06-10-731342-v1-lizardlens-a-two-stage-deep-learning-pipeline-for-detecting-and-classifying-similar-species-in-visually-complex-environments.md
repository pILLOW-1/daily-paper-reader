---
title: "LizardLens: A Two-Stage Deep Learning Pipeline for Detecting and Classifying Similar Species in Visually Complex Environments"
title_zh: "LizardLens: 一种用于在视觉复杂环境中检测和分类相似物种的两阶段深度学习管线"
authors: "Chia, W. H., Jahanshahi, I., Loh, L. Y., Zheng, A., Verma, N., Mussman, S., Shi, B., Stroud, J. T."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.10.731342v1.full.pdf"
tags: ["query:agent-detect"]
score: 7.0
evidence: 两阶段深度学习流水线，用于在复杂视觉环境中检测和分类相似物种
tldr: "社区科学平台iNaturalist产生大量生物多样性数据，但非专家用户常导致物种识别错误。本文提出LizardLens，一种两阶段深度学习流水线，将YOLO目标检测与Swin Transformer细粒度分类解耦，用于佛罗里达五种相似Anolis蜥蜴的识别。在10000张图片上，该方法达到83.0% Top-1准确率和89.0%宏平均F1，优于YOLOv8和YOLOv12单阶段模型。Grad-CAM分析显示模型关注与专家诊断一致的特征。该工作以web应用形式部署，直接支持社区科学项目，为复杂环境中微小生物的识别提供了可泛化框架。"
source: biorxiv
selection_source: fresh_fetch
motivation: 社区科学数据因非专家参与存在物种误识别问题，急需自动方法提升数据质量。
method: 两阶段流水线：YOLO检测器定位蜥蜴，Swin Transformer分类器进行物种细分类。
result: "在五物种任务上达83.0% Top-1准确率、89.0%宏平均F1，比单阶段模型提升10.5-13.2%。"
conclusion: 两阶段架构有效处理相似物种，可部署为交互式web应用，提升社区科学数据质量并支持教育。
---

## 摘要
像iNaturalist这样的社区科学平台产生了前所未有的生物多样性数据量，但其科学效用关键依赖于准确的物种鉴定；当贡献者通常缺乏分类学专业知识时，这一挑战持续存在。我们开发了LizardLens，这是一个两阶段机器学习管线，将目标检测与物种分类解耦，从而能够对视觉复杂的野外照片中形态相似的生物进行细粒度识别。使用佛罗里达州五种安乐蜥属蜥蜴的10,000张经过验证的iNaturalist图像，我们训练了基于YOLO的专用检测模型和Swin Transformer分类模型，并与最先进的单阶段架构进行了性能比较。我们的两阶段管线达到了83.0%的Top-1准确率和89.0%的宏观平均F1分数，表明在所有物种上具有强大的精确率-召回率性能，并且在所有评估指标上均优于单阶段YOLOv8和YOLOv12模型，相对改进幅度从10.5%到13.2%不等。梯度加权类激活映射（Grad-CAM）表明，模型的预测始终与对应于诊断性形态（如头型、脚和四肢长度）和图案特征（如眼环和身体图案）的区域相关联，提供了LizardLens利用与专家分类学家所使用的生物相关视觉线索一致的证据。误差分析确定了部分遮挡和多个邻近个体是漏检的主要来源，而对蜥蜴状环境特征（如棍棒、树皮）的虚假检测则是主要的假阳性错误模式。我们将LizardLens部署为一个可访问的Web应用程序，具有交互式边界框校正、带有置信度分数的排名物种预测，直接支持“蜥蜴在野外”中学社区科学倡议。通过将细粒度视觉分类的技术进步与以用户为中心的设计相结合，LizardLens展示了机器学习如何同时提高生物多样性监测的数据质量，并为学生参与者提供真实的科学体验。我们的方法可推广到复杂栖息地中的其他小型生物，并为将计算机视觉进展转化为社区科学和保护的实际工具提供了框架。

## Abstract
Community science platforms like iNaturalist generate unprecedented volumes of biodiversity data, but their scientific utility depends critically on accurate species identification; a persistent challenge when contributors often lack taxonomic expertise. We developed LizardLens, a two-stage machine learning pipeline that decouples object detection from species classification to enable fine-grained identification of morphologically similar organisms in visually complex field photographs. Using 10,000 verified iNaturalist images of five Anolis lizard species in Florida, we trained specialized YOLO-based detection and Swin Transformer classification models and compared performance against state-of-the-art single-stage architectures. Our two-stage pipeline achieved 83.0% Top-1 accuracy and a macro-averaged F1-score of 89.0%, indicating strong precision-recall performance across species and outperforming single-stage YOLOv8 and YOLOv12 models across all evaluation metrics for all species, with relative improvements ranging from 10.5% to 13.2%. Gradient-weighted Class Activation Mapping (Grad-CAM) indicated that the models predictions were consistently associated with regions corresponding to diagnostic morphological (e.g., head shape, feet, and limb lengths) and pattern features (e.g., ocular rings and body patterning), providing evidence that LizardLens leverages biologically relevant visual cues consistent with those used by expert taxonomists. Error analysis identified partial occlusion and multiple proximate individuals as primary sources of missed detections, while spurious detections of lizard-like environmental features (e.g., sticks, bark) represented the dominant false positive error mode. We deployed LizardLens as an accessible web application featuring interactive bounding box correction, ranked species predictions with confidence scores, directly supporting the Lizards on the Loose middle school community science initiative. By combining technical advances in fine-grained visual classification with user-centered design, LizardLens demonstrates how machine learning can simultaneously enhance data quality for biodiversity monitoring and provide authentic scientific experiences for student participants. Our approach is generalizable to other small-bodied organisms in complex habitats and provides a framework for translating computer vision advances into practical tools for community science and conservation.