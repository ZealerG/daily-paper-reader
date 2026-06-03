---
title: Learning on Large Graphs using Intersecting Communities
title_zh: 使用相交社区在大图上学习
authors: "Ben Finkelshtein, Ismail Ilkan Ceylan, Michael M. Bronstein, Ron Levie"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=pGR5X4e1gy"
tags: ["query:graph-part"]
score: 6.0
evidence: 基于社区的图近似，与图划分相关
tldr: 本文提出将大图近似为相交社区图（ICG）用于图神经网络，使得内存复杂度与图大小无关。该工作利用弱图正则引理构造社区结构，能够有效保留图的关键划分特征，从而支持大规模图的高效学习。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 300, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 300, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 479, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 460, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1427, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1430, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1436, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1426, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pgr5x4e1gy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1122, \"height\": 811, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 615, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 899, \"height\": 613, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 637, \"height\": 685, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 434, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1018, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 781, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 840, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 682, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 600, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1247, \"height\": 551, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 756, \"height\": 472, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pgr5x4e1gy/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 835, \"height\": 550, \"label\": \"Table\"}]"
motivation: 消息传递神经网络在大图上内存开销过大，尤其非稀疏图。
method: 用相交社区近似原图，基于弱图正则引理构造社区分解。
result: 社区数量与图大小无关，大幅降低内存消耗且保持性能。
conclusion: 相交社区是一种高效的大图近似方法，可应用于图划分学习。
---

## Abstract
Message Passing Neural Networks (MPNNs) are a staple of graph machine learning. MPNNs iteratively update each node’s representation in an input graph by aggregating messages from the node’s neighbors, which necessitates a memory complexity of the order of the __number of graph edges__. This complexity might quickly become  prohibitive for large graphs provided they are not very sparse.  In this paper, we propose a novel approach to alleviate this problem by  approximating the input graph as an  intersecting community graph (ICG) -- a combination of intersecting cliques. The key insight is that the number of communities required to approximate a graph  __does not depend on the graph size__. We develop a new constructive version of the Weak Graph Regularity Lemma to efficiently construct an approximating ICG for any input graph. We then devise an efficient graph learning algorithm operating directly on ICG in linear memory and time with respect to the __number of nodes__ (rather than edges).  This offers a new and fundamentally different pipeline for learning on very large non-sparse graphs, whose applicability is demonstrated empirically on node classification tasks and spatio-temporal data processing.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：消息传递神经网络（MPNN）在大图上的内存复杂度与边数（E）呈线性关系，对于非稀疏大图（如社交网络，节点数10^8~10^9，平均度10^2~10^3），GPU内存往往无法容纳。
- **整体含义**：本文提出一种全新的图学习范式，通过将输入图近似为**相交社区图（Intersecting Community Graph, ICG）**，使得学习阶段的内存和时间复杂度降至与节点数（N）线性相关，从根本上突破了MPNN的瓶颈。

## 2. 论文提出的方法论

### 核心思想
- 利用**弱图正则引理（Weak Graph Regularity Lemma）**的构造性版本，证明任何图都可以用少量（K个）相交社区（clique）的线性组合来近似，且K与图大小N无关，仅与近似精度相关（K ~ ε^{-2}）。
- 将图表示为ICG：\( C = Q \operatorname{diag}(r) Q^\top \)，信号部分 \( P = QF \)，其中 \( Q \in \mathbb{R}^{N \times K} \) 为软隶属矩阵，\( r \in \mathbb{R}^K \) 为社区幅度，\( F \in \mathbb{R}^{K \times D} \) 为社区特征。

### 关键技术细节
1. **构造性弱正则引理（Theorem 3.1）**：
   - 优化Frobenius范数误差可以保证在cut度量下具有相同量级的误差，从而避免直接优化NP难的cut范数。
   - 关键不等式：若Frobenius误差接近最优，则cut度量误差有上界 \( O\left(\frac{N}{\sqrt{E}}\sqrt{\frac{R}{K}}+\delta\right) \)。

2. **ICG拟合算法**：
   - 目标函数：\( \mathcal{L}(Q, r, F) = \|A - Q\operatorname{diag}(r)Q^\top\|_F^2 + \lambda \|S - QF\|_F^2 \)。
   - 通过梯度下降优化，利用Proposition 4.1将计算复杂度降至 \( O(K^2N + KE) \)，空间复杂度 \( O(KN + E) \)。
   - 初始化：基于特征向量分解（Corollary D.1），将前K/3个特征向量转换为软指示函数。

3. **ICG神经网络（ICG-NN & ICG u-NN）**：
   - 每层包含节点空间和社区空间的操作：分析 \( Q^\dagger S \)、合成 \( QF \)、社区处理（MLP或注意力）、节点处理（逐点MLP）。
   - 复杂度：每层 \( O(NK + K^2D + ND) \)，远低于MPNN的 \( O(ED^2) \)。
   - 对于时空图，预处理一次ICG后，每个时间步的学习复杂度为 \( O(TN(K+D)) \)，而MPNN为 \( O(TED^2) \)。

## 3. 实验设计

### 数据集和场景
- **节点分类**：tolokers（11,758节点，异配）、squirrel（5,201节点）、twitch-gamers（168,114节点）。
- **时空图**：METR-LA（207节点，密度3.54×10⁻²）、PEMS-BAY（325节点，密度2.24×10⁻²）。
- **大规模图**：Reddit（232,965节点）、Flickr（89,250节点）。
- 此外还有在ER随机图上的运行时对比和消融实验。

### Benchmark与对比方法
- **节点分类**：MLP、GCN、GAT、GT、H2GCN、GPR-GNN、LINKX、GloGNN。
- **时空图**：DCRNN、GraphWaveNet、AGCRN、T&S-IMP等。
- **图粗化/压缩**：Coarsening、Random、Herding、K-Center、One-Step、GCOND、SFGC、GC-SNTK。

## 4. 资源与算力

- 所有实验均在**单块NVIDIA L40 GPU**上完成（论文正文脚注7说明）。
- 训练时长：附录F.8给出了tolokers（ICG u-NN：33秒 vs GCN：510秒）、squirrel（225秒 vs 3790秒）、twitch-gamers（49秒 vs 1220秒）的时间直到收敛。
- 未给出GPU使用小时数总数，但可以推断算力需求较低。

## 5. 实验数量与充分性

- **实验数量**：包含3个节点分类、2个时空图、2个大规模图（与粗化方法对比）、运行时分析（图6-7）、子图采样实验（图3）、社区数量消融（图4）、初始化对比（表5）、cut范数与Frobenius范数相关性（图5）、内存分析（图8）。总计约10组以上实验。
- **充分性与公平性**：对比方法均为强基线，使用公开数据划分（如Platonov等、Li等的标准划分），报告均值和标准差，遵循已有设置。消融实验覆盖关键超参数。结论客观。

## 6. 论文的主要结论与发现

- ICG方法在保持与MPNN相当或更优性能的同时，大幅降低了内存和计算开销（复杂度O(N) vs O(E)）。
- 构造性弱正则引理提供了理论保证，使ICG逼近在cut度量下有效，且K与N无关。
- 在多个真实数据集上，ICG-NN/ICG u-NN达到或超过了现有方法，尤其是在异构图（tolokers、squirrel）和大规模图（Reddit、Flickr）上表现突出。
- 时空图任务中，ICG方法同样具有竞争力，且效率优势随时间尺度放大。

## 7. 优点

- **理论创新**：首次提出ICG的构造性近似定理，将难以优化的cut度量转化为可操作的Frobenius范数优化。
- **实用优势**：预计算ICG后，后续学习全流程与节点数线性相关，可处理GPU无法容纳的大而密的图。
- **通用性**：同时适用于节点分类、时空预测和图粗化等任务，且可通过子图SGD进一步降低预计算内存。
- **实证充分**：在多场景、多数据集上进行验证，并提供消融和相关性分析。

## 8. 不足与局限

- **图类型限制**：当前仅支持无向图，许多实际问题（如交通网络）中的有向图无法直接处理。
- **不可迁移性**：ICG依赖特定图结构，不同图需要重新拟合，不能跨图转移。
- **预处理瓶颈**：拟合ICG需要一次性读取所有边（O(E)），对于边数极大但节点数适中的图，仍可能遇到内存压力（论文已通过子图采样缓解）。
- **稀疏图保证弱**：理论要求 \( d^2 > N \)（即半稠密条件）才能确保ICG优于MPNN，但实验表明在稀疏图上仍有效，缺乏更紧的稀疏情况理论。
- **超参数敏感性**：社区数量K需要手动调节，虽实验显示对性能不敏感，但选优仍依赖验证集。

（完）
