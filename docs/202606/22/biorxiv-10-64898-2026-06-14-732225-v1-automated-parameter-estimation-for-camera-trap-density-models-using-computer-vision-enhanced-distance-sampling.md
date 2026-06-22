---
title: Automated Parameter Estimation for Camera Trap Density Models Using Computer Vision-Enhanced Distance Sampling
title_zh: 基于计算机视觉增强的距抽样法自动化参数估计用于相机陷阱密度模型
authors: "McMurry, S., Alyetama, M., Goldstein, B., Kays, R."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.14.732225v1.full.pdf"
tags: ["query:agent-detect"]
score: 8.0
evidence: 计算机视觉增强的距离采样用于检测参数估计
tldr: 传统相机陷阱密度估计依赖人工测量四个参数（速度、活动、停留、检测距离），效率低下。本文提出计算机视觉管道，利用MegaDetector、SAM和DPT自动提取参数，并引入联合多物种层次距离函数。处理了12种动物的12.2万帧图像，自动速度估计为GPS数据的2.7-4.3倍，有效检测距离4.1-7.6米。该管道实现了大规模相机陷阱网络的可扩展自动化密度估计。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决传统人工测量参数费时费力的问题，实现相机陷阱密度估计的自动化。
method: 利用MegaDetector检测、SAM分割、DPT深度估计，从图像坐标重建轨迹提取速度、停留时间和活动水平，结合联合层次距离函数估计检测距离。
result: 处理181个部署的12.2万帧图像，对12个物种无需人工标注，自动速度估计范围2.7-4.3倍GPS数据，有效检测距离4.1-7.6米。
conclusion: 该管道支持大规模相机陷阱网络的无标注密度估计，具有可扩展性。
---

## 摘要
从相机陷阱估计动物密度的模型需要四个检测参数：移动速度、日常活动水平、停留时间（动物在检测区域内停留的持续时间）和有效检测距离。传统上，这些参数来自耗时的手动测量和辅助遥测。计算机视觉的最新进展可以提供相机陷阱图像中动物的位置，这些位置已用于距离采样。我们扩展了这种方法，从图像中提取所有四个参数，提供了首个基于自动坐标跟踪的AI估计的移动速度和停留时间。我们还引入了一个新的联合多物种分层距离函数，该函数估计部署特定的有效检测距离，同时通过部分池化跨物种借用强度。

我们的流程集成了MegaDetector用于动物检测、Segment Anything Model用于分割以及Dense Prediction Transformers用于单目深度估计。从帧级坐标出发，我们重建了爆发序列中的移动轨迹，以使用大小偏差分布校正估计速度，通过边界框插值计算停留时间，并根据检测时间戳估计活动水平。联合分层距离函数将检测尺度参数分解为共享的部署级效应和物种特定的偏移，因此物种效应表示与多物种平均值的偏差，使得数据丰富的物种能够为稀有物种观测很少的检测条件提供信息。AI衍生的场景深度作为检测范围的协变量进入模型，从同一流程中提供植被开放度指标。为了解决深度估计中的位置误差，我们应用了数据质量过滤器。

我们处理了来自华盛顿和蒙大拿州山地森林的181个部署的122,574帧图像，在没有手动标注的情况下生成了12个物种的参数估计。自动速度估计产生的日范围是GPS遥测衍生日距离的2.7至4.3倍，反映了检测区域内的遭遇速度与景观尺度位移之间的差异。部署级别的可检测性变异是物种级别差异的3:1，场景深度强烈预测检测范围；平均有效检测距离在4.1至7.6米之间。应用于随机遭遇模型，这些参数在蒙大拿州得出白尾鹿密度估计为每平方公里21.4只，而随机遭遇停留时间模型得出每平方公里11.6只。该流程能够在大规模相机陷阱网络中进行可扩展的密度估计。

## Abstract
Models for estimating animal density from camera traps require four parameters informing detection: movement speed, daily activity level, staying time (duration animals remain within the detection zone), and effective detection distance. These parameters traditionally come from labor-intensive manual measurements and auxiliary telemetry. Recent advances in computer vision can provide the positions of animals in camera trap images, which have been used for distance sampling. We extend this approach to extract all four parameters from imagery, providing the first AI-derived estimates of movement speed and staying time from automated coordinate tracking. We also introduce a new joint multi-species hierarchical distance function that estimates deployment-specific effective detection distances while borrowing strength across species through partial pooling.

Our pipeline integrates MegaDetector for animal detection, the Segment Anything Model for segmentation, and Dense Prediction Transformers for monocular depth estimation. From frame-level coordinates, we reconstruct movement trajectories across burst sequences to estimate speed with size-biased distribution corrections, calculate staying time through bounding box interpolation, and estimate activity levels from detection timestamps. The joint hierarchical distance function decomposes the detection scale parameter into a shared deployment-level effect and species-specific offsets, so species effects represent deviations from the multi-species average, allowing data-rich species to inform detection conditions where rare species have few observations. AI-derived scene depth enters the model as a covariate on detection range, providing a vegetation openness metric from the same pipeline. To address position errors from depth estimation, we apply data quality filters.

We processed 122,574 frames from 181 deployments across montane forests in Washington and Montana, generating parameter estimates for 12 species without manual annotation. Automated speed estimates produced day ranges 2.7 to 4.3 times GPS telemetry-derived daily distances, reflecting differences between encounter velocity within detection zones and landscape-scale displacement. Deployment-level variation in detectability exceeded species-level differences 3:1, with scene depth strongly predicting detection range; mean effective detection distances ranged from 4.1 to 7.6 m. Applied to a Random Encounter Model, these parameters yielded a white-tailed deer density estimate of 21.4 animals/km{superscript 2} and the Random Encounter Staying Time model yielded 11.6animals/km{superscript 2} in Montana. This pipeline enables scalable density estimation across large camera trap networks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：从相机陷阱（camera trap）估计动物密度需要四个检测参数：移动速度、日常活动水平、停留时间（动物在检测区域内停留的持续时间）和有效检测距离。传统上这些参数依赖耗时的人工测量和辅助遥测（如GPS项圈），限制了大规模相机陷阱网络的可扩展性。
- **整体含义**：本文旨在利用计算机视觉技术，从相机陷阱图像中自动提取所有四个参数，实现无人工标注的密度估计，从而推动大规模、自动化野生动物监测的发展。

## 2. 提出的方法论

- **核心思想**：通过集成多个计算机视觉模型，从单张图像获取动物位置（二维坐标和深度），进而重建运动轨迹，计算速度、停留时间和活动水平；同时引入联合多物种层次距离函数，估计部署特异的有效检测距离，并在物种间借用统计强度。
- **关键技术细节**：
  - **检测与分割**：使用 **MegaDetector** 检测动物，**Segment Anything Model (SAM)** 进行分割，以获取精确的边界框和轮廓。
  - **深度估计**：利用 **Dense Prediction Transformers (DPT)** 进行单目深度估计，得到场景深度作为检测范围的协变量（植被开放度指标）。
  - **轨迹重建**：从帧级坐标出发，通过爆发序列（burst sequences）中的边界框插值，重建移动轨迹，估计速度（使用大小偏差分布校正）、停留时间（通过边界框内插）和活动水平（基于检测时间戳）。
  - **联合分层距离函数**：将检测尺度参数分解为共享的部署级效应和物种特异性偏移。物种效应表示与多物种平均值的偏差，使得数据丰富的物种可以为稀有物种提供检测条件信息。
  - **数据质量过滤**：应用过滤器去除深度估计中的位置误差。
- **流程概述**：输入图像 → MegaDetector 检测动物 → SAM 分割 → DPT 深度估计 → 帧级坐标与边界框 → 轨迹重建 → 参数估计（速度/停留/活动） → 联合分层距离函数（含AI深度协变量） → 密度估计（随机遭遇模型REM或随机遭遇停留时间模型REST）。

## 3. 实验设计

- **数据集/场景**：
  - 来自华盛顿州和蒙大拿州的 **山地森林** 生态系统，共 **181个部署**（部署位置），处理了 **122,574帧** 图像。
  - 覆盖 **12个物种**（包括白尾鹿等），无需任何手动标注。
- **Benchmark与对比方法**：
  - **速度估计**：与其自动速度估计相比，使用GPS遥测衍生的日距离作为参考。发现自动速度估计产生的日范围是GPS数据的 **2.7~4.3倍**（解释为检测区域内遭遇速度与景观尺度位移的差异）。
  - **密度估计**：在蒙大拿州，使用随机遭遇模型（REM）得到白尾鹿密度 **21.4只/km²**，随机遭遇停留时间模型（REST）得到 **11.6只/km²**。未明确与人工标注方法直接对比，但展示了自动管道的可行结果。
- **对比方法**：未提及与其他自动化方法（如纯人工测量）的定量比较，主要是内部验证和参考GPS数据。

## 4. 资源与算力

- 论文未明确说明使用的GPU型号、数量或训练时长。
- 仅提及使用了 **MegaDetector、SAM、DPT** 等预训练模型进行推理，未报告训练新模型所需算力。
- 注意：管道中模型均为现成的预训练模型，推理阶段的计算开销取决于图像数量和部署规模。

## 5. 实验数量与充分性

- **实验数量**：
  - 单一数据集（181个部署、12.2万帧、12个物种）。
  - 开展了一次速度估计的对比（自动vs GPS），以及两种密度模型（REM与REST）的应用。
  - 没有列出多组消融实验（如不同深度估计方法、不同质量过滤阈值等）。
- **充分性评估**：
  - **优点**：覆盖多个物种和跨区域部署，展示了端到端自动化的可行性。
  - **不足**：缺乏与人工标注参数的严格基准对比（如人工测量速度、停留时间等）；仅一个区域（山地森林），生态代表性有限；未进行统计显著性检验或置信区间报告；未扰动系统参数进行敏感性分析。实验设计尚不能证明方法在不同生态系统中的泛化能力。

## 6. 主要结论与发现

- 管道成功处理12.2万帧图像，无需人工标注即生成12个物种的参数。
- 自动速度估计值高于GPS日距离（2.7~4.3倍），体现了检测区域内“遭遇速度”与长距离位移的区别。
- 部署级可检测性变异是物种级差异的 **3:1**，表明环境因素（如植被）对检测范围影响更大。
- 场景深度强烈预测检测范围；平均有效检测距离在 **4.1~7.6米** 之间。
- 在蒙大拿州，白尾鹿密度估计：REM模型 **21.4只/km²**，REST模型 **11.6只/km²**（未说明何者更可靠）。
- 该管道可扩展至大规模相机陷阱网络。

## 7. 优点

- **全自动化**：首次实现从图像中自动提取所有四个密度模型参数，避免人工测量和辅助遥测。
- **利用现成CV模型**：集成MegaDetector、SAM、DPT等先进模型，无需训练新网络，降低复现门槛。
- **联合多物种层次模型**：通过部分池化跨物种借用强度，数据丰富的物种可帮助稀有物种，提升检测距离估计的稳健性。
- **场景深度作为协变量**：从同一管道获得植被开放度指标，无需额外现场测量。
- **数据质量过滤**：处理深度估计误差，提升参数可靠性。

## 8. 不足与局限

- **速度估计偏差**：自动速度估计明显高于GPS数据，但未解释是否真实反映动物在检测区域的运动（可能受帧率、轨迹重建质量影响），也缺乏地面真值验证。
- **缺乏人工标注基准**：未与手动测量的速度、停留时间、活动水平直接对比，难以评估参数绝对准确性。
- **实验覆盖有限**：仅山地森林生态系统、12种哺乳动物，未验证在其他生境（如草原、雨林）或更多物种（如鸟类）的适用性。
- **深度估计误差**：单目深度估计本身存在歧义，质量过滤器可能丢弃有效数据，影响样本量。
- **密度模型未验证**：给出的两个密度估计值差异较大（21.4 vs 11.6），未提供独立参考（如标记-重捕）来评判准确性。
- **未报告不确定性**：缺乏置信区间或后验分布，无法判断估计精度。
- **算力信息缺失**：无法评估实际运行成本。

（完）
