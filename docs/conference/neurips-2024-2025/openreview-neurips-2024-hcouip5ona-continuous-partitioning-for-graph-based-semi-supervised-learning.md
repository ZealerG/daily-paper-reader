---
title: Continuous Partitioning for Graph-Based Semi-Supervised Learning
title_zh: 基于图半监督学习的连续划分
authors: "Chester Holtz, Pengwen Chen, Zhengchao Wan, Chung-Kuan Cheng, Gal Mishne"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=hCOuip5Ona"
tags: ["query:graph-part"]
score: 7.0
evidence: 通过连续二次规划进行图划分用于半监督学习
tldr: 该论文提出CutSSL框架，将图半监督学习转化为一个基数约束最小割图划分问题的连续二次规划松弛，并能够获得整数解。该方法在低标签率和类别不平衡情况下相比拉普拉斯学习显著提升性能，为图划分在机器学习中的应用提供了新视角。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcouip5ona/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1378, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcouip5ona/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcouip5ona/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1170, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcouip5ona/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 698, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcouip5ona/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1387, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcouip5ona/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1379, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hcouip5ona/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1412, \"height\": 368, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1327, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1388, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 708, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 891, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 840, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1249, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1438, \"height\": 831, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1543, \"height\": 724, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1004, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hcouip5ona/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1377, \"height\": 212, \"label\": \"Table\"}]"
motivation: 拉普拉斯学习在图半监督学习中在低标签率和类别不平衡时产生退化预测，需要更鲁棒的划分方法。
method: 基于连续非凸二次规划对最小割图划分问题进行精确松弛，并开发CutSSL框架求解整数划分。
result: 实验表明CutSSL在多个基准数据集上优于拉普拉斯学习，尤其是在低标签率场景下。
conclusion: 该工作建立了图划分与半监督学习的显式联系，提供了一种新的理论分析和实用方法。
---

## Abstract
Laplace learning algorithms for graph-based semi-supervised learning have been shown to produce degenerate predictions at low label rates and in imbalanced class regimes, particularly near class boundaries. We propose CutSSL: a framework for graph-based semi-supervised learning based on continuous nonconvex quadratic programming, which provably obtains \emph{integer} solutions. Our framework is naturally motivated by an \emph{exact} quadratic relaxation of a cardinality-constrained minimum-cut graph partitioning problem. Furthermore, we show our formulation is related to an optimization problem whose approximate solution is the mean-shifted Laplace learning heuristic, thus providing new insight into the performance of this heuristic. We demonstrate that CutSSL significantly surpasses the current state-of-the-art on k-nearest neighbor graphs and large real-world graph benchmarks across a variety of label rates, class imbalance, and label imbalance regimes. Our implementation is available on Colab\footnote{\url{https://colab.research.google.com/drive/1tGU5rxE1N5d0KGcNzlvZ0BgRc7_vob7b?usp=sharing}}.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：图半监督学习中的拉普拉斯学习（Laplace learning）在标签率极低和类别不平衡时会产生退化预测——解趋向于常值，导致阈值化后分类集中于某一类，准确率低下。以往工作通过“均值平移（mean-shift）”启发式部分缓解该问题，但缺乏理论保证。
- **核心问题**：如何设计一种基于图划分的、能直接得到整数标签预测的半监督学习方法，克服低标签率下的退化，并自然处理类别不平衡。
- **整体含义**：作者将半监督学习重新表述为基数约束的最小割图划分问题的精确连续二次规划松弛，并开发了CutSSL框架，在理论上证明了可以恢复整数解，实验上大幅超越现有方法。

## 2. 论文提出的方法论

- **核心思想**：将图半监督学习转化为一个带基数约束的k-way最小割问题，通过添加对角扰动矩阵S（如S = sD）使得原凸的拉普拉斯二次型变为非凸，其局部极小值恰好对应整数（0-1）标签分配。通过同伦路径（homotopy path）逐步增大s，从拉普拉斯解出发最终得到整数解。
- **关键技术细节**：
  - **问题形式**：最小化 F_s(X) = 1/2 tr(X^T (L_u - sD) X) - tr(X^T B)，约束为 X^T 1_n = m, X 1_k = 1_n, X ≥ 0。其中L_u是未标记节点的图拉普拉斯子矩阵，B是标签传播项。
  - **定理保证**：当选取s使得 (L_{u,s})_{ii} + (L_{u,s})_{jj} < 2 (L_{u,s})_{ij} 对所有i,j成立时，每个局部极小值都是0-1解（Proposition 3.2）。
  - **算法流程**：采用ADMM（交替方向乘子法）求解序列二次规划。每次迭代分为三步：X更新（解一个线性系统）、T更新（投影到非负约束）、Λ更新（拉格朗日乘子）。
  - **与均值平移的关系**：论文证明，当s=0时，该问题等价于带基数约束的拉普拉斯学习，其精确解可通过投影共轭梯度（PCG）求得，而均值平移启发式只是该问题的近似投影。

## 3. 实验设计

- **使用数据集**：
  - 图像数据集：MNIST、Fashion-MNIST、CIFAR-10（使用预训练自编码器提取特征，构建k-NN图）。
  - 引文网络：Cora、Citeseer、Pubmed（Planetoid）。
  - 大型图：OGB Arxiv（约17万节点）、OGB Products（约250万节点）。
- **Benchmark场景**：
  - 不同标签率：每类1、3、5、10个标签，以及全标签训练。
  - 标签不平衡：奇偶类赋予不同标签数。
  - 类别不平衡：偶类样本数为奇类的10倍。
- **对比方法**：
  - 拉普拉斯学习（LP）、均值平移拉普拉斯、精确拉普拉斯（本文提出的投影CG）、LE-SSL、Sparse LP、Poisson Learning、Poisson-MBO、Volume-MBO、GraphHop、p-Laplace等。

## 4. 资源与算力

- **文中明确说明**：所有实验在Google Colab实例上运行，配备2核AMD EPYC 7B12 CPU和13 GB RAM，未使用GPU。训练时长在表格中有显示，例如OGB-Arxiv上CutSSL耗时122秒，Poisson-MBO耗时341秒。但未提供GPU型号或集群信息。

## 5. 实验数量与充分性

- **实验组数**：
  - 三个图像数据集上每种方法进行100次随机试验，报告均值和标准差。
  - 引文网络上同样进行100次试验。
  - OGB网络进行低标签率（每类1标签）和全标签训练两种场景。
  - 消融实验：不同k-NN图参数k（5,10,15,100）、不同边权重方式（高斯、奇异、均匀、NNK）、不同S选择（sI vs sD）、不同同伦路径序列。
  - 另外比较了在“小边界”样本上的准确率（Table 7）。
- **充分性评价**：实验覆盖了多种图类型（k-NN、真实网络）、多种标签率、不平衡场景、不同数据规模，且报告了方差，对比方法均为近年SOTA。消融实验较为全面，实验结果客观，统计上可靠。

## 6. 论文的主要结论与发现

- CutSSL在所有标签率（1~4000标签/类）和所有数据集上一致超越所有对比方法。
- 在CIFAR-10上，1标签/类时准确率44.7% vs 第二好41.8%（Poisson-MBO），提升2.9%；4000标签/类时82.0% vs 81.1%（精确拉普拉斯）。
- 在OGB-Arxiv和Products上，低标签率准确率分别提升5%以上，且运行时间低于Poisson-MBO。
- 均值平移启发式本质上是带基数约束拉普拉斯学习的一种近似解，而精确解（投影CG）提升有限（约1-2%），但CutSSL通过整数恢复带来显著增益。
- 在标签/类别不平衡场景下，CutSSL鲁棒性更强。

## 7. 优点

- **理论创新**：建立了带基数约束的图划分与半监督学习的精确连续松弛，并给出整数解恢复的充分条件。
- **算法高效**：ADMM迭代可高效求解，特别是当图稀疏时每次迭代主要代价为解一个类拉普拉斯系统（可预处理共轭梯度）。
- **实验全面**：覆盖多种图类型、规模、标签率和不平衡场景，与多个SOTA方法严格对比。
- **可解释性**：解释了均值平移启发式的理论基础，并指出其子最优性。
- **代码开源**：提供Colab可重复实验。

## 8. 不足与局限

- **图结构依赖**：方法性能依赖于图构建质量（如k-NN参数、核宽度），文中虽做了消融但未深度讨论图构建失效场景。
- **超参数选择**：主要超参数s需要根据数据集调整，文中通过同伦路径设置固定s=0.1，但理论最优s可能随图变化。
- **仅节点特征空间**：图像数据集使用了预训练自编码器特征，而未在其他特征提取方式下验证。
- **规模限制**：虽然测试了百万级节点图，但算法复杂度与节点数线性相关，对于极大图可能仍需近似。
- **非凸性风险**：虽然理论保证局部极小为整数解，但ADMM可能收敛到较差的局部极小，尤其当s较大时。

（完）
