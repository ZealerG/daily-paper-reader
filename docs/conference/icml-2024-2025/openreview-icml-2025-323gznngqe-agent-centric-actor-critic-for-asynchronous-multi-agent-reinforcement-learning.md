---
title: Agent-Centric Actor-Critic for Asynchronous Multi-Agent Reinforcement Learning
title_zh: 面向异步多智能体强化学习的智能体中心Actor-Critic
authors: "Whiyoung Jung, Sunghoon Hong, Deunsol Yoon, Kanghoon Lee, Woohyung Lim"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=323GZNnGqe"
tags: ["query:graph-part"]
score: 9.0
evidence: 异步多智能体强化学习中的智能体中心Actor-Critic
tldr: 多智能体强化学习中宏动作引入异步性，现有填充方法导致伪相关。本文提出ACAC算法，采用智能体中心编码器和注意力聚合模块，无需填充即可处理异步轨迹，在稀疏奖励环境中显著提升了协调性能，为异步MARL提供了鲁棒解决方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 771, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 786, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 844, \"height\": 1198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 865, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 737, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 846, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1785, \"height\": 1161, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 863, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 861, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1482, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1751, \"height\": 1144, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1744, \"height\": 1735, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1783, \"height\": 1157, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1781, \"height\": 796, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-323gznngqe/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1784, \"height\": 797, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-323gznngqe/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1772, \"height\": 1290, \"label\": \"Table\"}]"
motivation: 异步MARL中现有填充方法容易导致伪相关。
method: 提出ACAC，用智能体中心编码器独立处理轨迹，注意力聚合集成。
result: 在稀疏奖励环境中表现优异，有效处理异步性。
conclusion: ACAC无需填充即可实现有效的异步MARL训练。
---

## Abstract
Multi-Agent Reinforcement Learning (MARL) struggles with coordination in sparse reward environments. Macro-actions —sequences of actions executed as single decisions— facilitate long-term planning but introduce asynchrony, complicating Centralized Training with Decentralized Execution (CTDE). Existing CTDE methods use padding to handle asynchrony, risking misaligned asynchronous experiences and spurious correlations. We propose the Agent-Centric Actor-Critic (ACAC) algorithm to manage asynchrony without padding. ACAC uses agent-centric encoders for independent trajectory processing, with an attention-based aggregation module integrating these histories into a centralized critic for improved temporal abstractions. The proposed structure is trained via a PPO-based algorithm with a modified Generalized Advantage Estimation for asynchronous environments. Experiments show ACAC accelerates convergence and enhances performance over baselines in complex MARL tasks.

---

## 论文详细总结（自动生成）

# 面向异步多智能体强化学习的智能体中心 Actor-Critic（ACAC）论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：在多智能体强化学习（MARL）中，稀疏奖励环境下的协调是一大挑战。采用宏动作（macro-action，即一个动作序列作为一个高层次决策）可以有效促进长期规划，但宏动作的执行时长因智能体而异，导致智能体间决策时间点不同步，即引入**异步性**。
- **现有方法局限**：主流框架集中训练分散执行（CTDE）在同步环境中效果良好，但直接应用于异步环境时会遇到困难——因为集中式评论家需要每个时刻所有智能体的观测，而异步环境下只有部分智能体有新观测。现有方法（如 Xiao et al. 2020）采用**填充（padding）**技术，用智能体最新的观测替代缺失数据。但 Liang et al. 2022 指出，填充会混淆“新信息”与“复用旧信息”，导致伪相关，降低学习效率和策略质量。
- **论文动机**：设计一种无需填充即可处理异步性的 CTDE 算法，使评论家能够准确获取每个智能体的真实历史抽象，从而加速学习并提升最终性能。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想
- 提出**智能体中心 Actor-Critic（ACAC）**算法，核心是**按智能体分别编码历史**，再通过注意力机制聚合各智能体的历史表示为集中式评论家使用，完全避免填充操作。

### 2.2 关键技术细节

#### 智能体中心编码器（Agent-Centric Encoder）
- 每个智能体 i 维护一个独立的历史编码器（GRU），输入为：
  - 宏观测 $z_i^t$
  - 对应时间戳 $p_i^t$（通过正弦位置编码嵌入）
- 时间信息编码使得编码器能感知两次宏观测之间的间隔长度（例如间隔 1 步还是 10 步），避免因缺乏跨度信息导致历史抽象不稳定。
- 更新规则：只有获得新观测的智能体才更新其隐藏状态 $h_i^t$；未获得新观测的智能体保持之前的隐藏状态。

#### 集中式评论家（Centralized Critic）
- 每个智能体的隐藏状态 $h_i^t$ 输入**注意力聚合模块（Self-Attention + Average Pooling + MLP）**，生成联合历史表示 $\tilde{h}^t$，进而输出价值 $V_\psi(\tilde{h}^t)$。
- 结构图见论文图 4：左侧为编码器，右侧为评论家整体。

#### 分散式演员（Decentralized Actor）
- 每个智能体 i 的演员 $\pi_{\theta_i}(m_i^t | h_i^t)$ 使用自己的隐藏状态（来自其编码器）选择宏动作。
- 训练采用 PPO 风格的裁剪损失，与 MAPPO 类似。

#### 改进的广义优势估计（GAE）用于异步环境
- 标准 GAE 在微观时间步上做 λ 折扣，但异步环境中宏动作持续步数不一，微观折扣会不当贬低长宏动作的价值。
- **宏级 λ 折扣**：将 λ 的指数改为宏决策步数 k（而非微观步数 $l(k)$），即 $A^{\lambda,\text{macro}}_{l(0)} = \sum_{k=0}^{\infty} \lambda^k \gamma^{l(k)-l(0)} \delta_{l(k)}$。
- 保持 GAE 性质：λ=0 为单步 TD，λ=1 为完整回报减基线。
- 推导过程见附录 D。

#### 训练流程
- 使用 PPO 算法，评论家损失为均方误差（目标回报与价值估计），演员损失为裁剪后的重要性采样优势损失。
- 价值归一化采用 PopArt（同 MAPPO）。

## 3. 实验设计

### 3.1 环境与场景
- **BoxPushing**：两智能体协作推箱子至目标区，地图尺寸 6×6、8×8、10×10。奖励稀疏（大型箱子需双人合作）。
- **Overcooked**：三智能体合作制作沙拉（番茄、洋葱等），地图 A、B、C（7×7 网格）。任务包括获取蔬菜、切菜、装盘、送达。
- **Overcooked-Rand**：在 Overcooked 基础上随机化物体和智能体初始位置，增加不确定性，评估泛化能力。
- **Overcooked-Large**：地图扩大至 11×11，智能体增至 6 个，工具数量增加，进一步加大难度。

### 3.2 Benchmark 与对比方法
| 方法 | 描述 |
|------|------|
| **ACAC（本文）** | 提出的智能体中心架构 + PPO + 宏级 GAE |
| **ACAC-Vanilla** | 同架构但使用与基线相同的损失（非 PPO） |
| **Mac-NIACC** | 单个集中式评论家 + 填充（Xiao et al. 2022） |
| **Mac-IAICC** | 每个智能体独立评论家 + 填充（Xiao et al. 2022） |
| **ACAC-Duplicate** | 消融变体：重复填充历史（与 ACAC 对比去填充效果） |
| **ACAC (micro-level GAE)** | 消融变体：使用微观级 λ 折扣 |
| **ACAC micro / MAPPO micro** | 微动作（原始动作）基线（无宏动作） |
| 所有方法均使用相同或兼容的超参数集（见附录表 1）。 |

### 3.3 评估指标
- 奖励曲线（训练过程中每 1M 环境步的平均回报及标准误差），每个实验 5 个随机种子。

## 4. 资源与算力

- 论文附录 G 中明确说明：
  - **CPU**：AMD EPYC 7453 28-Core Processor
  - **GPU**：NVIDIA A10
  - **训练时长**：
    - BoxPushing 环境：约 30 分钟至 2 小时
    - Overcooked 环境：约 24 至 150 小时
- 未说明 GPU 数量和具体种子数对应的耗时细节，但提供了估算范围。

## 5. 实验数量与充分性

- **主实验**：在 BoxPushing（3 个地图）、Overcooked（3 个地图）、Overcooked-Rand（3 个地图）、Overcooked-Large（6 个地图，含 -Rand）上各做 5 次重复。总计约 15+15+15+30 = 75 条训练曲线（原文图 7、图 8）。
- **消融实验**：
  - 去除填充（ACAC vs ACAC-Duplicate）——图 9
  - 宏级 vs 微级 GAE——图 9
  - 时间嵌入和自注意力的作用——附录图 15
  - 裁剪率 ϵ 的敏感性——附录图 14
- **公平性**：所有方法共享大部分超参数，基线方法直接使用原文推荐值；ACAC 与基线在相同环境、相同种子下运行。
- **客观性**：报告了平均和标准误，使用多次重复，避免单次结果偏差。
- **充分性评价**：覆盖了从简单（BoxPushing）到复杂（Overcooked-Large-Rand）的多种场景，包含确定性环境与随机化环境，进行了足够多的消融。实验设计较为充分，但未提供真实世界或多机器人平台验证。

## 6. 主要结论与发现

1. **ACAC 在所有测试环境中均优于填充基线**：收敛更快、最终回报更高，尤其在 Overcooked-Large 等复杂任务中优势显著。
2. **去填充至关重要**：ACAC-Duplicate（模拟填充）性能明显下降，证实填充引入伪相关损害学习。
3. **宏级 GAE 优于微级 GAE**：在异步环境下，对 λ 基于宏决策步折扣更适合，能更好地平衡偏差与方差。
4. **PPO 风格的损失提升效率**：ACAC-Vanilla（非 PPO）虽优于填充基线，但弱于 ACAC。
5. **微动作基线的局限性**：宏动作显著加速学习，微动作基线在稀疏奖励任务中难以达到最优。

## 7. 优点

- **方法创新**：提出无需填充的智能体中心结构，从根本上解决异步 CTDE 中信息冗余与伪相关的问题。
- **实用性强**：采用 PPO 和改进 GAE，易于集成到现有 MARL 框架。
- **实验全面**：多个环境、多种对比、多种消融，验证了各模块的有效性。
- **可扩展性**：通过自注意力聚合，可适应任意数量智能体（即使不同时刻有不同智能体新观测）。
- **透明性**：附录提供了详细的 GAE 推导、超参数、训练细节，可复现性高。

## 8. 不足与局限

- **动作空间限制**：当前方法仅针对离散宏动作，未扩展到连续动作空间。论文承认缺乏异步连续动作基准，未来需要开发相关测试环境。
- **宏动作预设**：实验使用的宏动作（如 GO TO TOMATO）是预定义的，未探讨学习宏动作本身（即层次化技能发现）的问题。
- **环境规模**：虽然 Overcooked-Large 增加了难度，但所有场景仍为网格世界，未在真实机器人或大规模随机环境中验证。
- **偏差风险**：填充基线（Mac-NIACC/IAICC）可能未经过充分调优（但论文声明使用了原文参数），且 ACAC 的复杂架构（注意力、PPO）可能引入额外计算负担，但论文未对比计算效率。
- **统计细节**：仅报告了 5 个种子的均值与标准误，未进行假设检验（如 t 检验）以严格证明显著性差异。
- **未分析失败情况**：未讨论在哪些情况下 ACAC 可能失败或与基线差距小。

（完）
