---
title: Structured Reinforcement Learning for Combinatorial Decision-Making
title_zh: 面向组合决策的结构化强化学习
authors: "Heiko Hoppe, Léo Baty, Louis Bouvier, Axel Parmentier, Maximilian Schiffer"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=GS9o7u5njS"
tags: ["query:graph-part"]
score: 9.0
evidence: 结构化强化学习用于组合决策，可应用于图划分
tldr: 提出结构化强化学习，将组合优化层嵌入演员-评论家网络，利用Fenchel-Young损失实现端到端学习，并在六个组合决策环境中达到或超越现有方法。该方法直接面向路由、调度等组合问题，对图划分任务具有高方法论价值。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-gs9o7u5njs/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gs9o7u5njs/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1300, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gs9o7u5njs/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1313, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gs9o7u5njs/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gs9o7u5njs/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1423, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gs9o7u5njs/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1432, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gs9o7u5njs/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1440, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gs9o7u5njs/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1425, \"height\": 630, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1190, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1034, \"height\": 618, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1276, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1174, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1236, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1463, \"height\": 580, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1344, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1362, \"height\": 618, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1159, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1070, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gs9o7u5njs/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1011, \"height\": 358, \"label\": \"Table\"}]"
motivation: 标准强化学习难以处理具有组合动作空间的现实问题，无法利用结构信息。
method: 提出结构化强化学习，在演员网络中嵌入组合优化层，使用Fenchel-Young损失进行端到端训练。
result: 在多个组合决策环境中匹配或超越现有方法。
conclusion: SRL为组合优化问题提供了高效的强化学习框架。
---

## Abstract
Reinforcement learning (RL) is increasingly applied to real-world problems involving complex and structured decisions, such as routing, scheduling, and assortment planning. These settings challenge standard RL algorithms, which struggle to scale, generalize, and exploit structure in the presence of combinatorial action spaces. We propose Structured Reinforcement Learning (SRL), a novel actor-critic paradigm that embeds combinatorial optimization-layers into the actor neural network. We enable end-to-end learning of the actor via Fenchel-Young losses and provide a geometric interpretation of SRL as a primal-dual algorithm in the dual of the moment polytope. Across six environments with exogenous and endogenous uncertainty, SRL matches or surpasses the performance of unstructured RL and imitation learning on static tasks and improves over these baselines by up to 92\% on dynamic problems, with improved stability and convergence speed.

---

## 论文详细总结（自动生成）

# 面向组合决策的结构化强化学习（SRL）论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：现实工业问题（如车辆路径、机器调度、分类规划）常涉及**组合马尔可夫决策过程（C-MDP）**，其动作空间呈指数级大小，且具有复杂组合结构。
- **现有方法局限**：
  - 标准 RL 算法（如 PPO、SAC）难以处理巨大动作空间的探索与泛化，训练不稳定、收敛慢。
  - 结构化模仿学习（SIL）需要专家演示，在动态环境中性能受限于专家策略，且无法从探索中改进。
  - 传统预测‑优化方法（如 predict-then-optimize）将预测与决策分离，在动态场景下效果差。
- **研究动机**：提出一种**端到端**的 RL 框架，能在**无需专家演示**的情况下，利用动作空间的组合结构进行稳定、高效的策略学习。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 核心思想
- 将**组合优化（CO）层**嵌入 actor‑critic 架构中的 actor 网络，形成 **CO‑augmented Machine Learning（COAML）流水线**。
- 通过 **Fenchel‑Young 损失**训练 actor，实现通过不可微 CO 层的梯度传播。
- 将学习过程解释为**采样‑原始‑对偶算法**，在矩多面体的对偶空间中进行更新。

### 关键技术细节
- **Actor 架构**：
  - 统计模型 \( \phi_w \)（神经网络）将状态 \( s \) 映射为分数向量 \( \theta \)。
  - CO 层 \( f(\theta, s) = \arg\max_{a \in A(s)} \langle \theta, a \rangle \) 求解线性目标的最大化问题，返回可行动作。
  - 推断时 actor 策略为 Dirac 分布：\( \pi_w(\cdot|s) = \delta_{f(\phi_w(s), s)} \)。
- **训练流程（Algorithm 1）**：
  1. 采样状态 \( s \) 并计算分数 \( \theta \)。
  2. 使用高斯噪声扰动 \( \theta \)（标准差 \( \sigma_f \)）得 \( \eta \)，求解 CO 得到探索动作 \( a = f(\eta, s) \)并执行，收集经验。
  3. 从回放缓冲区采样转移，再次扰动 \( \theta \)（标准差 \( \sigma_b \)）生成 \( m \) 个候选 \( \eta \)，求解 CO 得到候选动作 \( a' \)。
  4. 用 critic \( Q_{\psi_\beta} \) 评估各候选动作的 Q 值，通过**softmax**（温度 \( \tau \)）计算目标动作 \( \hat{a} = \text{softmax}_{a'} \left( \frac{1}{\tau} Q_{\psi_\beta}(s,a') \right) \)。
  5. 最小化 **Fenchel‑Young 损失** \( L_\Omega(\theta; \hat{a}) = \mathbb{E}_Z [\max_{a \in A(s)} (\theta+Z)^\top a] - \theta^\top \hat{a} \)（\( Z \sim \mathcal{N}(0,\varepsilon) \)）来更新 actor。
  6. 使用 TD 误差更新 critic。
- **几何解释**：
  - 动作集凸包为矩多面体 \( C(s) \)，score 向量对应多面体的法锥。
  - SRL 更新等价于在分布单形上进行采样原始‑对偶步骤（Proposition 2），其中 negentropy 和稀疏扰动的正则化被交替使用。

## 3. 实验设计

### 环境与场景
- **3 个静态环境**（T=1）：
  1. Warcraft 最短路径问题（WSPP）：从地图图像中找最低成本路径。
  2. 单机调度问题（SMSP）：排序作业最小化总完成时间。
  3. 随机车辆调度问题（SVSP）：考虑随机延误的车辆路线规划。
- **3 个动态环境**（T>1）：
  1. 动态车辆调度问题（DVSP）：随时间到达的请求，需实时调度车队。
  2. 动态分类问题（DAP）：选择商品子集展示给顾客，基于 MNL 模型购买，商品特征受历史选择影响。
  3. 网格世界最短路径问题（GSPP）：机器人找路径到达移动目标，路径成本影响后续成本参数（内生不确定性）。

### 基准方法（benchmark）
- **SIL**：结构化模仿学习，使用专家演示的 Fenchel‑Young 损失。
- **PPO**：近端策略优化（无结构 RL 代表）。
- **专家策略**：静态环境为离线最优解；动态环境为已知信息下的在线最优策略。
- **贪婪策略**：简单启发式策略。

### 评估指标
- 最终模型在训练集/测试集上的性能（相对于贪婪策略的改进百分比 \( \Delta_{\text{greedy}} \)）。
- 训练期间验证奖励曲线（收敛速度）。
- 10 个随机种子的标准差（稳定性）。
- 训练时间。

### 超参数调优
- 每个环境、每个算法都进行了网格搜索（3‑30 次运行），使用相同 episode 数（基于 PPO 优化）确保公平。

## 4. 资源与算力

- **硬件**：所有实验在**MacBook Air M3** 上运行，使用 Julia 编程语言。
- **GPU**：未使用 GPU。
- **训练时间**：每个算法运行时间根据环境和复杂性不同：
  - 静态环境：WSPP/SMSP 约 9‑15 分钟；SVSP 中 SRL 23 分钟，PPO 3 分钟，SIL 11 分钟。
  - 动态环境：DVSP 中 SRL 31 分钟，PPO 3 分钟；DAP 中 SRL/SIL 约 31 分钟；GSPP 中约 34 分钟（SRL）。
- **说明**：算力消耗中等，无 GPU 需求。

## 5. 实验数量与充分性

- **总体实验量**：
  - 每个方法在 6 个环境上各运行 10 个随机种子。
  - 每个环境有独立训练/验证/测试数据集。
  - 超参数通过网格搜索（3‑30 次训练）确定。
- **充分性评价**：
  - 覆盖了静态与动态、外生与内生不确定性等多种场景，具有代表性。
  - 与 SIL、PPO、专家、贪婪策略的对比全面，且使用相同的 COAML 流水线和 critic 架构，保证了公平。
  - 缺乏与 Soft Actor‑Critic、神经组合优化方法（如注意力模型、图神经网络）的直接对比，作者在附录中说明了原因（架构适配问题）。
  - 未做消融实验（如单独分析扰动标准差、温度参数的影响），但超参数敏感性已隐含在网格搜索中。
- **总体评价**：实验设计合理、结果可信，但对比方法范围可进一步扩展。

## 6. 主要结论与发现

- **性能**：
  - 静态环境：SRL 性能与 SIL 相当，优于 PPO 5‑54%；SIL 在静态环境下表现良好但需要专家演示。
  - 动态环境：SRL 比 SIL 提升最高 78%（GSPP），比 PPO 提升最高 92%（GSPP），在 DVSP 和 DAP 中也显著优于 PPO。
  - SRL 在 GSPP 中甚至超过了在线最优专家策略 79%，表明其能学习到超越简单贪心的策略。
- **稳定性**：SRL 和 SIL 的验证奖励标准差远低于 PPO（最高 80 倍），在组合动作空间中更为稳健。
- **收敛速度**：SRL 在大多数动态环境中收敛速度与 SIL 相近，但略慢于 SIL（因为需要探索而非直接模仿），远快于 PPO。
- **计算成本**：SRL 训练时间通常是 PPO 的 5‑10 倍，CO 层越复杂开销越大。但考虑到性能提升，成本可接受。

## 7. 优点

- **方法创新**：首次将 CO 层嵌入 actor‑critic 框架，利用 Fenchel‑Young 损失实现**端到端**的 RL 训练，**无需专家演示**。
- **几何理论**：提供了采样原始‑对偶算法的几何解释，连接了结构化学习与 RL，增强了方法可解释性。
- **适用范围广**：方法对动作空间的分解性无要求，可应用于各种组合优化问题（路径、调度、分类等）。
- **实验全面**：覆盖静态/动态、外生/内生不确定性，多环境、多基线对比，展示了 SRL 在复杂场景下的优越性和稳定性。
- **代码开源**：提供完整 Julia 代码，便于复现和后续研究。

## 8. 不足与局限

- **计算开销**：SRL 需要多次求解 CO 层（每个更新步 m ≈ 40 次），尤其在 CO 层复杂时训练时间显著增加，不利于大规模实时应用。
- **额外超参数**：需要调节三个噪声标准差（\( \sigma_f, \sigma_b, \varepsilon \)）和温度 \( \tau \)，调参工作量较高。
- **对比范围有限**：
  - 未与 SAC 等现代 off‑policy 算法、以及专门的神经组合优化方法（如 Attention Model、GNN）比较。
  - 未进行消融研究以明确每个组件的贡献（如采样数量、正则化类型）。
- **收敛速度**：在 DAP 和 GSPP 中，SRL 收敛比 SIL 慢 10‑150 个 episode，因为需要依靠 critic 引导而非直接利用专家目标。
- **Critic 依赖采样**：SRL 通过采样估计目标动作 \( \hat{a} \)，可能不是最优的；当采样数不足或 critic 偏差大时可能影响性能。
- **应用限制**：方法依赖可高效求解的 CO 层；对于 NP‑hard 的在线问题，求解 CO 可能成为瓶颈。
- **理论收敛性**：论文未提供 SRL 的收敛性证明（仅给出了静态 case 的 primal‑dual 联系），在一般 C‑MDP 中的理论保证有待建立。

（完）
