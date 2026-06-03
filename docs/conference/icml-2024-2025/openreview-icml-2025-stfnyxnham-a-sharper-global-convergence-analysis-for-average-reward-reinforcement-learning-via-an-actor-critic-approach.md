---
title: A Sharper Global Convergence Analysis for Average Reward Reinforcement Learning via an Actor-Critic Approach
title_zh: 通过演员-评论家方法对平均奖励强化学习进行更精确的全局收敛分析
authors: "Swetha Ganesh, Washim Uddin Mondal, Vaneet Aggarwal"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=stfnyxnhAm"
tags: ["query:graph-part"]
score: 9.0
evidence: 平均奖励强化学习与演员-评论家算法收敛性分析
tldr: 本文针对平均奖励强化学习问题，提出基于多层蒙特卡洛的自然演员-评论家算法（MLMC-NAC），首次在演员-评论家框架下实现全局收敛速率，解决了现有方法可扩展性差和迭代复杂度高的问题。理论证明了收敛率，为平均奖励MDP提供了更优的保证。
source: ICML-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-stfnyxnham/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1542, \"height\": 496, \"label\": \"Table\"}]"
motivation: 现有平均奖励强化学习收敛性保证次优且可扩展性差。
method: 提出MLMC-NAC算法，结合多层蒙特卡洛估计与自然梯度。
result: 首次实现全局收敛速率。
conclusion: 为平均奖励强化学习提供了更优的理论保证。
---

## Abstract
This work examines average-reward reinforcement learning with general policy parametrization. Existing state-of-the-art (SOTA) guarantees for this problem are either suboptimal or hindered by several challenges, including poor scalability with respect to the size of the state-action space, high iteration complexity, and a significant dependence on knowledge of mixing times and hitting times. To address these limitations, we propose a Multi-level Monte Carlo-based Natural Actor-Critic (MLMC-NAC) algorithm. Our work is the first to achieve a global convergence rate of $\tilde{\mathcal{O}}(1/\sqrt{T})$ for average-reward Markov Decision Processes (MDPs) (where $T$ is the horizon length), using an Actor-Critic approach. Moreover, the convergence rate does not scale with the size of the state space, therefore even being applicable to infinite state spaces.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：平均奖励强化学习（Average Reward RL）在机器人、交通、通信网络、医疗等实际应用中至关重要。现有基于演员-评论家（Actor-Critic）的方法存在三个主要缺陷：（1）全局收敛速率仅为 $\tilde{\mathcal{O}}(T^{-1/4})$，远低于最优的 $\tilde{\mathcal{O}}(T^{-1/2})$；（2）依赖对混合时间和命中时间的精确知识，这在实践中难以获得；（3）可扩展性差，尤其不适用于大规模或无限状态空间。
- **核心问题**：能否设计一种实用且可扩展的演员-评论家算法，在平均奖励无限时域MDP中，对一般参数化策略实现与状态空间大小无关的 $\tilde{\mathcal{O}}(T^{-1/2})$ 全局收敛率？
- **整体含义**：本文通过提出基于多层蒙特卡洛（MLMC）的自然演员-评论家算法（MLMC-NAC），从理论上回答了这个问题，首次在演员-评论家框架下达到最优收敛速率，且不依赖状态空间大小，为平均奖励RL提供了更优的理论保证。

## 2. 论文提出的方法论

- **核心思想**：
  - 将算法分为两个主要子程序：**自然策略梯度（NPG）子程序**用于估计NPG方向并更新策略参数；**评论家子程序**通过时序差分（TD）学习估计平均奖励和值函数。两个子程序均采用**多层蒙特卡洛（MLMC）梯度估计器**，消除了对混合时间的依赖。
  - 通过精细的误差分解，将全局收敛误差与NPG估计的偏差和二阶误差联系起来，并进一步将偏差项从 $\mathbb{E}\|\xi_t - \xi^*\|$ 改进为 $\|\mathbb{E}[\xi_t] - \xi^*\|$，显著降低了上界。
  - 利用MLMC方法降低Markov采样导致的偏置，同时避免使用AdaGrad等复杂优化器，仅通过经典SGD配合恰当的超参数即可实现最优速率。

- **关键技术细节**：
  - **算法流程**：运行 $K$ 个外部循环，每个循环 $k$ 中：
    - 先执行 $H$ 步内部循环更新评论家参数 $\xi_k = [\eta_k, \zeta_k]^T$（平均收益和值函数参数），使用MLMC估计梯度。
    - 再执行 $H$ 步内部循环更新NPG方向 $\omega_k$，同样使用MLMC估计梯度。
    - 最后更新策略参数 $\theta_{k+1} = \theta_k + \alpha \omega_k$。
  - **MLMC估计**：生成服从几何分布长度的轨迹，计算不同层级样本均值之差，组合成最终估计。能在保持与 $T_{\max}$ 个样本均值相同偏置阶数的同时，平均仅需 $\mathcal{O}(\log T_{\max})$ 个样本。
  - **理论分析**：基于**一般线性递归**（定理2）统一分析NPG和评论家更新，利用MLMC估计的偏置和方差性质（引理2、3），最终得到全局收敛率（定理1）。

- **公式/算法流程说明**：详见论文算法1，包含两个阶段的内部循环，使用几何分布采样确定轨迹长度，并利用MLMC组合公式更新参数。

## 3. 实验设计

- **本文为纯理论分析论文，未进行任何实验或数值验证。** 研究完全集中于理论收敛性证明，未提供数据集、对比方法或Benchmark。

## 4. 资源与算力

- **未提及任何计算资源或算力信息。** 由于无实验，故不涉及GPU型号、数量、训练时长等。

## 5. 实验数量与充分性

- **无实验，因此无法评价实验充分性。** 论文的贡献全在于理论证明，需要依赖后续工作或实验验证其实际效果。

## 6. 论文的主要结论与发现

- 提出的MLMC-NAC算法在平均奖励MDP中实现全局收敛速率 $\tilde{\mathcal{O}}(1/\sqrt{T})$（其中 $T$ 为总步数），这是演员-评论家方法在该设定下的最优结果。
- 收敛速率不依赖于状态空间大小 $|S|$，因此可应用于无限状态空间。相比现有直接策略梯度方法，不依赖混合时间和命中时间的先验知识，更具实用性。
- 通过精细的误差分解（尤其是利用 $\|\mathbb{E}[\xi_t] - \xi^*\|$ 代替 $\mathbb{E}\|\xi_t - \xi^*\|$），将收敛率从 $\tilde{\mathcal{O}}(T^{-1/4})$ 提升至 $\tilde{\mathcal{O}}(T^{-1/2})$。
- 证明了MLMC估计在Markov噪声下能有效降低偏置，并给出了通用线性递归的收敛定理（定理2），可独立应用于其他算法分析。
- 与现有方法的对比（表1）：与UCRL2、PSRL、PPGAE、PHPG、NAC-CFA、MAC等方法相比，MLMC-NAC在支持无限状态空间、模型无关、一般参数化等方面均具优势，且收敛率最优。

## 7. 优点

- **理论贡献突出**：首次在演员-评论家框架下获得 $\tilde{\mathcal{O}}(T^{-1/2})$ 全局收敛率，显著优于前人 $\tilde{\mathcal{O}}(T^{-1/4})$ 的结果。
- **方法创新**：将MLMC应用于平均奖励演员-评论家，巧妙平衡了偏置与方差，无需混合时间先验知识，更实际。
- **分析精致**：通过一般线性递归统一分析两个子程序，并利用更紧的偏差项 $\|\mathbb{E}[\xi_t] - \xi^*\|$ 得出更优界限。
- **可扩展性强**：收敛率与状态空间大小无关，适用于大规模或无限状态空间，弥补了直接策略梯度方法的不足。
- **假设合理**：所有假设（如Fisher非退化策略、线性评论家、L平滑目标函数）均为领域常见，理论框架通用。

## 8. 不足与局限

- **缺乏实验验证**：纯理论工作，未提供数值仿真或实际任务验证，实际性能有待检验。
- **评论家线性假设**：论文假设值函数可由线性特征近似，限制了其处理复杂非线性任务的能力。作者指出将神经网络评论家扩展至平均奖励设定仍为开放问题。
- **依赖某些强假设**：例如混合时间 $t_{\text{mix}}$ 有限、Fisher矩阵正定等，虽然在理论分析中常见，但实际MDP可能不严格满足。
- **隐藏常数较大**：收敛率中的大O记号隐藏了与 $t_{\text{mix}}$、$\mu$、$G_1$ 等参数的多项式依赖，实际收敛可能较慢。
- **未考虑弱通信MDP**：部分相关工作（如Wei et al. 2020）能在弱通信MDP假设下工作，而本文需要马尔可夫链每步策略都遍历（Assumption 1），要求更强。
- **复杂度分析不完整**：虽然给出了样本复杂度，但未讨论空间复杂度或实际运行时间。

（完）
