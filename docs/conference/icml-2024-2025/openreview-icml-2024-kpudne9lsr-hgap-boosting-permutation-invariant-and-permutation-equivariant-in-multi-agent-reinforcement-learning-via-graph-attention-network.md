---
title: "HGAP: Boosting Permutation Invariant and Permutation Equivariant in Multi-Agent Reinforcement Learning via Graph Attention Network"
title_zh: HGAP：通过图注意力网络提升多智能体强化学习中的排列不变性和排列等变性
authors: "Bor-Jiun Lin, Chun-Yi Lee"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=KpUdNe9lsr"
tags: ["query:graph-part"]
score: 9.0
evidence: 基于图注意力的多智能体强化学习，处理排列不变性
tldr: 针对多智能体强化学习中排列不变性和等变性问题，本文提出HGAP框架，利用图注意力网络对观测实体进行建模，从而自然地实现智能体间的排列不变性。在多种MARL任务中，HGAP显著提升了训练效率和协同性能，为图表示在MARL中的应用提供了有效方案。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1756, \"height\": 847, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1684, \"height\": 736, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1643, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1779, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 871, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 842, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1770, \"height\": 765, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1747, \"height\": 1539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1136, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1746, \"height\": 799, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1749, \"height\": 799, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1745, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1771, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1770, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1769, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1766, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kpudne9lsr/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1770, \"height\": 512, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-kpudne9lsr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kpudne9lsr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1558, \"height\": 585, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kpudne9lsr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 791, \"height\": 1148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kpudne9lsr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1752, \"height\": 1486, \"label\": \"Table\"}]"
motivation: 传统MARL方法忽略排列不变性导致训练困难。
method: 采用图注意力网络将观测实体建模为图，实现排列不变性。
result: 在多个MARL环境中展现更好的性能和训练稳定性。
conclusion: 图表示有效解决了MARL中的排列问题，提升了泛化能力。
---

## Abstract
Graph representation has gained widespread application across various machine learning domains, attributed to its ability to discern correlations among input nodes. In the realm of Multi- agent Reinforcement Learning (MARL), agents are tasked with observing other entities within their environment to determine their behavior. Conventional MARL methodologies often suffer from training difficulties if Permutation Invariant (PI) and Permutation Equivariant (PE) properties are not considered during training. The adoption of graph representation offers a solution to these challenges by conceptualizing observed entities as a graph. In this context, we introduce the Hyper Graphical Attention Policy (HGAP) Network, which employs a graph attention mechanism to fulfill the PI and PE properties, while also understanding inter-entity interactions for decision-making. HGAP is assessed across various MARL benchmarks to confirm its effectiveness and efficiency. In addition, a series of ablation studies are provided to demonstrate its adaptability, transferability, and the capability to alleviate the complexities introduced by the POMDP constraint.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：多智能体强化学习（MARL）中，传统方法在训练时往往忽略排列不变性（Permutation Invariant, PI）和排列等变性（Permutation Equivariant, PE）这两个关键性质。PI要求智能体对同一类型实体的不同排列顺序做出相同的行为决策；PE要求智能体理解实体与自身之间的映射关系，而非依赖实体的观测位置。忽视这些性质会导致训练效率低下，尤其在部分可观测的马尔可夫决策过程（POMDP）场景下问题更为突出。
- **整体含义**：为了同时保证PI和PE，并应对POMDP的挑战，本文提出基于图注意力网络（Graph Attention Network, GAT）的智能体网络框架HGAP，将观测实体建模为图结构，利用注意力机制捕捉实体间的相关性，从而自然地满足PI和PE，并提升决策质量与训练效率。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用图注意力网络（GATv2）对智能体观测的实体进行图表示，通过超网络生成动态注意力权重，实现排列不变性和等变性；同时利用图结构的传播能力推断未观测实体信息，缓解POMDP限制。
- **关键技术细节**：
  - 输入模块：使用超网络（Hypernetwork）生成独立权重矩阵，将原始观测映射为实体嵌入 \( \tau_i \)。
  - 图实体关系嵌入模块：构建 \( m \times m \) 的相关矩阵 \( C \)，通过超网络生成变换矩阵 \( \Gamma \) 得到注意力权重矩阵 \( \Omega \)，并执行图更新：
    \[
    \tau'_i[k] = \sum_{j=1}^{m} \Omega_{k,j} \cdot \tau_i[j]
    \]
    最终通过聚合函数得到潜在嵌入 \( z_i \)。
  - 动作生成模块：利用GRU处理 \( z_i \) 得到隐藏状态 \( h_i \)，用于生成自我动作（ego action）的Q值；对于指向动作（engagement action），采用配对函数 \( Q_i(a_{\text{eng}} \mid o_i)[j] = \tau'_i[j]^\top h_i \) 实现实体与动作的映射，满足PE。
  - 损失函数：采用与QMIX相同的TD误差：
    \[
    L(\theta) = \sum_{i=1}^{b} \left[ (y_{\text{tot}}^i - Q_{\text{tot}}(\tau; u, s; \theta))^2 \right]
    \]
    其中 \( y_{\text{tot}}^i = r + \max_{u'} Q(\tau; u', s'; \theta^-) \)。

## 3. 实验设计：数据集/场景、Benchmark、对比方法

- **数据集/场景**：
  - MPE（Multi-Particle Environments）：简单粒子物理模拟，用于验证actor-critic变体。
  - SMAC（StarCraft Multi-Agent Challenge）：包含Easy、Hard、Super-Hard三个难度等级（如3m, 2s3z, 3s5z, corridor等）。
  - SMACv2：对SMAC的改进，增加初始化随机性、实体类型随机化、调整视野和攻击范围，提供更多样化的挑战。
- **Benchmark**：统一使用QMIX作为值分解网络，对比各种智能体网络设计。
- **对比方法**：
  - 基本基线：RNN、UPDeT、DFAC、ResQ、RODE、ASN、HPN。
  - PI/PE相关方法：DA-MADDPG、Set、GNN、UPDeT、ASN、HPN。
  - 框架适应性实验：MADDPG、DA-MADDPG、PIC、QPLEX、MAPPO等。
  - 迁移学习：HPN作为对比。
  - 特殊设置：敌人拥有全信息而盟友受POMDP限制。

## 4. 资源与算力

- **文中未明确说明**：论文正文和附录中未给出具体的GPU型号、数量、训练时长等算力细节。仅在致谢部分提及NVIDIA捐赠GPU以及使用台湾国家高速网络与计算中心（NCHC）的计算资源。

## 5. 实验数量与充分性

- **实验数量**：相当充分，涵盖：
  - 主要对比实验：在SMAC的多个场景（约16个地图）和SMACv2的9个地图上进行测试，每个设置使用5个随机种子。
  - 消融实验：HGAP整合到MADDPG、QPLEX、MAPPO三个不同框架中；与PI/PE基线（DA、Set、GNN、UPDeT、ASN、HPN）对比；迁移学习（4组任务）；对抗全信息敌人实验。
  - 额外实验（附录）：大型群体环境、更多SMAC场景对比、注意力热图分析等。
- **充分性与客观性**：实验设计较为全面，覆盖多种MARL范式（actor-critic、值分解、策略梯度），对比方法代表性好，采用固定随机种子和多次重复，结果曲线平滑稳定。结论可信度高。

## 6. 论文的主要结论与发现

- HGAP通过图注意力机制同时满足PI和PE，显著优于不考虑或仅部分考虑这些性质的方法。
- HGAP具备良好的适应性，可无缝集入MADDPG、QPLEX、MAPPO等不同MARL框架，并提升性能。
- HGAP的图表示能力使其在POMDP场景下能够隐式推断未观测实体信息，即使敌人拥有全信息，HGAP仍优于基线。
- HGAP具有可迁移性，预训练策略可加速新场景的学习，训练时间减少约60%以上。
- 注意力图分析表明，HGAP能快速聚焦关键实体（如敌人）并基于距离分配注意力，训练效率高。

## 7. 优点

- **方法创新**：首次将GATv2系统性地应用于MARL智能体网络设计，同时解决PI、PE和POMDP挑战；超网络生成的动态注意力权重适应可变实体数量。
- **设计合理**：通过图结构自然实现PI/PE，无需数据增强或固定顺序输入；动作生成模块中配对函数直接体现PE。
- **实验全面**：在多个标准基准上验证，包含大量消融实验和迁移学习，对比方法丰富，结果稳健。
- **性能优异**：在大多数SMAC和SMACv2场景中达到100%胜率或显著高于现有方法，且收敛更快。
- **可拓展性**：框架不依赖特定值分解网络，易于推广到其他MARL算法。

## 8. 不足与局限

- **缺乏教练式方法**：论文在Limitation部分指出，HGAP目前未集成教练（coach）机制，如专家反馈、课程学习等，限制了进一步性能提升。
- **算力细节缺失**：未提供GPU型号、数量、训练时长等硬件信息，不利于复现和效率评估。
- **实验覆盖有限**：虽然场景多样，但主要基于StarCraft II和简易物理环境，未在更复杂的真实世界任务（如机器人协作、自动驾驶）上验证。
- **潜在偏差**：所有实验使用固定超参数（如学习率、网络尺寸），未进行广泛的超参数搜索，可能影响对比公平性；另外，对比方法均为论文发表时的最优配置，但可能存在过时版本。
- **理论分析不足**：缺少对PI/PE严格的理论证明或收敛性分析，主要依赖实验验证。

（完）
