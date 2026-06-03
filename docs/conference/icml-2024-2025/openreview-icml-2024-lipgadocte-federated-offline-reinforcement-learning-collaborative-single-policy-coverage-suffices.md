---
title: "Federated Offline Reinforcement Learning: Collaborative Single-Policy Coverage Suffices"
title_zh: 联邦离线强化学习：协作单策略覆盖即可
authors: "Jiin Woo, Laixi Shi, Gauri Joshi, Yuejie Chi"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=LIPGadocTe"
tags: ["query:graph-part"]
score: 7.0
evidence: 联邦离线强化学习，多智能体并行决策
tldr: 离线强化学习在数据收集困难的应用中至关重要，但单智能体数据有限。该论文提出FedLCB-Q算法，通过重要性平均聚合多个智能体的本地Q函数，并设计悲观机制，实现了联邦离线RL下的高效协作学习，为多智能体并行决策提供了新方法。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-lipgadocte/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 842, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lipgadocte/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 748, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lipgadocte/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1756, \"height\": 693, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-lipgadocte/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1761, \"height\": 788, \"label\": \"Table\"}]"
motivation: 离线强化学习需要大量数据，联邦学习可让多个智能体协作利用离线数据。
method: 设计FedLCB-Q算法，采用新型学习率调度和重要性平均聚合Q函数。
result: 在表格型MDP中证明了算法的样本效率。
conclusion: 联邦离线RL可以通过协作显著提升学习效率。
---

## Abstract
Offline reinforcement learning (RL), which seeks to learn an optimal policy using offline data, has garnered significant interest due to its potential in critical applications where online data collection is infeasible or expensive. This work explores the benefit of federated learning for offline RL, aiming at collaboratively leveraging offline datasets at multiple agents. Focusing on finite-horizon episodic tabular Markov decision processes (MDPs), we design FedLCB-Q, a variant of the popular model-free Q-learning algorithm tailored for federated offline RL. FedLCB-Q updates local Q-functions at agents with novel learning rate schedules and aggregates them at a central server using importance averaging and a carefully designed pessimistic penalty term. Our sample complexity analysis reveals that, with appropriately chosen parameters and synchronization schedules, FedLCB-Q achieves linear speedup in terms of the number of agents without requiring high-quality datasets at individual agents, as long as the local datasets collectively cover the state-action space visited by the optimal policy, highlighting the power of collaboration in the federated setting. In fact, the sample complexity almost matches that of the single-agent counterpart, as if all the data are stored at a central location, up to polynomial factors of the horizon length. Furthermore, FedLCB-Q is communication-efficient, where the number of communication rounds is only linear with respect to the horizon length up to logarithmic factors.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：离线强化学习（Offline RL）利用预先收集的静态数据集学习最优策略，在在线交互成本高昂或不可行的场景中具有重要应用。然而，单个智能体的离线数据集往往覆盖不足，导致策略性能受限。
- **整体含义**：本文研究联邦离线强化学习（Federated Offline RL），通过多个智能体协作利用各自离线数据集来学习最优策略，既无需共享原始数据，又能突破单智能体数据覆盖的瓶颈。核心问题是：如何在联邦设置下引入悲观原则（pessimism）以避免过估计，同时保持样本效率和通信效率。

## 2. 论文提出的方法论

### 核心思想
- 设计了一种基于Q-learning的联邦离线强化学习算法 **FedLCB-Q**，在中央服务器和多个智能体之间迭代执行本地更新和全局聚合。
- 通过**重要性平均**（importance averaging）在服务器聚合时对智能体的本地Q值进行加权，降低不确定性的局部估计权重。
- 引入**全局悲观惩罚项**（global penalty），基于所有智能体的聚合访问计数计算，用于抑制未充分访问的状态-动作对上的过估计。
- 设计**新型学习率调度**，学习率在本地更新阶段快速衰减，限制本地Q值漂移；聚合后学习率重置，利用全局信息加速收敛。

### 关键技术细节
- 本地更新：每个智能体按其离线数据集中的轨迹逐episode更新Q值，学习率由全局计数和本地访问计数共同决定。
- 全局聚合：服务器计算加权平均Q值后减去全局惩罚项，并更新值函数和策略。
- 悲观惩罚项：基于聚合访问次数 `N_{k,h}(s,a)` 和惩罚常数计算，保证对不确定性的控制。
- 同步策略：采用指数同步（初始频繁、后期稀疏）或周期同步，在满足收敛条件的同时减少通信轮数。

### 算法流程（文字描述）
1. 初始化所有智能体和服务器的Q表、值函数为0。
2. 对于每个episode k，各智能体从本地数据集采样轨迹，更新本地Q值（基于当前学习率和本地计数）。
3. 若episode k为同步点，各智能体将本地Q值和访问计数发送至服务器。
4. 服务器根据公式计算加权平均Q值，减去全局惩罚项，更新全局值函数和策略，并将结果同步回各智能体。
5. 重复直至K个episode结束，输出最终Q值和策略。

## 3. 实验设计

- **论文性质**：本文为纯理论分析，**未进行任何实验验证**。因此没有使用具体数据集、benchmark或对比方法。
- **理论保证**：在有限时域表格型MDP（finite-horizon episodic tabular MDP）下，分析了样本复杂度和通信复杂度，并与单智能体最优界以及集中式全数据情形下的下界进行了理论比较。

## 4. 资源与算力

- **未明确提及**：论文未涉及任何实验，因此没有提及GPU型号、数量、训练时长等算力信息。

## 5. 实验数量与充分性

- **实验数量**：0。
- **充分性评估**：由于是理论工作，其贡献在于推导算法收敛性及样本/通信复杂度上界，而非实验验证。对于理论论文，其“充分性”体现在数学证明的严谨性和完整性。从公开内容看，证明包含详细的引理、分解和递归分析，逻辑链完整。

## 6. 论文的主要结论与发现

- **线性加速**：FedLCB-Q 的样本复杂度随智能体数量 M 线性下降（即 `O(H^7 S C*_avg / (M ε^2))`），表明协作可显著提升效率。
- **弱数据要求**：不要求每个智能体单独覆盖最优策略，只需各智能体数据集**集体覆盖**最优策略访问的状态-动作对，即 `C*_avg < ∞`。
- **通信高效**：采用指数同步策略时，通信轮数仅为 `O(H)`（与状态空间大小、episode总数和智能体数量几乎无关）。
- **几乎最优**：与集中式数据情形下的单智能体最优下界相比，FedLCB-Q 的样本复杂度仅差 `H^3` 因子，接近最优。

## 7. 优点

- **方法论创新**：首次在联邦离线 Q-learning 中有效结合悲观原则，同时解决本地更新带来的不确定性增长问题。
- **理论深度**：给出了完整的样本复杂度上界和通信复杂度分析，证明了线性加速和弱覆盖假设下的可行性。
- **参数设计巧妙**：重要性平均权重和学习率调度均基于全局与局部计数，自适应地平衡信息利用与不确定性。
- **通信轮次极少**：指数同步使通信需求几乎与问题规模无关，实用价值高。

## 8. 不足与局限

- **缺乏实验验证**：作为理论论文，未在真实或模拟环境中实验，其实际性能（例如对非表格MDP、连续状态空间或函数近似）未经验证。
- **最优性有差距**：样本复杂度中的 `H^7` 因子与集中式下界 `H^4` 仍有差距，虽在表格设置下可接受，但策略可能非最优。
- **假设较强**：假设所有智能体共享相同MDP、初始分布固定、每智能体数据量相等；实际中环境异质性、数据数量不均衡等挑战未处理。
- **仅限表格MDP**：未扩展至连续状态/动作空间或函数近似，限制了现实应用场景。
- **未讨论隐私保护**：虽未共享原始数据集，但服务器会聚合Q参数，仍需额外的差分隐私机制才能满足严格隐私要求。
- **同步策略参数依赖**：指数同步的初始参数（如 `τ1 = H`）需要已知horizon长度，可能不适用于未知环境。

（完）
