---
title: Can Learned Optimization Make Reinforcement Learning Less Difficult?
title_zh: 学习优化能否让强化学习不再困难？
authors: "Alexander D. Goldie, Chris Lu, Matthew Thomas Jackson, Shimon Whiteson, Jakob Nicolaus Foerster"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=YbxFwaSA9Z"
tags: ["query:graph-part"]
score: 7.0
evidence: 元学习优化器解决强化学习的非平稳性、塑性损失和探索问题
tldr: 本文提出元学习优化器OPEN，针对强化学习固有的非平稳性、塑性损失和探索困难三个难题，学习统一的更新规则。特征输入和输出结构融合了先前解决办法。实验表明OPEN在连续控制任务中显著提升样本效率和最终性能，展示了元优化克服RL多重困难的潜力。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 945, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1235, \"height\": 290, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1406, \"height\": 334, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1335, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 676, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1413, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 640, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 583, \"height\": 274, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 819, \"height\": 175, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1227, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1310, \"height\": 794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1399, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1337, \"height\": 1638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1334, \"height\": 239, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1332, \"height\": 237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1344, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1282, \"height\": 1175, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1020, \"height\": 1236, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1133, \"height\": 1131, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ybxfwasa9z/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1116, \"height\": 1005, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 584, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 583, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1133, \"height\": 671, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1103, \"height\": 647, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1071, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1451, \"height\": 647, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1302, \"height\": 712, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1417, \"height\": 787, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1330, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 617, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 974, \"height\": 967, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 863, \"height\": 846, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1280, \"height\": 515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ybxfwasa9z/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1003, \"height\": 477, \"label\": \"Table\"}]"
motivation: RL面临非平稳性、塑性损失和探索困难，需要针对性处理。
method: 元学习一个通用更新规则OPEN，其结构与已有解决方案对齐，同时应对三个难题。
result: 在连续控制任务中，OPEN提升样本效率和最终回报，优于基线。
conclusion: 元学习优化器可统一解决RL多个核心困难。
---

## Abstract
While reinforcement learning (RL) holds great potential for decision making in the real world, it suffers from a number of unique difficulties which often need specific consideration. In particular: it is highly non-stationary; suffers from high degrees of plasticity loss; and requires exploration to prevent premature convergence to local optima and maximize return. In this paper, we consider whether learned optimization can help overcome these problems. Our method, Learned **O**ptimization for **P**lasticity, **E**xploration and **N**on-stationarity (*OPEN*), meta-learns an update rule whose input features and output structure are informed by previously proposed solutions to these difficulties. We show that our parameterization is flexible enough to enable meta-learning in diverse learning contexts, including the ability to use stochasticity for exploration. Our experiments demonstrate that when meta-trained on single and small sets of environments, *OPEN* outperforms or equals traditionally used optimizers. Furthermore, *OPEN* shows strong generalization characteristics across a range of environments and agent architectures.

---

## 论文详细总结（自动生成）

# 论文总结：Can Learned Optimization Make Reinforcement Learning Less Difficult?

## 1. 论文的核心问题与整体含义（研究动机和背景）

强化学习（RL）在真实世界决策中潜力巨大，但面临三大独特困难：
- **非平稳性（Non-stationarity）**：训练过程中智能体的行为不断改变输入和输出分布，导致训练分布随时间变化。
- **塑性损失（Plasticity loss）**：神经网络在训练后期逐渐丧失拟合新目标的能力，表现为神经元“休眠”（dormancy）。
- **探索（Exploration）**：需要有效探索以避免过早收敛到局部最优，最大化最终回报。

现有的手工设计优化器（如Adam、RMSProp）主要针对监督学习设计，未考虑RL的这些特定问题。已有的一些学习优化器（如VeLO、Optim4RL）在RL中表现不佳，因为它们没有针对性解决RL的困难。本文旨在通过**元学习（meta-learning）**为RL学习一个专门设计的优化器，能够同时缓解上述三个问题。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
提出 **OPEN**（Learned Optimization for Plasticity, Exploration and Non-stationarity），它是一个参数化的更新规则（update rule），通过元训练学习得到。其输入特征和输出结构借鉴了以往针对RL三大困难的手工解决方案，使优化器能够有针对性地处理非平稳性、塑性损失和探索。

### 关键技术细节
- **架构**：使用一个**门控循环单元（GRU）**来捕捉历史依赖（类似动量），后接两个全连接层和LayerNorm。所有层规模较小以节省内存。
- **更新表达式**：
  1. 基础更新：  
     \( \hat{u}_i = \alpha_1 m_i \exp(\alpha_2 e_i) \)  
     其中 \( m_i \) 和 \( e_i \) 是优化器输出，\( \alpha_1, \alpha_2 \) 为缩放因子，使更新能跨越多个数量级。
  2. **针对探索的随机性**（仅用于actor）：  
     \( \hat{u}_{\text{actor}, i}^{\text{new}} := \hat{u}_{\text{actor}, i} + \alpha_3 \delta_{\text{actor}, i} \epsilon \)  
     其中 \( \epsilon \sim \mathcal{N}(0,1) \)，\( \delta_{\text{actor}, i} \) 是学习的每参数方差，用于添加参数空间噪声。这有助于探索，同时还能通过噪声重新激活休眠神经元（缓解塑性损失）。
  3. **零均值化**：最后减去均值，防止数值不稳定。
- **输入特征**（关键创新）：
  - **梯度**和**动量**（多个β值：0.1, 0.5, 0.9, 0.99, 0.999, 0.9999），经符号和log变换。
  - **当前参数值**。
  - **训练比例**（training proportion）：当前batch在整个训练中的进度，针对非平稳性。
  - **批次比例**（batch proportion）：当前更新在同一个batch内的进度，允许学习率调度等。
  - **休眠度（dormancy）**：下游神经元的τ=0休眠率，针对塑性损失。
  - **层比例**（layer proportion）：参数所在层在网络中的相对位置，允许在不同层采取不同行为。
- **训练方法**：使用**进化策略（OpenAI ES）**，以最终回报作为适应度（fitness）。采用**排名变换**（rank transform）将群体排名映射到[-0.5, 0.5]以稳定训练。多任务训练时，每个环境的回报除以Adam在该环境的回报进行归一化，再平均后做排名变换。

## 3. 实验设计

### 使用的数据集/场景
- **MinAtar**（Breakout, Asterix, Space Invaders, Freeway）
- **Brax/Ant**（连续控制）
- **Gridworlds**（来自Jackson et al.的分布，以及Oh et al.的三种gridworld和minigrid三种迷宫）
- **Craftax-Classic**（Crafter的Jax重实现）
- **Deep Sea**（bsuite，用于测试探索）
- **PQN**（另一种RL算法）

### Benchmark
- **单任务训练**（Single-Task Training）：在单个环境上训练并评估。
- **多任务训练**（Multi-Task Training）：同时在所有四个MinAtar环境上训练，评估平均归一化回报。
- **分布内任务泛化**（In-Distribution Task Generalization）：在gridworld分布上训练，同分布评估。
- **分布外任务泛化**（Out-Of-Support Task Generalization）：在未见的gridworld、minigrid迷宫以及Craftax-Classic上0-shot评估。

### 对比的方法
- 手工优化器：**Adam**、**RMSProp**
- 符号发现优化器：**Lion**
- 预训练学习优化器：**VeLO**
- 针对RL的学习优化器：**Optim4RL**
- 消融基线：**No Features**（仅输入梯度和动量，无额外特征）

## 4. 资源与算力

论文详细报告了计算资源：
- **训练硬件**：混用Nvidia A40、L40s、GTX 1080Ti、RTX 2080Ti、RTX 3080等（内部集群）。
- **单任务训练**：每个学习优化器约 **16-32 GPU天**。
- **多任务训练**：每个优化器约 **60 GPU天**。
- **网格世界训练**：约 **7 GPU天**。
- **消融实验**：约 **8 GPU天**（119个优化器）。
- **Deep Sea实验**：约 **8 GPU天**。
- **总计算量**：约 **2.1 GPU年**（含前期未报告实验）。
- **推理时间**：OPEN比Adam慢约1.5-2倍，但远快于VeLO，与其他学习优化器相当。

## 5. 实验数量与充分性

- **单任务**：5个环境，每个环境训练一次OPEN（单种子），评估16个随机种子。
- **多任务**：4个MinAtar环境，训练300代，评估16个种子。
- **网格世界泛化**：7个gridworld变体（包括分布内和分布外），每个评估64个种子，覆盖不同网络宽度（8-128）和不同训练长度。
- **Craftax-Classic**：0-shot测试，32个种子。
- **消融实验**：17个优化器×每个消融配置（共6种消融+基线+OPEN），每个优化器评估64个种子。另对探索单独在Deep Sea上实验（128种子）。
- **替代RL算法**：PQN在Asterix上，64种子。
- **充分性**：实验覆盖了单任务、多任务、泛化、消融等多个维度，使用了多种环境和种子数量。但**每个学习优化器只训练一次（单一随机种子）**，这是计算成本限制下的常见做法（与VeLO等类似）。置信区间通过bootstrap计算，评估了统计显著性。总体而言实验设计比较全面，但元训练阶段的随机性未被充分刻画，可能影响结论的稳健性。

## 6. 论文的主要结论与发现

- **OPEN在单任务上显著优于所有基线**（除Ant外与手工优化器持平），在某些MinAtar环境上超越Adam 30-50%。
- **多任务训练中，OPEN是唯一归一化回报超过Adam的学习优化器**，其他学习优化器均低于Adam。
- **泛化能力强**：在未见过的gridworld、不同网络宽度、不同训练长度下，OPEN始终优于Adam；在Craftax-Classic上0-shot优于仅同分布调优的Adam。
- **消融实验表明**：每个设计组件（训练比例、批次比例、休眠度、层比例、随机性）都对性能有正面贡献，去除后会降低回报和增加塑性损失。
- **探索方面**：带有可学习随机性的OPEN在Deep Sea大尺寸环境中显著优于无随机性的版本，并且随机性随环境大小自动增加。
- **适用于不同RL算法**：在PQN（类似DQN）上也取得优于Adam的性能。

## 7. 优点

- **问题导向设计**：从RL三大困难出发设计输入特征和输出结构，而非简单端到端学习，使优化器有明确的可解释目标和针对性。
- **方法简洁有效**：使用小型GRU+MLP，训练成本相对可控（约1 GPU月），却能在多个场景超越大规模预训练的VeLO（4000 TPU月）。
- **泛化能力突出**：跨环境、跨agent架构、跨训练长度都表现出色，证明了方法的鲁棒性。
- **消融实验完整**：系统分析每个组件的影响，验证了设计选择的合理性。
- **低计算门槛**：相比VeLO等，OPEN的元训练成本低，便于复现和应用。

## 8. 不足与局限

- **元训练仅单次运行**：受限于计算成本，每个设置只训练一个优化器，未报告元训练随机性对结果的影响，可能降低结论的统计可靠性。
- **多任务训练中的归一化偏差**：使用Adam回报归一化会导致优化器偏向Adam较差的场景，可能限制了性能上限。作者也承认需要更优的课程学习（curriculum）。
- **仅测试了PPO和PQN**：未在SAC、A2C等流行算法上验证，普适性待进一步确认。
- **推理速度**：OPEN比手工优化器慢约1.5-2倍，虽然优于VeLO，但在实时或大规模应用中可能成为瓶颈。
- **可解释性有限**：由于使用黑箱GRU，很难解释学习到的更新规则的具体行为，对调试和理解不利。
- **不支持离线/批处理RL场景**：实验仅基于on-policy PPO和off-policy PQN的在线设置，未涵盖离线RL等。
- **对连续控制任务（Ant）改善有限**：在Ant上与其他方法相当，未体现显著优势。

（完）
