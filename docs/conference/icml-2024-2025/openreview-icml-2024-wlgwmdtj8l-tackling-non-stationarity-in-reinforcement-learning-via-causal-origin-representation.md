---
title: Tackling Non-Stationarity in Reinforcement Learning via Causal-Origin Representation
title_zh: 通过因果起源表示应对强化学习中的非平稳性
authors: "Wanpeng Zhang, Yilin Li, Boyu Yang, Zongqing Lu"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=WLGWMDtj8L"
tags: ["query:graph-part"]
score: 9.0
evidence: 处理非平稳性的强化学习算法
tldr: 针对强化学习中的非平稳性问题，现有方法通常需要环境的先验知识来显式建模变化。本文提出COREP算法，通过隐式追踪非平稳性的因果起源，引导状态表示更新，从而在不依赖先验知识的情况下提升策略学习性能。实验表明该方法在多个非平稳环境中优于基线方法，为复杂现实场景中的RL应用提供了新思路。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 817, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1733, \"height\": 738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1747, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 1023, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 678, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1020, \"height\": 701, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1761, \"height\": 1113, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1770, \"height\": 1361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1678, \"height\": 1239, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1775, \"height\": 1247, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1326, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1330, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wlgwmdtj8l/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1329, \"height\": 642, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-wlgwmdtj8l/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1746, \"height\": 1000, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-wlgwmdtj8l/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1753, \"height\": 575, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-wlgwmdtj8l/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1766, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-wlgwmdtj8l/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1767, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-wlgwmdtj8l/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1235, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-wlgwmdtj8l/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 657, \"height\": 621, \"label\": \"Table\"}]"
motivation: 现有方法依赖先验知识显式建模环境变化，难以应对复杂的非平稳性。
method: 提出COREP算法，通过引导更新机制隐式追踪非平稳性的因果起源，调整状态表示。
result: 在多个非平稳环境中，COREP优于现有基线方法，提升了策略学习效率。
conclusion: COREP为无需先验知识的非平稳RL提供了有效方案。
---

## Abstract
In real-world scenarios, the application of reinforcement learning is significantly challenged by complex non-stationarity. Most existing methods attempt to model changes in the environment explicitly, often requiring impractical prior knowledge of environments. In this paper, we propose a new perspective, positing that non-stationarity can propagate and accumulate through complex causal relationships during state transitions, thereby compounding its sophistication and affecting policy learning. We believe that this challenge can be more effectively addressed by implicitly tracing the causal origin of non-stationarity. To this end, we introduce the Causal-Origin REPresentation (COREP) algorithm. COREP primarily employs a guided updating mechanism to learn a stable graph representation for the state, termed as causal-origin representation. By leveraging this representation, the learned policy exhibits impressive resilience to non-stationarity. We supplement our approach with a theoretical analysis grounded in the causal interpretation for non-stationary reinforcement learning, advocating for the validity of the causal-origin representation. Experimental results further demonstrate the superior performance of COREP over existing methods in tackling non-stationarity problems. The code is available at https://github.com/PKU-RL/COREP.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与研究动机
- **问题**：真实世界中的强化学习面临复杂的非平稳性挑战（环境动态随时间变化）。现有方法大多需要环境的先验知识来显式建模变化，这在现实场景中往往不可行。
- **核心观点**：非平稳性可通过状态转移中的复杂因果关系传播和积累，从而加剧其复杂性并影响策略学习。本文提出应当**隐式追踪非平稳性的因果起源**，而非显式建模。
- **整体目标**：设计一种无需先验知识、能够稳定应对非平稳性的强化学习算法。

## 2. 方法论
### 2.1 核心思想
- 将非平稳环境视为多个平稳子环境的混合，非平稳性表现为子环境分布的时变。
- 引入**因果起源表示（Causal-Origin Representation）**，学习对非平稳性鲁棒的状态图结构表示。
- 基于图注意力网络（GAT）与TD误差引导更新机制实现。

### 2.2 关键技术细节
- **因果解释**：将动力学函数改写为含掩码（mask）的形式，表示状态元素间的因果依赖。提出**环境共享联合图（Environment-shared Union Graph）**，由各子环境的最大祖先图（MAG）合并得到，并证明其仍是MAG。
- **双GAT结构**：
  - **核心GAT（Core-GAT）**：学习稳定图结构，通过TD误差检测机制选择性更新（仅当近期TD误差超出置信区间时更新）。
  - **通用GAT（General-GAT）**：持续更新，补偿核心GAT可能遗漏的边缘信息。
  - 两者输出拼接形成最终因果起源表示。
- **与VAE结合**：将因果起源表示输入VAE，学习潜在表示h，用于策略优化。
- **损失函数**：包括策略优化损失、引导损失、MAG结构正则化、稀疏正则化、VAE损失。

### 2.3 算法流程（文字说明）
1. 收集轨迹，更新经验回放缓冲区。
2. 从缓冲区采样批次，将状态映射为节点特征，计算加权邻接矩阵。
3. 计算近期TD误差均值，判断是否在置信区间内，以决定是否冻结/解冻核心GAT。
4. 分别通过核心GAT和通用GAT得到图表示，拼接后输入VAE编码器得到潜在表示h。
5. 解码重建状态，计算各损失，反向传播更新参数。
6. 将TD误差存入缓冲区，重复迭代。

## 3. 实验设计
### 3.1 数据集/场景
- 使用**DeepMind Control Suite**中的12个环境，涵盖简单（如Cartpole Swingup）到高维（如Quadruped Walk）
- 人为引入非平稳噪声：按式(4.1)添加周期性噪声，同时包含**episode内**和**跨episode**的非平稳性。

### 3.2 基准对比方法
- **FN-VAE**：SOTA非平稳RL方法
- **VariBAD**：元强化学习算法
- **PPO**：标准强化学习算法
- **Oracle**：完全知晓非平稳信息的上界

### 3.3 实验设置
- 在(W+A)-EP、W-EP、A-EP三种非平稳设置下测试。
- 不同非平稳度（α_d 从0.2到1.8）实验。
- 每个实验5个随机种子。

## 4. 资源与算力
- **硬件**：Intel I9-12900K (24核)，Nvidia RTX 3090 (24GB) × 2，RAM 256GB
- **训练时长**：每个环境单次试验12~42小时不等（见表E.2），复杂度高者更长（Quadruped Walk需42小时）
- 论文未明确说明总GPU小时数，但提供了详细硬件配置。

## 5. 实验数量与充分性
- **数量**：在12个环境上进行主实验，外加消融实验、不同非平稳度实验、超参数敏感度实验、图结构可视化。
- **充分性**：
  - 消融实验覆盖了去除各组件（COREP整体、VAE、引导机制、稀疏正则、MAG正则、单GAT）的情况。
  - 在三种非平稳设置下都进行了消融，验证设计的必要性。
  - 超参数λ1、λ2的敏感度分析显示性能稳定。
  - 可视化核心GAT与通用GAT的邻接矩阵，验证双GAT的分工。
- **公平性**：所有基线使用相同PPO骨干网络，超参数一致；Oracle提供性能上界。对比方法均为公开SOTA或代表性方法。

## 6. 主要结论与发现
- COREP在所有12个环境上均优于FN-VAE、VariBAD、PPO，尤其在复杂环境（Swimmer6、Quadruped Walk等）优势显著。
- 双GAT结构及TD误差引导更新是性能提升的关键（消融实验证明）。
- COREP对不同非平稳程度（低至0.2，高至1.8）表现稳定，而基线方法波动大。
- 理论分析证明环境共享联合图仍为MAG，为算法提供支持。

## 7. 优点
- **新颖的因果视角**：将非平稳性解释为子环境混合，提供理论支撑。
- **无需先验知识**：不要求显式建模变化，通过隐式追踪因果起源适应非平稳性。
- **模块化设计**：COREP可灵活集成到现有RL算法（如PPO）中。
- **全面的实验验证**：涵盖多环境、多非平稳类型、多维度消融，结论可靠。
- **代码开源**便于复现。

## 8. 不足与局限
- **扩展性问题**：高维状态空间下，图表示的计算开销大，可能面临可扩展性挑战。论文在讨论中承认这一点。
- **只测试了模拟环境**：实验限于DeepMind Control Suite，未涉及真实机器人或更复杂现实场景。
- **非平稳模式有限**：仅测试了三角函数噪声，未覆盖其他类型（如突变、漂移等）。
- **理论分析尚浅**：虽然证明了联合图是MAG，但未提供收敛性保证或最优性界。
- **需要调参**：尽管敏感度低，但仍有λ1、λ2等超参数，实际应用可能需要调整。

（完）
