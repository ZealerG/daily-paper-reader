---
title: Learning Mean Field Control on Sparse Graphs
title_zh: 稀疏图上的平均场控制学习
authors: "Christian Fabian, Kai Cui, Heinz Koeppl"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Y34a82DptF"
tags: ["query:graph-part"]
score: 7.0
evidence: 稀疏图上的平均场控制，多智能体RL并行决策
tldr: 多智能体强化学习在大规模稀疏图（如幂律网络）中面临计算和理论挑战。该文提出基于局部弱收敛的平均场控制模型，适用于稀疏图序列，并设计了可扩展学习算法。理论分析和实验表明该模型在合成数据和真实数据上的有效性，为多智能体并行决策在复杂图环境中的应用铺平了道路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-y34a82dptf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1750, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y34a82dptf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 866, \"height\": 259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y34a82dptf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 225, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y34a82dptf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 226, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-y34a82dptf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 857, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y34a82dptf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1759, \"height\": 648, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y34a82dptf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1752, \"height\": 326, \"label\": \"Table\"}]"
motivation: 现有平均场方法仅适用于密集或中等稀疏图，无法处理实际中的稀疏图。
method: 提出基于局部弱收敛的平均场控制模型，并设计可扩展学习算法。
result: 在多种稀疏图示例上验证了模型和算法的有效性。
conclusion: 将平均场控制扩展到稀疏图，拓展了MARL的应用范围。
---

## Abstract
Large agent networks are abundant in applications and nature and pose difficult challenges in the field of multi-agent reinforcement learning (MARL) due to their computational and theoretical complexity. While graphon mean field games and their extensions provide efficient learning algorithms for dense and moderately sparse agent networks, the case of realistic sparser graphs remains largely unsolved. Thus, we propose a novel mean field control model inspired by local weak convergence to include sparse graphs such as power law networks with coefficients above two. Besides a theoretical analysis, we design scalable learning algorithms which apply to the challenging class of graph sequences with finite first moment. We compare our model and algorithms for various examples on synthetic and real world networks with mean field algorithms based on Lp graphons and graphexes. As it turns out, our approach outperforms existing methods in many examples and on various networks due to the special design aiming at an important, but so far hard to solve class of MARL problems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：多智能体强化学习（MARL）在大规模智能体网络上（如社交网络、生物网络、互联网等）面临计算和理论上的巨大挑战。现有平均场方法（如基于图论Graphon的平均场博弈和控制）仅适用于密集或中等稀疏图（平均度趋于无穷），无法处理许多现实世界中存在的**非常稀疏的图**（如幂律指数大于2且均值有限但方差发散的图）。
- **背景**：现实中许多重要网络（如互联网、合著网络、生物网络）具有稀疏性，现有方法（Lp图论、Graphex）要求平均度发散，导致对低度节点占多数的稀疏图近似精度低。局部弱收敛（local weak convergence）是处理此类稀疏图的合适图论收敛框架。
- **意义**：将平均场控制（MFC）扩展到稀疏图，解决了一类此前难以处理的重要MARL问题，为大规模并行决策在复杂图环境中的应用提供了理论基础和实用算法。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：利用**局部弱收敛**（local weak convergence in probability）作为图序列的理论基础，定义一个新的平均场控制模型——**局部弱平均场控制（LWMFC）**。该模型适用于期望平均度有限、方差可以发散的稀疏图序列（如配置模型、偏好依附模型、Chung-Lu图）。
- **关键技术与细节**：
  1. **图序列假设**：假设图序列在概率意义下局部弱收敛到某个随机极限图。
  2. **有限系统与极限系统**：定义有限智能体系统，每个节点的策略依赖于自身状态和其k-邻域分布。定义极限LWMFC系统，其中每个度k的智能体的平均场演化为确定性方程。
  3. **理论结果**：
     - 定理3.1：经验平均场收敛到极限平均场。
     - 命题3.3：目标函数收敛。
     - 推论3.4：最优策略在有限系统中也渐近最优。
  4. **双系统近似**：由于精确极限系统复杂度极高（邻域数量随度指数增长，引理4.1），提出两系统近似：将低度节点（≤ k*）单独处理，高度节点（> k*）统一用一个近似平均场表示。使用Heuristic 1（邻居度分布近似为度加权分布）来估计高度节点的邻域状态。
  5. **另一个更精确的“扩展近似”**（附录B）复杂度更高，仅用于对比。
  6. **学习算法**：
     - **算法1：LWMFC策略梯度**（基于模型的MFC求解）。使用PPO在MFC MDP上学习高层策略，输出每个时刻的低度和高度策略。
     - **算法2：LWMFMARL策略梯度**（无模型，直接与真实网络交互学习）。同样基于PPO，但每一步使用真实网络样本更新MFC MDP状态，避免模型误差。
  7. **策略参数化**：为降低复杂度，策略简化为仅依赖于节点状态的分布（不依赖邻域），即π∈P(U)^X。

## 3. 实验设计
- **数据集/场景**：
  - **合成图**：基于Chung-Lu模型生成不同规模（N=167, 406, 860, 1598）的幂律图（γ>2）。
  - **真实世界网络**：8个KONECT数据集（CAIDA, Cities, Digg, Enron, Flixster, Slashdot, Yahoo, YouTube），节点数从1.4万到3.2M不等，均为稀疏图。
  - **四个控制问题**：
    - SIS（易感-感染-易感）
    - SIR（易感-感染-康复）
    - Graph coloring（图着色）
    - Rumor（谣言传播）
- **Benchmark与对比方法**：
  - 平均场动力学对比：LPGMFG（基于Lp图论）、GXMFG（基于Graphex）、LWMFC（本文双系统近似）、LWMFC*（本文扩展近似，仅部分问题可行）。
  - 学习算法对比：IPPO（独立PPO，标准多智能体基线）、LWMFC（本文基于模型的）、LWMFMARL（本文无模型）。
- **评估指标**：
  - 动力学逼近：平均期望总变差Δμ（表1）。
  - 学习性能：最优目标函数值（表2），训练曲线（图3，图4）。

## 4. 资源与算力
- 文中明确提到：**使用了约80,000核心小时的CPU计算时间**。每次训练通常需要**一天**，最多使用**96个并行CPU核心**。**未使用GPU**。
- 计算平台：TU Darmstadt的Lichtenberg高性能计算集群。

## 5. 实验数量与充分性
- **实验数量**：共进行了多组实验：
  - 动力学逼近实验（表1）：4个问题 × 8个网络 × 4种方法（LPGMFG, GXMFG, LWMFC, LWMFC*），但Color和Rumor问题没有LWMFC*结果（因计算复杂度过高）。每个组合50次试验，报告均值和标准差。
  - 学习算法实验（表2）：4个问题 × 4种图规模 × 3种算法（IPPO, LWMFC, LWMFMARL），24小时训练后最优目标值。
  - 训练曲线展示（图2,3,4）：典型场景。
- **充分性评价**：
  - 动力学对比充分：覆盖多种真实网络和问题，统计量合理。
  - 学习对比有限：仅用了合成图，未在真实网络上对比学习算法（只在表2中训练曲线展示了真实网络结果，但表2本身是合成图）。作者解释LWMFC是基于极限模型评估，LWMFMARL与网络交互，但未在真实网络上系统对比IPPO（表2仅合成图）。
  - 消融实验：有两个近似（LWMFC vs LWMFC*），且独立运行多次。
  - 总体实验设计较为客观，但**真实网络上的学习对比缺失**是一个潜在不足。

## 6. 主要结论与发现
- **动力学精度**：LWMFC在所有真实网络和问题上的平均场近似精度显著优于LPGMFG和GXMFG（总变差低几倍到几十倍）。扩展近似LWMFC*在多数情况下略优于LWMFC，但计算成本高得多。
- **学习性能**：在合成图上，LWMFC和LWMFMARL在较大图上（860, 1598节点）优于IPPO，在较小图上（167, 406）与IPPO竞争力相当或略逊。LWMFMARL作为无模型方法在多数情况下优于LWMFC（因为避免了模型误差）。
- **方法有效性**：提出的LWMFC框架成功将平均场控制扩展到非常稀疏的图（如幂律网络），理论与实验一致。双系统近似在精度和计算复杂度之间取得了良好平衡。

## 7. 优点
- **理论扎实**：严格证明了收敛性、最优性渐近性质，基于局部弱收敛这一数学成熟框架。
- **方法实用**：双系统近似极大降低了复杂度，且在实际网络中表现优秀。
- **算法可扩展**：基于PPO的MFC求解和直接MARL算法均适用于大规模网络，避免了独立学习的指数复杂度。
- **实验验证充分**：在8个不同规模、不同领域的真实网络上测试，结果一致优于现有方法。
- **开源友好**：代码基于MARLlib和RLlib，可复现。

## 8. 不足与局限
- **实验覆盖不足**：
  - 学习算法对比仅在合成图上进行，未在真实网络上与IPPO等基准对比。真实网络的结果仅用于动力学精度比较，弱化了学习算法部分的结论强度。
  - 未进行大规模真实网络上的训练性能比较（可能受限于计算资源）。
- **近似误差**：双系统近似依赖Heuristic 1（邻居度分布近似），在某些图结构（如非Chung-Lu类）可能不准确。扩展近似虽更准但计算不可行。
- **模型假设限制**：假设图序列局部弱收敛，虽覆盖广泛但并非所有实际网络都满足（如动态变化网络）。策略限于有限状态/动作空间，且假设所有同度节点共享策略，可能损失灵活性。
- **应用限制**：问题设计较简单（SIS, SIR等），未涉及更复杂的MARL任务（如部分可观测、异构奖励等）。
- **算力依赖**：CPU密集型训练（80k core hours），对可重复性有一定门槛。

（完）
