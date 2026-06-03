---
title: Graph-Assisted Stitching for Offline Hierarchical Reinforcement Learning
title_zh: 基于图辅助拼接的离线分层强化学习
authors: "Seungho Baek, taegeon park, Jongchan Park, Seungjun Oh, Yusung Kim"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=73EwiOrN8W"
tags: ["query:graph-rl"]
score: 8.0
evidence: 在离线分层强化学习中使用图搜索选择子目标
tldr: 离线分层强化学习在长任务中效率低下，且难以跨轨迹拼接有效状态转换。本文提出图辅助拼接GAS，将子目标选择转化为图搜索问题：通过时间距离表示嵌入状态并聚类为图节点，利用最短路径算法选择子目标序列。实验证明该方法显著提升了长任务下的性能，为RL中图结构的 활용提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1702, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 820, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 816, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1601, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 805, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1738, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1743, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1741, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1729, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-73ewiorn8w/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1760, \"height\": 910, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-73ewiorn8w/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1754, \"height\": 481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73ewiorn8w/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1521, \"height\": 443, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73ewiorn8w/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1754, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73ewiorn8w/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73ewiorn8w/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 868, \"height\": 623, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73ewiorn8w/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1679, \"height\": 844, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73ewiorn8w/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1357, \"height\": 689, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-73ewiorn8w/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1746, \"height\": 847, \"label\": \"Table\"}]"
motivation: 现有离线分层RL在长任务中效率低，缺乏状态转换拼接策略。
method: 将子目标选择建模为图搜索，使用时间距离表示构建状态图。
result: 在长任务中显著提升性能，有效拼接跨轨迹转换。
conclusion: GAS将图搜索引入层次RL，提升了长时域任务表现。
---

## Abstract
Existing offline hierarchical reinforcement learning methods rely on high-level policy learning to generate subgoal sequences. However, their efficiency degrades as task horizons increase, and they lack effective strategies for stitching useful state transitions across different trajectories. We propose Graph-Assisted Stitching (GAS), a novel framework that formulates subgoal selection as a graph search problem rather than learning an explicit high-level policy. By embedding states into a Temporal Distance Representation (TDR) space, GAS clusters semantically similar states from different trajectories into unified graph nodes, enabling efficient transition stitching. A shortest-path algorithm is then applied to select subgoal sequences within the graph, while a low-level policy learns to reach the subgoals. To improve graph quality, we introduce the Temporal Efficiency (TE) metric, which filters out noisy or inefficient transition states, significantly enhancing task performance. GAS outperforms prior offline HRL methods across locomotion, navigation, and manipulation tasks. Notably, in the most stitching-critical task, it achieves a score of 88.3, dramatically surpassing the previous state-of-the-art score of 1.0. Our source code is available at: https://github.com/qortmdgh4141/GAS.

---

## 论文详细总结（自动生成）

# 详细中文总结：Graph-Assisted Stitching for Offline Hierarchical Reinforcement Learning

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：离线强化学习（offline RL）利用预先收集的数据集学习策略，无需与环境交互，在机器人、医疗等高风险场景中极具价值。其中，离线目标条件强化学习（GCRL）可学习多任务策略，但在长时域、稀疏奖励任务中面临挑战，因为奖励仅在最终状态给出，中间决策缺乏明确信号。
- **核心问题**：现有的离线分层强化学习（HRL）方法依赖高层策略学习生成子目标序列，存在三大局限：
  1. **缺乏时间感知的子目标采样**：多数方法按固定时间间隔采样子目标，无法捕捉状态间的时序依赖，导致冗余或低效的子目标。
  2. **长时域推理能力弱**：随任务步数增加，学习信号稀疏，高层策略生成子目标的效果显著下降。
  3. **无效的轨迹拼接**：离线数据通常由多条不同目标轨迹组成，但现有方法缺乏跨轨迹的有效状态拼接能力，无法组合有意义的片段形成新轨迹。
- **论文目标**：提出一种无需显式高层策略学习、通过图搜索进行子目标选择的框架，提升长时域推理和轨迹拼接能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **将子目标选择建模为图搜索问题**：在时间距离表示（Temporal Distance Representation, TDR）空间中构建图，节点代表语义相似的状态，边表示可达关系。使用最短路径算法（Dijkstra）选择子目标序列，同时训练一个低层策略（low-level policy）来达到子目标。

### 关键技术细节
1. **时间距离表示（TDR）学习**：
   - 学习一个嵌入函数 ψ: S → H，使得欧氏距离 ∥ψ(s) − ψ(g)∥₂ 近似于从状态 s 到目标 g 的最优时间步数 d*(s,g)。
   - 通过将 -∥ψ(s)−ψ(g)∥₂ 视为目标条件价值函数，采用类似 IQL 的期望分位数回归（expectile regression）进行优化，损失函数见公式 (5)-(6)。

2. **TD感知的图构建（TD-aware Graph Construction）**：
   - 将所有状态在 TDR 空间中按目标时间距离 HTD 进行聚类：第一个状态作为第一个簇中心，后续状态若与最近簇中心距离 < HTD 则归入该簇，否则新建簇。
   - 簇中心更新为簇内均值，作为图节点。若两节点间距离 ≤ HTD 则添加边。
   - 这种聚类方式保证了节点间均匀的时序间隔，自然实现了不同轨迹间状态的拼接。

3. **时间效率度量（Temporal Efficiency, TE）**：
   - 定义：从当前状态 scur 出发，将 HTD 步后实际到达的状态 s_reached 与从 scur 开始达到最优距离 HTD 的状态 s_opt 进行比较，计算方向向量的余弦相似度 θ_TE = cos(ψ(s_opt)−ψ(scur), ψ(s_reached)−ψ(scur))。
   - 仅保留 θ_TE ≥ θ_thresh (如0.9) 的状态用于图构建，过滤掉低效（次优）的过渡状态，提高图质量并降低计算开销。

4. **低层策略训练**：
   - **价值函数学习**：使用方向奖励 r_dir(s, s', h_dir) = ⟨ψ(s')−ψ(s), h_dir⟩，其中 h_dir 是从单位球面上均匀采样的方向向量。利用 IQL 框架拟合 Q 函数和 V 函数。
   - **子目标条件策略学习**：采用 TD 感知的子目标采样，即从当前状态出发，在轨迹中选取距离为 HTD 的状态作为子目标，并表示为相对方向向量 h_dir = dir(ψ(s_t), ψ(s_sub))。使用 DDPG+BC 目标进行策略优化，平衡 Q 值最大化和行为克隆正则化。

5. **任务规划与执行**：
   - 在每轮执行开始时，使用 Dijkstra 算法预计算所有图节点到最终目标的最短距离。
   - 每个时间步，从当前状态在 TDR 空间中可达（距离 ≤ HTD）的节点中，选择到目标距离最短的节点作为子目标。
   - 低层策略根据当前状态和子目标方向向量执行动作，直到达到最终目标。

## 3. 实验设计

- **数据集与基准**：
  - 主要使用 **OGBench**（Offline Goal-Conditioned Benchmark）和 **D4RL** 中的环境，包括三类数据集：
    - **运动（Locomotion）**：antmaze 不同尺寸迷宫（medium、large、giant）的导航、拼接、探索任务。
    - **操作（Manipulation）**：scene-play（UR5e机械臂操作多种物体）、kitchen-partial（Franka机械臂完成四个子任务）。
    - **视觉（Pixel-based）**：上述环境的视觉化版本（64×64 RGB图像输入）。
  - 数据集类型包括：navigation（长时域推理）、stitching（拼接能力）、exploratory（低质量高覆盖数据）、play（探索式交互数据）等。

- **对比方法**：
  - **离线目标条件方法**：GCBC、GCIQL、QRL、CRL。
  - **离线分层方法**：HGCBC、HIQL、HHILP。
  - 所有方法均基于 JAX 实现，超参数尽量统一。

- **评价指标**：
  - 归一化回报（normalized return），每个任务在5个测试目标上取平均，每个目标50次 rollout，共4个随机种子。

## 4. 资源与算力

- **文中说明**：论文在 "Implementation" 部分提到实验运行于内部集群，配备 **RTX 3090 GPU**。但**未明确给出训练时长、GPU数量、总计算量等具体数字**，仅表明代码基于 JAX 实现。

## 5. 实验数量与充分性

- **实验数量**：
  - **主实验**：表1（状态空间9个任务）、表2（像素空间9个任务），共18个数据集任务。
  - **消融实验**：包括 TE 过滤效果（表3）、TE 阈值影响（图5）、图节点选择方法对比（图6，FPS vs K-Means++ vs 本文方法）、子目标采样策略（表4）、时间距离阈值 HTD 影响（表5）、TDR 期望分位数、TDR 维度、BC 系数等（图7-9）。
  - **额外可视化**：图11展示迷宫中的最短路径投影。

- **充分性与公平性**：
  - 覆盖了多种环境（导航、拼接、探索、操作）和数据类型（低质量、高质量、视觉），对比方法全面（7个基线）。
  - 消融实验针对关键设计分别验证，分析充分。
  - 采用统一框架、统一超参数尽可能保证公平，并使用多随机种子报告均值和标准差。
  - 但**缺乏在更大规模或真实机器人环境上的验证**，且像素环境下的性能普遍低于状态环境（作者也指出这一点）。

## 6. 论文的主要结论与发现

- GAS 在 **所有18个任务** 上均达到最佳或接近最佳的性能，显著超越现有离线 HRL 方法。
- **关键突破**：
  - 在最具拼接挑战的 antmaze-giant-stitch 任务中，GAS 达到 **88.3**，而此前最优 HIQL 仅 **1.0**。
  - 在低质量探索数据集 antmaze-large-explore 中，GAS 达 **94.2**，对比方法最高仅 2.9。
  - 在视觉环境下的类似任务同样大幅领先。
- **消融结论**：
  - TE 过滤可降低图构建计算开销（节点数 < 数据集的1%）并提升任务性能。
  - 本文的 TD 感知聚类优于 FPS 和 K-Means++。
  - 子目标采样与图节点时间间隔对齐（即使用 HTD）对训练与执行一致性至关重要。

## 7. 优点：方法或实验设计上的亮点

- **方法创新性**：
  - 首次将图搜索与时间距离表示结合，替代传统高层策略学习，解决了因稀疏奖励导致的高层学习困难。
  - TE 度量简单有效，自动过滤低效过渡，提高图质量。
  - TD 感知聚类自然实现均匀间隔节点，便于拼接和规划。
  - 支持高维状态和视觉输入（通过 TDR 空间和 CNN）。

- **实验设计**：
  - 在公认的离线目标条件基准（OGBench）上进行系统评估，涵盖多种难度和数据质量。
  - 消融实验全面，每个关键组件都被单独检验。
  - 结果以均值±标准差呈现，随机种子多样，可信度高。

## 8. 不足与局限

- **实验覆盖限制**：
  - 仅评估了模拟环境（MuJoCo），未在真实机器人或实际应用场景中验证。
  - 像素环境性能明显低于状态环境，表明对高维视觉输入的表示学习仍有改进空间。
  - 数据集规模有限（最大5M步），未测试超大规模离线数据。

- **偏差风险**：
  - TE 阈值需手动设置（文中默认为0.9/0.99），不同任务可能需调整，但未给出自动选择方法。
  - HTD 作为超参数在各任务上取值不同（如 AntMaze 常用8，scene-play 用48），其选择依赖先验知识。

- **应用限制**：
  - 图构建和最短路径计算为离线阶段，但执行时需实时查询，在大规模图中可能带来延迟。
  - 低层策略训练依赖 TDR 嵌入，而 TDR 本身需要通过IQL训练，若数据集分布偏移严重可能影响表示质量。
  - 缺乏与在线微调或分布外泛化的分析。

（完）
