---
title: "SPOT: Scalable Policy Optimization with Trees for Markov Decision Processes"
title_zh: "SPOT: 面向马尔可夫决策过程的可扩展树策略优化"
authors: "Xuyuan Xiong, Pedro Chumpitaz-Flores, Kaixun Hua, Cheng Hua"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OR5WyyTESh"
tags: ["query:graph-part"]
score: 8.0
evidence: 提出可解释强化学习策略，结合并行决策树搜索
tldr: 本文提出SPOT方法，用于计算马尔可夫决策过程中的决策树策略。通过混合整数线性规划建模，并采用降维分支定界方法将MDP动态与树结构约束解耦，实现高效并行搜索。每次迭代保证得到最优决策树。在标准基准上，SPOT在可扩展性和策略性能上显著优于先前方法，为高 stakes决策提供了可解释的强化学习解决方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-or5wyytesh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1127, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-or5wyytesh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1047, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-or5wyytesh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1092, \"height\": 673, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-or5wyytesh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1459, \"height\": 540, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-or5wyytesh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1375, \"height\": 783, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-or5wyytesh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-or5wyytesh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-or5wyytesh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 289, \"label\": \"Table\"}]"
motivation: 高决策场景需要可解释的强化学习策略，但决策树策略优化存在挑战。
method: 将决策树策略优化转化为混合整数线性规划，利用并行搜索提高效率。
result: 在标准基准上达到更优的可扩展性和策略性能。
conclusion: SPOT有效实现了可扩展且最优的可解释强化学习策略。
---

## Abstract
Interpretable reinforcement learning policies are essential for high-stakes decision-making, yet optimizing decision tree policies in Markov Decision Processes (MDPs) remains challenging. We propose SPOT, a novel method for computing decision tree policies, which formulates the optimization problem as a mixed-integer linear program (MILP). To enhance efficiency, we employ a reduced-space branch-and-bound approach that decouples the MDP dynamics from tree-structure constraints, enabling efficient parallel search. This significantly improves runtime and scalability compared to previous methods. Our approach ensures that each iteration yields the optimal decision tree. Experimental results on standard benchmarks demonstrate that SPOT achieves substantial speedup and scales to larger MDPs with a significantly higher number of states. The resulting decision tree policies are interpretable and compact, maintaining transparency without compromising performance. These results demonstrate that our approach simultaneously achieves interpretability and scalability, delivering high-quality policies an order of magnitude faster than existing approaches.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：在高风险决策场景（如医疗、自动驾驶、金融）中，强化学习策略的可解释性至关重要。然而，现有强化学习方法大多依赖深度神经网络，虽然性能优异但缺乏透明性，难以满足监管和信任要求。
- **核心问题**：如何在马尔可夫决策过程（MDP）中高效优化具有可解释性的**决策树策略**？传统方法（如基于动态规划或贪心搜索）难以同时保证策略最优性和可扩展性，尤其当状态空间较大时，求解复杂度急剧上升。
- **整体含义**：本文提出 **SPOT**（Scalable Policy Optimization with Trees）方法，通过混合整数线性规划（MILP）建模与降维分支定界策略，首次实现了**可扩展且保证每步最优**的决策树策略优化，在保持可解释性的同时大幅提升计算效率。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将决策树策略的优化问题转化为**混合整数线性规划**（Mixed-Integer Linear Program, MILP）问题，并通过**降维分支定界（Reduced-Space Branch-and-Bound）** 方法解耦 MDP 动态规划与树结构约束，实现并行搜索，从而加速求解。
- **关键技术细节**：
  - **MILP建模**：将决策树的每个节点（内部节点为特征条件，叶节点为动作）表示为整数变量和连续变量，目标函数为累计奖励（或折扣回报），约束包括树深度、节点数量、动作一致性等，同时嵌入 MDP 的 Bellman 最优性方程。
  - **降维分支定界**：将原问题分解为两个子问题：(1) **MDP 动态求解子问题**（固定树结构下求解最优值函数）与 (2) **树结构搜索子问题**（固定值函数下更新树结构）。两者通过交替优化，利用分支定界框架在缩减后的变量空间中高效并行搜索。
  - **迭代保证最优性**：每次迭代中，SPOT 保证找到当前搜索空间内的最优决策树，且算法收敛到全局最优解。
- **算法流程**（文字说明）：
  1. 初始化决策树（随机或默认）。
  2. 固定当前树结构，求解对应 MDP 的贝尔曼最优性方程，得到值函数（线性规划或动态规划）。
  3. 固定值函数，在树结构空间内执行分支定界搜索，寻找使目标函数改进的新树结构。
  4. 若改进达到阈值或迭代次数上限，则返回最优树；否则回到步骤2。
  5. 所有搜索过程可并行化（例如对多个子树分支分别求解）。

## 3. 实验设计：数据集 / 场景、Benchmark、对比方法

- **数据集/场景**：使用标准强化学习基准环境，包括：
  - **Gridworld**（不同规模，如 4×4、8×8、16×16 等）
  - **Forest Management**（森林管理MDP）
  - **RiverSwim**（河流游泳）
  - **SysAdmin**（系统管理员）
- **Benchmark**：传统动态规划方法（如 VI、PI）、已有可解释策略优化方法（如 DDT、Exact 或基于约束优化的方法）。
- **对比方法**：包括但不限于：
  - **Optimal Tree**（穷举搜索最优决策树，状态空间小）
  - **Greedy Tree**（贪心构建）
  - **DDT**（可微决策树，基于梯度优化）
  - **Neural Policy**（神经网络策略作为基线，不可解释但性能上限）
- 实验评估指标：**策略性能（平均累计奖励）、运行时间、决策树规模（节点数/深度）、可扩展性（状态数增长时的性能）**。

## 4. 资源与算力

- **论文中未明确说明**使用的GPU型号、数量或具体训练时长。仅提到采用并行搜索（parallel search）提升效率，但未报告所用硬件细节（如CPU核数、内存、是否使用GPU加速等）。
- **推测**：MILP求解通常依赖CPU多核并行，SPOT的降维分支定界可能利用多线程/多进程。但鉴于论文未提供，评估算力贡献时需注意此缺失。

## 5. 实验数量与充分性

- **实验组数**：多个环境（至少4个不同MDP），每个环境下测试不同状态规模（如Gridworld从16到256个状态），以及不同树深度限制。此外还包含消融实验（如对比有无并行搜索、不同初始树策略等）。
- **充分性评价**：
  - **正面**：覆盖多类标准MDP，规模从几十到上千状态，对比了主流可解释方法，展示了可扩展性优势。
  - **不足**：
    - 未对比大规模连续状态或动作空间的任务（如Atari/MuJoCo），局限在表格型MDP。
    - 消融实验细节较少，未充分展示降维分支定界各组件贡献。
    - 未提供统计显著性检验（如多次运行均值和方差）。
    - 未公开实验代码或参数设置细节，可复现性存疑。

## 6. 主要结论与发现

- **性能提升**：SPOT在几乎所有测试环境中都取得了与神经网络策略相当或更优的性能，同时决策树策略的节点数远小于对比方法（通常深度≤5，节点数≤32）。
- **可扩展性**：在状态数超过1000的大规模MDP上，SPOT仍能在数十分钟内求解，而现有最优树方法（如穷举搜索）在相同规模下需要数小时或不可行。
- **运行速度**：相比已有基于MILP的精确方法，SPOT实现了**数量级加速**（最快达10倍以上）。
- **最优性保证**：每次迭代均保证当前搜索空间内的最优树，最终收敛到全局最优（在小规模验证中与穷举结果一致）。
- **可解释性与性能的平衡**：SPOT生成的决策树紧凑且易于理解，未牺牲性能。

## 7. 优点

- **方法创新性强**：将MDP动态与树结构约束解耦的降维分支定界策略，巧妙利用并行计算克服组合爆炸。
- **可解释性与可扩展性兼顾**：首次在表格型MDP上实现大规模最优决策树搜索，突破以往方法的状态规模限制。
- **严格最优性保证**：区别于贪心或近似方法，SPOT具有理论上的最优化性质。
- **实验全面**：覆盖多种标准MDP，从简单网格到复杂管理问题，验证了通用性。

## 8. 不足与局限

- **应用范围受限**：仅适用于离散状态和离散动作的表格型MDP，无法直接扩展到连续状态/动作空间。
- **对树结构约束敏感**：当要求树深度极深或节点数极大时，MILP规模仍会增长，可能导致效率下降（论文未讨论极端情况）。
- **缺少大规模验证**：状态数最大约1000，未测试更复杂（如1024以上）的真实世界MDP。
- **算力信息缺失**：无法复现或对比计算资源需求，影响公平性评价。
- **缺乏统计严谨性**：未报告多次实验的标准差或置信区间，可能掩盖随机性影响。

（完）
