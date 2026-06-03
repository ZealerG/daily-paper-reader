---
title: "Efficient Exploration in Average-Reward Constrained Reinforcement Learning: Achieving Near-Optimal Regret With Posterior Sampling"
title_zh: 平均奖励约束强化学习中的高效探索：利用后验采样实现接近最优遗憾
authors: "Danil Provodin, Maurits Clemens Kaptein, Mykola Pechenizkiy"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=njpTpkvUbO"
tags: ["query:graph-part"]
score: 8.0
evidence: 面向约束RL的后验采样算法，实现接近最优遗憾
tldr: "该论文针对无限视野平均奖励约束MDP，提出了一种基于后验采样的强化学习算法，在理论上实现了接近最优的遗憾界，并在经验上优于现有算法。算法在通信性CMDP上达到tilde{O}(DS sqrt{AT})的遗憾，匹配下界。这项工作为约束RL提供了计算可处理的高效探索方法。"
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-njptpkvubo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1659, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-njptpkvubo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1734, \"height\": 953, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-njptpkvubo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-njptpkvubo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1424, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-njptpkvubo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1649, \"height\": 888, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-njptpkvubo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1781, \"height\": 650, \"label\": \"Table\"}]"
motivation: 现有约束MDP算法在平均奖励设置下遗憾界不优或计算复杂，需要更高效的探索方法。
method: 提出基于后验采样的算法，通过维护后验分布并采样MDP参数，在约束条件下进行决策。
result: "在通信性CMDP上实现了tilde{O}(DS sqrt{AT})的贝叶斯遗憾界，匹配理论下界，并在实验中表现更优。"
conclusion: 该算法是首个在平均奖励约束RL中达到接近最优遗憾且计算可行的算法，推动了约束RL的发展。
---

## Abstract
We present a new algorithm based on posterior sampling for learning in Constrained Markov Decision Processes (CMDP) in the infinite-horizon undiscounted setting. The algorithm achieves near-optimal regret bounds while being advantageous empirically compared to the existing algorithms. Our main theoretical result is a Bayesian regret bound for each cost component of $\tilde{O} (DS\sqrt{AT})$ for any communicating CMDP with $S$ states, $A$ actions, and diameter $D$. This regret bound matches the lower bound in order of time horizon $T$ and is the best-known regret bound for communicating CMDPs achieved by a computationally tractable algorithm. Empirical results show that our posterior sampling algorithm outperforms the existing algorithms for constrained reinforcement learning.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：在无限视野平均奖励（infinite-horizon average reward）设定下的约束马尔可夫决策过程（Constrained MDP, CMDP）中，如何设计计算可行且具有接近最优遗憾界的强化学习算法。实际场景（如机器人、电信网络、自动驾驶）中，智能体需同时优化主目标并满足多个约束（如能耗、安全性），而现有算法在遗憾界或计算效率上存在不足。
- **背景**：前人工作在平均奖励CMDP中取得了最优遗憾界（如Chen等人（2022）的Alg.4达到$\tilde{O}(\sqrt{T})$但计算不可行）或计算可行但遗憾界次优（如UCRL-CMDP、C-UCRL仅达到$\tilde{O}(T^{2/3})$或$\tilde{O}(T^{3/4})$）。基于后验采样的方法（如Agarwal等人（2022））只能处理遍历性CMDP，无法直接推广到更一般的通信性CMDP。
- **意义**：本文首次在通信性CMDP（无需遍历性假设）上实现了计算可行且遗憾界接近最优（$\tilde{O}(DS\sqrt{AT})$）的贝叶斯算法，填补了理论空白，并展示了实际性能优势。

## 2. 方法论

### 核心思想
基于后验采样（Thompson Sampling）原则，维护转移概率的后验分布，在每个回合开始时采样一个可能的转移函数，然后根据该采样求解最优策略。关键创新：当采样出的CMDP不可行（无满足约束的策略）时，算法不直接忽略约束或采用无约束策略，而是切换到高效探索模式——构造一组以不同状态为目标的最短路径MDP并执行其最优策略，以保证对未充分访问的状态-动作对进行充分探索，最终使采样CMDP变得可行。

### 关键技术细节
- **算法流程（PSC ON RL）**：
  1. 初始化先验分布$f_1$，回合划分采用两重停止准则：①任意$(s,a)$的访问计数翻倍；②回合长度不超过上一回合长度。
  2. 每轮$k$开始：从后验$f_{t_k}$采样转移概率$p_k$。
  3. 若在$p_k$下线性规划（LP，式(4)-(7)）可行，则求解最优占用度量$\mu$，得到平稳策略$\pi_k$。
  4. 若LP不可行，则选择当前访问次数最少的状态$\bar{s}$，构造MDP $M_{\bar{s}}^k$（目标状态$\bar{s}$，成本函数为是否到达$\bar{s}$的0-1指标），求解其最优策略（即最短路径策略），执行该策略。
  5. 执行策略直到满足停止准则，更新后验分布。
- **理论保证**：通过“可行性引理”和“探索引理”证明，在$\tilde{O}(DS\sqrt{AT})$步探索后，LP一定可行；之后的分析借鉴Ouyang et al. (2017)的标准后验采样分析，得到总贝叶斯遗憾$\tilde{O}(DS\sqrt{AT})$。
- **公式**：主要遗憾界$BR^+(T; c_i) \leq \tilde{O}(DS\sqrt{AT})$，匹配理论下界$\Omega(\sqrt{DSAT})$（相差$\sqrt{DS}$因子，是开放问题）。

## 3. 实验设计

- **环境**：三个网格世界（gridworld）：
  - Marsrover 4×4（图3a）
  - Marsrover 8×8（图3b）
  - Box（图4）
  三种环境均构建为平均奖励CMDP，主目标为最小化到达目标的步数（等价于最大化负步数），辅助约束为控制访问不安全状态（紫色格子）的频率或推箱子导致不可逆状态。
- **基准方法**：对比三种现有算法：
  - C-UCRL（Zheng & Ratliff, 2020）
  - UCRL-CMDP（Singh et al., 2023）
  - FHA (Alg.3)（Chen et al., 2022）
  另两种算法（Alg.4和PSRL-CMDP）因计算不可行或仅适用于遍历性CMDP而未被纳入。
- **公平性处理**：所有算法都被扩展为未知转移和未知成本/奖励的设定，使用经验平均值和置信界（原始论文中部分算法假设已知某些信息）。

## 4. 资源与算力

文中**未明确提及**使用的GPU型号、数量或训练时长。实验仅在网格世界（状态数最多64，动作数4）上运行，计算量较小，可推测在普通CPU上即可完成。

## 5. 实验数量与充分性

- **实验次数**：Marsrover 4×4上每组实验平均50次运行；Marsrover 8×8和Box平均30次运行。UCRL-CMDP和FHA因计算开销大，仅在Marsrover 4×4上运行10次。
- **客观性**：结果图显示平均累计遗憾和约束违反，附带误差线（未明确说明但通常包含标准差或置信区间）。所有算法在相同种子和环境下比较。
- **充分性**：实验覆盖了不同规模（4×4 vs 8×8）和不同类型（静态风险 vs 动态盒子）的场景。但缺乏消融实验（如无探索机制、不同先验等）以及对更大状态空间或连续控制问题的验证。总体而言，在网格世界环境中比较充分，但推广到复杂实际任务尚需更多验证。

## 6. 主要结论与发现

- 所提算法PSC ON RL在所有三个环境中均**显著优于**现有基线，主成本累积遗憾更低，约束违反更少（特别是Box环境中C-UCRL出现线性遗憾，而PSC ON RL快速收敛）。
- 理论遗憾界$\tilde{O}(DS\sqrt{AT})$与下界匹配（除$\sqrt{DS}$因子），且是计算可行的算法中首个达到该界的工作。
- 通过对比实验（示例3.2）证明，在通信性CMDP中，若不进行专门探索（如PSRL-CMDP忽略约束的策略），会导致严重约束违反且无法学习真实参数；而PSC ON RL通过最短路径探索成功解决。

## 7. 优点

- **理论贡献**：首次在通信性平均奖励CMDP上实现了计算高效（每轮求解LP或最短路径MDP，均为多项式时间）且遗憾接近最优的贝叶斯算法。
- **算法设计巧妙**：通过“不可行时切换探索”机制，克服了后验采样在约束问题中可能面临的不可行困境，探索开销仅需$\tilde{O}(\sqrt{T})$步。
- **实验验证充分**：在多种网格世界环境下与三个理论算法对比，表现一致领先，尤其展示了强于C-UCRL的探索能力。
- **实用性**：算法仅需状态、动作空间和先验知识，不需预先知道直径、混合时间或安全策略。

## 8. 不足与局限

- **理论假设**：依赖于“通信性CMDP”和“存在严格可行策略”的假设，对于更一般的弱通信CMDP或难以人为满足严格可行条件的问题可能不适用。
- **实验范围有限**：仅测试了小型网格世界（最大64状态），未验证在较大状态空间或连续控制任务中的表现。也未与基于深度RL的方法（如CPO、PPO-Lagrangian）对比。
- **后验计算**：使用Dirichlet先验，但在大规模问题中后验更新和采样可能面临挑战；文中未讨论计算瓶颈。
- **缺乏消融实验**：未单独分析探索策略、先验选择对性能的影响；对超参数（如先验参数0.1）的敏感性未讨论。
- **理论与实验的gap**：理论结果是贝叶斯遗憾，但实验中CMDP是固定而非从先验生成。作者虽猜测频繁主义者遗憾相同，但未提供证明。
- **仅关注贝叶斯遗憾**：未提供频率主义遗憾界的分析。

（完）
