---
title: "Enhancing Diversity In Parallel Agents: A Maximum State Entropy Exploration Story"
title_zh: 增强并行智能体多样性：最大状态熵探索的故事
authors: "Vincenzo de paola, Riccardo Zamboni, Mirco Mutti, Marcello Restelli"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=51SFypI0J8"
tags: ["query:graph-part"]
score: 8.0
evidence: 并行智能体多样性最大状态熵
tldr: 针对并行强化学习数据收集效率问题，提出最大化状态熵的探索框架。通过平衡单个智能体熵与智能体间多样性，有效减少数据冗余，实现了超越线性加速比的性能提升。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1754, \"height\": 1007, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 849, \"height\": 1002, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 847, \"height\": 1390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1244, \"height\": 780, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 576, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 438, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1747, \"height\": 1104, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1757, \"height\": 1688, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1655, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 623, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 676, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1403, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 620, \"height\": 615, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-51sfypi0j8/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 679, \"height\": 319, \"label\": \"Figure\"}]"
motivation: 并行强化学习中相同智能体导致数据冗余，无法充分利用并行加速潜力。
method: 设计集中式框架平衡个体熵与间多样性，最大化收集数据的熵。
result: 在多个环境上实现超线性加速，采样效率显著提升。
conclusion: 智能体专业化多样性是突破并行RL性能瓶颈的关键。
---

## Abstract
Parallel data collection has redefined Reinforcement Learning (RL), unlocking unprecedented efficiency and powering breakthroughs in large-scale real-world applications. In this paradigm, $N$ identical agents operate in $N$ replicas of an environment simulator, accelerating data collection by a factor of $N$. A critical question arises: *Does specializing the policies of the parallel agents hold the key to surpass the $N$ factor acceleration?*
In this paper, we introduce a novel learning framework that maximizes the entropy of collected data in a parallel setting. Our approach carefully balances the entropy of individual agents with inter-agent diversity, effectively minimizing redundancies. The latter idea is implemented with a centralized policy gradient method, which shows promise when evaluated empirically against systems of identical agents, as well as synergy with batch RL techniques that can exploit data diversity.
Finally, we provide an original concentration analysis that shows faster rates for specialized parallel sampling distributions, which supports our methodology and may be of independent interest.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：在并行强化学习（RL）中，通常使用 $N$ 个相同的智能体在 $N$ 个环境副本中并行采集数据，以实现 $N$ 倍的加速。然而，现有方法未考虑智能体间的行为冗余，导致计算资源浪费，无法充分发挥并行化的潜力。
- **核心问题**：如何通过专门化并行智能体的策略来超越 $N$ 倍的线性加速？更具体地说，如何在并行设置中高效地进行状态熵最大化探索，以收集更多样化、更有信息量的数据。
- **整体含义**：该工作提出一种新的学习框架，通过最大化并行收集数据的熵，并平衡个体智能体熵与智能体间多样性，从而有效减少冗余，提升探索效率。理论分析和实验表明，该框架能够实现更快的熵收敛速度和更好的下游任务性能（如离线RL）。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：
  - 将并行智能体视为一个整体，考虑它们联合诱导的状态分布（混合分布），而不是独立处理每个智能体。
  - 定义并行状态熵目标函数（有限样本情形）：$J_p(\pi_p) = \mathbb{E}_{d_{n,p} \sim p_{\pi_p}}[H(d_{n,p})]$，其中 $\pi_p = (\pi_i)_{i=1}^m$ 是并行策略集合，$d_{n,p}$ 是经验状态分布。
  - 通过最大化该目标，隐式地鼓励智能体间的多样性（KL散度项），使得各智能体专注于不同状态区域。
- **关键技术细节**：
  - 推导了并行策略梯度公式，每个智能体根据全局经验状态分布的熵更新自己的参数。
  - 提出了 **Policy Gradient for Parallel States Entropy maximization (PGPSE)** 算法（Algorithm 1）：在每个迭代中，所有智能体并行采样 $K$ 条轨迹，计算经验状态分布 $d_p$ 的熵，然后每个智能体使用 REINFORCE 风格的梯度：$\nabla_{\theta_i} J \approx \frac{1}{K} \sum_{k=1}^K \left( \sum_{t=0}^{T-1} \nabla_{\theta_i} \log \pi_{\theta_i}(a_{i,t,k}|s_{i,t,k}) \right) H(d_p^k)$。
  - 采用小批量（batch size $B$）降低梯度方差。
- **理论贡献**：
  - 证明了单智能体下经验熵与真实熵之间的浓度不等式（Theorem 4.1），并指出并行设置下，由于每个智能体诱导低熵分布但覆盖不同区域，混合熵的浓度速度更快（通过KL散度的分解说明）。

### 3. 实验设计：使用了哪些数据集/场景，benchmark，对比了哪些方法
- **实验场景**：
  - 离散网格世界环境：两种地形——**Room**（两个房间由窄走廊连接，43个状态，4个动作）和**Maze**（迷宫，相同状态/动作数）。每种地形又有**确定性版本（det）** 和**随机版本（stoc）**（动作以一定概率翻转）。
- **Benchmark**：
  - 基线方法：单个智能体使用相同算法（PGPSE但只用一个智能体），但采集 $K' = m$ 倍轨迹数（即总样本数匹配）。以及**随机策略**。
- **对比实验**：
  - **策略梯度优化**：比较2、4、6个并行智能体与单智能体（采集对应倍数轨迹）的归一化熵和支持集大小（覆盖状态数）。
  - **数据集熵评估**：从训练好的策略中采样一条轨迹/智能体，计算数据集的经验熵，对比并行、单智能体、随机策略。
  - **离线RL**：将收集的数据集重新标注稀疏奖励（目标状态+1，其余0），使用离线Q-learning训练，评估在不同目标状态下的成功率，对比并行数据集、单智能体数据集、随机数据集。

### 4. 资源与算力
- 论文**未明确说明**使用的GPU型号、数量或训练时长。实验基于离散网格世界（小规模），可以推测在CPU上即可完成。作者未提及任何大规模分布式训练细节。

### 5. 实验数量与充分性
- **实验数量**：
  - 策略梯度优化：在4种环境上分别测试2、4、6个智能体 vs 单智能体，每个设置5个随机种子。共 $4 \times (3+3) \times 5 = 120$ 次训练（但实际图中只展示了2和6代理的曲线，4代理在附录）。
  - 数据集熵评估：对每种环境，使用5个种子，每个种子从训练好的策略采样得到数据集，计算熵和标准差。
  - 离线RL：对每个环境、每种数据集（并行、单、随机），评估所有可能目标状态的成功率，每个种子重复，结果以柱状图或热力图呈现（图3）。
- **充分性与公平性**：
  - 实验覆盖了两种地形、确定/随机两种动态，验证了方法的鲁棒性。
  - 对比了单智能体在相同总样本数下的表现，确保公平比较。
  - 消融实验通过改变智能体数量（2,4,6）证明了扩展趋势。
  - 但**局限性**：所有环境均为离散网格世界，缺乏连续控制或高维状态空间实验；离线RL仅使用简单的Q-learning，未与现代离线RL算法（如CQL、IQL）对比。

### 6. 论文的主要结论与发现
- 并行智能体通过专门化策略能够显著超越单智能体在相同总样本数下的探索效率，在熵和支持集上均更优。
- 并行收集的数据集具有更高熵和更低方差，有利于下游离线RL任务，使得离线Q-learning在更多目标状态上成功。
- 理论分析表明并行混合熵的收敛速度更快，支撑了方法的合理性。
- 结论：**智能体专业化多样性是突破并行RL性能瓶颈的关键**。

### 7. 优点：方法或实验设计上有哪些亮点
- **理论创新**：首次为并行状态熵探索提供浓度界分析，揭示了并行化加速收敛的机理。
- **算法简洁高效**：PGPSE基于简单的REINFORCE梯度，易于实现和扩展；利用全局熵作为反馈，自然地促进多样性。
- **实验验证链条完整**：从策略学习→数据集质量→下游任务（离线RL）三层验证，展示了方法的实际价值。
- **开源性**：提供了代码链接，便于复现。

### 8. 不足与局限
- **实验环境局限**：仅测试了离散网格世界，未在连续控制（如MuJoCo、Isaac Sim）或高维视觉任务上验证，限制了通用性。
- **未与现有先进多智能体探索方法对比**：如基于互信息的技能发现方法（DIAYN、DADS）、基于集成的探索方法等。
- **离线RL实验简单**：仅使用Q-learning，未与更先进的离线算法（如CQL、IQL）对比，也未在多任务或复杂奖励下评估。
- **算力未报告**：缺乏训练资源配置，导致复现和成本评估困难。
- **理论部分浓度界依赖的假设**（如熵光滑性、有界性）在实际中可能不严格成立，且未讨论连续状态空间下的情况。

（完）
