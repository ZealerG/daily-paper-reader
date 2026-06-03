---
title: The Impact of On-Policy Parallelized Data Collection on Deep Reinforcement Learning Networks
title_zh: 关于策略并行数据收集对深度强化学习网络的影响
authors: "Walter Mayor, Johan Obando-Ceron, Aaron Courville, Pablo Samuel Castro"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=cnqyzuZhSo"
tags: ["query:graph-part"]
score: 8.0
evidence: 强化学习中并行数据收集的影响分析
tldr: 强化学习算法常使用并行环境进行数据收集，但相关超参数对网络和优化稳定的影响尚不明确。本文以PPO为例，系统分析了并行数量与rollout长度带来的偏差-方差权衡，以及训练轮次对过拟合的影响。实验揭示了网络可塑性与优化稳定性之间的联系，为超参数调优提供了指导。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1764, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 898, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1769, \"height\": 1266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 884, \"height\": 892, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1767, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1769, \"height\": 1113, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1756, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 858, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1778, \"height\": 862, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1322, \"height\": 2141, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1234, \"height\": 1010, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1237, \"height\": 1019, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1321, \"height\": 2140, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1594, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1772, \"height\": 1076, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1693, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1775, \"height\": 1170, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cnqyzuzhso/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1705, \"height\": 1315, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-cnqyzuzhso/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 888, \"height\": 762, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cnqyzuzhso/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 695, \"height\": 765, \"label\": \"Table\"}]"
motivation: 并行数据收集的超参数对网络可塑性和优化稳定性的影响未被充分理解。
method: 以PPO为重点，实证研究并行环境数量和rollout长度带来的偏差-方差权衡。
result: 发现并行策略会改变网络可塑性，影响样本效率和过拟合程度。
conclusion: 合理的并行配置能提升RL训练稳定性和网络泛化能力。
---

## Abstract
The use of parallel actors for data collection has been an effective technique used in reinforcement learning (RL) algorithms. The manner in which data is collected in these algorithms, controlled via the number of parallel environments and the rollout length, induces a form of bias-variance trade-off; the number of training passes over the collected data, on the other hand, must strike a balance between sample efficiency and overfitting. We conduct an empirical analysis of these trade-offs on PPO, one of the most popular RL algorithms that uses parallel actors, and establish connections to network plasticity and, more generally, optimization stability. We examine its impact on network architectures, as well as the hyper-parameter sensitivity when scaling data. Our analyses indicate that larger dataset sizes can increase final performance across a variety of settings, and that scaling parallel environments is more effective than increasing rollout lengths. These findings highlight the critical role of data collection strategies in improving agent performance.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义

**研究动机**：强化学习（RL）中，并行环境数据收集（通过并行环境和rollout长度控制）是提升样本效率的常用手段，但不同数据收集配置（并行环境数 `Nenvs` 与 rollout 长度 `NRO`）对网络可塑性、优化稳定性、过拟合的影响尚未被系统理解。现有研究指出，数据规模扩大会导致性能饱和（Singla et al., 2024），且算法常面临塑性损失（plasticity loss）和表征坍塌等问题。

**整体含义**：本文系统性地研究了并行数据收集策略（主要是 `Nenvs` 和 `NRO`）如何影响深度RL训练的稳定性、样本效率、网络表征质量以及最终性能，强调了数据收集的结构（而非仅数据量）在提升智能体性能中的关键作用。

## 2. 论文提出的方法论

**核心思想**：通过实证分析，比较不同数据收集配置（固定数据预算下改变 `Nenvs` 与 `NRO`，或按比例缩放二者）对PPO（以及PQN）的性能、学习动态指标的影响。论文还分析了数据重用（epoch数）加剧过拟合时，并行数据如何缓解退化。

**关键技术细节**：
- 固定数据预算：同时改变 `Nenvs` 与 `NRO` 使 `|B| = Nenvs × NRO` 不变，对比极端配置（如 `Nenvs=8, NRO=128` 与 `Nenvs=128, NRO=8`）。
- 数据缩放：通过单独加倍 `Nenvs` 或 `NRO` 增加批次大小。
- 数据重用：增加epoch数（从4倍到8倍、16倍），观察性能退化及缓解效果。
- 学习动态指标：feature rank、dormant neurons、weight norm、gradient kurtosis、policy variance、ESS（有效样本量）。

**算法流程**（文字说明）：
- 使用PPO（CleanRL实现），标准超参数，在Atari-10游戏套件上训练1亿时间步。
- 每5个种子运行，报告IQM（interquantile mean）及95%置信区间。
- 扩展分析至 Procgen（BigFish, StarPilot）和 Isaac Gym（AllegroHand, Humanoid, AnymalTerrain）环境，以及价值方法PQN。

## 3. 实验设计

**数据集 / 场景**：
- **主要 benchmark**：Arcade Learning Environment (ALE) 中的 Atari-10 游戏（Aitchison et al., 2023），包括 Amidar, Bowling, Frostbite, KungFuMaster, Riverraid, BattleZone, DoubleDunk, NameThisGame, Phoenix, Qbert。
- **扩展 benchmark**：
  - Procgen 套件（Cobbe et al., 2020）：BigFish, StarPilot（程序化生成关卡）。
  - Isaac Gym (Makoviychuk et al.)：AllegroHand, Humanoid, AnymalTerrain（连续控制任务）。
- **额外分析**： Freeway, Gravitar, MontezumaRevenge, Venture（硬探索游戏），使用PPO+RND。

**对比方法**：
- 主要聚焦于PPO（策略梯度方法），也对比了PQN（Parallel Q-Network，价值方法）。
- 对比不同 `Nenvs` 和 `NRO` 配置，以及不同epoch数、学习率、折扣因子γ的敏感性分析。
- 还对比了共享编码器与解耦（独立）actor-critic架构。

**评价指标**：
- 性能：Human-normalized IQM分数（聚合）、平均回合回报。
- 学习动态：feature rank、% dormant neurons、weight norm、gradient kurtosis、policy variance、ESS。
- 空间覆盖：UMAP投影 + coverage metric。

**公平性**：所有实验基于CleanRL标准实现，使用默认超参数，多个随机种子（5个），报告置信区间。

## 4. 资源与算力

论文明确说明：
- 使用 **NVIDIA Tesla A100 GPUs**。
- 每个实验大约需要 **2-3天**。
- 未明确给出GPU数量，但从并行环境数量（如Nenvs=128等）可推断需要多个环境实例，但未说明具体使用多少张GPU。算力消耗属于中等规模。

## 5. 实验数量与充分性

**实验数量**：
- 主实验（Atari-10）：5个种子 × 多种配置（默认、Nenvs×2、NRO×2、Nenvs=128 & NRO=8等）。
- 学习动态分析：在Atari-10上详细展示了4个代表性游戏（Amidar, NameThisGame, Phoenix, Riverraid）的指标曲线，其余游戏在附录中提供（Fig.10, Fig.13）。
- 消融实验：
  - 学习率缩放（Fig.11）
  - 折扣因子γ变化（Fig.12）
  - 解耦架构对比（Fig.5）
  - PQN对比（Fig.6, Fig.14）
- 扩展实验：Procgen（2个游戏），Isaac Gym（3个环境），硬探索游戏（Fig.15-16）。
- 总计约数十组独立实验（每组5个种子），覆盖多种环境和配置。

**充分性与客观性**：
- 实验覆盖较全面：不同算法（PPO, PQN）、不同任务类型（离散控制、连续控制、程序化生成）、不同网络架构（共享/解耦）。
- 使用标准benchmark和公认评估协议（Agarwal et al., 2021的IQM）。
- 然而，论文主要针对PPO，对PQN的分析较浅（性能提升不明显，仅轻度改善指标），未对其他算法（如SAC, DQN等）进行验证。此外，实验均基于仿真环境，未涉及真实机器人或大规模分布式系统。

## 6. 论文的主要结论与发现

1. **固定数据预算下，增加环境数比增加rollout长度更有效**（Fig.1a）。
2. **缩放数据时，增加 `Nenvs` 比增加 `NRO` 带来更高性能和样本效率**（Fig.1b）。
3. **增加环境数可缓解因数据重用（多epoch）导致的性能退化**（Fig.1c）。
4. **增加 `Nenvs` 改善了学习动态指标**：
   - 提升 feature rank（更丰富的表征）
   - 降低 dormant neurons（更大的网络利用率）
   - 降低 weight norm（训练更稳定）
   - 降低 gradient kurtosis（梯度分布更平滑，较少重尾）
   - 降低 policy variance，提升 ESS（更稳定的策略更新）
5. **解耦actor-critic架构在并行数据下获益更多**（Fig.5）。
6. **PPO对学习率和折扣因子的变化相对稳健**（Fig.11,12），性能增益不受超参数显著影响。
7. **价值方法（PQN）从 `Nenvs` 缩放中获益有限**，表明策略方法与价值方法对数据多样性的敏感度不同。
8. **在连续控制（Isaac Gym）和程序化生成（Procgen）环境中，趋势一致**（Fig.7,8）。

## 7. 优点

- **系统性的实证分析**：首次将 `Nenvs` 与 `NRO` 分开考虑，在固定和可变数据预算下进行多维度对比。
- **连接学习动态指标**：不仅报告最终性能，还从feature rank、dormant neurons、weight norm、kurtosis等角度解释性能提升原因，增强因果理解。
- **覆盖多种任务类型**：离散、连续、程序化生成，以及硬探索任务。
- **关注实际调参敏感性**：学习率、折扣因子、epoch数、架构选择，结果稳健。
- **开源实现**：基于CleanRL，可复现。

## 8. 不足与局限

- **算法覆盖有限**：主要验证PPO，对PQN的分析不深入，也未包括其他主流算法（如SAC, TD3, DQN等），结论普适性存疑。
- **数据多样性可观测性**：论文用UMAP和覆盖度度量状态空间覆盖，但未与更严格的entropy或探索奖励进行对比。
- **缺乏动态自适应策略**：训练中 `Nenvs` 和 `NRO` 是固定的，作者也承认未来可能动态调整。
- **计算资源未详细披露**：未明确使用多少GPU，也未提供完整的时间-性能折衷分析。
- **对塑性损失的分析有限**：虽然使用了dormant neurons等指标，但未与专门的塑性恢复方法（如Shrink and Perturb, ReDo等）进行对比。
- **实验环境相对简单**：Atari连续任务可能未能完全反映更复杂的RL场景（如布局、部分可观测等）。
- **消融实验不够全面**：例如未测试不同网络深度/宽度下的行为，也未测试不同优化器或激活函数。

（完）
