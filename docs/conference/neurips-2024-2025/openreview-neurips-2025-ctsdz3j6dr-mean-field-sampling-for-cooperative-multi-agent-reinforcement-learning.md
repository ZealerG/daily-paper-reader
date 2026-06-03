---
title: Mean-Field Sampling for Cooperative Multi-Agent Reinforcement Learning
title_zh: 面向合作多智能体强化学习的平均场采样
authors: "Emile Timothy Anand, Ishani Karmarkar, Guannan Qu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=CTsdZ3j6dR"
tags: ["query:graph-part"]
score: 8.0
evidence: 基于平均场采样的合作多智能体强化学习，用于并行决策
tldr: 提出SUBSAMPLE-MFQ算法，通过平均场采样和子采样策略，在多项式样本复杂度内学习大系统策略，并证明收敛到最优策略。该方法解决多智能体并行决策的维度灾难问题，与用户需求中的多智能体并行决策高度吻合。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ctsdz3j6dr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1201, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ctsdz3j6dr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ctsdz3j6dr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 619, \"height\": 269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ctsdz3j6dr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1462, \"height\": 464, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ctsdz3j6dr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 571, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ctsdz3j6dr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1501, \"height\": 1331, \"label\": \"Table\"}]"
motivation: 多智能体强化学习中，状态和动作空间随智能体数量指数增长。
method: 提出子采样平均场Q学习算法，基于子采样智能体学习并利用平均场近似。
result: 证明算法收敛速度随子采样数k以O(1/sqrt(k))减小。
conclusion: 为大规模多智能体系统提供了可扩展的强化学习方案。
---

## Abstract
Designing efficient algorithms for multi-agent reinforcement learning (MARL) is fundamentally challenging because the size of the joint state and action spaces grows exponentially in the number of agents. These difficulties are exacerbated when balancing sequential global decision-making with local agent interactions. In this work, we propose a new algorithm $\texttt{SUBSAMPLE-MFQ}$ ($\textbf{Subsample}$-$\textbf{M}$ean-$\textbf{F}$ield-$\textbf{Q}$-learning) and a decentralized randomized policy for a system with $n$ agents. For any $k\leq n$, our algorithm learns a policy for the system in time polynomial in $k$. We prove that this learned policy converges to the optimal policy on the order of $\tilde{O}(1/\sqrt{k})$ as the number of subsampled agents $k$ increases. In particular, this bound is independent of the number of agents $n$.

---

## 论文详细总结（自动生成）

# 论文《Mean-Field Sampling for Cooperative Multi-Agent Reinforcement Learning》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：多智能体强化学习（MARL）面临严重的“维度灾难”——联合状态-动作空间随智能体数量 \(n\) 指数级增长，导致传统 Q-learning（复杂度 \(O(|S||A|^n)\)）和平均场 MARL（复杂度 \(O(n^{|S||A|})\)）均无法处理大规模系统。
- **动机**：在合作式多智能体场景中，智能体具有同构性且系统存在全局与局部分层结构，能否设计一种算法，其样本复杂度与总智能体数 \(n\) 无关，而仅依赖于一个可控的小参数 \(k\)？
- **核心贡献**：提出 SUBSAMPLE-MFQ 算法，通过子采样 \(k\) 个局部智能体并运用平均场近似，在多项式时间（关于 \(k\)）内学到近似最优策略，且最优性差距以 \(\tilde{O}(1/\sqrt{k})\) 衰减，**该界与 \(n\) 无关**。

## 2. 论文提出的方法论

### 核心思想
- **系统模型**：包含一个全局智能体（global agent）和 \(n\) 个同构局部智能体（local agents）。状态和动作空间均为有限集。奖励结构分为全局项和局部项的均值。
- **子采样（Subsampling）**：随机选取大小为 \(k \leq n\) 的局部智能体子集 \(\Delta\)，仅基于这 \(k\) 个智能体构建一个“子 MDP”，并通过价值迭代学习该子系统的 Q 函数 \(\hat{Q}_k\)（对应确定性策略 \(\hat{\pi}_k\)）。
- **在线执行采样**：每一步，全局智能体均匀采样一个大小为 \(k\) 的子集，每个局部智能体均匀采样其余 \(k-1\) 个智能体，并应用已学的子策略 \(\hat{\pi}_k\) 决定动作。这构成一个随机策略 \(\pi_k\)。

### 关键技术细节
1. **两种实现模式**（Algorithm 1）：
   - **大状态/动作空间情形**（\(|Z_l|^k \leq |Z_l| k^{|Z_l|}\)）：使用标准 Q-learning 的子采样版本，Q 表大小为 \(|S_g||S_l|^k|A_g||A_l|^k\)。
   - **大智能体数情形**（反之）：使用平均场 Q-learning 的子采样版本，Q 表大小为 \(|S_g||S_l||\mu_{k-1}(Z_l)||A_g||A_l|\)，其中 \(\mu_{k-1}(Z_l)\) 为离散经验分布空间。
2. **经验 Bellman 算子**（公式 (8)(10)）：利用 \(m\) 个采样样本近似下一状态期望，保证 \(\gamma\)-压缩性。
3. **随机策略 \(\pi_k\)**（Algorithm 2）：在每步随机抽取子集，所有动作由子策略 \(\hat{\pi}_k\) 计算得到，实现去中心化执行。

### 核心理论保证
- ** Lipschitz 连续性**（Theorem E.3）：\(\hat{Q}_k^*\) 关于经验分布的总变差距离是 Lipschitz 的，系数与奖励界有关。
- **总变差界**（Theorem D.2）：基于采样无替换的 DKW 不等式，经验分布与真实分布的距离以高概率为 \(O(\sqrt{(n-k+1)/(nk)})\)。
- **性能差引理**（Performance Difference Lemma）结合上述结果，得到主定理（Theorem 4.4）：  
  \[
  V^{\pi^*} - V^{\pi_k} \leq \tilde{O}\left(\frac{1}{\sqrt{k}}\right),\quad \text{with high probability}.
  \]
- **Bellman 噪声控制**（Lemma 4.3）：适当地选取样本数 \(m\) 可将估计误差也控制在 \(\tilde{O}(1/\sqrt{k})\)。

## 3. 实验设计

- **场景**：
  - **高斯挤压（Gaussian squeeze）**：\(n\) 个同构智能体选择动作 \(a_i\)，共同最大化 \(r(x)=xe^{-(x-\mu)^2/\sigma^2}\)，其中 \(x=\sum a_i\)。模拟交通拥堵或资源竞争。
  - **约束探索（Constrained exploration）**：全局智能体引导局部智能体在一个 \(M\times M\) 网格中探索，奖励设计鼓励局部智能体跟随全局智能体活动范围（如仓库危险区域清理）。
- **数据集**：所有数据为模拟生成，无真实数据集。
- **对比方法**：
  - 当 \(k=n\) 时，SUBSAMPLE-MFQ 退化为标准值迭代或平均场 Q-learning，因此以 \(k=n\) 的结果作为最优基线。
  - 未与其他 MARL 算法（如 QMIX、MADDPG、MAPPO）进行对比。
- **评价指标**：累积折扣奖励（Reward optimality gap）、计算时间（分钟）。

## 4. 资源与算力

- 论文明确说明（Appendix B）：所有实验在 **2核 CPU 服务器、12GB RAM** 上运行。
- **未使用 GPU**，也未提供训练时长具体数值（仅给出图2b中计算时间随 \(k\) 的变化）。
- 算力水平较低，实验规模也较小（最大 \(n=50\)）。

## 5. 实验数量与充分性

- **实验组数**：
  - 约束探索：\(n=8\)，\(m=20\)，变化 \(k\) 值。
  - 高斯挤压：小规模 \(n=8\) 和大规模 \(n=50\)，\(m=20\)，变化 \(k\)。
- **消融实验**：未专门设计消融实验（如对 \(m\) 的敏感性、不同随机种子等）。
- **充分性评价**：
  - **优点**：验证了理论的两个主要趋势：① 随着 \(k\to n\) 累积奖励单调递增（图2a、2c）；② 计算时间随 \(k\) 指数增长（图2b），正好体现了算法复杂度优势。
  - **不足**：① 场景过于简单，仅合成数据，缺少真实世界应用；② 未与当前主流 MARL 算法（如基于值分解或策略梯度的方法）对比；③ 未报告多次运行的平均值和方差（仅给出误差条，但未说明是标准差还是极值）；④ 未展示 \(k\) 对不同环境参数（如 \(|S_l|,|A_l|\)）的敏感性。

## 6. 论文的主要结论与发现

1. **理论上**：SUBSAMPLE-MFQ 能以高概率学习一个策略，其与最优策略的价值差距为 \(\tilde{O}(1/\sqrt{k})\)，且该界独立于总智能体数 \(n\)。当选择 \(k=O(\log n)\) 时，可实现亚多项式（polylog）的样本复杂度，即指数级加速。
2. **实验上**：验证了最优性差距随 \(k\) 增加而单调减小，计算时间随 \(k\) 呈指数增长，与理论预期一致。
3. **扩展性**：算法可推广到随机奖励、离策略学习、连续状态/动作空间（线性 MDP）等场景，均保持类似的理论保证。

## 7. 优点

- **理论创新性强**：首次提出利用子采样结合平均场来独立于 \(n\) 控制复杂度，证明技巧新颖（如使用采样无替换的 DKW 不等式、Lipschitz 连续性等）。
- **样本复杂度大幅度突破**：传统方法为 \(O(\text{poly}(n))\) 或 \(O(\exp(n))\)，而本方法为 \(O(\text{poly}(k))\)，当 \(k=O(\log n)\) 时得到 polylog 复杂度。
- **算法简单实用**：学习阶段只需处理 \(k\) 个智能体的子 MDP，执行阶段仅需局部子集采样，易于分布式实现。
- **提供了多个扩展**（随机奖励、离策略、连续空间），显示了框架的灵活性。

## 8. 不足与局限

- **实验过于简单**：仅在小规模合成环境中进行，缺乏与真实世界应用或复杂 MARL benchmark（如 SMAC、Melting Pot）的对比。
- **与其他算法对比不足**：未与流行的值分解（QMIX、VDN）或策略梯度（MAPPO、MADDPG）方法比较，难以评估实际性能差距。
- **同构性强依赖**：理论假设局部智能体完全同构；虽提及可用类型扩展，但实验未涉及。
- **缺乏下界匹配**：理论上仅给出上界，未证明下界，无法判断 \(\tilde{O}(1/\sqrt{k})\) 是否最优。
- **未考虑竞争环境**：模型假设完全合作，不适用于竞争或混合场景。
- **在线 regret 分析缺失**：论文未在在线学习或无 regret 设定下进行理论分析，限制了在实时学习场景的应用。

（完）
