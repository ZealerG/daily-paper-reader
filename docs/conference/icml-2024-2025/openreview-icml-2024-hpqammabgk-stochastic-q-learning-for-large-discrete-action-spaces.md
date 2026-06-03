---
title: Stochastic Q-learning for Large Discrete Action Spaces
title_zh: 面向大离散动作空间的随机Q学习
authors: "Fares Fourati, Vaneet Aggarwal, Mohamed-Slim Alouini"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=HPQaMmABgK"
tags: ["query:graph-part"]
score: 8.0
evidence: 大离散动作空间的随机Q学习
tldr: 本文提出随机值函数强化学习方法，每轮只考虑次线性数量的动作（如对数级），大幅降低计算开销，适用于大规模离散动作空间的问题。理论分析和实验表明该方法在保持性能的同时显著提升效率，为实际大规模决策任务提供了可行方案。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 629, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 448, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 683, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 455, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1461, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 737, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1737, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1732, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1766, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1773, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1773, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-hpqammabgk/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1775, \"height\": 475, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-hpqammabgk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 583, \"height\": 466, \"label\": \"Table\"}]"
motivation: 传统Q学习在大离散动作空间中每轮需最大化所有动作的值函数，计算负担重。
method: 提出随机值函数方法，每轮仅考虑一个可变的随机子集动作（大小可低至对数级）。
result: 理论分析和实验证明该方法在大动作空间中有效且高效。
conclusion: 该工作为大规模离散动作强化学习提供了实用的高效算法。
---

## Abstract
In complex environments with large discrete action spaces, effective decision-making is critical in reinforcement learning (RL). Despite the widespread use of value-based RL approaches like Q-learning, they come with a computational burden, necessitating the maximization of a value function over all actions in each iteration. This burden becomes particularly challenging when addressing large-scale problems and using deep neural networks as function approximators. In this paper, we present stochastic value-based RL approaches which, in each iteration, as opposed to optimizing over the entire set of $n$ actions, only consider a variable stochastic set of a sublinear number of actions, possibly as small as $\mathcal{O}(\log(n))$. The presented stochastic value-based RL methods include, among others, Stochastic Q-learning, StochDQN, and StochDDQN, all of which integrate this stochastic approach for both value-function updates and action selection. The theoretical convergence of Stochastic Q-learning is established, while an analysis of stochastic maximization is provided. Moreover, through empirical validation, we illustrate that the various proposed approaches outperform the baseline methods across diverse environments, including different control problems, achieving near-optimal average returns in significantly reduced time.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的中文总结。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统的基于价值的强化学习（如Q-learning）在处理**大规模离散动作空间**时，每一步都需要对全部 $n$ 个动作计算 `max` 或 `arg max`，计算复杂度为 $\mathcal{O}(n)$。随着动作数量激增（例如上千甚至上万），这种线性复杂度变得不可承受，极大地限制了此类方法在现实大规模问题中的应用。
- **研究动机**：尽管已有一些利用动作空间结构（如多维度、组合性）的专用方法，但它们缺乏通用性。本文旨在提出一种**通用、简单且高效**的解决方案，在不假设任何动作空间结构的前提下，显著降低基于价值的方法的计算瓶颈，使其适用于广泛的单维或多维大离散动作空间问题。

### 2. 论文提出的方法论

- **核心思想**：引入**随机最大化（Stochastic Maximization）** 操作，取代传统Q-learning中的精确 `max` 和 `arg max`。核心在于：在每一步，仅从一个**随机抽取的、大小呈次线性（如 $\mathcal{O}(\log n)$ ）的动作子集**中寻找最大值，从而将每步复杂度从 $\mathcal{O}(n)$ 降至 $\mathcal{O}(\log n)$。
- **关键技术细节**：
    - **随机最大值（stoch max）** 和**随机自变元最大值（stoch arg max）**：给定一个状态 $s$，定义两个大小为 $\mathcal{O}(\log n)$ 的动作子集：
        - **随机子集 $R$**：从全部动作中均匀随机采样。
        - **记忆子集 $M$**：从近期探索过的动作中采样（在离散状态中取该状态最近使用的动作；在连续状态中从经验回放池随机采 $\log n$ 个动作）。
        - 最终搜索集合为 $C = R \cup M$，大小不超过 $2\lceil \log n \rceil$。然后在该集合上执行 `max` 或 `arg max`。
    - **随机Q学习（Stochastic Q-learning）**：将Q-learning的更新规则和 $\epsilon$-贪心策略中的 `max` 和 `arg max` 替换为上述随机版本。算法伪代码见论文Algorithm 1。
    - **随机深度Q网络（StochDQN / StochDDQN）**：将DQN和DDQN中的最大化步骤替换为随机最大化，同时动作选择也使用随机 $\epsilon$-贪心策略。
    - **理论收敛性**：对于有限MDP，证明了Stochastic Q-learning会**以概率1收敛**到一个新的目标Q函数 $Q^*$，该函数是在给定随机子集采样分布下的最优值函数（定理6.2）。该收敛性不依赖于子集大小，当采样分布退化为全集时，恢复为原始Q-learning。
    - **随机最大化分析**：给出了在均匀分布假设下，随机最大化的期望误差上界，并证明当Q函数趋于稳定时，带记忆的随机最大化最终会精确匹配原始最大化。

### 3. 实验设计

- **数据集/场景**：
    - **离散状态/动作**：Gymnasium标准环境 `CliffWalking-v0`（4动作）、`FrozenLake-v1`（4动作），以及一个**自定义MDP**（256动作，奖励服从正态分布）。
    - **连续状态/离散化动作**：MuJoCo控制任务，将连续动作空间离散化得到大规模离散空间。
        - `InvertedPendulum-v4`：1维动作，离散化为512个动作。
        - `HalfCheetah-v4`：6维动作，每维离散化为4个值，共4096个动作。
- **Benchmark 与对比方法**：
    - 对于表格方法：对比了标准 Q-learning、Double Q-learning、Sarsa 以及它们的随机版本。
    - 对于深度方法：对比了 DQN、DDQN，以及可直接处理连续动作空间的 PPO、A2C、DDPG（使用 Stable-Baselines 实现）。同时还包括随机策略作为基线。
    - 评估了壁钟时间随动作数增长的变化曲线。

### 4. 资源与算力

- **计算平台**：文中明确指出，所有实验均使用 **CPU**（11th Gen Intel Core i7-1165G7 @ 2.80GHz）和 16GB RAM 进行训练，**没有使用 GPU**。PyTorch 被用于深度学习方法，但训练是在 CPU 上完成的。
- **训练时长**：未给出总训练时间，但给出了单步时间对比。例如，在 HalfCheetah 实验中（4096动作），DQN 单步需 0.6 秒，运行 10 万步约需 17 小时；而随机版本（StochDQN/StochDDQN）约需 2 小时完成同样步数，效率提升约 8.5 倍。

### 5. 实验数量与充分性

- **实验数量**：
    - **表格方法**：在 3 个环境（CliffWalking、FrozenLake、自定义MDP）上测试，每个实验重复 10 次并取平均。
    - **深度方法**：在 2 个 MuJoCo 控制任务上测试，每个实验重复 5 次并取平均。
    - **消融与额外分析**：
        - 对比了**有记忆 vs 无记忆**的随机最大化在均匀分布模拟中的表现（图6）。
        - 跟踪了比例 $\omega_t$ 和差值 $\beta_t$ 来量化随机最大化与精确最大化的近似程度（图7、8）。
        - 测量了不同动作数下的行动选择时间和单步总耗时（图5）。
- **充分性与客观性**：实验设计较为全面。对比了多种基线和变体，覆盖了表格和深度场景，验证了加速效果、性能提升以及近似误差。实验条件（如超参数）在同类方法之间保持一致，**公平性较好**。不过，缺乏在具有真实大离散动作空间（如文本生成、组合优化）的复杂任务上的实验，仅在标准控制基准和合成MDP上验证。

### 6. 论文的主要结论与发现

- **主要结论**：提出的随机Q学习变体（Stochastic Q-learning, StochDQN, StochDDQN）能够成功地将价值函数最大化的复杂度从线性 $\mathcal{O}(n)$ 降至对数级 $\mathcal{O}(\log n)$，同时**在大多数任务上保持或超越**原始方法的平均回报。
- **具体发现**：
    - **显著加速**：在 1000 动作时，随机方法每步约 0.003 秒，而非随机方法约 0.18 秒，加速 60 倍。
    - **性能提升**：在 FrozenLake 和 InvertedPendulum 上，随机方法收敛更快，最终回报更高。作者归因于两点：①随机 $\arg\max$ 引入了额外探索；②随机 `max` 是原始 `max` 的下界，有助于**缓解Q-learning固有的过估计偏差**。
    - **理论有保障**：Stochastic Q-learning 的收敛性得到证明。
    - **通用性**：该方法不依赖动作空间的特殊结构（如维度、组合性），可适用于通用的大离散动作空间。

### 7. 优点

- **方法简单高效**：核心思想非常直观，实现改动极小（替换 `max` 为 `stoch max`），但能带来指数级的理论加速。
- **通用性强**：无需对动作空间的维度或组合结构做任何假设，适用于单维和多维、有结构和无结构的大动作空间，显著拓宽了价值方法的实用性。
- **理论扎实**：提供了随机Q学习的收敛性证明，以及对随机最大化误差的定量分析，增强了方法的可信度。
- **实验充分且公平**：涵盖了表格和深度两类方法，对比了多种强的基线，并对关键机制（记忆效果、近似误差）进行了可视化分析。超参数设置保持一致。
- **额外发现**：随机化不仅提高了计算效率，还通过减少过估计偏差和引入随机性在部分任务上提升了样本效率（更快收敛、更高回报）。

### 8. 不足与局限

- **实验覆盖有限**：
    - 深度方法仅在两个 MuJoCo 控制任务上测试，且动作空间是通过离散化得到的，并非原生的大离散空间。缺乏在真实大离散任务（如机器翻译、图组合优化、大规模推荐系统）上的验证。
    - 对比的基线方法（PPO、A2C、DDPG）是连续动作空间的成熟算法，但在离散化后与离散方法的直接比较可能不完全公平（尽管作者已尽力控制变量）。
- **偏差风险**：
    - 随机最大化的低估偏差虽然在实验中表现出积极作用，但在某些场景下可能导致严重欠估计，尤其当最优动作值远高于次优动作时，随机未能采到最优动作会使学习信号显著偏差。论文未充分讨论这种极端情况的风险。
    - 记忆机制在连续状态中的实现较为粗糙（随机从经验池采样 $\mathcal{O}(\log n)$ 个近期动作），其有效性可能高度依赖环境特点，缺乏深入的理论分析。
- **应用限制**：
    - 随机子集的大小（如 $\mathcal{O}(\log n)$）需要根据问题规模调整，过小可能导致近似误差过大，过大会损失加速优势。
    - 该方法继承了Q-learning的计算瓶颈，但在应对**非常深的神经网络**时，单次前向传播本身可能成为瓶颈，论文未探讨该情况。
- **缺少消融实验**：未系统比较不同随机子集大小、不同记忆策略（如保留更多历史动作）对性能的影响。

（完）
