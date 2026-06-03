---
title: Towards Large-Scale In-Context Reinforcement Learning by Meta-Training in Randomized Worlds
title_zh: 通过随机世界元训练迈向大规模上下文强化学习
authors: "Fan Wang, Pengtao Shao, Yiming Zhang, Bo Yu, Shaoshan Liu, Ning Ding, Yang Cao, Yu Kang, Haifeng Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=b6ASJBXtgP"
tags: ["query:graph-part"]
score: 4.0
evidence: 大规模上下文强化学习的元训练
tldr: 该论文为上下文强化学习（ICRL）的大规模扩展提出AnyMDP，通过过程生成制表MDP和分离策略蒸馏进行元训练，解决了ICRL缺乏可扩展任务集合的挑战，实验验证了任务规模对性能的正向影响。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1422, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1393, \"height\": 221, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1423, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1100, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1396, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1407, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 739, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1433, \"height\": 1475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1388, \"height\": 209, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1423, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 710, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1427, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1435, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1204, \"height\": 1173, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-b6asjbxtgp/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1248, \"height\": 312, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 742, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1430, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1405, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1244, \"height\": 1464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1377, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1276, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 973, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1198, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-b6asjbxtgp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 912, \"height\": 317, \"label\": \"Table\"}]"
motivation: 上下文强化学习面临任务集合规模不足的瓶颈，限制了其泛化能力。
method: 提出AnyMDP随机生成过程，结合分离策略蒸馏和先验注入，实现大规模元训练。
result: 在足够多的AnyMDP任务上元训练后，模型在未见任务上表现出强大的在线学习能力。
conclusion: 该工作为大规模ICRL提供了一种实用的任务生成和训练范式。
---

## Abstract
In-Context Reinforcement Learning (ICRL) enables agents to learn automatically and on-the-fly from their interactive experiences. However, a major challenge in scaling up ICRL is the lack of scalable task collections. To address this, we propose the procedurally generated tabular Markov Decision Processes, named AnyMDP. Through a carefully designed randomization process, AnyMDP is capable of generating high-quality tasks on a large scale while maintaining relatively low structural biases. To facilitate efficient meta-training at scale, we further introduce decoupled policy distillation and induce prior information in the ICRL framework. Our results demonstrate that, with a sufficiently large scale of AnyMDP tasks, the proposed model can generalize to tasks that were not considered in the training set through versatile in-context learning paradigms. The scalable task set provided by AnyMDP also enables a more thorough empirical investigation of the relationship between data distribution and ICRL performance. We further show that the generalization of ICRL potentially comes at the cost of increased task diversity and longer adaptation periods. This finding carries critical implications for scaling robust ICRL capabilities, highlighting the necessity of diverse and extensive task design, and prioritizing asymptotic performance over few-shot adaptation.

---

## 论文详细总结（自动生成）

### 论文的中文详细总结

#### 1. 核心问题与整体含义

- **研究动机与背景**：上下文强化学习（ICRL）能使智能体在交互过程中即时学习，无需调整参数。但ICRL扩展面临的核心瓶颈是**缺少可扩展的任务集合**。现有基准要么过于简化（如多臂老虎机），要么仅对表面参数随机化（如迷宫纹理），导致模型继承环境的结构性偏差，泛化能力有限。
- **整体目标**：本文提出两项互相关联的贡献——① **AnyMDP**：一种可扩展、低结构偏差的程序化生成MDP任务集；② **OmniRL**：结合解耦策略蒸馏与先验注入的可扩展ICRL框架。旨在推动ICRL的大规模元训练与泛化。

#### 2. 方法论

- **核心思想**：通过过程化生成离散MDP，并在元训练中使用解耦策略蒸馏与先验信息，让模型学会在上下文中动态适应新任务。
- **关键技术细节**：
  - **AnyMDP**：生成满足**带状态排序的带状转移矩阵**（banded transition matrix）与**递增价值函数**的MDP。通过定理1保证随机策略下状态的稳态分布呈指数衰减，模拟真实长程任务中高价值状态难以随机到达的特性。使用**复合奖励（Composite Reward）** 采样，降低结构偏差。
  - **OmniRL框架**：
    - **解耦策略蒸馏（DPD）**：将行为策略（用于生成训练轨迹）与参考策略（被模仿的最优策略）分离，减少训练与推理轨迹间的分布偏移，并支持逐点监督（step-wise supervision），提高训练效率。
    - **先验注入**：在轨迹中添加标记（tag），指示每个动作由何种策略生成（如贪婪、Q学习、模型基等），帮助模型理解异构行为。
    - **分块训练（Chunkwise Training）**：将长序列分段，利用线性注意力模型（如RWKV-7）的递归/分段前向传播，支持超长上下文（高达512K步）。
  - **损失函数**：逐点交叉熵损失，最小化预测动作与参考策略动作的差异。
- **算法流程**：数据采集时，使用多种行为策略（7种）生成轨迹，参考策略为oracle；训练时，每2K步为一个segment，梯度在段内计算并累积，序列结束时更新参数。

#### 3. 实验设计

- **数据集/场景**：
  - **AnyMDP任务**：训练集包含512K条序列，总步数60亿（6B steps），状态数ns∈[16,128]，动作数na=5。测试集独立采样256个未见任务（ns∈{1,16,32,64,128}）。
  - **Gymnasium环境**：CliffWalking、FrozenLake（滑动/非滑动）、Discrete-Pendulum等。
  - **其他基准**：DarkRoom（6x6,8x8,10x10）、Garnet MDP、多智能体Switch2。
- **Benchmark与对比方法**：
  - 对比算法：Tabular Q-Learning with UCB（TQL-UCB）、PPO、Algorithm Distillation（AD）、ADε、Decision Pre-Training Transformer（DPT）。
  - 消融：无先验信息（w/o a priori）、不同任务数量（100/1K/10K/128K）的影响、不同线性注意力架构（RWKV-7, GDN, GSA, Mamba2）。
- **评估设置**：三种初始化上下文：在线RL（空轨迹）、离线RL（含50回合次优演示）、模仿学习（含50回合oracle演示）。性能归一化为0%（随机策略）到100%（oracle策略）。

#### 4. 资源与算力

- 文中明确指出：元训练主要使用**8块Nvidia Tesla A800 GPU**，每GPU批次大小为5，每段2K步，序列长度12K步，总数据量60亿步。优化器为AdamW，峰值学习率2e-4。平均每次迭代耗时约8秒。
- 此外，AnyMDP任务生成在单CPU上进行，但支持并行加速。

#### 5. 实验数量与充分性

- 实验数量充足：包括不同规模任务集（100/1K/10K/128K）、不同架构、不同初始化模式（在线/离线/模仿）、多种未见环境（Gymnasium、DarkRoom、多智能体）以及泛化到连续空间（经离散化）。消融实验覆盖了先验信息、任务数量、上下文长度等因素。
- 充分性与客观性：所有基准方法均使用相同训练迭代和超参数优化，展现清晰趋势。报告了95%置信区间。对比方法（TQL-UCB, PPO）在各自任务族内进行了网格搜索调参。实验设计较为公平。

#### 6. 主要结论与发现

- **AnyMDP能生成高质量、高学习难度的任务**，且其稳态分布指数衰减，迫使学习者进行智能探索而非随机搜索。
- **OmniRL在未见AnyMDP任务、Gymnasium环境甚至多智能体任务上展现出强大的泛化能力**，且样本效率明显优于TQL-UCB和PPO。
- **任务数量与多样性是ICRL泛化的关键**：当训练任务数≤10K时，出现过拟合（仅泛化到已见任务）；当达到128K时，模型表现出对未见任务的强大ICL能力。
- **长上下文是泛化必须付出的代价**：更通用的ICRL需要更长的适应期，其零样本性能可能反而低于窄分布模型，因此应重视渐近性能而非少样本表现。
- **先验信息和解耦策略蒸馏显著提升性能**（图6、表2）。

#### 7. 优点

- **AnyMDP设计精巧**：通过带状转移矩阵和递增价值函数，在保持任务多样性的同时确保非平凡学习难度，且可扩展至任意状态/动作空间。
- **OmniRL框架高效**：解耦策略蒸馏避免了传统算法蒸馏（AD）的分布偏移问题，分块训练支持超长上下文，线性注意力架构（RWKV-7）便于扩展。
- **实验覆盖全面**：从表格MDP到连续环境、从单智能体到多智能体、从在线到离线/模仿学习，多角度验证了ICRL的通用性。
- **洞察深刻**：揭示了任务规模与ICL涌现之间的关系，以及长上下文与泛化间的权衡，对后续ICRL研究具有指导意义。

#### 8. 不足与局限

- **局限于离散状态-动作空间**：虽然通过离散化能处理部分连续环境（如Pendulum），但直接扩展到高维连续空间仍存在瓶颈。
- **AnyMDP仍是合成任务**：与真实世界复杂任务（如机器人控制、自动驾驶）存在差距，需进一步验证迁移能力。
- **计算资源需求高**：尽管效率较高，但训练6B步仍需要8卡A800；生成AnyMDP任务时对于小状态（如ns=8）需要频繁重采样，耗时较长。
- **对奖励塑形敏感**：在Gymnasium任务中需要手工调整奖励才能获得良好性能（如图13所示），说明模型对奖励函数的设计较为敏感。
- **未充分探讨灾难性遗忘**：当任务数过多时是否会发生遗忘或性能退化未详细讨论。
- **理论贡献较弱**：定理1给出了稳态分布的指数衰减保证，但其余部分主要依赖经验验证。

（完）
