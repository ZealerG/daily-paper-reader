---
title: Boosting Sample Efficiency and Generalization in Multi-agent Reinforcement Learning via Equivariance
title_zh: 通过等变性提升多智能体强化学习的样本效率和泛化
authors: "Joshua McClellan, Naveed Haghani, John Winder, Furong Huang, Pratap Tokekar"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=MQIET1VfoV"
tags: ["query:graph-part"]
score: 8.0
evidence: 使用等变图神经网络提升多智能体强化学习的样本效率和泛化
tldr: 本文针对多智能体强化学习样本效率低和泛化差的问题，引入等变图神经网络（EGNN）作为策略网络。利用多智能体场景中常见的旋转、平移等对称性，EGNN提供了强归纳偏置。实验证明EGNN显著提升了MARL的样本效率和泛化能力，在多个基准任务上优于传统网络。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 741, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 711, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 701, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1293, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 842, \"height\": 666, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1422, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 722, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1703, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1545, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1622, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1651, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1546, \"height\": 895, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mqiet1vfov/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1548, \"height\": 915, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-mqiet1vfov/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1352, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mqiet1vfov/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mqiet1vfov/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 484, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mqiet1vfov/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 533, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mqiet1vfov/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 311, \"label\": \"Table\"}]"
motivation: 多智能体RL样本效率低、泛化差，缺乏利用对称性等结构归纳偏置。
method: 在策略网络中使用等变图神经网络（EGNN），强制模型对旋转/平移等对称变换保持不变性。
result: 在多个MARL基准任务中，EGNN显著提升样本效率和泛化性能。
conclusion: 等变图神经网络是改善MARL学习效率的有效归纳偏置。
---

## Abstract
Multi-Agent Reinforcement Learning (MARL) struggles with sample inefficiency and poor generalization [1]. These challenges are partially due to a lack of structure or inductive bias in the neural networks typically used in learning the policy. One such form of structure that is commonly observed in multi-agent scenarios is symmetry. The field of Geometric Deep Learning has developed Equivariant Graph Neural Networks (EGNN) that are equivariant (or symmetric) to rotations, translations, and reflections of nodes. Incorporating equivariance has been shown to improve learning efficiency and decrease error [ 2 ]. In this paper, we demonstrate that EGNNs improve the sample efficiency and generalization in MARL. However, we also show that a naive application of EGNNs to MARL results in poor early exploration due to a bias in the EGNN structure. To mitigate this bias, we present Exploration-enhanced Equivariant Graph Neural Networks or E2GN2. We compare E2GN2 to other common function approximators using common MARL benchmarks MPE and SMACv2. E2GN2 demonstrates a significant improvement in sample efficiency, greater final reward convergence, and a 2x-5x gain in over standard GNNs in our generalization tests. These results pave the way for more reliable and effective solutions in complex multi-agent systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：多智能体强化学习（MARL）普遍存在**样本效率低**和**泛化能力差**的问题。传统使用的神经网络（如MLP、普通GNN）缺乏对**结构先验（归纳偏置）** 的利用，导致需要大量样本才能学到有效策略。
- **背景**：在多智能体场景中，经常存在**旋转、反射（即O(n)对称群）等对称性**。例如：环境中所有智能体旋转一定角度后，最优动作也应相应旋转（等变性），而奖励和值函数则应对旋转保持不变（不变性）。利用这种对称性可以显著缩小搜索空间，提升学习效率。
- **整体含义**：作者指出，将**等变图神经网络（EGNN）** 引入MARL作为策略函数近似器，可以强制策略满足旋转/反射等变，从而提升样本效率和泛化。但直接应用EGNN会导致**早期探索偏差（early exploration bias）**，因此进一步提出了改进版本 **E2GN2（Exploration-enhanced Equivariant Graph Neural Networks）**。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：
  - 使用EGNN作为策略网络，其坐标嵌入部分负责输出等变动作（如移动方向），特征嵌入部分负责输出不变动作（如攻击目标选择）。
  - 针对EGNN在早期探索时输出均值偏向智能体当前位置的问题（定理1和推论1.1），提出E2GN2：在等变更新公式中额外增加一项 `u_i * φ_u2(m_i)`，使得期望输出趋于零（定理2），从而消除偏差。
- **关键技术细节**：
  - **EGNN的标准更新公式**（仅列出坐标部分）：
    ```
    u^{l+1}_i = u^l_i + C * Σ_{j≠i} (u^l_i - u^l_j) * φ_u(m_ij)
    ```
  - **E2GN2的修改**：
    ```
    u^{l+1}_i = u^l_i * φ_u2(m_i) + C * Σ_{j≠i} (u^l_i - u^l_j) * φ_u(m_ij)
    ```
    其中 `φ_u2` 是一个MLP，其输出期望为零（当网络权重随机初始化时），从而抵消了 `u^l_i` 的偏置。
  - **复杂动作空间的适配**：
    - 不变特征 `h_i` → 输出离散动作（如攻击类型）或不变连续分量。
    - 等变坐标 `u_i` → 输出连续空间动作（如移动方向）。
    - 针对目标实体（如敌人）的离散动作，从对应节点输出logits，使得动作空间随实体数量可扩展。
  - **保持等变性**：E2GN2对旋转和反射等变（定理3），但不再对平移等变（作者认为平移等变在MARL中反而带来不利偏置）。
- **算法流程**：基于PPO算法（RLlib实现），使用E2GN2作为策略和价值网络（价值网络只使用不变特征 `h_i`），每个智能体共享网络参数（参数化）。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **环境（benchmark）**：
  - **MPE（Multi-agent Particle Environment）**：两个任务
    - **simple spread（合作导航）**：3个智能体需分别占据3个目标地标。
    - **predator-prey（tag）**：3个追捕者协作捕捉1个逃跑者（逃跑者使用简单启发式）。
  - **SMACv2（StarCraft Multi-Agent Challenge v2）**：三个种族（Terran, Protoss, Zerg），使用5v5对抗，初始配置为“surrounded”。
- **对比方法**：
  - **MLP**（两层隐藏层，宽度64或128）
  - **标准GNN**（类似EGNN但不带等变坐标更新）
  - **E3AC**（基于SEGNN的等变方法，来自同期工作Chen & Zhang, 2024）
  - **EGNN**（直接应用）
  - **E2GN2**（本文提出）
- **超参数**：在附录B中给出，遵循RLlib默认+文献[26]的调参指南，未使用集中式评论家等特殊技巧以隔离网络架构影响。
- **评估指标**：平均奖励（MPE）、胜率（SMACv2）、样本效率、泛化测试（初始化位置旋转和智能体数量扩展）。

## 4. 资源与算力

- 原文在附录B **Hardware** 部分说明：
  - 图神经网络模型（EGNN/E2GN2/GNN）主要使用 **A100 GPU**（但并非必须，A100仅提供充足显存）。
  - MLP使用 **CPU** 训练。
  - 每个训练运行使用 **4个rollout worker （4个CPU线程）**，加上主进程共 **5个CPU线程**。
- **训练时间**：在MPE上，E3AC需要约4小时采集100万步，而E2GN2不到1小时；其他网络更短。SMACv2总步数达1000万步（terran/protoss），但具体GPU时长未明确给出。
- 未详细说明所有实验具体累计GPU小时数。

## 5. 实验数量与充分性

- **重复次数**：每个实验使用 **10个随机种子**，图表中展示均值和标准误差（95%置信区间通过seaborn计算），统计上合理。
- **任务覆盖**：
  - MPE：2个环境（spread, tag）。
  - SMACv2：3个种族（terran, protoss, zerg），每个种族各有5v5场景。
  - **泛化测试**：对SMACv2的三种初始化配置（surrounded left（训练配置）、surrounded right、surrounded all）进行测试（表1）。
  - **可扩展性测试**：在5个智能体训练后，测试4、6、7、8个智能体（表2）。
  - **消融/补充实验**：附录C还包括离散动作映射、部分可观测、是否居中、单个单位类型等更多实验。
- **公平性**：所有方法共享相同的RL框架（RLlib）、PPO基线、训练流程；超参数在同一环境中保持一致；未使用对特定网络有利的技巧。对比包括非等变基线（MLP、GNN）和等变基线（E3AC、EGNN），较为全面。

## 6. 论文的主要结论与发现

1. **等变性显著提升样本效率和最终性能**：在MPE和SMACv2上，EGNN和E2GN2均大幅优于MLP和普通GNN。
2. **E2GN2消除早期探索偏差**：相比EGNN，E2GN2在早期训练中不会导致智能体远离原点，奖励不下降，收敛更快，最终性能更高。
3. **泛化性能优异**：在SMACv2的旋转泛化测试中，E2GN2在surrounded right配置下胜率保持在0.55左右，而GNN和MLP分别降至0.11和0.12，E2GN2的胜率是后者的**5倍**。
4. **可扩展性好**：E2GN2训练5个智能体后无需微调即可直接控制4-8个智能体，胜率下降平缓，而MLP无法直接扩展。
5. **实际训练速度优于E3AC**：E3AC因使用SEGNN，推理速度慢，训练耗时约为E2GN2的4倍以上。

## 7. 优点

- **理论贡献**：首次证明EGNN在MARL中会导致早期探索偏差，并提出简洁有效的改进方案E2GN2，同时保持旋转等变性。
- **实用性强**：提出的E2GN2能很好地适配混合离散/连续动作空间，且与主流MARL算法（如PPO）兼容。
- **实验充分**：覆盖多种场景（简单到复杂）、多种基线，并专门进行了泛化和扩展测试，结果统计显著。
- **使用开放框架**：基于RLlib实现，实验可重复性高（代码虽未完全开源，但可基于公开组件复现）。

## 8. 不足与局限

- **未处理部分对称性**：仅考虑旋转和反射的完全对称，现实场景可能存在部分对称或不完美对称，本文未探讨。
- **翻译等变被有意放弃**：文中称平移等变在MARL中可能带来偏置，但未提供严格分析或实验验证。
- **未处理角动量和加速度**：环境需要更高阶物理量（如角动量）时，EGNN/E2GN2可能不适用。
- **部分可观测场景处理不深入**：仅在附录C给出了部分可观测实验，且结果尚可，但未作为主要贡献；完整解决方案留待未来。
- **Zerg场景表现较弱**：在所有方法中，Zerg胜率较低，E2GN2提升有限，说明方法对某些复杂环境仍不够鲁棒。
- **未与传统集中式训练分散执行（CTDE）结合**：如MAPPO等算法使用集中式评论家，本文仅用分散评论家，可能限制了性能潜力的体现。
- **算力信息不完整**：未报告总GPU小时数，对可重复性和成本评估有影响。

（完）
