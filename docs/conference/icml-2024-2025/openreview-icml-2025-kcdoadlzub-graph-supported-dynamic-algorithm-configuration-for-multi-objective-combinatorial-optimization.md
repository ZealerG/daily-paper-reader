---
title: Graph-Supported Dynamic Algorithm Configuration for Multi-Objective Combinatorial Optimization
title_zh: 面向多目标组合优化的图支持动态算法配置
authors: "Robbert Reijnen, Yaoxin Wu, Zaharah Bukhsh, Yingqian Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=KCDoaDlzUB"
tags: ["query:graph-part"]
score: 4.0
evidence: 图上的深度强化学习算法配置
tldr: 针对多目标组合优化算法配置问题，提出基于图神经网络的深度强化学习方法。将解空间收敛建模为图，用GNN学习状态表示，动态调整演化算法参数。实验表明该方法显著优于固定配置和传统方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-kcdoadlzub/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1668, \"height\": 623, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kcdoadlzub/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1757, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kcdoadlzub/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 693, \"height\": 225, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1703, \"height\": 1325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1563, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1753, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1663, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1187, \"height\": 798, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1441, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1662, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 821, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1455, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 938, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kcdoadlzub/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 937, \"height\": 175, \"label\": \"Table\"}]"
motivation: 多目标组合优化中算法参数需动态调整，现有方法缺乏有效的状态表示。
method: 将配置过程建模为MDP，用GNN从目标空间图中学习状态嵌入。
result: 在多个基准问题上超过当前最优配置方法。
conclusion: 图神经网络能有效增强深度强化学习在算法配置中的表现。
---

## Abstract
Deep reinforcement learning (DRL) has been widely used for dynamic algorithm configuration, particularly in evolutionary computation, which benefits from the adaptive update of parameters during the algorithmic execution. However, applying DRL to algorithm configuration for multi-objective combinatorial optimization (MOCO) problems remains relatively unexplored. This paper presents a novel graph neural network (GNN) based DRL to configure multi-objective evolutionary algorithms. We model the dynamic algorithm configuration as a Markov decision process, representing the convergence of solutions in the objective space by a graph, with their embeddings learned by a GNN to enhance the state representation. Experiments on diverse MOCO challenges indicate that our method outperforms traditional and DRL-based algorithm configuration methods in terms of efficacy and adaptability. It also exhibits advantageous generalizability across objective types and problem sizes, and applicability to different evolutionary computation methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：多目标组合优化（MOCO）问题（如柔性作业车间调度、带容量约束的车辆路径问题）中，演化算法（EA）的参数对性能至关重要，而最优参数往往随搜索进程动态变化。现有静态算法配置方法（如SMAC3、irace）无法适应这种动态性，而已有的基于深度强化学习（DRL）的动态配置方法（如MADAC）主要面向连续优化，且依赖人工设计的状态特征，难以有效处理MOCO中离散、大规模、多目标的不平滑解空间。
- **研究动机**：针对上述挑战，作者提出一种基于图神经网络（GNN）和深度强化学习的动态算法配置框架（GS-MODAC），以端到端方式自动学习表示搜索状态，提升MOCO算法的收敛性和多样性，并具备良好的泛化能力。
- **整体含义**：将动态算法配置问题建模为马尔可夫决策过程（MDP），使用图结构表示当前种群在目标空间中的分布，通过GNN提取状态嵌入，并由DRL策略实时调节演化算法的关键参数（如交叉率和变异率），从而实现更优的帕累托前沿逼近。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 将动态算法配置建模为MDP，状态用图表示，节点为解（归一化目标值），边连接同一非支配前沿的解；使用图卷积网络（GCN）学习图级别嵌入，结合剩余预算特征，输入PPO策略网络输出连续动作（参数配置）。
- 设计问题无关的奖励函数，基于超体积改进的平方差，鼓励后期大幅提升，保证泛化性。

### 关键技术细节
- **状态构建**：对当前种群所有解进行非支配排序，同一前沿内节点互相连接；节点特征仅含归一化目标值（归一化使用首次种群中的最差值和当前最优值）；附加特征向量包含归一化已用代数。
- **动作空间**：连续动作，每个动作对应一个参数（如NSGA-II的交叉率[0.6,1.0]、变异率[0.0,0.1]），映射到标准化范围内。
- **奖励函数**：  
  若当前超体积 \(HV_{current}\) 超过历史最佳 \(HV_{best}\)，则计算  
  \[
  r_t = \Delta_{current}^2 - \Delta_{best}^2
  \]  
  其中  
  \[
  \Delta = \frac{HV - HV_{initial}}{HV_{ideal} - HV_{initial}} \times 100
  \]  
  否则奖励为0。\(HV_{ideal}\) 由加倍预算运行一次得到。该奖励在搜索后期放大改进幅度，推动精细优化。
- **训练算法**：使用PPO（Proximal Policy Optimization），策略网络先经过两层GCN提取节点嵌入，再经全局平均池化得到图嵌入，与额外特征（剩余预算）拼接，最后通过线性层输出动作分布均值。
- **目标算法**：GS-MODAC可应用于不同的MOEA，文中展示了NSGA-II和MOPSO。

## 3. 实验设计：数据集/场景、benchmark、对比方法

### 数据集/场景
- **FJSP（柔性作业车间调度）**：尺寸 5j5m, 10j5m, 25j5m；每尺寸200实例（100训练+100测试）；目标数分别为2、3、5（Bi-, Tri-, Penta-）。
- **CVRP（容量约束车辆路径问题）**：顾客数 100、200、500；200实例/尺寸；目标：最小化总距离和最远路径。
- **扩展泛化测试**：DAFJS-SDST（含装配约束和序列依赖设置时间的变体）；目标迁移（Bi-FJSP*，不同目标组合）；不同分布和异常值的CVRP实例。

### Benchmark与对比方法
- 基础算法：NSGA-II（默认参数0.7交叉/0.02变异），MOPSO（仅在附录展示）。
- 静态配置方法：SMAC3（贝叶斯优化+随机森林）、irace（迭代竞赛）。
- 动态配置基线：MADAC（多智能体DRL，离散动作空间）。
- 端到端方法：P-MOCO（仅在附录G比较，仅能处理CVRP）。
- 消融研究：移除特征向量、单层GCN、替换为Transformer/GAT。

## 4. 资源与算力

- **硬件**：Intel(R) Core(TM) i7-6920HQ CPU @ 2.90GHz，8GB RAM，5个并行环境。**未使用GPU**。
- **训练时长**：  
  - Bi-CVRP: ~11/15/26小时（按尺寸递增）  
  - FJSP变体：5小时至3天不等  
  - MADAC基线：2-8小时（CVRP），12-60小时（FJSP）  
  - SMAC3调参：5-40小时；irace：3-20小时  
- **训练步数**：调度问题1,000,000步；路径问题2,500,000步；2000轮，每轮500步。
- **模型参数**：网络层64节点，其余沿用PPO默认设置。

## 5. 实验数量与充分性

- **主实验**：每种问题/尺寸组合含100个测试实例，每个算法运行10次取均值。覆盖2种问题（FJSP的3种尺寸×3种目标数；CVRP的3种尺寸），共约9×3×2=54组实验（含统计显著性测试Wilcoxon rank-sum, p<0.05）。
- **泛化实验**：
  - 尺寸迁移：训练于小尺寸，测试于大尺寸（如100→200→500）。
  - 问题变体迁移：FJSP模型直接用于DAFJS-SDST。
  - 目标迁移：优化过A、B目标的模型用于不同目标组合（C、D）。
  - 分布外迁移：训练于均匀分布CVRP，测试于不同分布+5%异常值。
- **消融实验**：移除附加特征、单层GCN、GCN替换为Transformer/GAT。
- **替代性能指标**：IGD、IGD+、非支配解数量。
- **替代MOEA**：MOPSO（附录D）。
- **与端到端方法比较**：P-MOCO（附录G）。
- **充分性评价**：实验覆盖多种问题、多种尺寸、多种目标数、多种泛化场景，且统计检验显著，对比方法全面，消融验证组件必要性。但所有实验基于同一硬件（无GPU），且未讨论超参数敏感性，整体充分且公平。

## 6. 论文的主要结论与发现

1. **性能优势**：GS-MODAC在所有问题配置中取得最佳平均/最大超体积，尤其在多目标（5目标）和大尺寸问题上提升显著（如Penta-FJSP-25j5m均值提升8.2%，最大提升5.7% vs 最佳基线）。
2. **收敛更快**：以Tri-FJSP-10j5m为例，GS-MODAC收敛到更高超体积，解分布更宽更均匀。
3. **泛化能力强**：训练于小尺寸可迁移至大尺寸；训练于FJSP可迁移至更复杂的DAFJS-SDST变体；训练于一组目标可迁移至另一组目标；对分布外实例鲁棒。
4. **适用不同MOEA**：在NSGA-II和MOPSO上均有效。
5. **消融验证**：附加特征向量和GCN层数对性能有贡献；GCN略优于Transformer（0.3%），明显优于GAT（1.4%差异）。
6. **计算开销**：状态提取和策略推理仅占求解总时间的2%（小问题）且随问题规模增大占比下降。

## 7. 优点

- **状态表示创新**：首次将目标空间中的解集建模为图，利用GNN自动学习状态嵌入，避免了人工设计特征，且与目标数量无关，易于扩展。
- **奖励函数设计**：基于平方差放后阶段改进，问题无关，促进泛化。
- **连续动作空间**：相比MADAC的离散动作更精细，适合连续参数调控。
- **全面泛化验证**：涵盖尺寸、问题变体、目标组合、分布外迁移，结果鲁棒。
- **与端到端方法对比**：表明GS-MODAC在泛化性上显著优于P-MOCO（P-MOCO过拟合尺寸和分布）。

## 8. 不足与局限

- **计算资源**：仅使用CPU训练，未利用GPU加速（与P-MOCO对比中，P-MOCO可能受益于GPU）；训练时长可达数天，尤其在多目标调度问题。
- **状态图的规模**：当种群大小固定时，图节点数固定，但大规模问题中超体积计算代价可能增长（文中未讨论）。
- **基线缺失**：缺少与最近基于Transformer或神经组合优化的端到端方法（如DRL求解MOCO）的对比（只在附录G部分对比P-MOCO且仅限CVRP）。
- **超参数敏感性**：未对DRL自身超参数（如学习率、批大小、GCN层数等）进行系统搜索。
- **问题领域有限**：仅验证了FJSP和CVRP两类经典MOCO，未涉及更多领域（如投资组合、设施选址）。
- **奖励计算依赖近似理想点**：需要额外预算运行一次理想值搜索，可能在实际部署中不现实。
- **未讨论单目标或多目标交互**：未深入分析参数动态变化的规律或与问题特征的因果关系。

（完）
