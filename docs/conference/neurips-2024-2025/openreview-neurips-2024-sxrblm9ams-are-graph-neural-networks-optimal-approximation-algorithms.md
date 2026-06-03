---
title: Are Graph Neural Networks Optimal Approximation Algorithms?
title_zh: 图神经网络是最优近似算法吗？
authors: "Morris Yau, Nikolaos Karalias, Eric Hanqing Lu, Jessica Xu, Stefanie Jegelka"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=SxRblm9aMs"
tags: ["query:graph-part"]
score: 6.0
evidence: 通过图神经网络解决Max-Cut等图划分问题
tldr: 本文设计图神经网络架构OptGNN，利用半定规划工具捕获组合优化问题的最优近似算法，包括Max-Cut、Min-Vertex-Cover等图划分问题。理论上证明了消息传递算法可表示最强大的多项式时间算法，实验在真实和合成数据上取得强结果。虽然不直接使用强化学习，但为解决图划分问题提供了新的神经网络方法。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-sxrblm9ams/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 836, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-sxrblm9ams/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1281, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-sxrblm9ams/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1268, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-sxrblm9ams/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 711, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-sxrblm9ams/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 657, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-sxrblm9ams/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 880, \"height\": 1717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-sxrblm9ams/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 875, \"height\": 1720, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1024, \"height\": 472, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1407, \"height\": 435, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1465, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1045, \"height\": 973, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1190, \"height\": 965, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 538, \"height\": 554, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 585, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 494, \"height\": 514, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1211, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1034, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 537, \"height\": 515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-sxrblm9ams/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1273, \"height\": 848, \"label\": \"Table\"}]"
motivation: 探索图神经网络能否表示组合优化问题的最优近似算法。
method: 基于半定规划构造OptGNN架构，将最优近似算法参数化为消息传递网络。
result: 在Max-Cut等图划分问题上取得高质量近似解，实验优于基线。
conclusion: 图神经网络可以捕获强大的近似算法，为图划分提供新工具。
---

## Abstract
In this work we design graph neural network architectures that capture optimal
approximation algorithms for a large class of combinatorial optimization problems,
using powerful algorithmic tools from semidefinite programming (SDP). Concretely, we prove that polynomial-sized message-passing algorithms can represent
the most powerful polynomial time algorithms for Max Constraint Satisfaction
Problems assuming the Unique Games Conjecture. We leverage this result to
construct efficient graph neural network architectures, OptGNN, that obtain high quality approximate solutions on landmark combinatorial optimization problems
such as Max-Cut, Min-Vertex-Cover, and Max-3-SAT. Our approach achieves
strong empirical results across a wide range of real-world and synthetic datasets
against solvers and neural baselines. Finally, we take advantage of OptGNN’s
ability to capture convex relaxations to design an algorithm for producing bounds
on the optimal solution from the learned embeddings of OptGNN.

---

## 论文详细总结（自动生成）

# 论文总结：Are Graph Neural Networks Optimal Approximation Algorithms?

## 1. 论文的核心问题与整体含义
- **研究动机**：组合优化（CO）问题普遍NP-hard，但实际实例存在可以利用的结构。图神经网络（GNN）有望学习这些结构，但现有方法通常在效率与最优性之间权衡，缺乏最坏情况下的近似保证。
- **核心问题**：是否存在一种GNN架构，既能适应数据分布，又能捕获具有最优最坏情况近似比的算法？
- **整体含义**：论文证明，利用半定规划（SDP）工具，可以构造消息传递GNN（OptGNN），使其在Unique Games Conjecture（UGC）下，对于最大约束满足问题（Max-CSP）类实现最优的近似算法。该工作桥接了理论近似算法与神经组合优化，提供了同时具备理论保证和数据适应性的新范式。

## 2. 方法论
- **核心思想**：将UGC最优SDP的求解过程（投影梯度下降）参数化为一种可以在约束图上执行的消息传递算法，并用可学习的GNN层来模拟这一过程。
- **关键技术细节**：
  - 将SDP的二次惩罚拉格朗日函数Lρ(V)的梯度下降更新，转化为约束图上的消息传递：每个节点根据邻居嵌入的聚合更新自身嵌入。
  - OptGNN层定义：\( v^{t+1}_i = \text{Normalize}(M^t \cdot \text{AGG}(v^t_i, \nabla L_\rho(v^t_i))) \)，其中AGG为聚合函数（拼接当前嵌入和梯度），\( M^t \)为可学习矩阵。
  - 针对不同问题（Max-Cut、Min-Vertex-Cover、Max-3-SAT）给出具体的损失函数和消息形式。
  - 证明OptGNN可以表示UGC最优消息传递算法（Theorem 3.1），并且是PAC可学习的（Lemma 3.1）。
  - 利用学习到的嵌入可构造对偶证书，提供最优解的下界。

## 3. 实验设计
- **任务**：Maximum Cut（Max-Cut）、Minimum Vertex Cover（Min-Vertex-Cover）、Maximum 3-SAT（Max-3-SAT）。
- **数据集**：
  - 合成图：Erdos-Rényi (ER)、Barabási-Albert (BA)、Holme-Kim (HK)、Watts-Strogatz (WC)、forced RB（RB200/RB500）。
  - 真实图：TU-small（ENZYMES, PROTEINS, MUTAG, IMDB-BINARY, COLLAB）、TU-REDDIT（REDDIT-BINARY, REDDIT-M-5K, REDDIT-M-12K）。
  - 基准：GSET Max-Cut实例。
- **对比方法**：
  - 经典算法：Greedy、Gurobi（不同时间限制）、WalkSAT、Survey Propagation、SDP求解器。
  - 神经基线：ErdosGNN、ANYCSP、ECO-DQN、ECORD、GAT、GCNN、GIN、GatedGCNN、Low-rank SDP、Autograd SDP。
- **评价指标**：平均目标值（切边数、覆盖大小、未满足子句数），近似比，标准差，运行时间。

## 4. 资源与算力
- **硬件**：
  - 训练：20 核 Intel Xeon Gold 6248 CPU（数据加载与图生成） + 1 块 NVIDIA Tesla V100 GPU。
  - Gurobi 求解：8 线程 Intel Xeon Platinum 8260。
  - 其他基线：Intel Core i9-13900H + RTX 4060。
- **训练细节**：优化器为 Adam（学习率 0.001）；训练步数因数据集不同从 20k 到 200k；批大小 16 或 32；嵌入维度（rank）从 4 到 64；层数 8 或 16；随机运行次数 2~8 次。
- **总耗时**：未明确给出总GPU小时数，但每个实验在V100上数小时量级。

## 5. 实验数量与充分性
- **实验组数**：大量实验，覆盖三个问题、多个数据集（合成+真实）、多种超参数组合、多种基线。
- **消融实验**：对比不同GNN架构（GAT, GCNN, GIN, GatedGCNN）在相同损失下的表现，验证OptGNN架构优势。
- **超参数分析**：系统考察层数、隐藏维度、位置编码对性能的影响。
- **分布外（OOD）测试**：在一个数据集上训练，在其他数据集上测试，验证泛化能力。
- **证书实验**：在小图上对比OptGNN证书与SDP证书的紧度与速度。
- **充分性与公平性**：实验设计较全面，报告了平均值和标准差；对比了最先进的经典和神经基线；但在Max-3-SAT上未与更强大的局部搜索+后处理组合比较；GSET结果未超过ANYCSP（当前SOTA）。

## 6. 论文的主要结论与发现
- **理论贡献**：OptGNN 可以表示 UGC 最优的 Max-CSP 消息传递算法，且多项式大小即可达到 ϵ-近似解；OptGNN 是 PAC 可学习的。
- **实证表现**：
  - Max-Cut：OptGNN 显著优于贪心算法，与 Gurobi 短时间限制（0.1s~1s）相当或略低，在 GSET 上优于 SDP 和多数神经基线，但略逊于 ANYCSP。
  - Min-Vertex-Cover：OptGNN 匹配 Gurobi 0.5s 的表现，优于所有无监督神经基线，近似比接近 1.0。
  - Max-3-SAT：OptGNN 优于 ErdosGNN 和自动梯度 SDP，但不及 WalkSAT 和 Survey Propagation。
- **证书**：OptGNN 可快速生成紧度接近 SDP 证书的界，且速度快几十倍。
- **OOD 泛化**：模型在不同数据集间表现稳定，证明学到的是通用算法模式而非过拟合。

## 7. 优点
- **理论与实践的桥梁**：首次证明 GNN 可以捕获 UGC 最优近似算法，同时通过参数化适应数据分布。
- **无监督训练**：仅需问题实例，无需标签或执行跟踪。
- **统一的架构**：同一 OptGNN 框架可处理多种组合优化问题，只需更换损失函数。
- **可证明的证书**：从嵌入中提取对偶下界，提供解的置信度。
- **实验设计扎实**：涵盖多种数据集、基线，并进行了全面的消融和超参数分析。

## 8. 不足与局限
- **性能差距**：在 Max-3-SAT 和 GSET Max-Cut 上未达到当前最佳神经方法（ANYCSP）或传统局部搜索（WalkSAT）。
- **理论假设**：依赖 Unique Games Conjecture，其真实性尚未证明；且理论最优性仅针对最坏情况，实际性能可能受分布影响。
- **扩展性**：实验图最大约 2000 节点（REDDIT），未测试更大规模（如数万节点）的可扩展性；消息传递复杂度随约束图大小增长。
- **超参数敏感性**：嵌入维度、惩罚系数 ρ 等需要调参，缺少自动选择策略。
- **证书紧度**：虽然快，但紧度不如直接求解 SDP，尤其当 OptGNN 解非最优时证书可能不紧。
- **后处理缺失**：未结合局部搜索等后处理步骤以提升最终解质量（如 Max-3-SAT 可显著受益于 WalkSAT 后处理）。

（完）
