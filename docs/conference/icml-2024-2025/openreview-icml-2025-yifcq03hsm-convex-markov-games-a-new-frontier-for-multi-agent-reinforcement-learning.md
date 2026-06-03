---
title: "Convex Markov Games: A New Frontier for Multi-Agent Reinforcement Learning"
title_zh: 凸马尔可夫博弈：多智能体强化学习的新前沿
authors: "Ian Gemp, Andreas Alexander Haupt, Luke Marris, Siqi Liu, Georgios Piliouras"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=yIfCq03hsM"
tags: ["query:graph-part"]
score: 9.0
evidence: 凸马尔可夫博弈用于多智能体强化学习
tldr: 本文引入凸马尔可夫博弈类，允许在序贯决策中表达多样化的凸偏好（如多样性、公平性），并证明纯策略纳什均衡存在性。通过可剥削性的上界梯度下降逼近均衡，实验展示了在重复博弈、公平性和安全性任务中的新解。该工作拓展了多智能体强化学习的理论边界。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-yifcq03hsm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1653, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yifcq03hsm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 206, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yifcq03hsm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1762, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yifcq03hsm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1296, \"height\": 162, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yifcq03hsm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 270, \"height\": 151, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-yifcq03hsm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yifcq03hsm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 646, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yifcq03hsm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 783, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yifcq03hsm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 819, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yifcq03hsm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1166, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-yifcq03hsm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 381, \"height\": 151, \"label\": \"Table\"}]"
motivation: 现有马尔可夫博弈无法处理非累加时间偏好的偏好。
method: 定义凸马尔可夫博弈，梯度下降逼近均衡。
result: 在多种任务中实现公平和安全的方案。
conclusion: 为多智能体强化学习提供了新的理论框架。
---

## Abstract
Behavioral diversity, expert imitation, fairness, safety goals and others give rise to preferences in sequential decision making domains that do not decompose additively across time. We introduce the class of convex Markov games that allow general convex preferences over occupancy measures. Despite infinite time horizon and strictly higher generality than Markov games, pure strategy Nash equilibria exist. Furthermore, equilibria can be approximated empirically by performing gradient descent on an upper bound of exploitability. Our experiments reveal novel solutions to classic repeated normal-form games, find fair solutions in a repeated asymmetric coordination game, and prioritize safe long-term behavior in a robot warehouse environment. In the prisoner's dilemma, our algorithm leverages transient imitation to find a policy profile that deviates from observed human play only slightly, yet achieves higher per-player utility while also being three orders of magnitude less exploitable.

---

## 论文详细总结（自动生成）

# 凸马尔可夫博弈：多智能体强化学习的新前沿 — 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的多智能体强化学习（MARL）框架——马尔可夫博弈（Markov Game，MG）只支持线性可加的时间累加奖励函数，无法表达诸如行为多样性、专家模仿、公平性、安全性等非时间可加性的偏好。
- **背景**：单智能体领域已发展出凸马尔可夫决策过程（convex MDP, cMDP）来建模此类凸偏好，但在多智能体领域缺乏正式定义与理论分析。本文旨在填补这一空白，定义凸马尔可夫博弈（convex Markov Game, cMG），并证明纯策略纳什均衡的存在性，提出实用的均衡计算方法。
- **整体含义**：cMG 丰富了 MARL 的建模能力，允许在多个智能体的序贯决策中直接纳入多种复杂的凸目标，为创造性、模仿、公平、安全等现实需求提供了统一的理论框架与算法工具。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将每个智能体的偏好定义为其在长期占有测度（occupancy measure）上的凸函数（或凹效用函数）。这突破了传统 MG 中线性奖励函数的局限，使得更丰富的目标（如熵、KL散度、安全惩罚）可直接表达。
- **关键技术细节**：
  - **定义**：cMG 由状态空间、动作空间、转移核、折扣因子、初始分布以及每个智能体关于自身占有测度和他人策略的连续凹效用函数组成。智能体选择平稳策略，诱导出状态-动作占有测度。
  - **均衡存在性**：通过拓扑论证（利用最佳响应集合的可缩性, contractibility）证明了纯策略纳什均衡的存在，避免了传统 Kakutani 不动点定理对凸性的要求。
  - **均衡计算**：提出可微的上界损失函数 \( L_\tau(\pi) = \sum_i \| \Pi_{T_{U_i}} (\nabla_i^\tau \mu_i) \|^2 \)，其中 \(\Pi_{T_{U_i}}\) 是到可行集切空间的投影算子，\(\nabla_i^\tau \mu_i\) 是加熵正则化的梯度。该损失是 exploitability 的上界。通过梯度下降（如 Adam）最小化该损失，并随着训练逐步退火熵正则化温度 \(\tau\)（同伦策略），得到近似均衡。算法称为 PGL（Projected-Gradient Loss minimization）。
- **算法流程**：初始化策略 \(\pi\)，按温度计划 \(\tau_t\) 循环执行：计算损失 \(L_{\tau_t}\) 关于策略的梯度，用优化器（如 Adam）更新策略，退火温度。输出最终策略。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **实验场景**（共 7 个域）：
  1. **多智能体寻路**：两个机器人协作通过瓶颈门到达目标，奖励到达 +100，其他 -0.01。
  2. **重复囚徒困境（IPD）**：博弈状态为上一步联合行动，奖励经归一化处理。
  3. **重复公共物品博弈（IPGG）**：三个玩家选择是否全部贡献。
  4. **El Farol 酒吧问题**：三个玩家选择去酒吧或在家。
  5. **巴赫-斯特拉文斯基协调博弈**：两位玩家偏好不同但需协调。
  6. **合成安全域**：2 状态 2 行动，定义安全的占有测度区域（凸损失为零）。
  7. **机器人仓库**：2 个机器人在 4 状态网格中取放包裹，安全惩罚限制在“pickup”状态下的快动作频率。
- **基准算法与对比方法**：
  - **min ϵ**：直接通过可微凸优化库 CVXPYLAYERS 最小化 exploitability（不稳定，常崩溃）。
  - **Sim（同时梯度下降）**：所有玩家同时对各自策略做梯度上升，报告轨迹平均。
  - **RR（轮流梯度下降）**：玩家轮流执行梯度步。
  - **SGAMESOLVER**：基于同伦方法的马尔可夫博弈求解器。
  - **本文方法 PGL**：最小化投影梯度损失并退火温度。
- **性能指标**：exploitability（可剥削性）、策略特性（对称性、互惠性、公平性等）、人工模仿相似度。

## 4. 资源与算力

- 文中明确说明：除 **寻路实验** 使用 **1 GPU** 外，所有其他实验均在 **单 CPU** 上运行，每个实验大约需要 **1 分钟** 完成（但标注 exploitability 的 CVXOPT 求解会使时间增加约 10 倍）。
- 未提供 GPU 具体型号、显存、训练总时长等详细配置信息。

## 5. 实验数量与充分性

- **实验数量**：共 7 个不同域，涵盖创造力（4 个迭代博弈 + 寻路）、模仿、公平、安全。在巴赫-斯特拉文斯基实验中做了 10 次随机重复。寻路实验做了单次展示。
- **充分性**：横向对比了 4 种基线方法，观察了 exploitability 收敛曲线、策略概率表、动作重放等。实验覆盖了论文声称的主要用例（创造力、模仿、公平、安全），具有一定代表性。
- **客观性/公平性**：超参数统一列出；学习率和退火计划按域调优。基线设置合理（均使用相同策略表示），但某些基线（min ϵ）因数值问题几乎完全失败，对比可能偏向 PGL。整体而言，实验较为充分，但在更大规模、更复杂环境（如多智能体粒子环境、星际争霸等）上的验证缺失。

## 6. 论文的主要结论与发现

- **理论贡献**：cMG 中纯策略纳什均衡存在，推广了传统马尔可夫博弈。
- **算法贡献**：PGL 损失可微，通过梯度下降+退火可找到低 exploitability 的近似均衡。
- **实际发现**：
  - 在 IPD 中，PGL 找到的近似均衡策略与“以牙还牙”（tit-for-tat）高度相似，具有互惠性，高于经典“背叛”均衡的效用。
  - 在 IPGG 中，PGL 发现互惠捐款策略，而其他方法只得到零捐款。
  - 在模仿实验中，通过 KL 正则化得到与人类数据相近但更接近均衡、可剥削性低三个数量级的策略。
  - 在公平性实验中，在巴赫-斯特拉文斯基中实现约 60% 偏向自己偏好、但长期出席差异极小的策略。
  - 在安全域中，成功约束了快动作频率，实现了安全的长期行为。

## 7. 优点：方法或实验设计上的亮点

- **理论深度**：率先给出 cMG 的形式化定义与纯策略均衡存在性证明，突破传统对凸最佳响应的依赖。
- **统一框架**：将创造力、模仿、公平、安全等多样化目标纳入同一模型，具有较强的可扩展性。
- **算法实用性**：损失函数可自动微分，现有深度学习框架可直接使用；退火策略借鉴成功的同伦方法，实际效果良好。
- **实验新颖性**：通过 cMG 发现传统方法无法找到的“隐性合作”均衡（如 IPD 的互惠策略），展示了凸偏好对均衡选择的引导作用。
- **透明度**：提供了超参数、退火计划、各域详细配置（包括伪码片段），便于复现。

## 8. 不足与局限

- **收敛性保证缺失**：算法没有提供收敛到全局最优的理论保障，仅凭经验表现良好。
- **模型依赖与集中式**：假设已知转移动力学，算法是集中式的（需要完整模型梯度），不适用于无模型/分散式场景。
- **投影算子有偏**：文中指出投影算子 \(\Pi_{T_{U_i}}\) 的估计难以做到无偏，限制了在随机采样环境中的扩展。
- **可扩展性有限**：实验仅限小规模（2-3 玩家，2-4 状态），未测试大规模状态/动作空间（如现实机器人场景）。
- **计算成本**：准确计算 exploitability 依赖凸优化库（CVXOPT），显著增加运行时间。
- **对比公平性**：基线 min ϵ 多次崩溃，可能削弱对比的说服力。同时，未与最新的深度 MARL 方法（如 MAPPO、VDN 等）比较，因为那些方法无法直接处理凸目标。
- **安全性实验设计简单**：安全惩罚为手工设计的凸函数，其实际部署的鲁棒性和泛化性未讨论。

（完）
