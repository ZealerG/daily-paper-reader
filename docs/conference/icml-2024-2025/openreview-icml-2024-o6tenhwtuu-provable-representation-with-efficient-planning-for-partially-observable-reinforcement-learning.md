---
title: Provable Representation with Efficient Planning for Partially Observable Reinforcement Learning
title_zh: 部分可观测强化学习的可证明表示与高效规划
authors: "Hongming Zhang, Tongzheng Ren, Chenjun Xiao, Dale Schuurmans, Bo Dai"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=O6tenHWTUU"
tags: ["query:graph-part"]
score: 8.0
evidence: 部分可观测强化学习的可证明表示与高效规划
tldr: 本文针对部分可观测马尔可夫决策过程（POMDP），提出了基于表示的学习框架，有效解决部分可观测性带来的统计和计算挑战。通过学习紧凑表示，结合高效规划算法，在多个基准任务上取得显著性能提升。该方法为实际部分可观测强化学习提供了理论基础和可实现的算法途径。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-o6tenhwtuu/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1770, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-o6tenhwtuu/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-o6tenhwtuu/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1699, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-o6tenhwtuu/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1695, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-o6tenhwtuu/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1642, \"height\": 2413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-o6tenhwtuu/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 905, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-o6tenhwtuu/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 904, \"height\": 339, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-o6tenhwtuu/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1297, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-o6tenhwtuu/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1615, \"height\": 908, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-o6tenhwtuu/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1602, \"height\": 610, \"label\": \"Table\"}]"
motivation: 部分可观测性导致强化学习算法性能下降。
method: 基于表示的方法，结合高效规划。
result: 在多个任务上表现优异。
conclusion: 为POMDP提供了可行的理论框架和算法。
---

## Abstract
In most real-world reinforcement learning applications, state information is only partially observable, which breaks the Markov decision process assumption and leads to inferior performance for algorithms that conflate observations with state. Partially Observable Markov Decision Processes (POMDPs), on the other hand, provide a general framework that allows for partial observability to be accounted for in *learning, exploration and planning*, but presents significant computational and statistical challenges. To address these difficulties, we develop a representation-based perspective that leads to a coherent framework and tractable algorithmic approach for practical reinforcement learning from partial observations. We provide a theoretical analysis for justifying the statistical efficiency of the proposed algorithm, and also empirically demonstrate the proposed algorithm can surpass state-of-the-art performance with partial observations across various benchmarks, advancing reliable reinforcement learning towards more practical applications.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：现实世界强化学习（RL）中，状态信息通常是部分可观测的，这破坏了马尔可夫决策过程（MDP）的假设，导致基于MDP的算法性能显著下降。
- **现有挑战**：部分可观测马尔可夫决策过程（POMDP）虽能建模部分可观测性，但最优策略依赖于完整历史，导致状态复杂度随步数指数增长，且规划问题为PSPACE-complete，统计复杂度也指数爆炸。
- **核心问题**：能否设计高效且实用的RL算法，利用POMDP的自然结构（如L-可解码性）同时避免指数级复杂度？
- **整体目标**：提出一种基于表示的框架，实现可证明的统计效率与计算可处理性，并能在实际基准中超越现有方法。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用L-可解码POMDP的结构，发现值函数可被一个**多步潜变量表示（μLV-Rep）**精确线性表示，从而绕过显式的信念计算和指数级规划复杂度。
- **关键观察**：
  - L-可解码性保证信念可由长度为L的历史窗口恢复（而非完整历史）。
  - 通过“矩匹配策略”（moment matching policy）消除值函数对历史重叠部分的依赖，使得Q函数可分解为内积形式：$Q^\pi_h(x_h, a_h) = \langle p(\cdot|x_h, a_h), w^\pi(\cdot) \rangle$，其中$p$是潜变量表示。
- **算法流程**：
  - **表示学习**：通过最大化观测序列的ELBO来学习潜变量模型$p(z|x_h, a_h)$和$p(o_{h+1}|z)$。
  - **值函数参数化**：将Q函数近似为$E_{p(z|x_h)}[w^\pi(z)]$，可用蒙特卡洛或随机特征求积实现。
  - **规划**：利用学到的线性表示，通过最小二乘回归完成贝尔曼备份，并结合SAC等策略优化方法处理连续动作。
  - **探索**：通过添加椭球奖励（ellipsoid bonus）实现乐观探索（OFU），也可用于离线设定中的悲观惩罚。
- **理论保证**：在有限模型类、可实现性、正则化条件下，算法以$1-\delta$概率经过$N = \text{poly}(C, H, |A|^L, L, \varepsilon, \log(|\mathcal{M}|/\delta))$次交互可得到$\varepsilon$-最优策略。

## 3. 实验设计

- **数据集/场景**：
  - **Meta-world**：50个不同的视觉机器人操作任务（如Coffee Push、Plate Slide、Push等），使用64×64×3图像观测。
  - **DeepMind Control Suites**（DMC）：部分视觉控制任务（如Reacher Easy/Hard、Acrobot Swingup等）。
  - **部分可观测MuJoCo连续控制任务**：通过遮蔽速度信息构造部分可观测版本（如HalfCheetah、Humanoid等）。
- **基准方法**：
  - DreamerV2（模型基方法）
  - Masked World Model（MWM，基于掩码自编码器的方法）
  - SAC-MLP（模型无关，拼接历史观测）
  - SLAC（随机潜变量Actor-Critic）
  - PSR（预测状态表示）
  - DrQ-v2（作为消融基线）
  - Best-FO（使用完全可观测状态的理想上界）
- **评估指标**：成功率（Meta-world）、平均回报（DMC和MuJoCo）。

## 4. 资源与算力

- **论文未明确说明**使用的GPU型号、数量或训练总时长。仅提到Meta-world任务每实验1M环境步，DMC任务0.5M步，使用Adam优化器，学习率0.0001，批量大小256。未提供具体算力资源。

## 5. 实验数量与充分性

- **实验数量**：
  - Meta-world全部50个任务均报告了学习曲线（附录H.2提供了所有任务的曲线图）。
  - DMC上做了特征维度消融（128/512/2048）和窗口大小L消融（1/3/5）。
  - MuJoCo部分可观测任务上对比了5个基准，报告了4个随机种子的平均值。
  - 另外对L=1/3/5在Reacher Easy/Hard上做了与DrQ-v2的对比消融。
- **充分性评价**：
  - 覆盖了离散动作（Meta-world为离散成功/失败）和连续动作（MuJoCo/DMC），且包含多个领域（机器人操作、运动控制）。
  - 消融实验考察了表示维度和历史窗口长度，验证了L=3的必要性。
  - 基准方法选择较全面（模型基、模型无关、PSR等），对比公平。
  - 但缺少与其他最新POMDP专用算法（如SRNN、Recurrent PPO等）的对比，且未在标准离散POMDP基准（如RockSample）上测试。

## 6. 主要结论与发现

- **表示的有效性**：μLV-Rep能够很好地表示POMDP的值函数，并且可以通过变分学习高效获取。
- **性能优势**：
  - 在Meta-world 50个任务中，μLV-Rep在41个任务上优于或等于最佳基线（成功率差异≤10%），训练速度比MWM快约2.6倍（21.3步/秒 vs 8.1步/秒）。
  - 在MuJoCo部分可观测任务上，μLV-Rep在5项中4项取得最佳，且接近完全可观测的上界（Best-FO）。
- **理论保证**：算法具有多项式样本复杂度，避开了指数级复杂度，且规划步骤仅需最小二乘回归，可实际实现。
- **关键发现**：L=3的历史窗口足以处理DMC中的部分可观测性问题，而L=1则失效，证实了非马尔可夫依赖的必要性。

## 7. 优点

- **理论贡献**：首次揭示了L-可解码POMDP中值函数的线性表示，并给出了可证明的样本复杂度上界。
- **算法实用性**：所有组件（变分ELBO学习、SAC规划、奖励bonus）均可通过标准深度学习实现，无需不可行的积分oracle。
- **计算效率**：相比使用ViT的MWM，μLV-Rep具有更高的训练速度（21.3步/秒 vs 8.1步/秒）。
- **泛化能力**：在多个视觉控制任务和部分可观测连续控制任务上均取得领先结果，方法易于扩展。

## 8. 不足与局限

- **实验覆盖不足**：
  - 未在经典POMDP离散基准（如RockSample、Tiger、T-Maze）上测试，难以评估广义POMDP性能。
  - 缺少与最新的基于循环神经网络（如R2D2、Recurrent PPO、Deep Recurrent Q-Learning）的对比。
- **假设条件限制**：理论分析依赖L-可解码性假设，虽然可扩展到γ-可观测（需近似），但实际任务是否严格满足假设未知；且依赖有限模型类假设，对于无限模型类的泛化未提供保证。
- **算力资源未公开**：无法复现或评估计算成本。
- **消融实验局限**：消融仅在DMC两个任务上进行，未在Meta-world全任务上验证表示维度和窗口大小的影响。
- **偏差风险**：MuJoCo实验仅报告了4个随机种子，Meta-world使用5个种子，统计稳定性有待验证；未报告方差或置信区间。
- **应用限制**：方法需要预先设定历史长度L，任务间可能需要调参；连续潜变量模型训练不稳定，可能对超参数敏感。

（完）
