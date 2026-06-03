---
title: "SpEx: A Spectral Approach to Explainable Clustering"
title_zh: "SpEx: 可解释聚类的谱方法"
authors: "Tal Argov, Tal Wagner"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=heoHY4vcRl"
tags: ["query:graph-part"]
score: 7.0
evidence: 提出基于谱图划分的可解释聚类方法
tldr: 本文提出基于谱图划分的可解释聚类通用方法。它将给定聚类或数据集转化为解释树，通过优化图割来拟合树结构。该算法能处理任意聚类，并且揭示了先前可解释聚类算法也可视为图划分。实验显示该方法在保持可解释性的同时达到有竞争力的聚类质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-heohy4vcrl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 690, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-heohy4vcrl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 910, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-heohy4vcrl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1358, \"height\": 1149, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 745, \"height\": 1252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1381, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 483, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1439, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1036, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1436, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1439, \"height\": 643, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-heohy4vcrl/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1438, \"height\": 462, \"label\": \"Table\"}]"
motivation: 现有可解释聚类缺乏通用方法，且局限于特定聚类目标。
method: 将可解释聚类建模为谱图划分问题，设计算法拟合解释树。
result: 能对任意聚类生成解释树，性能与先前方法相当或更优。
conclusion: 谱图划分为可解释聚类提供了统一且通用的框架。
---

## Abstract
Explainable clustering by axis-aligned decision trees was introduced by Moshkovitz et al. (2020) and has gained considerable interest. Prior work has focused on minimizing the price of explainability for specific clustering objectives, lacking a general method to fit an explanation tree to any given clustering, without restrictions. In this work, we propose a new and generic approach to explainable clustering, based on spectral graph partitioning. With it, we design an explainable clustering algorithm that can fit an explanation tree to any given non-explainable clustering, or directly to the dataset itself. Moreover, we show that prior algorithms can also be interpreted as graph partitioning, through a generalized framework due to Trevisan (2013) wherein cuts are optimized in two graphs simultaneously. Our experiments show the favorable performance of our method compared to baselines on a range of datasets.

---

## 论文详细总结（自动生成）

# 论文《SpEx: A Spectral Approach to Explainable Clustering》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：现有可解释聚类（基于轴对齐决策树）方法大多针对特定聚类目标（如 k-means, k-medians）设计，缺乏一种通用的、能对任意给定的参考聚类（包括无质心的谱聚类、核 k-means）生成解释树的方法。CART 可被复用，但其目标是分类精度而非聚类一致性，在真实数据上表现不佳。
- **动机**：许多高效聚类方法（如谱聚类、核 k-means）不产生质心，无法被 IMM、EMN 等现有可解释聚类算法直接“圆整”为解释树。因此需要一种参考无关（reference-oblivious）的通用方案。
- **含义**：本文提出基于谱图划分的新思路，将可解释聚类转化为图割优化问题，既能对任意参考聚类拟合解释树，也能直接从数据构建解释树（无需参考聚类）。

## 2. 方法论：核心思想、关键技术细节与算法流程

### 核心思想
- 将数据集中的点视为图节点，通过构建合适的图（如参考聚类对应的团图或 kNN 图）来编码聚类结构。
- 利用 Cheeger 不等式的一个推广（定理 2.2），证明存在低电导的坐标割，且该割的电导上界由图中相邻点对与任意点对的期望平方距离之比决定。
- 迭代地在决策树每个内部节点选择使局部归一化割最小的坐标阈值，贪心地优化整体多路分割目标（式 3）。

### 关键技术细节
- **图构造**：
  - **SPEX-Clique**：对任意参考聚类，构建团图：同一簇内点之间边权为 1/(|Ci|-1)，不同簇间无边。
  - **SPEX-kNN**：不依赖参考聚类，直接基于数据集构建 k 近邻图（k=20），也可使用其他图。
- **树构建算法（Algorithm 1）**：
  1. 初始化根节点为全部数据。
  2. 每个叶子节点计算最佳坐标割（最小化 ψG(S)+ψG(X\S)），优先级为割减少的 ψG 值。
  3. 循环选取优先级最高的叶子分裂，直到达到目标叶子数 ℓ。
- **统一视角**：本文揭示 IMM、EMN、CART 均可视为在两种图（G 和 H）上优化非均匀稀疏割的特殊情形（Section 3）。
  - IMM ≈ 星图（G）+ 单边图（H 连接最远质心）
  - EMN ≈ 星图（G）+ 质心上的完全图（H）
  - CART ≈ 独立集图（H）+ 度加权完全图（G），且其目标近似等于最大化 H 上的电导，导致倾向于分割不同簇间边多的方向。

## 3. 实验设计

### 数据集
- 使用 8 个真实公开数据集：CIFAR-10（50k 点，512 维）、20Newsgroups（11k 点，768 维）、MNIST（60k 点，512 维）、Caltech 101（8.7k 点）、Beans（13.6k 点，16 维）、Breast Cancer（569 点，30 维）、Ecoli（336 点，7 维）、Iris（150 点，4 维）。涵盖不同规模与维度。
- 此外，附录使用 R15 和 Pathbased 两个小规模合成数据集。

### 对比方法
- **EMN**（Esfandiari et al., 2022）：需参考聚类有质心，仅适用于 k-means 参考。
- **CART**：复用监督决策树分类算法，分别以 k-means 和谱聚类为参考。
- **Kernel IMM**（Fleissner et al., 2024）：仅适用于核 k-means，且无法在较大数据集上运行（仅报告小数据集结果）。
- **本文方法**：SPEX-Clique（参考为谱聚类、k-means、核 k-means）、SPEX-kNN（k=20，无参考）。

### 评估指标
- 调整兰德指数（ARI）和调整互信息（AMI），均相对于真实类标签（ground truth）计算。

## 4. 资源与算力

- 文中明确表示所有实验在 **Google Colab 免费云 CPU 机器**上运行，未使用 GPU。
- 运行时限：每个算法在每个数据集上最多分配 3 小时。
- 实际运行时间：除 Kernel IMM 外的所有方法均在 16 分钟内完成（见表 4）。
- 未说明 CPU 具体型号、核数或内存，也未进行多轮重复运行以统计误差。因此资源细节不够透明。

## 5. 实验数量与充分性

- **主实验**：图 3 展示了 8 个真实数据集上 5 种方法（SPEX-Clique、SPEX-kNN、EMN、CART-谱、CART-kmeans）的 ARI 和 AMI。
- **附表**：表 2–3 和附录表 5–8 补充了更多参考设置（如核 k-means 参考、ℓ=2k 叶子数、kNN 不同 k 值）以及 Weighted CART 的修改版。
- **充分性评价**：
  - 👍 覆盖多种数据规模、维度、聚类结构，对比方法齐全（包括专用方法和通用方法）。
  - 👍 同时报告 ARI 和 AMI 两个互补指标。
  - 👎 未进行多次重复实验（算法确定无随机性，但谱聚类参考可能因初始化不同而有波动，文中未讨论）。
  - 👎 缺乏用户研究验证可解释性实际提升。
  - 总体上实验设计较为客观、公正，但消融实验仅体现在附录中（参数敏感性），主图未包含 error bars。

## 6. 主要结论与发现

- **SPEX-Clique 在大多数数据集上优于所有基线**，特别是当参考聚类为谱聚类时（此时 EMN 无法使用）。
- **SPEX-kNN 在低维数据集（Beans、Ecoli、Iris）上表现最佳**，但在高维图像/文本数据集上退化严重（ARI 低于 0.1）。
- **CART 在小数据集上表现尚可，在大数据集上表现差**，印证了其目标与聚类不一致的理论分析。
- **EMN 当参考为 k-means 时略优于 SPEX-Clique**，但差距不大；且无法扩展到其他参考类型。
- **与 IMM、EMN、CART 的统一图划分视角**揭示了现有方法的内在联系与局限。

## 7. 优点

- **通用性**：首个能对任意参考聚类（包括谱聚类、核 k-means）生成解释树的方法，无需质心或特定核。
- **理论基础**：通过 Cheeger 不等式将可解释聚类与谱图划分建立联系，并给出了一个有趣的上界。
- **统一视角**：将先前看似不同的算法纳入非均匀稀疏割框架，加深理解。
- **实用可扩展**：算法时间复杂度 O(kdn log n)，可在中等规模数据集上快速运行（表 4）。
- **开源代码**：附有匿名代码仓库，便于复现。

## 8. 不足与局限

- **缺乏最坏情况近似保证**：虽然定理 2.2 提供了单步割的电导上界，但整体贪心树构建过程无近似比，无法与专用方法（如 EMN 对 k-means 的近似比）直接竞争。
- **高维失效**：SPEX-kNN 在高维稀疏数据上性能极低，依赖欧氏距离和 kNN 图，后续需改进图构造。
- **实验未统计随机性**：谱聚类参考可能因初始化不同而变化，但文中没有报告多次运行的标准差；Kernel IMM 在中等以上数据集完全无法运行，仅在小数据集上比较。
- **可解释性验证缺失**：未进行用户调查或案例研究来衡量决策树的实际可解释性，仅用聚类一致性指标间接评估。
- **消融研究有限**：仅探索了 kNN 参数和叶子数，未分析不同图构造（如 ε 半径图、不同边权方案）对结果的影响。
- **部署限制**：方法中需要预先确定叶子数 ℓ，对于未知簇数的实际场景需要额外调参。

（完）
