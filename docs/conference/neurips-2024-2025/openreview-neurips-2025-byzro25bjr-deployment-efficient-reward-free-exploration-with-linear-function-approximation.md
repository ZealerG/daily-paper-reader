---
title: Deployment Efficient Reward-Free Exploration with Linear Function Approximation
title_zh: 线性函数近似下的部署高效奖励免费探索
authors: "Zihan Zhang, Yuxin Chen, Jason D. Lee, Simon Shaolei Du, Lin Yang, Ruosong Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ByzRO25Bjr"
tags: ["query:graph-part"]
score: 6.0
evidence: 部署高效的奖励免费强化学习探索算法
tldr: 本文研究线性MDP中部署高效的奖励免费探索，提出新算法仅需H个探索策略（H为horizon）即达到近乎最优，同时样本复杂度多项式。该工作显著减少了现实应用中策略部署的成本，为奖励免费RL提供了实用方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-byzro25bjr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1206, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-byzro25bjr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1508, \"height\": 603, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-byzro25bjr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1572, \"height\": 768, \"label\": \"Table\"}]"
motivation: 实际RL部署代价高，需要减少探索中使用的策略数量。
method: 设计新RL算法，在线性MDP中仅使用H个策略实现奖励免费探索，保持多项式样本复杂度。
result: 算法达到近乎最优的部署效率，并理论证明样本复杂度界限。
conclusion: 该工作显著降低了奖励免费RL的部署成本，适用于代价敏感场景。
---

## Abstract
We study deployment-efficient reward-free exploration with linear function approximation, where the goal is to explore a linear Markov Decision Process (MDP) without revealing the reward function, while minimizing the number of distinct policies implemented during learning. By ``deployment efficient'', we mean algorithms that require few policies deployed during exploration -- crucial in real-world applications where such deployments are costly or disruptive. We design a novel reinforcement learning algorithm that achieves near-optimal deployment efficiency for linear MDPs in the reward-free setting, using at most $H$ exploration policies during execution (where $H$ is the horizon length), while maintaining sample complexity polynomial in feature dimension and horizon length. Unlike previous approaches with similar deployment efficiency guarantees, our algorithm's sample complexity is independent of the reachability or explorability coefficients of the underlying MDP, which can be arbitrarily small and lead to unbounded sample complexity in certain cases -- directly addressing an open problem from prior work. Our technical contributions include a data-dependent method for truncating state-action pairs in linear MDPs, efficient offline policy evaluation and optimization algorithms for these truncated MDPs, and a careful integration of these components to implement reward-free exploration with linear function approximation without sacrificing deployment efficiency.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在机器人、医疗、推荐系统等真实应用中，部署新策略（policy deployment）代价高昂（如硬件重启、审批流程、安全测试等）。标准RL算法通常需要频繁切换策略，这不切实际。因此需要**部署高效**（deployment-efficient）的RL算法，即用尽可能少的策略部署次数完成学习。
- **背景**：已有工作（Huang et al., 2022；Qiao et al., 2022等）在线性MDP框架下研究了部署复杂度，但达到近乎最优的O(H)部署复杂度（H为horizon长度）时，要么只适用于表格环境，要么依赖**可达性假设**（reachability）或**可探索性假设**（explorability），这些假设要求所有特征方向都能被某些策略探索到，在实际中可能不成立（可达性系数可以任意小）。
- **核心问题**：**能否在不依赖可达性/可探索性假设的前提下，为线性MDP设计出达到近乎最优部署复杂度且样本复杂度多项式的RL算法？** 这是已有工作留下的开放问题。
- **整体含义**：本文正面回答了上述问题，设计了一个新算法，在**奖励免费探索**（reward-free exploration）设置下实现了部署复杂度O(H)和多项式样本复杂度，且不依赖任何额外结构假设，显著增强了算法的实际适用范围。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：
  1. **层叠式探索（layer-by-layer approach）**：按horizon层逐层设计探索策略，每一层只部署一个策略（共H次部署），后续层利用前面层收集的离线数据集进行策略评估与优化。
  2. **处理稀疏方向（infrequent directions）**：为避免可达性假设，算法需识别并“截断”（truncate）那些无法被任何策略频繁访问的特征方向。通过**数据依赖的截断技术**，只保留可被充分探索的方向，抑制不可达方向带来的指数级误差累积。
  3. **迭代信息矩阵估计**：使用Matrix-Eval算法迭代估计截断后的信息矩阵，通过潜在函数（如行列式）保证迭代收敛，且每次迭代误差关于真实信息矩阵是乘性的，避免指数爆炸。
  4. **独立副本与离线回归**：为了打破数据依赖，收集多组独立子数据集（sub-dataset），用于不同阶段的离线策略优化和矩阵评估。

- **关键技术细节**：
  - 定义截断算子 \( T(A, B) = \sup\{\zeta \leq 1 : \zeta A \preceq B\} \cdot A \)。
  - **Policy-Design（算法2）**：对当前层h，基于已学习的块矩阵 \(\{\check{\Lambda}_\tau\}_{\tau<h}\)，构造奖励函数 \( r_h^\ell(s,a) = \min\{\phi_h(s,a)^\top ( \Lambda_h^{\ell-1})^{-1} \phi_h(s,a), 1\} \)，调用离线规划（Planning-R）得到当前策略 \(\pi^\ell\)，然后通过Matrix-Eval截断并估计信息矩阵 \( \bar{\Lambda}_h^\ell\)，更新 \(\Lambda_h^\ell = \Lambda_h^{\ell-1} + \bar{\Lambda}_h^\ell\)，共m轮。
  - **Matrix-Eval（算法3）**：输入策略\(\pi\)和截断矩阵\(\Lambda\)，迭代调用Truncated-Matrix-Eval（算法4）来估计截断后的信息矩阵，若连续两次迭代结果相近（乘性条件下）则停止，返回最终信息矩阵。
  - **Truncated-Matrix-Eval（算法4）**：从h层开始，对每个状态-动作对，若特征\(\phi\)满足截断条件（\(\phi^\top \check{\Lambda}_\tau^{-1} \phi \leq 1\)），则通过离线线性回归（基于子数据集）递推计算截断矩阵 \( \hat{F}_\tau(s) \)，最终返回 \( \hat{F}_0 \)。
  - **Planning（算法5）** 和 **Planning-R（算法6）**：用于给定 reward 下计算最优策略或价值函数，后者额外考虑误差上界。
  - **Policy-Execution（算法7）**：使用混合策略（uniform over \(\{\pi_{i,h}\}\)）收集轨迹，并对每个样本赋予权重 \(\lambda_{h,j} = \min\left( \sqrt{\frac{f_1}{\phi_{h,j}^\top \check{\Lambda}_h^{-1} \phi_{h,j}}}, 1 \right)\)，构成子数据集。
  - 算法总部署次数为H，样本复杂度为 \(\tilde{O}(d^{15} H^{15} / \epsilon^5)\)，时间复杂度为 \(\tilde{O}(d^{32} H^{28} A / \epsilon^{10})\)。

### 3. 实验设计

- **本文是纯理论工作**，未设计任何实验。所有结果通过数学证明（若干引理和定理）支撑，没有使用数据集或benchmark。
- 对比方法：在理论层面与Huang et al. (2022)、Qiao and Wang (2022) 等进行了比较，指出本文去掉了可达性假设，且样本复杂度不依赖于可达性系数 \(v_{\min}\)；与Zhao et al. (2023) 相比，本文的部署复杂度为O(H)（优于他们的\(\tilde{O}(dH)\)）。
- **无实际实验**，因此不存在benchmark对比或消融实验。

### 4. 资源与算力

- **未涉及**：论文未进行任何实验，因此没有提及使用的GPU型号、数量、训练时长等资源。所有结果基于理论推导和数学分析。

### 5. 实验数量与充分性

- 由于是纯理论论文，**不涉及实验**。充分性体现在严格的数学证明：包括完整的引理（Lemma 5-19）、定理（Theorem 4）及其证明，覆盖了算法正确性、样本复杂度、部署复杂度等关键方面。
- 通过归纳法和概率论证（矩阵集中不等式等）确保了算法以高概率输出ϵ-最优策略。理论推导是严谨和充分的。

### 6. 论文的主要结论与发现

- 成功设计了**首个无需可达性/可探索性假设的、部署高效的奖励免费RL算法**，在线性MDP中达到近乎最优的部署复杂度O(H)和多项式样本复杂度（\(\tilde{O}(d^{15} H^{15} / \epsilon^5)\)）。
- 解决了已有工作（Huang et al., 2022; Qiao and Wang, 2022）留下的开放问题，表明即使特征空间存在难以到达的方向，也能通过截断技术实现部署高效。
- 算法同时适用于奖励免费设置，进一步增强了实用性。
- 技术贡献包括：数据依赖的截断方法、截断MDP上的离线评估与优化、多副本独立数据集的设计等。

### 7. 优点

- **理论突破性**：解决了重要开放问题，证明了在线性MDP中无需额外假设即可实现近乎最优部署复杂度。
- **算法设计新颖**：
  - 提出截断信息矩阵的迭代方法（Matrix-Eval），巧妙处理不可达方向，避免误差指数累积。
  - 利用独立子数据集和离线回归，同时保证统计独立性和计算可行性。
  - 整体算法结构清晰（逐层探索、迭代截断、离线规划）。
- **通用性**：算法在奖励免费框架下工作，可适应任意线性奖励函数。
- **计算复杂度多项式**：虽然依赖阶数较高，但仍为多项式时间算法，且比Huang et al. (2022)更优（后者依赖实现参数）。

### 8. 不足与局限

- **样本复杂度较高**：当前为 \(\tilde{O}(d^{15} H^{15} / \epsilon^5)\)，与理想界（如Qiao and Wang 2022的 \(\tilde{O}(d^2 H^3 / \epsilon^2)\) 但依赖可达性）相比差距较大。作者指出实现可达性无关性增加了技术难度，导致多项式指数较高。
- **仅针对线性MDP**：未推广到更一般的函数类（如bounded eluder dimension），作者提出这是未来方向。
- **计算效率**：虽然多项式时间，但指数较高（d^32 H^28），实际部署可能依然昂贵。
- **未进行实证验证**：纯理论论文，缺乏仿真或真实实验来验证算法的实际表现和运行效率。
- **假设较强**：仍使用线性MDP假设（特征Φ已知且奖励/转移线性），这在某些复杂应用中可能不满足。
- **未讨论低概率事件的处理细节**：关于置信参数、截断阈值等具体参数设置虽然给出，但未显示其在极端情况下的鲁棒性。
- **部署复杂度上界已被证明为Ω(H)**，本文达到O(H)，是最优的常数倍，但对于H较大时部署次数仍然不少。

（完）
