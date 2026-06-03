---
title: Sample-Efficient Multiagent Reinforcement Learning with Reset Replay
title_zh: 带重置回放的高样本效率多智能体强化学习
authors: "Yaodong Yang, Guangyong Chen, Jianye HAO, Pheng-Ann Heng"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=w8ei1o9U5y"
tags: ["query:graph-part"]
score: 8.0
evidence: 多智能体并行决策强化学习
tldr: 针对多智能体强化学习在并行环境下样本效率低的问题，提出带重置回放的多智能体强化学习（MARR）方法。首次在并行环境设置中实现高回放率训练，通过重置策略显著提升样本效率，加速了多智能体在真实世界任务中的部署。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1768, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1761, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 729, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 734, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 808, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 846, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 760, \"height\": 805, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1763, \"height\": 1320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1759, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1498, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1503, \"height\": 939, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1774, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1081, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1773, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-w8ei1o9u5y/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1773, \"height\": 333, \"label\": \"Figure\"}]"
motivation: 多智能体强化学习样本效率低，尤其在并行环境下研究不足，限制了实际应用。
method: 提出MARR方法，通过重置回放机制在并行环境中实现高回放率训练。
result: 实验表明MARR大幅提升样本效率，优于现有方法。
conclusion: MARR有效解决了并行多智能体强化学习的样本效率瓶颈。
---

## Abstract
The popularity of multiagent reinforcement learning (MARL) is growing rapidly with the demand for real-world tasks that require swarm intelligence. However, a noticeable drawback of MARL is its low sample efficiency, which leads to a huge amount of interactions with the environment. Surprisingly, few MARL works focus on this practical problem especially in the parallel environment setting, which greatly hampers the application of MARL into the real world. In response to this gap, in this paper, we propose Multiagent Reinforcement Learning with Reset Replay (MARR) to greatly improve the sample efficiency of MARL by enabling MARL training at a high replay ratio in the parallel environment setting for the first time. To achieve this, first, a reset strategy is introduced for maintaining the network plasticity to ensure that MARL continually learns with a high replay ratio. Second, MARR incorporates a data augmentation technique to boost the sample efficiency further. Extensive experiments in SMAC and MPE show that MARR significantly improves the performance of various MARL approaches with much fewer environment interactions.

---

## 论文详细总结（自动生成）

以下是对论文《Sample-Efficient Multiagent Reinforcement Learning with Reset Replay》的详细中文总结。

---

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：多智能体强化学习（MARL）在现实世界任务中需求日益增长，但其最大的瓶颈之一是**样本效率低下**——需要与环境进行大量交互才能学到有效策略。尤其是在**并行环境设置**（同时运行多个环境实例以加速采样）中，环境交互昂贵，样本效率更加关键。
- **现有不足**：尽管单智能体领域已有通过提升回放率（replay ratio）来改进样本效率的工作，但在 MARL 中**几乎没有研究关注这一方向**，特别是在并行环境下。已有的少数样本效率工作多依赖置换先验等数据增强，而未涉及高回放率训练。
- **整体含义**：本文首次在并行环境中实现高回放率（high replay ratio）的 MARL 训练，提出的 MARR 方法显著降低了所需环境交互次数，加速了 MARL 在真实世界的部署。

---

## 2. 方法论：核心思想、关键技术细节与算法流程

### 核心思想
通过**大幅提高回放率**（即每与环境交互一次就进行多次网络更新）来提升样本利用率，同时引入**重置策略**和**数据增强**来克服高回放率下的过拟合和网络塑性损失问题。

### 关键技术细节
- **Shrink & Perturb 重置策略**：定期将每个智能体的网络参数向初始参数插值，以注入网络塑性。公式为：
  \[
  \theta_i^t \leftarrow \alpha \theta_i^t + (1-\alpha)\theta_i^0, \quad \phi^t \leftarrow \alpha \phi^t + (1-\alpha)\phi^0
  \]
  其中 \(\alpha\) 控制当前参数保留比例（实验中设为 0.8），重置间隔 \(T_R = 2000\) 步。
- **随机振幅尺度数据增强（Random Amplitude Scale）**：对采样的每条经验中的观测和状态乘以一个随机缩放因子 \(z \sim U(a,b)\)（实验中 \(a=0.8, b=1.2\)），且对当前和下一帧使用相同缩放，保持符号一致性。这在高回放率下增加了样本多样性，帮助网络学习输入表示的固有不变性。
- **高回放率训练**：设置回放率 \(N_{RR}\) 为 50（SMAC）或 25（MPE），而基线算法默认值为 1。

### 算法流程（文字说明）
1. 初始化各智能体网络参数、集中式评论家参数、空回放缓冲区。
2. 每时间步：在并行环境中各智能体采样动作并执行，收集转移数据存入回放缓冲区。
3. 每隔 \(T_U\) 步：从回放缓冲区采样一个 mini-batch，先应用随机振幅尺度增强，然后用增强后的数据更新评论家和各智能体网络，重复 \(N_{RR}\) 次。
4. 每隔 \(T_C\) 步：更新目标网络。
5. 每隔 \(T_R\) 步：对所有网络参数执行 Shrink & Perturb 重置。

---

## 3. 实验设计

### 数据集/场景与 Benchmark
- **SMAC（StarCraft Multi-Agent Challenge）**：离散动作空间，选用 7 个地图（2s_vs_1sc, 2s3z, 3s5z, 10m_vs_11m, 5m_vs_6m, 3s5z_vs_3s6z, corridor），涵盖同构/异构、对称/非对称场景。
- **MPE（Multiagent Particle Environment）**：连续动作空间，使用经典捕食者-猎物任务（3 agents vs 1 prey, 6 agents vs 2 preys, 9 agents vs 3 preys）。

### 对比方法
- SMAC：QMIX, QPLEX, ATM（及其 MARR 变体）
- MPE：MADDPG, FACMAC（及其 MARR 变体）
- 消融对比：去掉 Shrink & Perturb、去掉数据增强、不同回放率设置、其他塑性保持方法（Weight Decay, L2 Init, 多层感知机置换, Layer Norm）。

### 评价指标
- SMAC：测试胜率（Test Win Rate）
- MPE：回合回报（Episodic Return）

### 实验设置
- 并行环境数：SMAC 为 8，MPE 为 4。
- 环境交互步数：SMAC 为 1M（基线算法也运行 5M 步进行对照），MPE 为 2M（基线运行 5M 步）。
- 每个配置运行 6 个随机种子，报告中位数/均值及置信区间。

---

## 4. 资源与算力

论文中**未明确说明**使用的 GPU 型号、数量或具体训练时长。仅提到代码基于 pyMARL 框架，实验在 SMAC 和 MPE 上完成。从实验规模看，涉及的场景和种子数较多（每个方法6次运行），推测使用了多 GPU 或单 GPU 长时间运行，但原文未披露算力细节。

---

## 5. 实验数量与充分性

- **实验数量**：共进行了 **7 个 SMAC 场景** + **3 个 MPE 任务** 的主实验，此外还有：
  - 串行 vs 并行设置下的回放率对比
  - MARR 在不同回放率下的性能
  - 组件消融（Shrink & Perturb 和随机振幅尺度）
  - 网络塑性度量（L2 gap）
  - 与其它塑性保持技术的比较（Weight Decay, L2 Init, MAP, Layer Norm）
  - 插值因子 \(\alpha\) 的消融
  - 随机振幅尺度的内在一致性分析
  - MARR 在完全分散式算法 IQL 上的推广实验
- **充分性**：实验覆盖了主流 off-policy MARL 算法（QMIX, QPLEX, ATM, MADDPG, FACMAC, IQL），在离散和连续动作空间、同构/异构、对称/非对称等多种场景下验证，消融实验全面，且代码已开源。结论具有较高的可信度。
- **公平性**：所有基线算法均使用作者官方代码和配置，MARR 仅增加少量超参数（\(\alpha=0.8, T_R=2000, a=0.8, b=1.2\)）且未专门调优，对比方式客观。

---

## 6. 主要结论与发现

1. **MARR 显著提升样本效率**：在 SMAC 和 MPE 的几乎所有任务中，MARR 在**1/5 甚至更少**的环境交互步数下就达到或超过基线算法在 5M 步的性能。
2. **Shrink & Perturb 是关键**：消融实验显示去掉 Shrink & Perturb 后性能急剧下降；随机振幅尺度在 Shrink & Perturb 存在时能进一步提升，但单独作用有限。
3. **并行环境更适合高回放率**：串行环境下最高回放率只能到 10，而并行环境可达 50，MARR 进一步将此推进到 50（SMAC）和 25（MPE）。
4. **MARR 维持网络塑性**：通过 L2 gap 度量，MARR 的参数始终更靠近初始值，表明其有效保持了网络对新数据的适应能力。
5. **通用性**：MARR 能即插即用到多种 off-policy MARL 算法中，仅需少量改动。

---

## 7. 优点

- **创新性**：首次在 MARL 并行环境设置中实现高回放率训练，填补了该领域空白。
- **简洁高效**：仅引入两个额外操作（重置和增强），无需改变算法核心结构，易于集成。
- **实验充分**：多场景、多算法、多种子验证，消融实验和对比分析完整。
- **实用性**：显著降低环境交互次数，直接有利于真实世界部署（如机器人集群、交通控制等）。

---

## 8. 不足与局限

- **不适用于 on-policy 算法**：MARR 依赖回放缓冲区和高回放率，不适合 A2C、PPO 等 on-policy 方法。
- **数据质量敏感**：若环境中存在大量噪声，高回放率可能放大不良经验的影响。
- **随机振幅尺度限制**：对线性缩放的特征需谨慎使用，可能破坏原有语义。
- **算力消耗未报告**：虽然减少了环境交互，但高回放率增加了计算开销，论文未给出实际 wall-clock 时间对比，不利于评估总体效率。
- **超参数敏感性**：虽然采用推荐值，但插值因子 \(\alpha\) 和重置间隔 \(T_R\) 可能需针对不同任务调整，论文仅在两个场景上做了 \(\alpha\) 消融。
- **理论分析不足**：对塑性损失的量化主要依赖 L2 gap 的代理度量，缺乏更深入的理论解释。

---

（完）
