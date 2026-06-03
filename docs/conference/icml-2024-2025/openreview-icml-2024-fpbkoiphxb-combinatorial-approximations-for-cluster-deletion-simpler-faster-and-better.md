---
title: "Combinatorial Approximations for Cluster Deletion: Simpler, Faster, and Better"
title_zh: 团删除的组合近似：更简单、更快、更好
authors: "Vicente Balmaseda, Ying Xu, Yixin Cao, Nate Veldt"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=FpbKoIPHxb"
tags: ["query:graph-part"]
score: 9.0
evidence: 直接研究图分区问题：团删除
tldr: 该论文研究团删除这一图分区问题，将两个已知近似算法的近似比从4改进到3，并给出简单的去随机化方法。进一步提出纯组合的近似算法，在理论和实践上都具有更高的可扩展性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-fpbkoiphxb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fpbkoiphxb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 797, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fpbkoiphxb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 625, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fpbkoiphxb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 838, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fpbkoiphxb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 619, \"height\": 445, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 854, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1167, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1681, \"height\": 1303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1669, \"height\": 2206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1669, \"height\": 2208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1670, \"height\": 2230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1668, \"height\": 2228, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fpbkoiphxb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1681, \"height\": 700, \"label\": \"Table\"}]"
motivation: 团删除是NP难的图聚类问题，需要更好的近似算法。
method: 重新分析已有算法，改进近似比；设计贪心去随机化及纯组合新算法。
result: 近似比降至3，新算法更简单且可扩展。
conclusion: 提供了更高效的团删除求解方案，对图分区研究有直接贡献。
---

## Abstract
Cluster deletion is an NP-hard graph clustering objective with applications in computational biology and social network analysis, where the goal is to delete a minimum number of edges to partition a graph into cliques. We first provide a tighter analysis of two previous approximation algorithms, improving their approximation guarantees from 4 to 3. Moreover, we show that both algorithms can be derandomized in a surprisingly simple way, by greedily taking a vertex of maximum degree in an auxiliary graph and forming a cluster around it. One of these algorithms relies on solving a linear program. Our final contribution is to design a new and purely combinatorial approach for doing so that is far more scalable in theory and practice.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究对象**：**团删除（Cluster Deletion）** 问题，即给定无向图，通过删除最少数量的边，使得剩余图变成不相交的团（clique）的集合。这是一个NP-hard的图聚类问题，在计算生物学（如基因网络分析）和社会网络分析（如社区检测）中有重要应用。
- **已有方法**：已有近似算法，包括基于线性规划（LP）舍入的4-近似算法（Charikar et al., 2005），以及基于强三元闭包（STC）标记的4-近似算法（Veldt, 2022）。其中STC方法有更快的组合算法MatchFlipPivot，但其近似比落后于基于经典LP的2-近似算法。且这些算法多为随机化，去随机化实现复杂、速度慢。
- **动机**：缩小理论与实践的差距——希望得到**更简单、更快、近似比更好**的确定性算法，并能扩展到更大规模的图。

## 2. 方法论：核心思想、关键技术细节

### 2.1 改进的近似分析
- 对两个已有算法（MatchFlipPivot和STC LP舍入算法）进行更紧的分析，**将近似比从4提升到3**。
- **核心引理（Pivoting Lemma）**：在形成的辅助图 $\hat{G}$ 上运行Pivot算法，如果选择**Pivot策略1（选择最大度顶点）** 或**策略2（选择使 $|B_k|/|N_k|$ 最小化的顶点）**，则边界边数 $|B| \le 2|N|$（其中 $B$ 是簇间边，$N$ 是簇内非边），从而保证3-近似。
- 策略1（最大度）简单、高效，且不需要像策略2那样维护复杂的 $B_k,N_k$ 值。

### 2.2 去随机化
- 证明只要在辅助图 $\hat{G}$ 上使用**策略1（贪心取最大度顶点）** 即可获得确定性3-近似，无需复杂的随机化或昂贵的比值计算。这比之前去随机化方法（如van Zuylen & Williamson的方案）**更简单、更快**。

### 2.3 更快计算下界
- **改进最大边不相交开口楔（open wedge）集合的算法**：将时间复杂度从 $O(mn)$ 降至 $O(m^{1.5})$，空间 $O(m)$。利用“一旦发现开口楔则删除其边”的策略，并将三角形探测次数限制在 $O(m^{1.5})$。
- **新的组合方法求解STC LP**：将STC LP归约为**最小s-t割问题**，构造一个仅有 $2m+2$ 个节点、$2m+2|W|$ 条边的流网络。这使得可以用高效的流算法（如近线性时间最大流算法）求解，避免了通用LP求解器的内存和速度瓶颈。

### 2.4 整体算法流程
- **MatchFlipPivot（MFP）**：① 找最大边不相交开口楔集合 $W$；② 将 $W$ 中楔的两边标记为弱边 $E_W$；③ 在 $\hat{G} = (V, E \setminus E_W)$ 上运行Pivot（使用最大度策略）。
- **STC-LP-Round**：① 解STC LP得到半整数解 $x_{ij} \in \{0,1/2,1\}$；② 设置弱边 $E_W = \{(i,j): x_{ij} \ge 1/2\}$；③ 在 $\hat{G} = (V, E \setminus E_W)$ 上运行Pivot（使用最大度策略）。

## 3. 实验设计

- **数据集**：
  - 大规模图来自**SNAP Repository**，包括社交网络、道路网络、引文网络、合作网络、网页图等，最大的图（com-Orkut）有1.17亿条边。
  - **Facebook100**数据集（Traud et al., 2012）的一部分（46个较小的图，最大约35万边）。
  - 其他小图来自**Suitesparse矩阵集合**（如Netscience、polblogs等）。
- **Benchmark与对比方法**：
  - **MatchFlipPivot变种**：随机化（RanMFP-100，运行100次取最佳）、基于度的确定性策略（DegMFP）、基于比值的最小化策略（RatMFP，van Zuylen & Williamson的去随机化）。
  - **STC LP舍入算法**：分别用**Gurobi LP求解器**（Gurobi-LP）和**组合最小割方法**（Comb-LP）求解STC LP，再执行Pivot。
  - 比较指标：**近似比**（实际删除边数/下界）、**运行时间**、**可扩展性**（能处理的图大小）。
- **实验环境**：配备16GB RAM的笔记本电脑，使用Julia实现。

## 4. 资源与算力

- 论文**未明确说明使用GPU**，所有实验均在**一台笔记本电脑（16GB RAM）** 上完成。
- 未报告具体的CPU型号、核心数或训练时长（对于LP求解，有运行时间记录，但没有像深度学习那样的多GPU训练设置）。
- 因此，可以认为资源要求较低，属于轻量级运算。

## 5. 实验数量与充分性

- **对比实验数量较多**：
  - 对大图（SNAP）中约34个图进行了MFP变种和STC LP求解器的全面对比，记录了下界、上界、时间等（表2）。
  - 对Facebook100的46个图展示了DegMFP和融合启发式的效果（图4）。
  - 对12个小图展示了融合合并启发式后的近似比改善（表1）。
- **可重复性**：提供了开源代码链接。
- **公平性**：与现有最好近似算法（随机MFP、Gurobi LP等）对比，考虑了运行时间和近似质量；为降低随机性影响，RanMFP-100取100次最佳。
- **充分性**：覆盖了不同规模（几十到几百万节点）、不同密度、不同类型的图，实验设计合理，能验证算法的普适性和优势。但**消融实验**（如仅对比不同pivot策略）较为充分，而**对LP舍入算法不同策略的消融不够**（例如未对比不同舍入阈值）。
- **局限性**：STC LP的Gurobi求解器因内存限制仅能处理6个图，而组合方法处理21个图，对比数据量稍有不对称，但已足以说明扩展性优势。

## 6. 主要结论与发现

1. **近似比改进**：MatchFlipPivot和STC LP舍入算法的近似比均可出从4提升到3，且分析是紧的（对于MFP存在渐近3的实例）。
2. **简单有效的去随机化**：基于最大度的Pivot策略（DegMFP）在速度和近似质量上与复杂的比值最小化策略（RatMFP）相当，但快一个数量级以上，且优于随机化策略的平均结果。
3. **更快下界计算**：新的最大边不相交开口楔算法和组合STC LP求解器显著加速了算法的瓶颈步骤。组合LP求解器比Gurobi LP快约2倍（小图），并能处理大一个数量级的图。
4. **实践性能**：MFP在许多图上近似比接近2，且DegMFP甚至能达到接近2的近似比，而随机化策略在某些情况下表现更差。合并启发式可进一步改善结果。
5. **可扩展性**：组合LP求解器可处理百万节点、数亿边的图，而通用LP求解器无法处理这些规模。

## 7. 优点

- **理论贡献**：将两个算法的近似比从4严格改进到3，并给出紧例，分析干净、有力。
- **算法简洁**：基于最大度的确定性pivot策略极其简单，易于实现且无需复杂数据结构，在理论和实践上均高效。
- **大规模可扩展**：组合最小割方法避开了通用LP求解器的内存瓶颈，使STC LP舍入算法能应用于此前不可行的图规模。
- **实证充分**：在多种类型和规模的图上进行了对比，结果令人信服。
- **开源复现**：代码公开，便于后续研究。

## 8. 不足与局限

- **近似比仍有差距**：当前已知最佳近似比为2（基于经典LP），本文未达到此下限。作者指出对STC LP舍入算法的分析可能不紧（3可能不是最优），但未给出进一步改进。
- **LP舍入方案较为朴素**：对半整数解中 $x_{ij}=1$ 和 $x_{ij}=1/2$ 的边一视同仁地删除，未充分挖掘LP信息，导致实际近似比有时不如MFP。论文也承认需要更好的舍入策略。
- **合并启发式实验规模有限**：合并步骤扫描所有簇对，时间复杂度高，论文仅在小图上演示，未在大图上有效实施。
- **STC LP的优化**：组合LP求解器虽然快，但调用的是通用流算法（push-relabel），未针对图结构优化；更高效的流算法可能进一步提升。
- **缺失部分消融**：未系统研究不同下界（MFP下界 vs STC LP下界）对最终结果的影响，也未分析STC LP解法唯一性问题（不同最优解可能产生不同结果，Gurobi和组合解法有时结果有差异）。
- **实验设备限制**：所有实验在单台笔记本电脑上运行，未测试更大内存/多核环境下的性能；对于超大规模图（如数十亿边），组合LP求解器仍可能面临内存压力。

（完）
