---
title: Preference Optimization for Combinatorial Optimization Problems
title_zh: 组合优化问题的偏好优化方法
authors: "Mingjun Pan, Guanquan Lin, You-Wei Luo, Bin Zhu, Zhien Dai, Lijun Sun, Chun Yuan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Jwe5FJ8QGx"
tags: ["query:graph-rl"]
score: 8.0
evidence: 面向组合优化的强化学习方法，可应用于图分区
tldr: 该论文针对强化学习在组合优化中奖励信号稀疏和探索效率低的问题，提出偏好优化方法，通过统计比较将定量奖励转化为定性偏好信号，并利用熵正则化策略进行优化。该方法在各类组合优化问题上取得显著性能提升，其通用框架可直接迁移至图分区等任务。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-jwe5fj8qgx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1550, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jwe5fj8qgx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1752, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jwe5fj8qgx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1748, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jwe5fj8qgx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1406, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jwe5fj8qgx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1472, \"height\": 1292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jwe5fj8qgx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1432, \"height\": 902, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1743, \"height\": 708, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1231, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1690, \"height\": 711, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 668, \"height\": 552, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 528, \"height\": 562, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 666, \"height\": 560, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 715, \"height\": 600, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 893, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 966, \"height\": 610, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1147, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jwe5fj8qgx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1448, \"height\": 458, \"label\": \"Table\"}]"
motivation: 现有强化学习组合优化方法面临奖励信号衰减和探索效率低下。
method: 提出偏好优化，通过统计比较将奖励转化为偏好信号，并引入熵正则化。
result: 在多个组合优化基准上超越现有方法，展示了强大的泛化能力。
conclusion: 偏好优化为组合优化提供了一种高效、通用的强化学习范式，有望应用于图分区等复杂问题。
---

## Abstract
Reinforcement Learning (RL) has emerged as a powerful tool for neural combinatorial optimization, enabling models to learn heuristics that solve complex problems without requiring expert knowledge. Despite significant progress, existing RL approaches face challenges such as diminishing reward signals and inefficient exploration in vast combinatorial action spaces, leading to inefficiency. In this paper, we propose **Preference Optimization**, a novel method that transforms quantitative reward signals into qualitative preference signals via statistical comparison modeling, emphasizing the superiority among sampled solutions. Methodologically, by reparameterizing the reward function in terms of policy and utilizing preference models, we formulate an entropy-regularized RL objective that aligns the policy directly with preferences while avoiding intractable computations. Furthermore, we integrate local search techniques into the fine-tuning rather than post-process to generate high-quality preference pairs, helping the policy escape local optima. Empirical results on various benchmarks, such as the Traveling Salesman Problem (TSP), the Capacitated Vehicle Routing Problem (CVRP) and the Flexible Flow Shop Problem (FFSP), demonstrate that our method significantly outperforms existing RL algorithms, achieving superior convergence efficiency and solution quality.

---

## 论文详细总结（自动生成）

# 论文总结：Preference Optimization for Combinatorial Optimization Problems

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：强化学习（RL）在神经组合优化（Neural Combinatorial Optimization）中展现出潜力，但现有RL方法面临两大核心挑战：
  - **奖励信号衰减**：随着策略提升，优势值（advantage value）幅度急剧减小，导致梯度消失与收敛缓慢。
  - **探索效率低**：组合优化问题具有巨大的动作空间，传统探索技术（如轨迹熵正则化）因计算不可行而难以应用。
- **整体含义**：本文旨在通过将定量奖励信号转换为定性偏好信号，并引入熵正则化目标，提出一种新的优化框架——**Preference Optimization（PO）**，以提升RL在组合优化中的收敛效率和解决方案质量。

## 2. 方法论
### 核心思想
- 将定量奖励信号（如路径长度）转化为**定性偏好信号**（如“解决方案A优于B”），避免对奖励绝对数值的依赖，从而稳定学习过程，并强调最优解的相对优越性。
- 基于最大熵强化学习框架（Haarnoja et al., 2017），推导出最优策略的解析形式，并利用偏好模型（如Bradley-Terry、Thurstone、Plackett-Luce）重新参数化奖励函数，将策略优化转化为偏好分类问题。

### 关键技术细节
- **重参数化奖励函数**：将奖励函数表示为策略对数概率的形式：\( r(x, \tau) = \alpha \log \pi(\tau | x) + \alpha \log Z(x) \)。由于 \( Z(x) \) 与轨迹无关，在比较中可消除，从而避免计算整个动作空间的配分函数。
- **偏好优化目标**：利用偏好模型（如Bradley-Terry模型）计算偏好概率 \( p(\tau_1 \succ \tau_2 | x) = \sigma(\alpha [\log \pi_\theta(\tau_1 | x) - \log \pi_\theta(\tau_2 | x)]) \)，并最大化偏好似然。
- **梯度形式**：得到的梯度类似于REINFORCE，但优势信号由成对比较生成，且具有量级不变性，可有效区分优劣解。
- **集成局部搜索（Local Search）**：在微调阶段（非后处理）将局部搜索（如2-Opt、Swap*）应用于采样解，生成改进解作为偏好对，使策略学习避开局部最优，且不增加推理时间。

### 算法流程（文字说明）
1. 对每个问题实例采样 \( N \) 个解；
2. （可选）对解执行少量局部搜索迭代，得到改进解；
3. 基于真实奖励函数生成无冲突偏好标签（如较短路径更优）；
4. 按式(8)计算梯度并更新策略参数 \( \theta \)；
5. 重复直至收敛。

## 3. 实验设计
### 使用的数据集/场景
- **标准基准**：Traveling Salesman Problem（TSP，n=20/50/100）、Capacitated Vehicle Routing Problem（CVRP，n=20/50/100）、Flexible Flow Shop Problem（FFSP，n=20/50/100）。
- **泛化测试**：零样本测试于非均匀分布（Cluster, Expansion, Explosion, Grid, Implosion）及真实基准库TSPLib和CVRPLib。
- **大规模问题**：TSP-500/1000/10000。

### Benchmark 与对比方法
- **启发式方法**：Concorde（TSP）、LKH3、HGS（CVRP）、CPLEX、Genetic Algorithm、Particle Swarm Optimization（FFSP）。
- **基于RL的神经求解器**：AM (Kool et al., 2019)、POMO (Kwon et al., 2020)、Sym-NCO (Kim et al., 2022)、Pointerformer (Jin et al., 2023)、ELG (Gao et al., 2024)、MatNet (Kwon et al., 2021)、DIMES (Qiu et al., 2022)、COMPASS、Poppy。
- 对比方式：将PO替换原REINFORCE（RF）算法，在相同网络架构下比较，确保公平。

## 4. 资源与算力
- **文中提及**：大多数实验在配备**NVIDIA 24GB-RTX 4090 GPU**和**Intel Xeon Gold 6133 CPU**的服务器上运行。
- **未明确说明**：具体GPU数量、训练总时长（仅给出每个epoch的大致时间，如TSP-100的训练epoch约9分钟，微调约12分钟；CVRP-100训练epoch约8分钟，微调约20分钟）。也未说明多卡并行情况。

## 5. 实验数量与充分性
- **实验组数**：广泛覆盖多种问题规模和变体：
  - 三个核心问题（TSP、CVRP、FFSP）各三个规模；
  - 零样本泛化实验（5种分布+2个真实基准库）；
  - 大规模问题（TSP-500/1000/10000）使用DIMES；
  - 消融研究：偏好模型比较（BT、PL、Th、Exp）、熵分析、一致性分析、优势分离可视化；
  - 额外实验：POMO长时训练、COMPASS/Poppy框架适配、FFSP更多规模。
- **充分性与公平性**：
  - 与多种启发式和神经方法比较，且所有对比均在同一架构下替换算法；
  - 提供了性能（Gap）、时间、样本效率等多维度指标；
  - 消融实验充分，验证了偏好模型选择、局部搜索微调等关键设计；
  - 但未在所有实验中进行超参数敏感性测试（仅简要提及α调参策略）。

## 6. 主要结论与发现
- **收敛效率**：PO在POMO、Sym-NCO、Pointerformer等模型上达到**1.5x~2.5x**加速，仅需REINFORCE 40%~60%的epoch即可达到同等或更优性能。
- **解质量**：在TSP、CVRP、FFSP上，PO训练的策略在相同推理时间内多数取得更低的Gap；结合局部搜索微调可进一步逼近最优（TSP-100 gap 0.03%，CVRP-100 gap 1.19%）。
- **泛化能力**：在零样本跨分布和真实基准测试中，PO均优于REINFORCE版本，验证了其稳定性。
- **探索-利用平衡**：PO能产生更分散的优势值分布、更高的轨迹熵，且策略一致性（根据奖励排序）显著优于REINFORCE。
- **偏好模型影响**：Bradley-Terry模型在较小规模上表现较好，而指数模型在复杂问题上更强。

## 7. 优点
- **方法创新性**：将基于偏好的优化（类似RLHF）成功引入组合优化领域，解决了奖励信号衰减和探索困难两大痛点。
- **通用性**：PO作为算法框架，可直接替换现有RL4CO求解器的策略梯度方法，不依赖特定网络结构，兼容POMO、Sym-NCO、DIMES等多种架构。
- **实用性**：将局部搜索从后处理嵌入微调，避免推理额外开销，同时提高解质量。
- **理论支撑**：基于最大熵RL推导，保证了策略最优性，且对奖励函数的仿射变换具有不变性。
- **实验丰富**：覆盖多问题、多规模、多分布，并进行大量消融和可视化分析，验证了方法的有效性。

## 8. 不足与局限
- **算力信息披露不充分**：未明确给出训练全程的GPU数量和总时间，不利于复现和成本估算。
- **超参数敏感性分析**：仅简述α的调参经验，未系统展示α对性能的影响曲线，可能影响通用性。
- **局部搜索微调阶段**：虽然减少了推理时间，但训练时仍需执行局部搜索（CPU计算），增加训练负担，论文未量化该开销。
- **偏好模型选择的指导**：虽然比较了四种模型，但未提供针对不同问题如何选择的明确准则或自适应机制。
- **应用范围限制**：论文主要关注确定性的经典组合优化问题（TSP、CVRP、FFSP），未探讨随机性或动态环境下的表现。
- **安全性/偏见风险**：由于偏好信号基于客观奖励（如路径长度），不存在人为偏好冲突，但未讨论对奖励设计错误的鲁棒性（如奖励噪声）。

（完）
