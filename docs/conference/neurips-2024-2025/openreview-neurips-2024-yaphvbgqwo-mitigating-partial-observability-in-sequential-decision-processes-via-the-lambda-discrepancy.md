---
title: Mitigating Partial Observability in Sequential Decision Processes via the Lambda Discrepancy
title_zh: 通过Lambda差异缓解序贯决策中的部分可观测性
authors: "Cameron Allen, Aaron T. Kirtland, Ruo Yu Tao, Sam Lobel, Daniel Scott, Nicholas Petrocelli, Omer Gottesman, Ronald Parr, Michael Littman, George Konidaris"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=YaPhvbGqwO"
tags: ["query:graph-part"]
score: 4.0
evidence: 基于lambda差异的部分可观测强化学习算法
tldr: 提出lambda差异度量，通过比较不同λ的时序差分估计来检测部分可观测环境中的马尔可夫状态表示，无需访问真实状态空间。该方法提升RL在部分可观测下的学习效率，但非图划分专用。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 585, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 789, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1418, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1389, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1338, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1357, \"height\": 623, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1138, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 878, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1166, \"height\": 247, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1424, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1401, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1400, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yaphvbgqwo/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1449, \"height\": 1097, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-yaphvbgqwo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1274, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yaphvbgqwo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 759, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yaphvbgqwo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1450, \"height\": 642, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yaphvbgqwo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1117, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yaphvbgqwo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 908, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yaphvbgqwo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 683, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yaphvbgqwo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 683, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yaphvbgqwo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 683, \"height\": 302, \"label\": \"Table\"}]"
motivation: 强化学习依赖马尔可夫状态假设，但部分可观测时难以学习有效状态表示。
method: 提出lambda差异作为度量，指导状态表示学习并检测其充分性。
result: 实验验证该度量能有效识别马尔可夫状态并提升性能。
conclusion: 为部分可观测RL提供了实用的自监督工具。
---

## Abstract
Reinforcement learning algorithms typically rely on the assumption that the environment dynamics and value function can be expressed in terms of a Markovian state representation. However, when state information is only partially observable, how can an agent learn such a state representation, and how can it detect when it has found one? We introduce a metric that can accomplish both objectives, without requiring access to---or knowledge of---an underlying, unobservable state space. Our metric, the λ-discrepancy, is the difference between two distinct temporal difference (TD) value estimates, each computed using TD(λ) with a different value of λ. Since TD(λ=0) makes an implicit Markov assumption and TD(λ=1) does not, a discrepancy between these estimates is a potential indicator of a non-Markovian state representation. Indeed, we prove that the λ-discrepancy is exactly zero for all Markov decision processes and almost always non-zero for a broad class of partially observable environments. We also demonstrate empirically that, once detected, minimizing the λ-discrepancy can help with learning a memory function to mitigate the corresponding partial observability. We then train a reinforcement learning agent that simultaneously constructs two recurrent value networks with different λ parameters and minimizes the difference between them as an auxiliary loss. The approach scales to challenging partially observable domains, where the resulting agent frequently performs significantly better (and never performs worse) than a baseline recurrent agent with only a single value network.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **核心问题**：强化学习（RL）通常假设环境状态是马尔可夫（Markovian）的，即当前状态足以预测未来。但在部分可观测环境（POMDP）中，智能体只能获得观测（observation），无法直接访问隐状态（hidden state），导致标准TD学习中的马尔可夫假设被违反，价值函数估计不准确。
- **整体含义**：本文旨在解决“智能体如何在不了解底层隐状态空间的情况下，自动检测并缓解部分可观测性带来的非马尔可夫性”的问题。作者提出了一种可计算、可微的度量——λ差异（λ-discrepancy），用于指导智能体学习有效的记忆表示，从而在部分可观测环境下提升RL算法性能。

---

### 论文提出的方法论

- **核心思想**：利用时序差分（TD）学习中不同λ参数（λ=0为单步TD，隐式依赖马尔可夫假设；λ=1为蒙特卡洛，不依赖马尔可夫假设）的价值函数差异来检测观测表示是否马尔可夫。若差异非零，则表明当前状态表示可能非马尔可夫，需引入记忆。
- **关键技术细节**：
  - **λ差异定义**：对于给定策略π，λ差异为两个不同λ对应的Q值函数之差的加权范数：  
    \( \Lambda^{\lambda_1,\lambda_2}_{P,\pi} = \| Q^{\lambda_1}_\pi - Q^{\lambda_2}_\pi \| \)，其中Q值通过封闭形式的TD(λ)固定点公式计算。
  - **理论保证**：定理1证明，对于非块MDP的POMDP，λ差异几乎处处非零（仅在零测集上为零）；定理2证明，当且仅当POMDP退化为块MDP（观测与状态一一对应）时，λ差异对所有策略为零。
  - **记忆学习**：通过最小化λ差异来学习参数化的记忆函数μ，该函数将历史映射到内部记忆状态，从而构建记忆增强的POMDP（Pμ）。
  - **可扩展算法**：将λ差异作为辅助损失，集成到递归PPO（Proximal Policy Optimization）中，同时训练两个不同λ的递归价值网络，并最小化其输出的均方差。

---

### 实验设计

- **数据集/场景**：
  - **小型经典POMDPs**：T-maze、Tiger问题、Paint、Cheese Maze、Network、Shuttle、4×3迷宫等，用于封闭形式的记忆优化验证。
  - **大型挑战性POMDPs**：Battleship（部分观测战舰）、部分观测PacMan（PocMan）、RockSample(11,11)和RockSample(15,15)。这些环境需要复杂记忆（如追踪船只位置、地图定位、岩石采样状态）。
- **基准方法**：
  - 无记忆PPO（基于当前观测）
  - 递归PPO（使用GRU，但只有单个价值网络）
- **对比方式**：在同一超参数搜索下，比较最终回报（undiscounted return）和折扣回报。此外，对小型环境通过与最优信念状态策略（POMDP求解器获得）对比进行归一化性能评估。

---

### 资源与算力

- 论文在附录I.4中提到，超参数搜索使用了一个由NVIDIA 3090 GPU组成的集群，每个实验运行1至12小时（取决于域）。未明确GPU具体数量，但指出环境被向量化到4个副本，所有训练在JAX上并行加速。因此，计算资源中等，但足够支持大规模实验。

---

### 实验数量与充分性

- **实验数量**：超参数搜索：每个算法在4个大型环境中各搜索5个种子，共约5×4×3种配置；最终报告30个种子的学习曲线（图6）。小型环境做30个种子（图5）。另外，还进行了记忆可视化（PocMan）和消融（如不同λ参数的效果）。
- **充分性判断**：实验覆盖了多种类型和复杂度的POMDP，对比了有无记忆、有无λ差异辅助损失，并进行了超参数调优。统计上使用95%置信区间，结果可靠。但未包含其他图划分或显式状态抽象方法作为对比，略有不足。

---

### 论文主要结论与发现

1. **λ差异可有效检测部分可观测性**：理论证明对于POMDP几乎处处非零，而对MDP为零；实证中，λ差异随部分可观测程度增加而增大。
2. **最小化λ差异有助于学习记忆**：在小规模POMDP中，基于封闭形式梯度下降学习记忆函数显著提升了后续策略梯度学习的性能。
3. **作为辅助损失可提升深度RL**：在大型POMDP基准中，λ差异辅助损失使递归PPO的性能始终不低于基线，且多数情况下显著更优（尤其在RockSample(15,15)上，基线仅学会立即退出，而增强方法学会了有效采样）。
4. **λ参数选择有规律**：最优λ通常一个接近0、一个接近1，与理论预测一致（差异最大时检测能力最强）。

---

### 优点

- **理论扎实**：提供了λ差异非零的充分条件（定理1）和零的充要条件（定理2），并给出封闭形式的Q值推导。
- **方法简洁实用**：无需访问隐状态空间或领域知识，仅使用价值函数差异，易于集成到任何TD-based RL算法中。
- **端到端可微**：可用于梯度优化，自然适配深度神经网络。
- **实验设计全面**：覆盖从公式化小环境到大规模挑战性POMDP，并包含可视化分析。
- **开源代码**：提供完整实现，有利于复现和扩展。

---

### 不足与局限

- **理论边缘情况**：存在“奇偶校验”类POMDP，λ差异对所有策略为零（对称性导致），虽随机记忆可解决，但需额外处理。
- **近似误差**：在线学习中使用未收敛的价值函数估计λ差异，理论上的固定点差异分析不直接适用于训练中，缺乏收敛保证。
- **计算开销**：需要训练两个价值网络，相当于约12%的参数增加和少量额外计算，但文末未详细比较训练时间成本。
- **环境覆盖有限**：对比基线仅限PPO变体，未与更先进的记忆增强RL方法（如Dreamer、R2D2等）比较；且未在连续控制或高维图像观测域上测试。
- **超参数敏感**：λ选取、β平衡系数等需调优，文中未提供鲁棒性分析。

---

（完）
