---
title: "Turning Sand to Gold: Recycling Data to Bridge On-Policy and Off-Policy Learning via Causal Bound"
title_zh: 变废为宝：利用因果界桥接在线与离线策略学习的数据回收方法
authors: "Tal Fiskus, Uri Shaham"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=5UtsjOGsDx"
tags: ["query:graph-part"]
score: 6.0
evidence: 利用事实损失因果界提升深度强化学习数据效率
tldr: 深度强化学习需要大量训练步数和经验回放缓冲，计算成本高。本文利用奈曼-鲁宾潜在结果框架推导出事实损失的因果界，通过存储过去的价值网络输出来有效利用通常被丢弃的数据，从而弥合在线策略和离线策略学习。理论分析表明该界可显著降低样本复杂度，实验结果验证了数据效率的提升。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1423, \"height\": 715, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1428, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 630, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1445, \"height\": 1715, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 1726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1420, \"height\": 1920, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1450, \"height\": 1726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1416, \"height\": 1919, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1450, \"height\": 1726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1442, \"height\": 1923, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1450, \"height\": 1727, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1441, \"height\": 1918, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1450, \"height\": 1727, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1445, \"height\": 1918, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1430, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5utsjogsdx/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1429, \"height\": 824, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 822, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1430, \"height\": 796, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1395, \"height\": 1064, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 654, \"height\": 2181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 900, \"height\": 2244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 898, \"height\": 2242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 498, \"height\": 732, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1208, \"height\": 2255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1238, \"height\": 2237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1278, \"height\": 2256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1405, \"height\": 2261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1255, \"height\": 2256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1232, \"height\": 2268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 815, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5utsjogsdx/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1103, \"height\": 339, \"label\": \"Table\"}]"
motivation: DRL对数据和计算资源需求巨大，需要更高效的数据利用方法。
method: 引入因果界分析事实损失，通过存储过去价值网络输出实现数据回收。
result: 理论和实验均证明该方法显著降低了样本复杂度。
conclusion: 因果界为提升DRL数据效率提供了有效新途径。
---

## Abstract
Deep reinforcement learning (DRL) agents excel in solving complex decision-making tasks across various domains.
However, they often require a substantial number of training steps and a vast experience replay buffer, leading to significant computational and resource demands.
To address these challenges, we introduce a novel theoretical result that leverages the Neyman-Rubin potential outcomes framework into DRL.
Unlike most methods that focus on bounding the counterfactual loss, we establish a causal bound on the factual loss, which is analogous to the on-policy loss in DRL.
This bound is computed by storing past value network outputs in the experience replay buffer, effectively utilizing data that is usually discarded.
Extensive experiments across the Atari 2600 and MuJoCo domains on various agents, such as DQN and SAC, achieve *up to 383%* higher reward ratio, outperforming the same agents without our proposed term, and reducing the experience replay buffer size by *up to 96%*, significantly improving *sample efficiency at a negligible cost*.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：深度强化学习（DRL）在解决复杂决策任务时表现出色，但需要大量的训练步数和巨大的经验回放缓冲区，导致极高的计算和资源需求。
- **核心矛盾**：在线策略（on-policy）方法样本效率低，每次迭代需新数据；离线策略（off-policy）方法可复用历史数据，但存在行为策略与目标策略的差异，导致学习不稳定。
- **整体目标**：提出一种新方法，通过因果推断框架桥接在线和离线策略学习，提高样本效率，同时保持低计算开销。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将Neyman-Rubin潜在结果框架引入DRL，建立事实损失（对应on-policy损失）的上界，该上界由可观测的反事实损失（off-policy损失）和估计的处理效应项（SUFT OPE项）组成。优化上界而非无法直接计算的事实损失，从而利用离线数据评估目标策略。
- **关键技术细节**：
  - 定义：事实损失 ϵF（on-policy loss）由目标策略生成的数据计算；反事实损失 ϵCF（off-policy loss）由其他行为策略生成的数据计算；估计处理效应 ψ（SUFT OPE项）度量行为策略与目标策略价值网络输出的差异。
  - **因果界定理**：ϵF ≤ ϵCF + ψ + δ，其中δ是与网络无关的常数，优化时可忽略。
  - **数据回收**：在经验回放中存储行为策略的价值网络输出（Q值或V值），这些值通常在动作选择后丢弃；利用它们计算ψ项，实现“变废为宝”。
  - 实现：在DQN和PPO的损失函数中添加λTF·ψ项；对于Actor-Critic方法，将ψ加入Critic损失。
- **算法流程**：
  - DQN：在存储经验时附加Q(s,a;θbehavior)；训练时采样mini-batch，计算目标Q值，梯度下降优化：标准TD loss + λTF·(Qbehavior - Qtarget)²。
  - PPO：在rollout时存储V(s;θbehavior)；多epoch优化时，对Critic损失添加SUFT项，同时Actor保持不变。

## 3. 实验设计

- **数据集 / 场景**：
  - Atari 2600（57款游戏，离散动作空间）
  - MuJoCo（5个连续控制环境，如Ant、Half Cheetah、Hopper、Humanoid、Walker2d）
- **基准**：人类平均得分、随机策略得分。
- **对比方法**：
  - 以DQN、Double DQN、Vanilla DQN、PPO、SAC为基线（均使用相同超参，仅是否添加SUFT项作为变量）。
  - 消融实验：对比增大缓冲区（4K→100K）、惯性正则化（用Qcurrent-Qtarget）²）等方法。
- **配置**：
  - 训练步数：Atari 400K步，MuJoCo 1M步；缓冲区大小：4K（主要）、100K（对比）。
  - 每个环境独立训练10个不同随机种子，取中位数作为最终得分。
  - 使用Gymnasium v5（Atari）和v4（MuJoCo），基于Stable-Baselines3默认架构和超参。
  - 统计显著性：对每个环境做t检验（双尾，显著性水平0.05）。

## 4. 资源与算力

- 论文明确提到：在单块NVIDIA L4 GPU上运行。
- 具体耗时：以Vanilla DQN为例，额外计算SUFT项耗时约23.77秒，总训练时间2980秒，额外计算开销仅0.8%。
- 空间开销：每个经验增加一个64位标量（Q值），4K缓冲区额外存储0.0305 MB，相对于总大小972.85 MB仅0.003%。
- 未给出总实验算力（如总GPU小时），但提到超过10K个个体实验，推测总资源中等。

## 5. 实验数量与充分性

- **实验数量**：涵盖57个Atari游戏 + 5个MuJoCo环境，每种配置10个种子，并探索不同λTF系数，总实验数超过10,000。
- **充分性评估**：
  - 对比了多种agent（DQN、Double DQN、Vanilla DQN、PPO、SAC），覆盖值函数和Actor-Critic架构。
  - 在Atari和MuJoCo两个不同领域验证，结果具有泛化性。
  - 消融实验（缓冲区大小、惯性正则化）隔离了SUFT项的真实贡献。
  - 统计检验表明多数结果显著（p<0.05）。
  - 报告了每种游戏的详细分数和中位数，实验设计客观、公平，随机种子保证了可重复性。

## 6. 论文的主要结论与发现

- SUFT方法在几乎所有游戏和环境上优于基线：
  - Atari：DQN、Double DQN、PPO分别达到383%、227%、197%的平均奖励比（相对于基线）。
  - MuJoCo：SAC达到225%，PPO达到111%的奖励比。
  - 可减少缓冲区大小96%（4K对比100K），仍获得437%的奖励比提升。
- 人类归一化均值：SUFT DQN达到63.45%，高于Double DQN（42.31%）和增大缓冲区的DQN（29.29%）。
- 因果界优化显著优于惯性正则化（惯性正则化仅83%奖励比，而SUFT达227%）。
- 额外计算和存储开销极低（<1%），实现“以可忽略成本提升样本效率”。

## 7. 优点

- **理论创新**：首次在DRL中建立事实损失上界，反向利用反事实损失和估计处理效应，提供严谨因果支撑。
- **数据再利用**：利用通常丢弃的行为策略输出，无需额外采样或网络存储，创新性强。
- **低开销高收益**：计算和存储增量极小，却带来大幅性能提升（最高383%奖励比）。
- **广泛适用性**：可用于值函数和Actor-Critic方法，覆盖在线和离线策略（PPO也受益于多epoch优化中的策略偏差）。
- **实验充分**：大规模、多场景、多种子、统计显著，结果可靠。

## 8. 不足与局限

- **假设限制**：Assumption 4.1（反向三角不等式）对L2损失不严格成立，论文虽通过实验（约80%样本满足）说明实际可行性，但理论上存在漏洞，可能在某些极端情况下削弱界效。
- **常数δ忽略**：δ不依赖于网络参数，但可能较大，导致优化上界不如直接优化事实损失精确。
- **实验环境局限**：仅在仿真环境（Atari、MuJoCo）上测试，未在真实机器人等实际资源受限场景验证，结论泛化至物理世界仍需更多验证。
- **超参敏感性**：λTF需要调优（文中给出范围0.5-1.5），不同agent和任务最佳值不同，虽有一定鲁棒性，但需额外搜索成本。
- **仅适用价值网络**：方法依赖于Q或V网络输出，对于纯策略梯度方法（无显式价值网络）无法直接应用。

（完）
