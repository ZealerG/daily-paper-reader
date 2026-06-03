---
title: "O-MAPL: Offline Multi-agent Preference Learning"
title_zh: O-MAPL：离线多智能体偏好学习
authors: "The Viet Bui, Tien Anh Mai, Thanh Hong Nguyen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=FYvrNKYu6H"
tags: ["query:graph-part"]
score: 7.0
evidence: 多智能体强化学习的偏好奖励学习，与并行决策相关
tldr: 该论文针对离线多智能体强化学习中奖励推断的困难，提出端到端偏好学习方法OMAPL，利用合作MARL中奖励函数与Q函数的内在联系，直接从偏好反馈中学习联合策略，避免了传统两阶段训练的不稳定性。方法在多个多智能体任务上取得优异表现。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1502, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 905, \"height\": 678, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 975, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1170, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1407, \"height\": 683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1160, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1405, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1169, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1403, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1158, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fyvrnkyu6h/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1410, \"height\": 681, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 835, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1778, \"height\": 908, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 867, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1781, \"height\": 1052, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1237, \"height\": 1054, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 841, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1176, \"height\": 1023, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1607, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1188, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1277, \"height\": 823, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1271, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1357, \"height\": 828, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1192, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1279, \"height\": 833, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1267, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1357, \"height\": 831, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1779, \"height\": 613, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1778, \"height\": 719, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1607, \"height\": 884, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fyvrnkyu6h/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1167, \"height\": 972, \"label\": \"Table\"}]"
motivation: 多智能体离线环境从偏好学习奖励函数存在训练不稳定问题。
method: 利用Q函数与奖励函数的内在联系，设计端到端偏好学习框架。
result: 在合作多智能体任务上超越了分离式训练方法。
conclusion: 为多智能体离线偏好学习提供了稳定高效的解决方案，支持并行决策场景。
---

## Abstract
Inferring reward functions from demonstrations is a key challenge in reinforcement learning (RL), particularly in multi-agent RL (MARL). The large joint state-action spaces and intricate inter-agent interactions in MARL make inferring the joint reward function especially challenging. While prior studies in single-agent settings have explored ways to recover reward functions and expert policies from human preference feedback, such studies in MARL remain limited. Existing methods typically combine two separate stages, supervised reward learning, and standard MARL algorithms, leading to unstable training processes. In this work, we exploit the inherent connection between reward functions and Q functions in cooperative MARL to introduce a novel end-to-end preference-based learning framework.
Our framework is supported by a carefully designed multi-agent value decomposition strategy that enhances training efficiency. Extensive experiments on two state-of-the-art benchmarks, SMAC and MAMuJoCo, using preference data generated by both rule-based and large language model approaches demonstrate that our algorithm consistently outperforms existing methods across various tasks.

---

## 论文详细总结（自动生成）

# 论文《O-MAPL: Offline Multi-agent Preference Learning》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：在多智能体强化学习（MARL）中，从演示数据（如人类偏好）中推断奖励函数极具挑战性，因为联合状态-动作空间巨大，智能体间交互复杂。传统方法采用“两阶段”流程——先通过监督学习训练奖励模型，再使用 MARL 算法优化策略，但这种分离式训练容易导致稳定性差、误差传播和阶段间不匹配。此外，离线环境下无法与环境交互，加剧了分布偏移（distribution shift）问题。
- **整体含义**：本文旨在提出一种**端到端**的离线多智能体偏好学习方法，直接从偏好数据中学习联合策略，避免显式奖励建模，从而提高训练稳定性与策略质量。这项工作填补了多智能体环境下偏好学习研究的空白，对现实世界中难以设计明确奖励信号的合作任务（如机器人集群、星际争霸微观控制）具有重要意义。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

### 2.1 核心思想
- 利用**最大熵强化学习（MaxEnt RL）** 中奖励函数与软Q函数之间的一一对应关系（逆软贝尔曼算子），将偏好学习问题转化为**Q空间**中的学习问题。这样无需显式学习奖励函数，直接通过优化Q函数和V函数，就能通过软策略公式（公式1）提取最优策略。

### 2.2 关键技术细节
- **偏好建模**：采用 Bradley-Terry 模型，偏好概率由轨迹的“逆软贝尔曼累加和”决定（公式4）。
- **价值分解（Value Factorization）**：在集中训练分散执行（CTDE）框架下，将全局Q函数和V函数通过**单层线性混合网络（Mixing Network）** 分解为局部Q函数和局部V函数的加权和。线性混合保证学习目标是**凸的/凹的**（Proposition 4.1），从而稳定优化；而两层非线性网络会破坏凸性（Proposition 4.2），且易过拟合。
- **训练目标**：
  - 最大化以轨迹对为单位的**偏好似然损失** \(L(q,v,w)\)（公式6）。
  - 通过**极端V损失（Extreme-V loss, \(J(v)\)）** 迫使全局V函数满足 log-sum-exp 关系（即 Bellman 一致性）。
  - 为防止奖励无界，引入 \(\chi^2\) 正则化项 \(\phi(x) = -\frac{1}{2}x^2 + x\)。
- **策略提取**：提出**加权行为克隆（Weighted Behavior Cloning, WBC）** 方法。通过最大化全局权重（soft advantage）加权的局部策略对数似然来训练每个智能体的局部策略网络。这种方法保证了**全局-局部一致性（GLC）**（Theorem 4.3），且适用于任意混合网络结构（包括非线性）。而传统的局部值直接提取方法需要归一化，会破坏 GLC。
- **算法流程**（Algorithm 1）：
  1. 初始化 Q/V 网络参数 \(\psi_q, \psi_v\)、混合网络参数 \(\theta\)、局部策略网络参数 \(\omega_i\)。
  2. 每步：
     - 最大化 \(L(\psi_q,\psi_v,\theta)\) 更新 \(\psi_q\) 和 \(\theta\)。
     - 最小化 \(J(\psi_v)\) 更新 \(\psi_v\)。
     - 最大化局部 WBC 损失 \(\Psi(\omega_i)\) 更新每个策略网络。
  3. 返回训练好的局部策略 \(\pi_i\)。

## 3. 实验设计

### 3.1 使用的数据集与场景
- **SMACv1**：4个任务（2c vs 64zg, 5m vs 6m, 6h vs 8z, corridor），离散动作空间。
- **SMACv2**：15个任务，按种族（Protoss, Terran, Zerg）和规模（5v5, 10v10, 10v11, 20v20, 20v23）划分，共15个子任务。
- **MAMuJoCo**：3个连续控制任务（Hopper-v2, Ant-v2, HalfCheetah-v2）。
- **偏好数据生成**：两种方式
  - **基于规则（Rule-based）**：从质量不同的离线数据集（poor, medium, expert）中采样轨迹对，按数据集质量定义偏好标签。
  - **基于大语言模型（LLM-based）**：使用 GPT-4o 根据提取的状态信息（如剩余生命、盾牌、敌我死亡数等）对轨迹对进行标注。仅适用于 SMAC（因为状态信息可解释）。每个任务生成了2000对偏好数据（SMAC）或1000对（MAMuJoCo）。

### 3.2 对比方法（Baselines）
- **BC**：行为克隆，在偏好轨迹上直接监督学习。
- **IIPL**：独立 IPL（每智能体独立运行单智能体 IPL 算法）。
- **IPL-VDN**：类似作者方法，但使用 VDN（简单求和）代替混合网络。
- **SL-MARL**：两阶段方法，先学习奖励函数，再用 OMIGA（离线 MARL 算法）训练策略。
- **O-MAPL（本文）**：端到端方法，使用作者提出的线性混合网络 + 加权行为克隆。

## 4. 资源与算力

- 文中明确提到：“All experiments were implemented using PyTorch and executed in parallel on a single NVIDIA® H100 NVL Tensor Core GPU”。
- 未提及具体训练时长、迭代次数或总 GPU 小时数，仅提到每个任务训练了 100 个评估步骤（evaluation steps），每次评估使用 32 个 episodes。
- 附录表 6 给出了超参数：学习率 1e-4、batch size 32、隐藏层维度 256、混合网络隐藏维度 64。
- 总体算力描述不够详细，属于中等规模实验（单卡 H100 可完成）。

## 5. 实验数量与充分性

- **实验总数**：涵盖 4（SMACv1）+ 15（SMACv2）+ 3（MAMuJoCo）= **22 个主任务**，每个任务使用两种数据生成方式（Rule 和 LLM，SMAC 部分），加上消融实验（数据保留比例、1-layer vs 2-layer mixers、GPT-4o vs GPT-4o-mini），总实验组数庞大，统计上充分。
- **客观性与公平性**：
  - 每个结果报告 4 个随机种子的均值与标准差，体现统计稳定性。
  - 对比方法包括最直接的离线 MARL 和偏好学习变体，且作者开源了代码（附录提到）。
  - 消融实验系统分析了不同组件的影响（混合结构、数据质量、数据量）。
- **充分性评价**：实验设计较全面，覆盖了离散和连续动作空间、不同任务复杂度、不同偏好质量来源。但缺少真实人类偏好数据（均为自动生成），也缺少在混合合作-竞争场景下的评估。

## 6. 主要结论与发现

- **O-MAPL 在几乎所有任务上显著优于所有基线**。
  - 在 SMACv1 的 corridor 任务中，O-MAPL 胜率达 93.2%（规则）和 94.5%（LLM），远超 SL-MARL（49.0% 和 57.6%）。
  - 在 MAMuJoCo 的 Hopper-v2 上，O-MAPL 平均回报 1114.4，比第二好的 SL-MARL（890.0）提升 25%。
- **LLM 生成的偏好数据比规则数据带来更高性能**，说明利用 LLM 进行自动偏好标注是有效且低成本的替代方案。
- **单层线性混合网络优于两层非线性混合网络**：不仅保证凸性/凹性稳定训练，而且实际性能更高，避免过拟合（表19）。
- **线性混合下的加权行为克隆优于局部值提取**：前者保持全局-局部一致性并生成有效概率分布。
- **随着偏好数据量减少，O-MAPL 仍保持较好性能**，但 SL-MARL 和 IPL-VDN 下降更剧烈（表17-18）。

## 7. 优点

- **端到端范式**：避免了显式奖励建模的两阶段不稳定性，优化更一致。
- **理论完备**：证明了损失函数的凸性/凹性，以及全局-局部一致性，为算法提供了良好的收敛保证。
- **实用性强**：提出的线性混合网络简单有效，加权行为克隆避免了归一化问题，适用于连续和离散动作空间。
- **系统消融**：对数据量、混合网络层数、LLM 模型版本均做了对比，验证了设计选择的合理性。
- **LLM 应用创新**：将 LLM 作为偏好标注器引入多智能体学习，展示了成本效益和性能增益。

## 8. 不足与局限

- **实验覆盖限制**：
  - 仅针对**完全合作**的多智能体场景，未涉及混合合作-竞争或完全竞争场景。
  - 偏好数据全部为自动生成（规则或 LLM），缺乏**真实人类反馈**验证，可能低估实际应用中的噪声和标签偏差。
- **应用限制**：
  - LLM 标注方法依赖可解释的状态信息（如生命值），不适用于图像观测或长时域任务，通用性受限。
  - 方法仍然需要一定数量的偏好对（2000对），在数据获取成本高的场景下效率有待提升。
- **算力报告不完整**：未提供训练总时间、迭代次数等资源消耗细节，不利于复现与公平比较。
- **其他潜在风险**：线性混合网络虽然保证了凸性，但可能限制了表达能力；离线设置下仍可能受分布偏移影响（尽管通过 KL 正则化缓解）。

（完）
