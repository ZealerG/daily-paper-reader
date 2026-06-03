---
title: Network Sparsity Unlocks the Scaling Potential of Deep Reinforcement Learning
title_zh: 网络稀疏性释放深度强化学习的扩展潜力
authors: "Guozheng Ma, Lu Li, Zilin Wang, Li Shen, Pierre-Luc Bacon, Dacheng Tao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=mIomqOskaa"
tags: ["query:graph-part"]
score: 7.0
evidence: 通过静态网络稀疏性改进DRL扩展
tldr: 该论文发现深度强化学习在扩展时面临训练困难，现有方法依赖复杂改进。作者提出在训练前对网络进行一次随机剪枝，引入静态稀疏性，即可使稀疏网络在参数效率和性能上超越密集网络，且无需额外复杂设计。实验表明稀疏结构有效解锁了扩展潜力，为DRL规模化提供了简洁高效的方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 927, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1635, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1684, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 848, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1755, \"height\": 934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 845, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 854, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 846, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 852, \"height\": 245, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 858, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 854, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 861, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 853, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1766, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1717, \"height\": 1937, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1715, \"height\": 1930, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1766, \"height\": 960, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-miomqoskaa/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1759, \"height\": 1508, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-miomqoskaa/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 824, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-miomqoskaa/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1045, \"height\": 920, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-miomqoskaa/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1039, \"height\": 831, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-miomqoskaa/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 973, \"height\": 853, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-miomqoskaa/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1068, \"height\": 1094, \"label\": \"Table\"}]"
motivation: 解决深度强化学习模型在规模化扩展时因网络病理导致的训练困难。
method: 提出在训练前对网络进行一次随机剪枝，引入静态稀疏性，不改变其他训练流程。
result: 稀疏网络在参数效率和性能上均超过最佳密集网络，验证了静态稀疏性对扩展的促进作用。
conclusion: 简单的随机剪枝即可有效释放深度强化学习模型的扩展潜力，是一种高效低成本的改进方案。
---

## Abstract
Effectively scaling up deep reinforcement learning models has proven notoriously difficult due to network pathologies during training,  motivating various targeted interventions such as periodic reset and architectural advances such as layer normalization. Instead of pursuing more complex modifications, we show that introducing static network sparsity alone can unlock further scaling potential beyond their dense counterparts with state-of-the-art architectures. This is achieved through simple one-shot random pruning, where a predetermined percentage of network weights are randomly removed once before training. Our analysis reveals that, in contrast to naively scaling up dense DRL networks, such sparse networks achieve both higher parameter efficiency for network expressivity and stronger resistance to optimization challenges like plasticity loss and gradient interference. We further extend our evaluation to visual and streaming RL scenarios, demonstrating the consistent benefits of network sparsity.

---

## 论文详细总结（自动生成）

# 论文总结：网络稀疏性释放深度强化学习的扩展潜力

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：深度强化学习（DRL）在模型规模扩大时面临严重的优化病理现象（如塑性损失、容量坍塌、梯度干扰等），导致性能不升反降，这与监督学习中“更大模型更好”的规律相悖。现有方法（如周期性重置网络、层归一化、残差连接等）虽有一定改善，但复杂的干预措施带来训练不稳定和计算开销，且当前最先进的SimBa架构在扩大规模后仍出现性能退化。
- **核心问题**：能否仅通过静态网络稀疏性（static network sparsity）——即简单的一次性随机剪枝——来进一步解锁DRL模型的扩展潜力，同时预防优化病理？
- **整体含义**：论文表明，在训练前对网络进行一次随机剪枝（固定稀疏拓扑），即可使稀疏网络在参数效率和抗优化病理方面显著超越其密集对应物，为DRL规模化提供了一种极简且有效的基线方案。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：在训练开始前，对网络各层进行一次随机剪枝，生成二进制掩码并在整个训练过程中固定不变（静态稀疏训练，SST）。该方法不依赖拓扑动态调整或针对性剪枝，仅通过引入权重级别的稀疏性来改善网络容量和优化动态。
- **关键技术细节**：
  - **随机剪枝**：对每个全连接层或卷积层，随机生成二进制掩码 $M_l \in \{0,1\}^{n_l \times n_{l-1}}$，有效权重为 $W_l^{\text{eff}} = M_l \odot W_l$。
  - **层间稀疏率分配**：采用Erdős–Rényi（ER）策略，根据层尺寸自适应分配稀疏率，而非均匀分配。对于全连接层，稀疏率 $s_l = 1 - (n_{l-1}+n_l)/(n_{l-1}n_l)$；对于卷积层，考虑核尺寸。
  - **无需改变优化算法或架构**：在SimBa等先进架构基础上直接应用稀疏掩码，不修改任何超参数或训练流程。
- **公式/算法流程（文字说明）**：
  1. 确定全局稀疏率 $S$（如0.8）。
  2. 根据ER规则计算每层稀疏率 $s_l$。
  3. 在初始化阶段，对每层权重随机生成掩码，固定该稀疏拓扑。
  4. 使用标准RL算法（SAC/DDPG）进行训练，训练和推理时仅计算未掩码的权重。

## 3. 实验设计：数据集/场景、benchmark、对比方法
- **数据集/场景**：
  - **主要实验**：DeepMind Control Suite（DMC）中的6个高难度连续控制任务（Humanoid Walk/Run/Stand, Dog Walk/Trot/Run），统称为DMC Hard。
  - **扩展场景**：
    - 视觉RL：基于图像输入的DMC任务（Quadruped Run, Hopper Hop），使用DrQ-v2算法。
    - 流式RL：MuJoCo的Ant-v4和Walker2d-v4，使用Stream AC(λ)算法。
    - 离散动作空间：Atari-100k基准，使用Data Efficient Rainbow（DER）算法。
- **Benchmark**：以SimBa架构为基线（默认大小约4.5M参数），对比增大模型尺寸（宽度/深度缩放）后的密集网络与稀疏网络。
- **对比方法**：
  - 密集网络（无稀疏性）在不同宽度/深度缩放下的表现。
  - 稀疏网络（固定稀疏率）在不同宽度/深度缩放下的表现。
  - 消融实验：改变稀疏率（0.1~0.9）与模型尺寸的组合。
  - 与周期性重置（Reset）方法对比。
  - 在流式RL中与SparseInit（零初始化但可训练）方法对比。

## 4. 资源与算力
- 论文未明确说明使用的GPU型号、数量及具体训练时长。仅提及计算资源由Mila提供，并感谢相关支持。未提供详细的算力统计。

## 5. 实验数量与充分性
- **实验数量**：涵盖了6个DMC Hard任务 × 2种算法（SAC/DDPG） × 多种宽度/深度缩放比例 × 多种稀疏率组合，以及视觉RL（2任务）、流式RL（2任务）、Atari-100k（多个游戏）。总计约数十组对比实验，每个设置使用8个随机种子（部分场景5个种子）。
- **充分性与公平性**：
  - 实验设计较为系统：先验证稀疏性在相同参数量下提升性能，再探究稀疏率与模型尺寸的交互效应，最后通过诊断指标（Srank、休眠比率、梯度范数、参数范数、梯度协方差）揭示内在机制。
  - 使用相同的超参数、训练步数、架构基座，仅改变稀疏性，对比公平。
  - 扩展至视觉和流式RL，增加泛化验证。
  - 不足之处：主要基于SimBa架构，未测试对其他架构（如纯MLP）的适用性；Atari-100k实验仅呈现改进比例，未列出绝对分数；计算资源细节缺失。

## 6. 主要结论与发现
- **核心发现**：简单的静态随机剪枝就能有效解锁DRL模型的扩展潜力。在相同参数量下，稀疏网络比密集网络性能更优；在相同模型尺寸下，稀疏网络显著更好。稀疏网络在扩大规模时能持续受益，而密集网络在超过临界点后性能崩溃。
- **机制分析**：
  - **表征能力**：稀疏网络有效秩（Srank）更高，避免容量坍塌。
  - **塑性保持**：稀疏网络休眠神经元比例更低，梯度范数不衰减，无需重置即可维持学习能力。
  - **正则化作用**：稀疏网络参数范数更小，且具有更强的简单性偏差（Simplicity Bias），促进学习简单泛化模式。
  - **梯度干扰减轻**：稀疏网络梯度协方差更弱，梯度更独立，减少冲突。
- **最佳实践**：扩大模型尺寸的同时保持高稀疏率（如0.8~0.9）可获得最佳性能。

## 7. 优点
- **极简有效**：仅需一次随机剪枝，不改变训练流程，易于实现且与任何RL算法兼容。
- **深刻机理分析**：利用Srank、休眠比率、梯度协方差等多种诊断指标，解释了稀疏性为何能缓解优化病理。
- **全面泛化验证**：在主实验基础上扩展到视觉RL、流式RL和Atari，证明方法的普适性。
- **对比清晰**：与周期性重置方法对比，说明稀疏网络不需要这种补救措施即能保持塑性。
- **开源代码**：提供了可复现的代码仓库。

## 8. 不足与局限
- **依赖先进架构**：实验主要基于SimBa架构，对更基础的MLP或卷积网络是否同样有效未充分测试。
- **缺乏计算资源细节**：未报告GPU型号、数量、训练时长，影响可复现性评估。
- **Atari-100k实验不够深入**：仅展示了改进百分比，未提供绝对分数和训练曲线，且低数据场景下扩展优势可能不明显。
- **静态稀疏的灵活性有限**：与动态稀疏训练（如RigL、SET）相比，不利用训练信息调整拓扑，可能在高稀疏率时丢失重要连接。
- **理论解释尚浅**：对“为什么随机剪枝能带来这么好效果”缺乏更严格的数学理论支撑。
- **超参数敏感性**：最优稀疏率需针对任务和规模手动调整，缺乏自动选择机制。

（完）
