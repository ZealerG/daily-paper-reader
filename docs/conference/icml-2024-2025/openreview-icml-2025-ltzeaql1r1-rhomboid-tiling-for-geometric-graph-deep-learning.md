---
title: Rhomboid Tiling for Geometric Graph Deep Learning
title_zh: 菱形平铺用于几何图深度学习
authors: "Yipeng Zhang, Longlong Li, Kelin Xia"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=lTZEAqL1R1"
tags: ["query:graph-part"]
score: 6.0
evidence: 基于菱形平铺的几何图深度学习聚类方法
tldr: 本文提出一种基于菱形平铺结构的几何图聚类方法，利用数据的复杂几何信息进行聚类并提取高阶结构，克服了传统图神经网络依赖连接结构的局限。在几何图数据集上的实验表明，该方法能捕获更丰富的几何特征，提升聚类质量和模型表达能力，为几何图深度学习提供了新工具。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ltzeaql1r1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1679, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ltzeaql1r1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1218, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ltzeaql1r1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1671, \"height\": 1137, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1781, \"height\": 1157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 703, \"height\": 528, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 663, \"height\": 527, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 748, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 508, \"height\": 525, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1717, \"height\": 111, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1292, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 565, \"height\": 481, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 518, \"height\": 693, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 543, \"height\": 609, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1064, \"height\": 552, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 856, \"height\": 1113, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1756, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ltzeaql1r1/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1641, \"height\": 510, \"label\": \"Table\"}]"
motivation: 传统图神经网络依赖图连接结构，难以捕捉几何图中的丰富几何特征。
method: 提出菱形平铺聚类，基于菱形平铺结构进行聚类，提取高阶几何信息。
result: 实验验证了所提方法在几何图上的聚类效果和表达能力提升。
conclusion: 该工作为几何图学习提供了新的聚类范式，增强了模型对几何特征的捕获能力。
---

## Abstract
Graph Neural Networks (GNNs) have proven effective for learning from graph-structured data through their neighborhood-based message passing framework. Many hierarchical graph clustering pooling methods modify this framework by introducing clustering-based strategies, enabling the construction of more expressive and powerful models. However, all of these message passing framework heavily rely on the connectivity structure of graphs, limiting their ability to capture the rich geometric features inherent in geometric graphs. To address this, we propose Rhomboid Tiling (RT) clustering, a novel clustering method based on the rhomboid tiling structure, which performs clustering by leveraging the complex geometric information of the data and effectively extracts its higher-order geometric structures. Moreover, we design RTPool, a hierarchical graph clustering pooling model based on RT clustering for graph classification tasks. The proposed model demonstrates superior performance, outperforming 21 state-of-the-art competitors on all the 7 benchmark datasets.

---

## 论文详细总结（自动生成）

# 中文总结：Rhomboid Tiling for Geometric Graph Deep Learning

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统图神经网络（GNN）及其层次化图聚类池化方法（如DiffPool、MinCutPool）严重依赖图的连接结构（邻接矩阵），无法有效捕捉几何图中蕴含的丰富几何特征（如分子构象、空间邻近关系）。几何图（如分子图）的节点具有空间坐标，但现有方法仅利用拓扑连接，忽略了高阶几何信息。
- **研究意义**：提出一种全新的、基于几何驱动的聚类方法——菱形平铺（Rhomboid Tiling, RT）聚类，将计算几何中的Alpha Shape概念推广到高阶，构建一种能够自动捕捉点云高阶几何结构的层次聚类框架，并据此设计池化模型RTPool，显著提升几何图上的图分类性能。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：
  - 利用高阶Voronoi图、高阶Delaunay复形及菱形平铺结构，将点云按球面划分成子集，每个子集代表一个几何簇。
  - 不同阶数Delaunay复形之间的菱形平铺对应关系提供了一种自然的层次聚类机制：高阶复形的每个顶点对应低阶复形的一个簇，且这种聚类完全由几何结构驱动，无需学习。
- **关键技术细节**：
  - **高阶Voronoi划分**：对点集X，定义阶‑k Voronoi图，其每个单元对应一个大小为k的子集Q，Q中的点能被一个球面与其他点分离。
  - **高阶Delaunay复形**：作为阶‑k Voronoi图的神经（nerve），每个顶点对应一个簇，簇之间的连接表示几何邻近。
  - **菱形平铺**：将不同阶Delaunay复形的顶点提升到Rd+1空间，定义由球面S诱导的菱形（rhomboid）集合，形成复形Rhomb(X)。Rhomb(X)与超平面x_{d+1}=-k的交集恰为Del^k(X)。
  - **RT聚类**：利用菱形平铺，将阶‑k1的顶点聚类到阶‑k2的顶点（k2>k1），聚类条件由定理3.1给出。定理3.2指出在R3中，阶差Δk=k2−k1最佳取1或2，此时所有点均能归入至少一个簇，且Δk=1时簇关系由子集包含直接保证。
  - **权重机制**：使用同时包含两个顶点的最大菱形（深度‑(d+1)）的数量N(Q, Q′)作为权重，衡量几何亲密度。定理3.3表明该权重能有效反映子集间的几何关系。
  - **池化模型RTPool**：
    - 构建关联矩阵I_k（顶点‑菱形隶属关系）。
    - 聚类矩阵 C_{k2>k1} = (I_{k2})^T · I_{k1}，其元素即为N(Q_i, Q′_j)，同时包含归属信息与权重。
    - 行归一化后得到\hat{C}_l，用于从第l层到第l+1层的池化：Z^{(l+1)} = \hat{C}_l · H^{(l)}。
    - 使用GNN更新特征：H^{(l+1)} = GNN(Z^{(l+1)}, A_{l+1})，其中底层图A_{l+1}可选用Delaunay图或由原始分子图生成的图（实验表明生成图更好）。
    - 最终图级表示：H_final = (H^{(L)})^T · (H^{(L)}W)，再经MLP分类。
  - **时间复杂度**（定理3.4）：在d=3, Δk和层数L很小（K为常数）时，复杂度可降为O(n²)，实际可行。

## 3. 实验设计

- **数据集**：7个真实世界图分类基准（来自TUDataset）：
  - 化学化合物集：COX2、BZR、MUTAG。
  - 分子化合物集：PTC MM、PTC MR、PTC FM、PTC FR。
- **基准方法**：21个先进方法，分为4类：
  - (I) 图核：WL, WL-OA, HGK-WL, HGK-SP, CSM.
  - (II) GNN：GCN, DGCNN, GIN.
  - (III) 图池化：SAGPool, EigenGCN, MinCutPool, Top‑K, DiffPool, HaarPool, HopPool, MvPool.
  - (IV) 拓扑方法：PersLay, MPR, FC‑V, SIN, Wit‑TopoPool.
- **主要对比**：所有基线结果直接引用自Wit‑TopoPool论文（Chen & Gel, 2023），采用相同随机种子90/10训练/测试划分，保证公平。HopPool和MvPool结果由本文复现（网格搜索最优超参）。
- **实验设置**：500 epochs，每个数据集运行5次取均值标准差；超参数（学习率、dropout、池化层数等）在验证集上调优；节点特征为1‑hot原子类型。

## 4. 资源与算力

- **硬件**：单台机器配备NVIDIA RTX A5000 GPU（32GB显存）。
- **训练时长**：论文未给出每次实验的确切总时长，但在附录F提供了100 epoch下的运行时间（包含菱形平铺构建和时间训练），例如MUTAG上构造约190秒、训练约1042秒；COX2上构造约2356秒、训练约1053秒。完整500 epoch的耗时可按比例推算。
- **软件框架**：未明确说明，但代码已在GitHub公开（https://github.com/ZhangYipeng01/RT_pooling）。

## 5. 实验数量与充分性

- **主要实验**：在7个数据集上与21个基线对比，RTPool在所有数据集上均排名第一，平均相对改进5.94%。
- **消融实验**：
  - 替换RTPool为均值/最大池化（3个数据集）。
  - 不同GNN（GCN, GAT, GIN）更新特征（3个数据集）。
  - 不同底层图（Delaunay图 vs. 生成图）（3个数据集）。
- **超参数敏感性**：对Δk（1,2,3）、池化层数、学习率、dropout进行了网格搜索分析（3个数据集）。
- **扩展实验**：
  - 图回归任务（Esol、FreeSolv、Lipo）与7种池化方法对比。
  - 社会网络（IMDB‑BINARY/MULTI）与20种基线对比（使用拉普拉斯谱嵌入）。
  - 效率分析（100 epoch下的精度与运行时间，与7种池化方法对比）。
- **充分性**：实验覆盖分类、回归、非几何图场景，包含充分的消融和敏感性分析，对比方法充足且采用公平训练/测试划分，实验设计客观。但未在更大规模数据集（如OGG‑Molhiv）上验证，且社会网络性能并非最优（IMDB‑BINARY上低于Wit‑TopoPool）。

## 6. 论文的主要结论与发现

- **主要结论**：
  - 基于菱形平铺的RT聚类能有效提取几何图的**高阶几何结构**，且具有严格的几何保证（定理3.1‑3.3）。
  - RTPool在7个化学/分子图分类基准上**显著优于21个基线**，平均相对提升5.94%。
  - 消融实验表明：RTPool远超均值/最大池化；GIN是最佳特征更新器；生成图（保留原始连接）优于Delaunay图。
  - Δk=1或2为最优步长，理论分析与实验一致。
  - 模型在回归和社会网络任务上也取得有竞争力的结果，具有泛化能力。
- **理论贡献**：提供了RT聚类存在性、阶差范围、权重合理性定理以及时间复杂度界。

## 7. 优点

- **方法新颖性**：首次将菱形平铺结构引入GNN，完全基于几何驱动实现层次聚类，摆脱了传统对连接矩阵的依赖。
- **理论严谨**：提供多个定理支撑聚类条件、最优步长、权重意义及复杂度，设计有据可依。
- **性能突出**：7个数据集上全部超越21个SOTA，平均提升近6%，且部分数据集提升巨大（如PTC MR上78.86% vs. Wit‑TopoPool 70.57%）。
- **消融完整**：从池化方法、GNN类型、底层图结构三个维度深入分析，验证各组件贡献。
- **扩展性**：通过谱嵌入可应用于非几何图（社会网络），并展示了图回归能力。
- **效率合理**：复杂度在常用设置下为O(n²)，实证运行时间与多数池化方法相当或更快。

## 8. 不足与局限

- **实验覆盖有限**：仅测试了7个小规模化学/分子数据集，未在更大规模分子数据集（如ESOL、FreeSolv等回归任务虽测试但仅3个）或更复杂的几何图（如蛋白质、点云）上验证。
- **非几何图性能较弱**：在社会网络IMDB‑BINARY上RTPool（73.06%）低于Wit‑TopoPool（78.40%），表明通过谱嵌入投射的几何信息可能不足以超越为图拓扑特化的方法。
- **依赖点云坐标**：方法本质要求节点具有欧几里得坐标，对于无坐标的抽象图需要额外嵌入步骤，可能引入信息损失。
- **超参数敏感**：学习率、dropout、池化层数需要网格搜索调优，且Δk=1或2虽优但不同数据集表现不同（COX2上Δk=2优于1，MUTAG相反），实际部署需试错。
- **可解释性**：菱形平排本身是复杂计算几何结构，其聚类结果对非领域用户较难直观理解。
- **资源消耗**：菱形平铺构建在点云较大时（如n≈50）尚可，但理论复杂度含n^{floor((d+1)/2)}项，在更高维或大规模点时可能成为瓶颈。
- **未开源完整代码**：虽提供GitHub链接，但论文审阅期间无法验证代码完整性与再现性。

（完）
