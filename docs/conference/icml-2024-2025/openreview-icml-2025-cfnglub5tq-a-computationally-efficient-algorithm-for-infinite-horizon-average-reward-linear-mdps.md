---
title: A Computationally Efficient Algorithm for Infinite-Horizon Average-Reward Linear MDPs
title_zh: 无限视野平均奖励线性MDP的计算高效算法
authors: "Kihyuk Hong, Ambuj Tewari"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=cFNgLub5tQ"
tags: ["query:graph-part"]
score: 8.0
evidence: 无限视野平均奖励线性MDP的高效算法
tldr: 该论文针对无限视野平均奖励线性MDP，提出了一种计算高效的值迭代算法。传统方法需要在整个状态空间上计算值函数的最小值，计算代价高昂；本文通过仅对算法访问过的状态进行裁剪操作，大幅降低了复杂度。理论分析证明了统计效率，并在实验中验证了性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-cfnglub5tq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1644, \"height\": 456, \"label\": \"Table\"}]"
motivation: 平均奖励线性MDP的现有算法需要计算整个状态空间的最小值，难以扩展到大规模或无限状态空间。
method: 提出一种高效裁剪操作的值迭代算法，仅利用访问过的状态集计算最小值。
result: 算法在保持统计效率的同时显著降低计算复杂度，实验表现优越。
conclusion: 为解决无限状态空间下的平均奖励RL提供了一种可扩展的方法。
---

## Abstract
We study reinforcement learning in infinite-horizon average-reward settings with linear MDPs. Previous work addresses this problem by approximating the average-reward setting by discounted setting and employing a value iteration-based algorithm that uses clipping to constrain the span of the value function for improved statistical efficiency. However, the clipping procedure requires computing the minimum of the value function over the entire state space, which is prohibitive since the state space in linear MDP setting can be large or even infinite. In this paper, we introduce a value iteration method with efficient clipping operation that only requires computing the minimum of value functions over the set of states visited by the algorithm. Our algorithm enjoys the same regret bound as the previous work while being computationally efficient, with computational complexity that is independent of the size of the state space.

---

## 论文详细总结（自动生成）

以下是根据给定论文内容生成的中文总结，按照要求的八大要点组织。

---

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在无限视界平均奖励强化学习（RL）中，线性MDP（Markov Decision Process）是大状态空间下的重要模型。现有算法（如Hong et al., 2025的γ-LSCVI-UCB）通过折扣奖励近似与值函数裁剪（clipping）来约束值函数的跨度（span），从而实现统计高效性。然而，其裁剪操作需要在**整个状态空间**上计算值函数的最小值，这在状态空间巨大或无限时计算代价极高。
- **整体含义**：本文旨在回答一个开放问题：是否存在一种算法，在无限视界平均奖励线性MDP下，其计算复杂度与状态空间大小无关，仅与问题参数（维数d、动作数A、时间T）多项式相关，同时保持最优的遗憾界（regret bound）。作者给出了肯定答案。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：提出两种新技术——
  1. **高效裁剪（Efficient Clipping）**：仅基于算法访问过的状态集合（visited states）计算裁剪下界，而非遍历整个状态空间。
  2. **偏差受控值迭代（Deviation-Controlled Value Iteration）**：通过引入额外的裁剪步骤，控制不同时间步生成的值函数序列之间的偏差，使得算法即使在裁剪阈值（clipping threshold）逐时间步更新时，仍能保持值函数的近似一致性，从而完成遗憾分析。

- **关键技术细节**：
  - 算法名为 **γ-DC-LSCVI-UCB**（Discounting Deviation-Controlled Least Squares Clipped Value Iteration with Upper Confidence Bound）。
  - **输入**：折扣因子γ，正则化常数λ，跨度H（已知sp(v*)的上界），奖励放大因子β。
  - **每步流程**（简化）：
    - 对于当前时间步t，从T向后值迭代到t，生成动作值函数 \( \tilde{Q}_t^u \)。
    - 对 \( \tilde{Q}_t^u \) 与之前两次生成的值函数 \( \tilde{Q}_{t-1}^u, \tilde{Q}_{t-2}^u \) 进行上下界裁剪（Clip），得到 \( Q_t^u \)。
    - 状态值函数 \( \tilde{V}_t^u = \max_a Q_t^u(\cdot, a) \)，再裁剪至 [m_t, m_t + H]，其中 m_t 是当前使用的裁剪阈值。
    - 采取贪婪动作 \( a_t = \arg\max_a Q_t^t(s_t, a) \)。
    - 更新协方差矩阵 Λ_t，并更新下步裁剪阈值 \( m_{t+1} = \tilde{V}_t^{t+1}(s_{t+1}) \land m_t \)（此处用到了高效裁剪）。
  - 关键差异性：将裁剪下界的计算从“全局最小值”替换为“当前访问过的状态最小值”，并引入偏离控制保证值函数序列的相对稳定性。

- **公式与算法流程**：使用文字说明见上文；具体伪代码见原论文Algorithm 2。

## 3. 实验设计：数据集、场景、对比方法

- **本文为纯理论论文，未进行任何数值实验或仿真**。
- 对比方法：表中列出了五种相关工作：
  - FOPO (Wei et al., 2021)
  - OLSVI.FH (Wei et al., 2021)
  - LOOP (He et al., 2024)
  - MDP-EXP2 (Wei et al., 2021)
  - γ-LSCVI-UCB (Hong et al., 2025)
- 对比维度包括：遗憾界（理论上界）、假设条件、计算复杂度（多项式于哪些参数）。本文宣称在相同假设下达到相同遗憾界，但计算复杂度与状态空间规模无关，成为首个满足eO(√T)遗憾界且计算高效的平均奖励线性MDP算法。

## 4. 资源与算力

- **论文未提及任何硬件资源（GPU型号、数量、训练时长等）**。
- 由于无实验，无需计算资源。但理论分析涉及的计算复杂度为：\( O(T^3 d^2 A) \)，独立于状态空间大小。

## 5. 实验数量与充分性

- **无实验**。因此无法评价实验数量和充分性。论文仅通过理论证明和复杂度分析支持结论。

## 6. 论文的主要结论与发现

- 提出γ-DC-LSCVI-UCB算法，在满足Bellman最优性方程（Assumption A）和线性MDP假设（Assumption B）的条件下，以概率至少 1-δ 达到遗憾界：
  \[
  R_T \le O\left( \operatorname{sp}(v^*) \sqrt{d^3 T \log(dT/\delta) \log T} \right)
  \]
  其中 sp(v*) 是最优偏置函数的跨度，d是特征维数。
- 计算复杂度为 \( O(T^3 d^2 A) \)，与状态空间大小无关；而先前γ-LSCVI-UCB的计算复杂度依赖状态空间大小S。
- 该结果首次证明了存在计算高效且遗憾最优的平均奖励线性MDP算法。

## 7. 优点

- **计算效率显著提升**：裁剪操作仅需访问过状态，避免全局遍历，使算法适用于大规模/无限状态空间。
- **理论严密**：对每个关键步骤（乐观性、浓度不等式、偏差控制、残差项）都给出了引理和证明，遗憾界与先前最优工作一致。
- **无额外强假设**：除标准的线性MDP和Bellman最优性方程假设外，不需要均匀混合等额外条件。
- **方法新颖**：同时提出高效裁剪与偏差受控值迭代两个技术，可看作对Hong et al. (2025)的改进，具有推广潜力。

## 8. 不足与局限

- **缺少实验验证**：纯理论论文，未进行任何数值模拟或实际应用验证，可能影响实践可接受度。
- **计算复杂度仍为T的超线性**：\( O(T^3 d^2 A) \) 对于长视界T (如10^6) 仍可能过高；作者承认留下“线性于T”作为未来工作。
- **对时间预知和重启假设**：需要已知T来设置γ=1-1/√T；可通过倍增技巧（doubling trick）转化为anytime算法，但会增加分析复杂度。
- **假设跨度已知**：需要已知最优偏置跨度sp(v*)的上界；最近工作（Boone & Zhang, 2024）在表格设置中可去除此假设，但线性MDP中仍是开放问题。
- **偏差控制机制引入额外保守性**：裁剪可能会略微降低值函数估计的精度，尽管理论界未变，但实际常数可能更大。

（完）
