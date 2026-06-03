---
title: Online Episodic Convex Reinforcement Learning
title_zh: 在线情节式凸强化学习
authors: "Bianca Marin Moreno, Khaled Eldowa, Pierre Gaillard, Margaux Brégère, Nadia Oudjane"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=d8xnwqslqq"
tags: ["query:graph-part"]
score: 9.0
evidence: 在线凸强化学习算法
tldr: 凸强化学习（CURL）因非线性损失而挑战经典贝尔曼方程。本文提出首个无需先验转移知识的在线CURL算法，通过带可变约束集的在线镜像下降和精心设计的探索奖励，达到近最优遗憾界。还首次解决了CURL的赌博机版本，仅需观察奖励信号。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-d8xnwqslqq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 786, \"height\": 247, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d8xnwqslqq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 798, \"height\": 606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d8xnwqslqq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 870, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d8xnwqslqq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1743, \"height\": 816, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-d8xnwqslqq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1725, \"height\": 304, \"label\": \"Table\"}]"
motivation: 凸目标函数使经典贝尔曼方程失效，需要新的算法框架。
method: 提出在线镜像下降算法，结合可变约束集和探索奖励，处理凸损失。
result: 理论证明近最优遗憾界，实验验证算法有效性。
conclusion: 首次为在线CURL提供了无需先验知识的算法与理论保证。
---

## Abstract
We study online learning in episodic finite-horizon Markov decision processes (MDPs) with convex objective functions, known as the concave utility reinforcement learning (CURL) problem. This setting generalizes RL from linear to convex losses on the state-action distribution induced by the agent’s policy. The non-linearity of CURL invalidates classical Bellman equations and requires new algorithmic approaches. We introduce the first algorithm achieving near-optimal regret bounds for online CURL without any prior knowledge on the transition function. To achieve this, we use a novel online mirror descent algorithm with variable constraint sets and a carefully designed exploration bonus. We then address for the first time a bandit version of CURL, where the only feedback is the value of the objective function on the state-action distribution induced by the agent's policy. We achieve a sub-linear regret bound for this more challenging problem by adapting techniques from bandit convex optimization to the MDP setting.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：传统的强化学习（RL）处理线性损失函数，基于贝尔曼方程进行动态规划。然而许多实际应用（如能源网格优化、平均场博弈、风险敏感RL等）涉及**凸（或凹）目标函数**，即Concave Utility RL（CURL）问题。CURL中损失是状态-动作分布的非线性函数，导致贝尔曼方程失效，需要全新的算法框架。
- **核心问题**：现有CURL方法大多针对离线设置或假设已知转移概率。在线CURL面临**对抗性损失**和**未知环境动态**的双重挑战，已有方法（如Greedy MD-CURL）依赖于强模型假设（如已知确定性动态加独立噪声），限制了实际应用。
- **论文目标**：提出首个在无先验转移知识条件下实现**近最优遗憾界**的在线CURL算法，并首次解决CURL的**赌博机（bandit）反馈**版本。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用**在线镜像下降（Online Mirror Descent, OMD）** 框架，在估计的MDP上优化，并使用**探索奖励（exploration bonus）** 处理探索-利用权衡。通过调整OMD中的子梯度（减去奖励），使算法在未知动态下也能获得亚线性遗憾。
- **关键技术细节**：
  - **全信息反馈设置**（Section 3）：算法（Bonus O-MD-CURL）在每轮OMD更新中使用子梯度 `∇F_t(μ^{π_t, \hat{p}_t}) - b_t`，其中 `b_t` 是精心设计的**探索奖励向量**（式(11)）。奖励依赖于访问次数 `N_t^n(x,a)`，用于补偿由模型估计误差导致的遗憾项（`R^{policy/MDP}_T`），并利用**重要性加权**技巧抵消额外奖励项。
  - **赌博机反馈设置**（Section 4）：
    - **标准RL赌博机**（Section 4.1）：采用置信集和重要性加权损失估计，配合探索奖励，获得亚线性遗憾。
    - **CURL赌博机**（Section 4.2）：提出两种方法。
      1. **熵正则化方法**（Section 4.2.1，Alg. 3）：利用球形扰动估计梯度，但需要转移概率有正下界（Assumption 4.2），获得 `T^{3/4}` 遗憾。
      2. **自和谐正则化方法**（Section 4.2.2，Alg. 4）：使用对数障碍函数作为正则化器，无需正下界假设，但限于已知MDP，同样获得 `T^{3/4}` 遗憾。
- **算法流程**（以全信息为例）：初始化均匀策略和估计转移概率；每轮：执行当前策略，更新转移计数；计算奖励 `b_t`；观察到完整目标函数；计算OMD更新得到新策略。

### 3. 实验设计

- **场景与数据集**：使用来自 (Geist et al., 2022) 的两个任务：
  - **多目标任务（Multi-objectives）**：在11×11四房间网格世界中，使最终状态分布集中在三个目标上，目标函数为 `f_n = -∑_{k=1}^3 (1 - ⟨μ_n^{π,p}, e_k⟩)^2`。
  - **约束MDP任务（Constrained MDP）**：集中分布到黄色目标，同时避免蓝色约束状态，目标函数为 `f_n = -⟨r, μ_n⟩ + (⟨μ_n, c⟩)^2`。
- **对比方法**：与 Greedy MD-CURL (Moreno et al., 2024) 比较。
- **评估指标**：损失（log-loss）和静态遗憾（与最优策略对比）。
- **参数设置**：`N=40`, `τ=0.01`, 每个实验重复5次。

### 4. 资源与算力

- **论文未明确说明使用的GPU型号、数量、训练时长**。实验基于网格世界小规模模拟（状态121个，动作5个），计算成本较低，未提及分布式或大规模训练。

### 5. 实验数量与充分性

- **实验数量**：两个任务，每个任务报告了状态分布图、log-loss和遗憾曲线，共约6个子图。重复5次（但图中是否显示误差线？文本未明确）。未进行消融实验或超参数敏感性分析。
- **充分性**：实验设计聚焦于验证探索奖励的有效性（Bonus O-MD-CURL vs Greedy MD-CURL），结果定性显示奖励帮助更快探索到目标。但覆盖范围有限：固定目标函数和转移概率（非对抗性），且仅与一个基线比较。缺乏与更先进RL方法（如UCRL、UCB-VI）的对比，也未测试赌博机或全信息对抗场景。实验较为初步。

### 6. 论文的主要结论与发现

- **理论保证**：全信息CURL实现 `Ō(L N^3 |X|^{3/2} √|A| T)` 遗憾（Theorem 3.2），匹配带加强假设的先前工作的最优率。赌博机RL达到 `Ō(T^{1/2})`（Theorem 4.1），赌博机CURL（熵正则化）达到 `Ō(T^{3/4})`（Theorem 4.3），而自和谐正则化方法在已知MDP下达到 `Ō(T^{3/4})`（Theorem 4.5）。
- **实验验证**：Bonus O-MD-CURL 在网格世界任务中显著快于 Greedy MD-CURL 达到目标状态，尤其在约束MDP中非奖励方法完全失败。证明了奖励对探索的重要性。

### 7. 优点

- **方法创新**：首次为在线CURL（未知动态）提供了近最优遗憾的理论保证，克服了此前方法对模型假设的依赖。
- **探索奖励设计巧妙**：通过将奖励添加到子梯度中，在OMD框架下自然处理了模型误差带来的额外遗憾，且保持了闭式解的计算效率（低计算复杂度）。
- **赌博机反馈扩展**：开创性地处理CURL的赌博机问题，引入BCO技术，为后续工作奠定基础。
- **理论分析严谨**：详细证明了学习率、奖励参数的影响，并利用多种集中不等式。

### 8. 不足与局限

- **实验不够充分**：仅测试两个静态目标函数（非对抗性），未验证对抗损失或赌博机设置；只与一个基线比较，缺乏与model-optimistic方法的对比；未做消融实验分析奖励各项贡献。
- **赌博机CURL遗憾较差**：达到 `T^{3/4}` 而非最优 `T^{1/2}`，且熵正则化方法依赖强假设（转移概率有正下界）。
- **自和谐方法限于已知MDP**：无法扩展到未知动态，实用性受限。
- **理论遗憾依赖于状态和动作空间大小**：全信息遗憾包含因子 `|X|^{3/2}` 和 `N^3`，在较大问题中可能过大。
- **未讨论实际应用中的计算开销**：虽然闭式解，但每轮需要计算 `μ^{π_t, \hat{p}_t}` 和更新计数，对于大规模状态空间仍可能昂贵。

（完）
