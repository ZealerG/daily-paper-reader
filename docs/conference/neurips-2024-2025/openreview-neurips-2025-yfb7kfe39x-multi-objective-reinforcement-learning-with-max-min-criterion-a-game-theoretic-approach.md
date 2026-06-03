---
title: "Multi-Objective Reinforcement Learning with Max-Min Criterion: A Game-Theoretic Approach"
title_zh: 基于最大最小准则的多目标强化学习：博弈论方法
authors: "Woohyeon Byeon, Giseung Park, Jongseong Chae, Amir Leshem, Youngchul Sung"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=YFb7KFE39x"
tags: ["query:graph-part"]
score: 7.0
evidence: 多目标强化学习新算法，采用博弈论最大最小准则
tldr: 本文针对多目标强化学习中的最大最小准则问题，提出一种基于博弈论视角的算法框架，将问题转化为二人零和正则化连续博弈，并利用镜像下降法简化策略更新，实现了全局最后迭代收敛。理论分析包含精确和近似策略评估下的迭代复杂度及样本复杂度界限，并通过自适应正则化进一步提升性能。实验验证了算法的有效性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 457, \"height\": 274, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 411, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 519, \"height\": 555, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 734, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1433, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1431, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 517, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1364, \"height\": 1703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yfb7kfe39x/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 385, \"height\": 383, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 953, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 1142, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 397, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1420, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 906, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1411, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1163, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yfb7kfe39x/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1429, \"height\": 217, \"label\": \"Table\"}]"
motivation: 多目标强化学习常需平衡多个竞争目标，现有算法收敛性保证不足。
method: 将最大最小多目标强化学习转化为二人零和正则化连续博弈，采用镜像下降更新策略，并引入自适应正则化。
result: 提供了算法在精确和近似策略评估下的迭代复杂度及样本复杂度界限，实验表明算法收敛稳定。
conclusion: 所提框架在保证全局收敛的同时简化了优化过程，适用于多种多目标RL场景。
---

## Abstract
In this paper, we propose a provably convergent and practical framework for multi-objective reinforcement learning with max-min criterion. From a game-theoretic perspective, we reformulate max-min multi-objective reinforcement learning as a two-player zero-sum regularized continuous game and introduce an efficient algorithm based on mirror descent. Our approach simplifies the policy update while ensuring global last-iterate convergence. 
We provide a comprehensive theoretical analysis on our algorithm, including iteration complexity under both exact and approximate policy evaluations, as well as sample complexity bounds. 
To further enhance performance, we modify the proposed algorithm with adaptive regularization.
Our experiments demonstrate the convergence behavior of the proposed algorithm in tabular settings, and our implementation for deep reinforcement learning significantly outperforms  previous baselines in many MORL environments.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：多目标强化学习（MORL）中，许多实际场景（如资源分配、交通信号控制）需要优化公平性而非简单的加权和。最大最小（max-min）准则自然适用于此类场景，但它具有非光滑性，传统方法难以直接求解。
- **背景**：现有方法如 Park et al. (2024) 通过凸优化公式求解，但需要双循环迭代、高内存占用，且仅保证平均迭代收敛；其他近似方法（如 GGF-PPO）只优化代理目标。本文旨在提供一种单循环、低复杂度、保证最后迭代收敛的算法。
- **整体含义**：通过博弈论视角，将 max-min MORL 转化为二人零和连续博弈，利用镜像下降和熵正则化获得闭式更新，显著降低了计算和内存开销，并证明全局收敛。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将熵正则化 max-min MORL 等价转化为 min-max 问题（式 (5)），并证明其鞍点即为原问题最优解。由此构建二人零和博弈：学习者（Learner）最大化加权软值 ⟨w, Vπτ⟩，对手（Adversary）最小化该值。
- **关键技术细节**：
  - 学习者的策略更新：采用自然策略梯度（NPG）或 PPO，在表格设置下得到闭式更新（式 (11)）：  
    πθ_{t+1}(a|s) ∝ (πθ_t(a|s))^α exp( (1-α)/τ · Q^{πθ_t}_{w_t,τ}(s,a) )，其中 α = 1 - ητ/(1-γ)。
  - 对手的权重更新：采用带熵正则化的镜像下降，得到闭式解（式 (13)）：  
    w_{t+1} = softmax( - (1-β)/τ_w · V^{πθ_t} + β log w_t )，其中 β = 1/(λτ_w+1)。
  - 自适应正则化版本 ARAM：用动态参考向量 c 代替均匀参考，c 基于当前最差目标与其他目标的协方差（式 (14)），进一步加速收敛。
- **算法流程**（ERAM/ARAM）：  
  1. 收集样本，用 PPO 更新策略 θ（基于加权优势函数 ⟨w, Â⟩）；  
  2. 根据式 (13) 或 (40) 更新权重 w；  
  3. 重复直到收敛。  
  整体为单循环算法。

### 3. 实验设计：数据集/场景、benchmark、对比方法
- **场景与数据集**：
  - **表格 MOMDP**：随机生成三种规模 (|S|,|A|,K) = (2,2,2), (3,3,6), (4,4,4)，验证收敛性。
  - **交通信号控制**：基于 SUMO 仿真平台，三个场景：
    - Base-4：对称流量，4 个目标（每条道路的等待时间）。
    - Asym-4：非对称流量，4 个目标。
    - Asym-16：非对称流量，16 个目标（每条车道）。
  - **辅助环境**：Species Conservation（2 目标）、MO-Reacher（4 目标）、Four-Room（2 目标）。
- **对比方法**：GGF-DQN、GGF-PPO、Park et al. (2024)、Avg-DQN（优化平均奖励）。
- **benchmark**：采用 max-min 性能指标（min_k 累积折扣回报），报告均值与标准差。

### 4. 资源与算力
- **硬件**：所有实验在 **Intel Xeon Gold 6238R CPU**（双路）上运行，未使用 GPU。
- **训练时长**：如表 2 所示，Base-4 场景中 ERAM 约 111 分钟，ARAM 约 120 分钟，远快于 Park et al. (2024) 的 346 分钟。其他场景类似。
- **内存**：ERAM/ARAM 参数量仅为 Park et al. 的约 5%（例如 Base-4 中 13,704 vs 274,084）。
- **算力总量**：未给出总 GPU/CPU 小时数，但可推断实验在单机 CPU 集群上完成。

### 5. 实验数量与充分性
- **实验组数**：
  - 表格实验：3 种规模，各 50 随机实例，重复运行。
  - 交通信号控制：3 个场景，各 5 个随机种子。
  - 辅助环境：3 个环境，各 5 个随机种子。
  - 消融实验：对超参数 λ 和 β 进行网格搜索（6×7 组合），共 42 组，每个场景单独运行。
- **充分性**：实验覆盖了多种问题规模、目标维度、离散/连续动作空间，对比了最先进的 baseline。消融实验系统分析了关键超参数影响。统计显著性和误差棒均有报告。整体设计客观、公平。

### 6. 论文的主要结论与发现
- ERAM 和 ARAM 在所有测试环境中均取得最优或次优的 max-min 性能，显著优于 GGF-PPO、Park et al. 等方法。
- 实现了 **最后迭代收敛**（last-iterate convergence），而 Park et al. 仅保证平均迭代收敛。
- 计算效率和内存效率极高：训练时间减少 63%–68%，内存减少 94%–95%。
- 理论证明：在表格设置下，算法以线性速率全局收敛（精确策略评估下迭代复杂度 O(1/ε² log 1/ε_acc)，近似评估下增加误差项）。
- 自适应正则化（ARAM）在复杂环境（高目标维度、非对称流量）中比 ERAM 进一步提升性能。

### 7. 优点：方法或实验设计上的亮点
- **理论贡献**：首次为 max-min MORL 提供最后迭代收敛保证，且分析覆盖精确和近似策略评估。
- **算法创新**：通过博弈论视角获得双闭环式更新，避免了复杂的投影梯度或子循环，易于实现。
- **效率优势**：单循环结构，内存和计算开销与普通 PPO 相当，适合大规模应用。
- **实验设计**：涵盖了从简单表格到复杂交通仿真、再到标准 MORL 环境的多层次验证，消融实验完整，统计可靠。
- **可复现性**：提供了开源代码（GitHub），超参数详细公布。

### 8. 不足与局限
- **理论范围**：收敛性分析限于表格设置下的 softmax 策略，未扩展到神经网络函数逼近。
- **同质性假设**：max-min 准则假设各目标具有可比较尺度，对异构目标（单位/范围不同）需预先归一化，文中未深入探讨。
- **评估偏差风险**：所有对比实验在 CPU 上运行，可能未充分优化 GPU 加速，但公平性尚可（均在同一设备）。
- **应用限制**：仅考虑有限目标数（K≤16），未测试极高维目标场景。ARAM 中自适应参考向量的计算依赖样本期望，可能引入方差。
- **未讨论的方面**：未分析正则化系数 τ, τ_w 对真实最优解的近似误差（文中仅提及线性界，无定量分析）。

（完）
