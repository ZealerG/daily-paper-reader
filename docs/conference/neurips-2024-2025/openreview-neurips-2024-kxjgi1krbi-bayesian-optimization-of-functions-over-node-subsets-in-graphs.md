---
title: Bayesian Optimization of Functions over Node Subsets in Graphs
title_zh: 图节点子集函数的贝叶斯优化
authors: "Huidong Liang, Xingchen Wan, Xiaowen Dong"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=KxjGi1krBi"
tags: ["query:graph-part"]
score: 6.0
evidence: 图节点子集函数的贝叶斯优化
tldr: 本文针对图上节点子集函数的黑箱优化问题，提出贝叶斯优化框架。通过将每个k-节点子集映射到新组合图中的一个节点，并采用局部移动代理来高效采集样本。方法在合成和真实图上验证，相比现有算法更样本高效。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 721, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 1004, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1402, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1411, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1322, \"height\": 309, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1448, \"height\": 299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1423, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1439, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1420, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1440, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1448, \"height\": 770, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1447, \"height\": 782, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1446, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1450, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1442, \"height\": 293, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1442, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1452, \"height\": 842, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1450, \"height\": 842, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1454, \"height\": 854, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kxjgi1krbi/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1449, \"height\": 845, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-kxjgi1krbi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 478, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kxjgi1krbi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1299, \"height\": 246, \"label\": \"Table\"}]"
motivation: 图节点子集上的函数优化是组合黑箱问题，现有方法样本效率低或任务特定。
method: 将节点子集映射到新组合图节点，利用贝叶斯优化和局部移动代理进行高效搜索。
result: 在多个图任务上，所提框架比基线方法以更少评估找到更优解。
conclusion: 贝叶斯优化可有效用于图节点子集优化问题。
---

## Abstract
We address the problem of optimizing over functions defined on node subsets in a graph.  The optimization of such functions is often a non-trivial task given their combinatorial, black-box and expensive-to-evaluate nature. Although various algorithms have been introduced in the literature, most are either task-specific or computationally inefficient and only utilize information about the graph structure without considering the characteristics of the function. To address these limitations, we utilize Bayesian Optimization (BO), a sample-efficient black-box solver, and propose a novel framework for combinatorial optimization on graphs. More specifically, we map each $k$-node subset in the original graph to a node in a new combinatorial graph and adopt a local modeling approach to efficiently traverse the latter graph by progressively sampling its subgraphs using a recursive algorithm. Extensive experiments under both synthetic and real-world setups demonstrate the effectiveness of the proposed BO framework on various types of graphs and optimization tasks, where its behavior is analyzed in detail with ablation studies.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- 在图（如交通、社交、流行病网络）中，常需要选择一组 **k 个节点**（node subset）以最大化某种效用函数，例如最大化信息传播、最小化感染时间、增强网络弹性等。
- 这类问题具有**组合爆炸**（搜索空间为 $\binom{|V|}{k}$）、**黑箱性**（函数无解析形式）和**评估昂贵**（需大量模拟或调用图神经网络）的特点。
- 现有方法（如贪心算法、PageRank 等代理法）大多**任务特定**或**计算效率低**，且忽略底层函数的特性。
- 本文提出**贝叶斯优化（BO）框架**，将每个 k-节点子集映射到一个**组合图（combo-graph）** 的节点上，利用 BO 的样本高效性来求解这类黑箱组合优化问题。

### 2. 方法论：核心思想、关键技术细节

- **核心思想**：构建一个**组合图** $\hat{G}_{\langle k \rangle}$，其中每个 combo-节点对应原始图 $G$ 的一个 k-节点子集；两个 combo-节点相邻当且仅当它们**恰好有一个元素不同**，且不同的两个元素在原始图中相邻。
- **算法流程**：
  1. **初始化**：在组合图中选择一个起始 combo-节点（随机或根据先验）。
  2. **局部子图采样**（Algorithm 1）：以当前最佳 combo-节点为中心，递归地采样一个大小为 $Q$ 的**局部 combo-子图**，逐步揭示原始图的结构（无需事先知道全图）。
  3. **代理建模**：在局部子图上拟合**图高斯过程（Graph GP）**，使用扩散核（Diffusion Kernel）衡量 combo-节点间的相似性。
  4. **采集函数**：采用**期望改进（EI）** 在子图内选择下一个待评估的 combo-节点。
  5. **移动策略**：若新查询点的函数值优于当前最佳，则将中心移动到该点并重新采样子图；否则保持原中心。
  6. **重启机制**：设置失败容忍度 `failtol`，连续未改进次数超过该阈值则重启（可随机、回到最佳点或初始点），以平衡探索与开发。
- **关键技术**：
  - 组合图的性质（引理 3.2、3.3）保证了局部搜索的可行性：ℓ 跳内最多改变 ℓ 个元素；combo-节点度随 k 线性增长。
  - 图 GP 利用图拉普拉斯的特征分解构建核函数，计算复杂度通过局部子图限制在 $O(Q^3)$。

### 3. 实验设计

- **数据集/场景**：
  - **合成问题**：4 种随机图（BA、WS、SBM、2D-Grid），底层函数分别为平均特征向量中心性、度中心性、PageRank 和 Ackley 函数。
  - **真实场景**：5 个任务——
    1. 流行病曲线平坦化（SIR 模拟，接触网络）
    2. 病人零号追踪（SBM 网络上的感染时间）
    3. 社交网络影响力最大化（独立级联模型，Coauthor CS 网络）
    4. 交通网络弹性测试（曼哈顿路网，使用线图转换）
    5. 图神经网络黑箱攻击（GIN 模型，分子图 ENZYMES）
- **基准方法（6 种）**：
  - 在原始图上操作：Random、k-Random Walk、k-Local Search。
  - 在组合图上操作：BFS、DFS、Local Search（相当于 BO 的随机代理版本）。
- **实验设置**：子集大小 k ∈ {4, 8, 16, 32}，查询预算 300 次，重复 20 个随机种子，报告均值与标准误。使用扩散核 + EI，子图大小 Q=4000，failtol=30。

### 4. 资源与算力

- 论文未明确说明 GPU 型号或数量，所有实验在 **96 核 Intel Xeon @ 2.30GHz CPU 集群**（250GB 内存）上完成。
- 合成任务通常在 **1 小时内**完成；基于模拟的真实任务（如 SIR/IC）约需 **12 小时**；其他真实任务约 1 小时。

### 5. 实验数量与充分性

- 共进行 **9 个主实验**（4 合成 + 5 真实），每个实验覆盖 4 种 k 值，合计 36 组子实验。
- 额外包含：
  - **核函数验证**（4 种核在组合图上的预测相关性）
  - **信号平滑度影响分析**（不同频率特征向量的表现）
  - **消融实验**（子图大小 Q、失败容忍度 failtol）
  - **噪声场景实验**（高斯噪声 σ=0.1~1.0）
  - **与 COMBO 的比较**（小图）
  - **大规模图实验**（OGB-arXiv，|V|≈1.7×10⁵，k≤128）
- 结论：实验覆盖多种图结构、函数类型和噪声条件，对比基线合理，且进行了消融和鲁棒性测试，**充分且客观**。但未直接与经典组合优化方法（如贪心算法）对比（仅通过局部搜索间接反映）。

### 6. 主要结论与发现

- **GraphComBO 在大多数任务中显著优于所有基线**，尤其当 k 较小时。
- 性能随 k 增大逐渐下降，原因包括：局部子图覆盖邻域变小、代理模型对非平滑函数拟合能力减弱。
- 探索与开发的平衡（通过 failtol 和 Q 控制）对性能影响关键：对于平滑函数，更偏重 exploitation 效果更好；对于非平滑函数，需要更多 exploration。
- 图 GP 的核函数对信号平滑度敏感，平滑度越低，预测相关性越差，BO 的优势相应减弱。
- 在较大图（OGB-arXiv）上仍保持领先，表明方法具有一定可扩展性。

### 7. 优点

- **首次将 BO 应用于图上节点子集优化**，开辟新研究方向。
- **函数无关**：可适配任意黑箱昂贵函数，无需任务特定设计。
- **局部建模 + 递归采样**创新地处理组合爆炸，且能在**未知图结构**下逐步揭示邻域。
- 对组合图的定义（恰好一个元素不同）赋予了自然的距离度量，利于 GP 建模。
- 实验设计全面，包含合成/真实、不同 k、消融、噪声、大规模等多种场景，验证了方法的鲁棒性。
- 代码开源（github.com/LeonResearch/GraphComBO），促进复现和后续研究。

### 8. 不足与局限

- **扩展性问题**：k 增大时性能下降明显，组合爆炸仍难以完全克服，未来需改进探索策略或引入全局信息。
- **局部建模的局限**：仅依赖局部子图，可能遗漏全局结构信息，导致陷入次优解。论文提及可引入 GNN 等全局嵌入作为改进方向。
- **超参数固定**：Q 和 failtol 为固定值，未自适应调整，可能影响泛化性。论文建议未来可研究动态 Q 和 ℓmax。
- **初始化依赖**：默认随机初始化，当无先验时可能浪费预算。若可利用领域知识指定初始点，有望提升效率。
- **与其他优化方法对比不足**：未与贪心算法（如 CELF）、启发式算法（如遗传算法）等非 BO 方法对比，限制了说服力。
- **实验资源限制**：主要用于 CPU 计算，未测试大规模 GPU 加速场景，且部分模拟任务耗时较长。

（完）
