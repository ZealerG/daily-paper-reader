---
title: Multi-objective Linear Reinforcement Learning with Lexicographic Rewards
title_zh: 词典序奖励的多目标线性强化学习
authors: "Bo Xue, Dake Bu, Ji Cheng, Yuanyu Wan, Qingfu Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=RTHTyTsRT3"
tags: ["query:graph-part"]
score: 7.0
evidence: 词典序奖励的多目标线性强化学习
tldr: 本文研究词典序奖励结构下的多目标强化学习，其中目标按层次优先级排序。提出首个具有可证明遗憾保证的多目标强化学习算法，为每个目标顺序优化。理论证明了算法的有效性，填补了多目标强化学习理论空白。
source: ICML-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-rthtytsrt3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rthtytsrt3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 385, \"label\": \"Table\"}]"
motivation: 多目标强化学习理论研究不足，缺乏遗憾保证。
method: 针对词典序奖励设计算法，按优先级优化。
result: 首个具有遗憾保证的MORL算法。
conclusion: 推进了多目标强化学习的理论发展。
---

## Abstract
Reinforcement Learning (RL) with linear transition kernels and reward functions has recently attracted growing attention due to its computational efficiency and theoretical advancements. However, prior theoretical research in RL has primarily focused on single-objective problems, resulting in limited theoretical development for multi-objective reinforcement learning (MORL). To bridge this gap, we examine MORL under lexicographic reward structures, where rewards comprise $m$ hierarchically ordered objectives. In this framework, the agent the agent maximizes objectives sequentially, prioritizing the highest-priority objective before considering subsequent ones. We introduce the first MORL algorithm with provable regret guarantees. For any objective $i \in \\{1, 2, \ldots, m\\}$, our algorithm achieves a regret bound of $\widetilde{O}(\Lambda^i(\lambda) \cdot \sqrt{d^2H^4 K})$, where $\Lambda^i(\lambda) = 1 + \lambda + \cdots + \lambda^{i-1}$, $\lambda$ quantifies the trade-off between conflicting objectives, $d$ is the feature dimension, $H$ is the episode length, and $K$ is the number of episodes. Furthermore, our algorithm can be applied in the misspecified setting, where the regret bound for the $i$-th objective becomes $\widetilde{O}(\Lambda^i(\lambda)\cdot(\sqrt{d^2H^4K}+\epsilon dH^2K))$, with $\epsilon$ denoting the degree of misspecification.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：传统强化学习（RL）理论研究大多聚焦于单目标问题，而现实世界中的决策任务往往需要同时优化多个、甚至相互冲突的目标（例如自动驾驶中的安全性与效率、能源管理中的成本与可持续性）。现有工作中的多目标强化学习（MORL）主要依赖标量化（加权求和）或帕累托前沿构建，但标量化需要精确的权重先验，帕累托方法则假设所有目标同等重要，不适合目标优先级明确（如用户偏好中价格 > 位置 > 服务）的场景。
- **整体含义**：本文引入**词典序奖励结构**（lexicographic reward structure），将目标按层次优先级排序，代理按优先级顺序依次优化。在此框架下，作者首次提出了具有**可证明遗憾保证**的多目标强化学习算法（LLRL），填补了多目标线性强化学习理论的空白。论文证明了算法的遗憾界，并在近似线性模型（misspecified setting）下也给出了理论保证。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用线性马尔可夫决策过程（Linear MOMDP）的结构，将每个目标的Q函数表示为特征向量的线性形式。由于词典序奖励下Bellman最优性方程不成立（见Proposition 2），不能直接采用贪心动作选择。作者设计了一种**多阶段动作细化策略**，通过逐步缩小的置信阈值（$2^{-s}$）来平衡探索与利用，并引入词典序动作消除（Lexicographic Action Elimination, LAE）子程序，优先保留高优先级目标的最优动作。
- **关键技术细节**：
  - **线性MOMDP建模**：假设转移概率和每个目标的奖励函数均为特征映射 $\phi(x,a)$ 的线性函数，存在未知测度 $\mu_h$ 和未知向量 $\theta_i^h$。
  - **算法流程**（Algorithm 1, LLRL）：每轮（k=1..K）的每个步骤h，初始化候选动作集 $A_s = A$，迭代进行三个阶段：
    1. 如果所有动作的置信范数 $\|\phi(x,a)\|_{U_h} \le 1/\sqrt{K}$，则调用LAE（算法2）生成最终动作集，随机选动作。
    2. 如果存在动作满足 $\|\phi(x,a)\|_{U_h} > 2^{-s}$，直接选择该动作（高不确定性优先探索）。
    3. 否则，调用LAE细化候选集（阈值 $2^{-s}$），并将阶段 $s$ 加1。
  - **词典序动作消除（LAE, Algorithm 2）**：按目标优先级顺序，对于第 $i$ 个目标，计算当前候选集中估计Q值最大的动作 $\hat{a}_{k,h}^i$，然后保留与 $\hat{a}_{k,h}^i$ 的Q值差距不超过 $(2+4\lambda+\cdots+4\lambda^{i-1})\beta_k C$ 的动作。$C$ 为当前阶段的阈值（$1/\sqrt{K}$ 或 $2^{-s}$），$\beta_k$ 为置信参数。
  - **策略更新**：每轮结束后，采用最小二乘回归更新每个目标的Q函数估计 $\hat{Q}_h^i(x,a)=\langle \hat{w}_h^i, \phi(x,a)\rangle$，其中 $\hat{w}_h^i$ 通过岭回归得到。更新过程从最后一层向第一层反向进行。

## 3. 实验设计

- 本文是**纯理论论文**，未包含任何实际实验或仿真。所有结果均以数学定理和证明形式呈现。
- 文中没有使用任何数据集、benchmark场景，也没有对比其他算法的实验评估。唯一对比（表1）是与其他单目标线性RL算法的理论遗憾界比较。

## 4. 资源与算力

- 论文未提及任何计算资源、GPU型号、训练时长等信息。由于是理论工作，不涉及实际计算需求。

## 5. 实验数量与充分性

- 没有实验，因此无法评估实验的充分性、客观性、公平性。所有结论均基于理论分析。

## 6. 主要结论与发现

- **定理1**：对于精确线性MOMDP，LLRL算法在每个目标 $i$ 上的遗憾界为 $\widetilde{O}(\Lambda^i(\lambda) \cdot \sqrt{d^2 H^4 K})$，其中 $\Lambda^i(\lambda)=1+\lambda+\cdots+\lambda^{i-1}$。该界在 $d$ 和 $K$ 的阶上与单目标最优算法（He et al., 2023）一致，且首要目标因 $\Lambda^1=1$ 而具有更紧的界（比Jin et al., 2020 改进$d$因子）。
- **定理2**：对于 $\epsilon$ -近似线性MOMDP，遗憾界变为 $\widetilde{O}(\Lambda^i(\lambda)\cdot(\sqrt{d^2 H^4 K}+\epsilon d H^2 K))$，与 $\epsilon$ 线性相关，体现了对模型规范误差的鲁棒性。
- 本文是第一个在词典序多目标线性强化学习中获得可证明遗憾保证的工作。

## 7. 优点

- **理论贡献**：首次为词典序MORL提供了严格的遗憾分析，填补了该方向的理论空白。
- **算法设计巧妙**：面对Bellman最优性失效的挑战，设计了多阶段动作细化与词典序动作消除机制，通过几何衰减的置信阈值保证了最优动作的保留，同时控制了累积次优性。
- **鲁棒性**：算法自然扩展到近似线性模型，仅需微小修改即可保持理论保证，实用性更强。
- **性能对比**：在主导阶 $K$ 上与单目标最优算法持平，且首要目标项与He et al. (2023) 在 $d$ 和 $K$ 上近乎一致（表1）。

## 8. 不足与局限

- **缺乏实验验证**：纯理论工作，未在真实或仿真环境中验证算法效果，实际性能未知。
- **强假设依赖**：
  - 线性MDP假设限制了应用范围，许多实际问题未必满足精确线性结构。
  - 词典序假设中引入了参数 $\lambda$ 来量化目标间的折中（Assumption 1），该参数在实际中难以准确获取，且文章未讨论其敏感度。
  - 要求特征映射 $\phi$ 已知且范数有界，实际中可能未知。
- **计算复杂度较高**：文中指出总复杂度含 $O(K^2)$ 项（因每轮反向更新需重新计算矩阵逆），相比单目标算法在 $K$ 较大时可能成为瓶颈（作者也提及可通过更新机制改进）。
- **局限性未深入探讨**：作者在结论中承认，算法是否能在无Assumption 1条件下达到类似界仍是一个开放问题。

（完）
