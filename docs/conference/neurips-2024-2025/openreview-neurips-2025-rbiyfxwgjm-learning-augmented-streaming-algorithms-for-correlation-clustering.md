---
title: Learning-Augmented Streaming Algorithms for Correlation Clustering
title_zh: 面向相关性聚类的学习增强流式算法
authors: "Yinhao Dong, Shan Jiang, Shi Li, Pan Peng"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=RBiyFxwGJm"
tags: ["query:graph-part"]
score: 7.0
evidence: 研究相关性聚类，属于图划分问题
tldr: 本文研究相关性聚类的流式算法，该问题要求将图顶点划分为不相交的簇以最小化不一致边数。作者提出了首个学习增强的流式算法，利用距离预测器，在完全图上达到优于3的近似比，同时使用O(n)空间。该方法改进了现有的空间-近似权衡，展示了预测在流式聚类中的有效性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbiyfxwgjm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1431, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbiyfxwgjm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rbiyfxwgjm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1433, \"height\": 338, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbiyfxwgjm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1500, \"height\": 401, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbiyfxwgjm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1199, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbiyfxwgjm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 599, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbiyfxwgjm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1198, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbiyfxwgjm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 936, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rbiyfxwgjm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 896, \"height\": 225, \"label\": \"Table\"}]"
motivation: 解决相关性聚类在流式场景下空间-近似权衡不佳的问题。
method: 利用预测器提供顶点间距离估计，结合现有流式算法框架设计学习增强算法。
result: 在完全图上，预测质量好时达到优于3的近似比，空间复杂度为O(n)。
conclusion: 预测能够显著改进流式相关性聚类的近似性能。
---

## Abstract
We study streaming algorithms for Correlation Clustering. Given a graph as an arbitrary-order stream of edges, with each edge labeled as positive or negative, the goal is to partition the vertices into disjoint clusters, such that the number of disagreements is minimized. In this paper, we give the first learning-augmented streaming algorithms for the problem on both complete and general graphs, improving the best-known space-approximation tradeoffs. Based on the works of Cambus et al. (SODA'24) and Ahn et al. (ICML'15), our algorithms use the predictions of pairwise distances between vertices provided by a predictor. For complete graphs, our algorithm achieves a better-than-$3$ approximation under good prediction quality, while using $\tilde{O}(n)$ total space. For general graphs, our algorithm achieves an $O(\log |E^-|)$ approximation under good prediction quality using $\tilde{O}(n)$ total space, improving the best-known non-learning algorithm in terms of space efficiency. Experimental results on synthetic and real-world datasets demonstrate the superiority of our proposed algorithms over their non-learning counterparts.

---

## 论文详细总结（自动生成）

## 论文《Learning-Augmented Streaming Algorithms for Correlation Clustering》详细中文总结

### 1. 核心问题与整体含义（研究动机和背景）
- **研究问题**：在流式（streaming）场景下求解**相关性聚类（Correlation Clustering）**问题。给定一个边流（每条边带正/负标签），目标是将顶点划分为不相交的簇，使得“正边跨簇”和“负边同簇”的总数（即不一致边数）最小化。
- **背景与动机**：传统流式算法在**空间-近似权衡**上存在瓶颈。例如，完全图上现有动态流算法最好只能达到 (3+ε) 近似；一般图上算法需存储所有负边，空间开销大。作者希望利用**机器学习预测**来突破最坏情况下的折衷，实现**一致性（预测好时近似比更优）与鲁棒性（预测差时不劣于基线）**。

### 2. 论文提出的方法论
#### 核心思想
- 假设算法可以访问一个**预测器**，提供任意两点之间的**距离预测** \(d_{uv} \in [0,1]\)，且满足三角不等式，并用一个参数 \(\beta\) 度量预测质量（\(\beta\) 越小预测越好）。
- 将预测距离作为**近似 LP 解**的替代，结合现有流式算法框架（Truncated Pivot、Pairwise Dissimilarity、球生长等）设计学习增强版本。

#### 关键技术细节
| 场景 | 方法 | 关键技术 |
|------|------|----------|
| **完全图（动态流）** | 同时运行两个 pivot 算法，输出成本较低者 | (1) 用 ℓ0‑sampler 在流中恢复“有趣顶点”的邻接信息；(2) Truncated Pivot 基于随机排列；(3) Truncated Pivot with Pred 以概率 \(1-p_{uv}\) 添加顶点（\(p_{uv}=f(d_{uv})\)，其中 \(f\) 为分段函数）；(4) 用一个 ε‑谱稀疏化器 \(H^+\) 近似聚类成本。 |
| **一般图（动态流）** | 结合球生长与预测距离 | (1) 流中维护 G⁺ 的 ε‑谱稀疏化器 \(H^+\)；(2) 同时存储负边，但若空间超过 \(\tilde{O}(\varepsilon^{-2}n)\) 则停止；(3) 后处理阶段：若负边空间未超限，运行 Ahn et al. (ICML'15) 后处理；否则，以预测距离为度量在 \(H^+\) 上执行球生长（ball‑growing），保证每次切割满足 \(\partial_{H^+}(B) \le 3\ln(n+1)\cdot \text{vol}_{H^+}(B)\)。 |

#### 主要定理
- **完全图**（Theorem 1.3）：给定 β‑级预测器，算法在动态流中期望达到 \((\min\{2.06\beta,\,3\}+\varepsilon)\) 近似，总空间 \(\tilde{O}(\varepsilon^{-2}n)\)。
- **一般图**（Theorem 1.4）：在适应型 β‑级预测器下，达到 \(O(\beta\log|E^-|)\) 近似，总空间 \(\tilde{O}(\varepsilon^{-2}n)\)。

### 3. 实验设计
- **数据集**：
  - **合成数据**：随机块模型 (SBM)，设置不同簇内部正边概率 \(p\)（0.7/0.8/0.9/0.95）和不同顶点数 \(n\)（100–3600）。
  - **真实数据**：Email‑Core、Facebook（三个 ego‑网络：FB0, FB414, FB3980）、LastFM、DBLP（采样 10k 顶点）。
- **预测器**：
  1. **噪声预测器**：基于最优聚类（已知或通过 Gurobi 求解）加入噪声扰动得到。
  2. **谱嵌入**：利用图拉普拉斯嵌入到 \(d\) 维空间，距离定义为 \(1-\cos\langle x_u,x_v\rangle\)。
  3. **二元分类器**：用 MLP 模型预测两点是否同簇，输出 0/1 作为距离。
- **对比方法**：
  - 完全图：CKLPU24（(3+ε) 近似）、CLMNPT21（多遍算法但实践中高质量）、CM23（单遍近似算法）。
  - 一般图：Ahn et al. (ICML'15) 作为基线。
- **评估指标**：聚类成本（不一致边数），多次重复取均值并附误差条。

### 4. 资源与算力
- 论文明确提到：所有实验在 **CPU i7-13700H + 32 GB RAM** 上运行，**未使用 GPU**。
- 训练时间仅以毫秒计（如 Facebook 子图上单次运行 2–1700 ms），未报告大规模持续训练时长。

### 5. 实验数量与充分性
- **实验组数**：包括（1）完全图动态流算法（Algorithm 1）在合成数据上变 β、变 p、变 n；在真实数据上变 β 或变嵌入维度 d；以及二元分类器对比。（2）插入流算法（Algorithm 8）类似实验。（3）消融：不同预测器类型、不同 k 值（队列大小）等。
- **充分性判断**：实验覆盖了多种数据规模、多种预测质量、多种基线，每个条件独立重复 5–20 次并报告误差，结果直观展示了优势。但**未见一般图算法（Algorithm 2）的实验验证**，文中仅提供了理论分析。
- **公平性**：所有基线均用同等努力实现，预测器构造方法公开（如 Gurobi 求解 LP 或标准谱嵌入），不存在明显偏向。

### 6. 主要结论与发现
- **完全图**：当预测质量 \(\beta\) 较小时，学习增强算法成本显著低于非学习基线（例如比 CKLPU24 降低 26%）；即使 \(\beta\) 较大，算法仍保持与 (3+ε) 近似相当的性能，体现了鲁棒性。
- **一般图**：理论上在良好预测下达到 \(O(\beta\log|E^-|)\) 近似，空间需求从 \(O(n+|E^-|)\) 降至 \(\tilde{O}(n)\)。
- **实际可行性**：基于学习到的二元分类器（MLP）的预测力同样有效，在 SBM 和 DBLP 上成本降低 60%–72%。
- **扩展性**：随着图规模增大，算法的近似比优势保持稳定。

### 7. 优点
- **理论创新**：首次将学习增强思想引入流式相关性聚类，提出 β‑级预测器定义，并给出完整的近似比分析。
- **算法设计**：同时满足**一致性**（预测好时优于 3‑近似）和**鲁棒性**（预测差时不差于 3‑近似），且后处理时间多项式。
- **空间效率**：完全图动态流算法空间 \(\tilde{O}(\varepsilon^{-2}n)\)，优于之前需指数后处理时间的 (1+ε) 近似方案。
- **实验验证**：在多种预测器（含学习得到的）上验证了理论的合理性，且代码开源。

### 8. 不足与局限
- **一般图算法的实验缺失**：论文未对 Algorithm 2（一般图动态流）进行任何实验，仅依靠理论保证，缺乏实证可重复性。
- **预测器假设严格**：β‑级预测器要求满足三角不等式且线性组合成本不超过 β·OPT，实际中难以严格保证（尤其对于学习出来的距离）。虽然作者称算法仍可用，但理论保证可能失效。
- **数据环境限制**：实验仅模拟**插入流**，未覆盖**动态流（含删除）**；且所有图视为**完全图**（非边隐式视为负边），真实场景中稀疏图更常见。
- **负边存储的极端情况**：一般图算法中，若负边空间超限，算法转用球生长，但此时只有正边稀疏化器，负边信息丢失，理论近似比依赖于 \(|E^-|\ge n\)，若 \(|E^-|\) 很小则分析失效。
- **算力报告不足**：未提供完整训练预测器（如 MLP）的耗时，仅报告了聚类阶段运行时间。

（完）
