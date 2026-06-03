---
title: Near-Optimal Reinforcement Learning with Self-Play under Adaptivity Constraints
title_zh: 适应性约束下基于自对弈的接近最优强化学习
authors: "Dan Qiao, Yu-Xiang Wang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=pPNMhdYMaz"
tags: ["query:graph-part"]
score: 8.0
evidence: 多智能体强化学习在适应性约束下自对弈，适用于并行决策
tldr: 该论文研究了多智能体强化学习中策略更新次数的适应性约束问题，针对二人零和马尔可夫博弈，设计了一种基于策略消除的算法，在保证接近最优遗憾的同时，将批次复杂度降至最低。算法有效减少了策略部署成本，对于并行决策场景具有重要参考价值。
source: ICML-2024-Public
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-ppnmhdymaz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1765, \"height\": 686, \"label\": \"Table\"}]"
motivation: 在实际多智能体系统中，策略更新成本高昂，需要最小化更新次数。
method: 提出基于策略消除的自对弈算法，通过精心设计的消除规则控制批次复杂度。
result: 算法在理论遗憾界上达到近优，且批次复杂度仅与状态数和博弈范围对数相关。
conclusion: 所提算法在保持性能的同时显著降低了策略更新频率，适用于资源受限的多智能体并行决策。
---

## Abstract
We study the problem of multi-agent reinforcement learning (MARL) with adaptivity constraints --- a new problem motivated by real-world applications where deployments of new policies are costly and the number of policy updates must be minimized. For two-player zero-sum Markov Games, we design a (policy) elimination based algorithm that achieves a regret of $\widetilde{O}(\sqrt{H^3 S^2 ABK})$, while the batch complexity is only $O(H+\log\log K)$. In the above, $S$ denotes the number of states, $A,B$ are the number of actions for the two players respectively, $H$ is the horizon and $K$ is the number of episodes. Furthermore, we prove a batch complexity lower bound $\Omega(\frac{H}{\log_{A}K}+\log\log K)$ for all algorithms with $\widetilde{O}(\sqrt{K})$ regret bound, which matches our upper bound up to logarithmic factors. As a byproduct, our techniques naturally extend to learning bandit games and reward-free MARL within near optimal batch complexity. To the best of our knowledge, these are the first line of results towards understanding MARL with low adaptivity.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：实际多智能体系统中（如自动驾驶、电网调度），部署新策略的成本极高（例如车辆固件更新需数周），因此必须最小化策略更新次数。现有单智能体低适应性RL算法已被广泛研究，但多智能体场景（马尔可夫博弈）尚属空白。
- **核心问题**：能否在二人零和马尔可夫博弈中，设计一种自对弈算法，同时达到**接近最优的遗憾**和**接近最优的批次复杂度**（即策略更新次数）？
- **整体含义**：首次将“适应性约束”引入多智能体强化学习，证明在几乎不牺牲样本效率的前提下，可将批次复杂度降至理论下界。这对分布式并行决策、通信受限场景具有重要指导意义。

#### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：基于**策略消除**的批处理框架。维护一个待选策略集，每一批次通过粗估计和细估计构建经验转移核，然后根据值函数下界消除次优策略，确保Nash策略始终保留。
- **关键技术细节**：
  - **批次调度**：采用指数递减的批次大小 $T^{(k)} = K^{1-1/2^k}$，总阶段数 $K_0 = O(\log\log K)$，前两个阶段执行完整的“粗探索+细探索”步骤，后续仅更新细探索。
  - **粗探索（Algorithm 2）**：逐层探索每个 $(h,s,a,b)$ 对，通过构建**吸收马尔可夫博弈**（将访问不足的转移归入吸收态 $s^\dagger$）解决覆盖缺失问题，并输出中间转移核 $P^{int}$、稀少元组集 $\mathcal{F}$ 和均匀探索策略 $\pi$。
  - **细探索（Algorithm 3）**：利用 $P^{int}$ 的接近性，求解一个最小化最大比值的混合策略 $\pi$ 来覆盖所有剩余策略的访问概率；同时运行辅助探索策略 $\pi'$（保证每个非稀少元组被多次访问）；最后基于收集的数据得到经验转移核 $\hat{P}$。
  - **策略消除**：使用 $\inf_{\nu} V^{\mu,\nu}(r,\hat{P})$ 作为 $V^{\mu,\dagger}(r,P)$ 的估计，以 $4\epsilon_k$ 的置信半径消除明显次优策略，其中 $\epsilon_k = \widetilde{O}\bigl(\sqrt{H^3 S^2 AB / T^{(k)}}\bigr)$。
- **理论保证**：遗憾界 $\widetilde{O}(\sqrt{H^3 S^2 AB T})$，批次复杂度 $O(H + \log\log K)$，且证明了下界 $\Omega\bigl(\frac{H}{\log_A K} + \log\log K\bigr)$，因此批次复杂度接近最优。

#### 3. 实验设计：数据集 / 场景、benchmark、对比方法
- **实验情况**：**本文是纯理论论文，未包含任何实验或数值验证**。
- **Benchmark与对比**：仅在理论表格（Table 1）中与现有算法进行比较，包括：
  - 马尔可夫博弈：VI-ULCB (Bai & Jin, 2020)、Nash VI (Liu et al., 2021)、单智能体批处理RL (Zhang et al., 2022)；
  - 博弈老虎机：BaSE (Gao et al., 2019)；
  - 无奖励探索：VI-Explore (Bai & Jin, 2020)、LARFE (Qiao et al., 2022)。
- 表格中列出了各算法的遗憾/样本复杂度、批次复杂度，明确标注了是否适用于多智能体。

#### 4. 资源与算力
- **未提及**。论文为理论分析，未使用GPU或大规模计算集群，因此无相关资源消耗的说明。

#### 5. 实验数量与充分性
- **无实验**。所有结论均通过数学证明得出，包括高概率事件下的遗憾界、批次复杂度上界和下界。
- **充分性评估**：理论证明链完整（引理、定理逻辑清晰），覆盖了算法所有关键步骤的误差界（偏差项、方差项），并推导了PAC样本复杂度。作为理论论文，证明的严密性可视为充分。

#### 6. 论文的主要结论与发现
- **算法（Algorithm 1）**：首次为二人零和马尔可夫博弈提供低适应性算法，达到 $\widetilde{O}(\sqrt{H^3 S^2 ABK})$ 遗憾和 $O(H+\log\log K)$ 批次复杂度。
- **下界**：任何具备 $\widetilde{O}(\sqrt{K})$ 遗憾的算法至少需要 $\Omega\bigl(\frac{H}{\log_A K}+\log\log K\bigr)$ 批次，证明算法批次复杂度几乎是紧的。
- **扩展到博弈老虎机**：Algorithm 6达到 $\widetilde{O}(\sqrt{ABK})$ 遗憾和 $O(\log\log K)$ 批次，计算高效，推广了单智能体批处理Bandit结果。
- **扩展到无奖励探索**：Algorithm 4以 $O(H)$ 批次和 $\widetilde{O}(H^3 S^2 AB/\epsilon^2)$ 样本复杂度输出任意奖励函数的 $\epsilon$-Nash策略，样本复杂度优于先前低适应性方法。

#### 7. 优点
- **问题新颖性**：首次将适应性约束引入多智能体强化学习，填补了理论空白。
- **理论紧致性**：同时给出上界和下界，批次复杂度达到近最优；遗憾界对 $T$ 最优。
- **技术通用性**：提出的吸收马尔可夫博弈框架、层间粗探索与最优实验设计细探索，可自然推广到博弈老虎机和无奖励探索。
- **结果丰富性**：不仅给出了遗憾最小化算法，还提供了PAC样本复杂度保证，为实际应用提供了理论支撑。

#### 8. 不足与局限
- **计算效率**：算法需要显式枚举所有马尔可夫策略以进行消除和构建探索策略，时间复杂度指数级，无法直接应用于大规模问题。论文仅指出可通过覆盖集或梯度优化近似求解，未给出具体高效实现。
- **遗憾在 $S$ 上的次优性**：与单智能体MDP信息论下界 $\Omega(\sqrt{H^2 SAT})$ 相比，本算法在 $S$ 上多出 $\sqrt{S}$ 因子（当 $B=1$ 时）。作者认为改进 $S$ 依赖需要新思路。
- **无法处理一般函数逼近**：仅适用于表格型状态空间，未讨论线性或非线性函数逼近情况。
- **未进行实验验证**：作为纯理论工作，缺乏仿真或实际环境实验，无法验证算法在实际任务中的性能（如收敛速度、资源消耗）。
- **偏差风险**：假设奖励已知、转移核非平稳，且依赖于均匀覆盖假设，实际中可能不满足。

（完）
