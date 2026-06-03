---
title: Multi-View Stochastic Block Models
title_zh: 多视图随机块模型
authors: "Vincent Cohen-Addad, Tommaso d'Orsi, Silvio Lattanzi, Rajai Nasser"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=BJx1K4lAAX"
tags: ["query:graph-part"]
score: 9.0
evidence: 多视图随机块模型用于图聚类，等同于图划分
tldr: 图聚类是核心无监督学习问题，多视图场景下多个图源提供互补信息。该文提出多视图随机块模型，并设计了分别分析每个图结构的高效算法，理论证明优于简单拼接方法，并给出了信息论下界。该工作直接对应图划分任务，但未使用RL方法。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-bjx1k4laax/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 781, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-bjx1k4laax/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 775, \"height\": 532, \"label\": \"Figure\"}]"
motivation: 多视图图聚类中，简单拼接多个图会丢失结构信息。
method: 提出多视图随机块模型，并设计分别分析各图结构的算法。
result: 算法性能优于拼接方法，并得到信息论下界。
conclusion: 为多视图图聚类提供了理论框架和高效算法。
---

## Abstract
Graph clustering is a central topic in unsupervised learning with a multitude of practical applications. In recent years, multi-view graph clustering has gained a lot of attention for its applicability to real-world instances where one often has access to multiple data sources. In this paper we formalize a new family of models, called *multi-view stochastic block models* that capture this setting. For this model, we first study efficient algorithms that naively work on the union of multiple graphs. Then, we introduce a new efficient algorithm that provably outperforms previous approaches by analyzing the structure of each graph separately. Finally, we complement our results with an information-theoretic lower bound studying the limits of what can be done in this model.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：现实中的图聚类任务往往有多源数据（如社交网络中的好友图、评论图、点赞图等），单个视图只能提供粗粒度的社区信息，而多视图联合分析有望恢复更精细的聚类结构。现有理论工作多局限于每个视图都有相同数量的社区，而实际中每个视图可能仅反映部分信息（如二分类）。
- **论文贡献**：形式化定义了“多视图随机块模型”（Multi-View SBM, MV-SBM），该模型允许每个视图的潜在标签是原始 k 个社区通过随机二值映射得到的两个“伪标签”。在此模型下，论文分析了两种融合策略（早期融合 vs. 晚期融合）的理论性能，并给出了信息论下界。

### 2. 方法论
- **核心思想**：早期融合（直接将所有图合并为一张图）会将信号稀释，导致需要 Ω(k²) 个视图才能达到与单视图相当的恢复能力；晚期融合则先对每个视图独立进行弱恢复（估计二值标签矩阵），再通过组合这些估计来推断原始 k 个社区。
- **关键技术细节**：
  1. **单视图弱恢复**：提出一个针对可能不平衡的2社区SBM的专用算法（Theorem 3.1），它能在每个视图达到 Kesten-Stigum 阈值时返回一个矩阵 \(\hat{X}_\ell\)，使得同社区与不同社区对的期望差异为常数 \(C_\ell\)。
  2. **多视图融合（Algorithm 1）**：
     - 对每个视图运行上述弱恢复算法，得到 \(\hat{X}_\ell\)。
     - 对每个节点 i，计算所有节点 j 的 \(\sum_{\ell} \hat{X}_\ell(i,j)\)，并选出最大的 n/k 个节点作为“邻居”，构建有向图 F。
     - 对 F 的邻接矩阵运行第二轮聚类（Algorithm 2：第二矩舍入），通过比较行的距离恢复 k 个社区。
  3. **理论保证**：当每个视图满足 \(d_\ell \varepsilon_\ell^2/4 > 1\) 且视图数 \(t = \Omega(\log k / C_T^2)\) 时，可达到弱恢复；若 \(t = \Omega(\log n / C_T^2)\) 则可达到精确恢复。
  4. **信息论下界**：证明任何仅基于黑箱估计器（即每个视图只提供具有固定相关性的矩阵）的算法，必须满足 \(t = \Omega(\log k / C_T)\)，说明对 \(C_T\) 的依赖是本质的。

### 3. 实验设计
- **数据集**：从 \((d,\varepsilon,k,t)\)-MV-SBM 模型中合成的数据，固定 \(n=1000, k=10\)，变化 \(\varepsilon\) 或 \(d\)。
- **基准（Benchmark）**：对比两种方法：
  - A.1：在合并图（union graph）上运行 Louvain 算法（早期融合）。
  - A.2：Algorithm 1 中替换 Theorem 3.1 的专用估计器为 Louvain 算法（晚期融合，实际使用 Louvain 代替复杂算法）。
- **评价指标**：协议（agreement），即预测标签与真实标签的最佳排列匹配比例。

### 4. 资源与算力
- 论文未明确提及使用的 GPU 型号、数量或训练时长。所有实验基于合成数据，规模较小（n=1000），推测在普通 CPU 上即可完成。因此无法判断算力需求，也未提供可复现性细节。

### 5. 实验数量与充分性
- **实验数量**：仅有 2 组实验（图1和图2），每组为改变一个参数（\(\varepsilon\) 或 \(d\)）的曲线，每个点平均20次模拟。
- **充分性评价**：实验数量较少，且未覆盖更多参数空间（如不同 k、不同 n、不同 t 值），也未与现有多视图聚类方法（如 De Santiago et al. 2023 中的方法）比较。实验主要作为理论结果的直观验证，而非全面的性能评估。由此，实验的客观性和公平性存在一定局限，尤其是用 Louvain 替代理论算法，可能无法充分展示所提方法的优势。

### 6. 主要结论与发现
- 在多视图 SBM 下，**晚期融合（先分别分析再合并）在理论上显著优于早期融合（合并图后再分析）**：只需 \(O(\log k)\) 个视图即可弱恢复，而早期融合需要 \(O(k^2)\) 个视图。
- 每个视图的弱恢复能力通过一个与 Kesten-Stigum 阈值相关的常数 \(C_\ell\) 刻画；所需视图数反比于这些常数的平均值平方。
- 存在信息论下界：若每个视图的估计器是黑箱的（只知道其相关性），则视图数必须至少 \(O(\log k / C_T)\)，表明算法常数依赖是不可避免的。

### 7. 优点
- **理论创新**：首次为多视图图聚类建立了清晰的理论模型（MV-SBM），并给出了早期与晚期融合的严格比较，填补了理论空白。
- **算法简洁**：晚期融合算法思路清晰，可分解为已知的弱恢复算法和第二矩聚类，便于理论分析。
- **信息论下界**：不仅给出构造性算法，还证明了黑箱情形下的最优性（除常数因子外），增强了结论的完整性。

### 8. 不足与局限
- **实验覆盖不足**：仅有2组合成数据实验，缺乏真实数据集、更多视图数、更多社区数的比较，也未与现有其他多视图聚类方法（如谱聚类、多视图图神经网络等）对比。
- **实际实现障碍**：Theorem 3.1 中使用的弱恢复算法依赖于高次 sum-of-squares 方法（Ding et al. 2022, 2023），论文自身承认该算法复杂且难以在实验中实现，只能用 Louvain 替代，导致实验与理论算法不一致。
- **模型限制**：当前模型每个视图仅映射为2个伪标签（二分类），虽然推广到 \(k_\ell > 2\) 的讨论在结论部分，但未给出算法和理论，限制了模型的一般性。
- **黑箱假设的限制**：下界部分假设算法仅基于黑箱估计器（仅知相关性），不排除存在更聪明的非黑箱算法可能突破该下界。

（完）
