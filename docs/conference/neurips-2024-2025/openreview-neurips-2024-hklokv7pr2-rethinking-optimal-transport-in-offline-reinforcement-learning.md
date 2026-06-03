---
title: Rethinking Optimal Transport in Offline Reinforcement Learning
title_zh: 重新思考离线强化学习中的最优传输
authors: "Arip Asadulaev, Rostislav Korst, Alexander Korotin, Vage Egiazarian, Andrey Filchenkov, Evgeny Burnaev"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=hKloKv7pR2"
tags: ["query:graph-part"]
score: 8.0
evidence: 提出使用最优传输的新型离线强化学习算法
tldr: 本文重新思考离线强化学习，将其建模为最优传输问题，旨在从多专家数据中拼接最佳行为。提出将状态映射到最佳专家动作的部分分布的策略。在D4RL连续控制任务上，该方法优于现有方法，展示了最优传输在离线RL中拼接行为的有效性。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-hklokv7pr2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1417, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hklokv7pr2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1427, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hklokv7pr2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1375, \"height\": 853, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-hklokv7pr2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 397, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hklokv7pr2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1493, \"height\": 371, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hklokv7pr2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1476, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hklokv7pr2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1459, \"height\": 636, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hklokv7pr2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 824, \"height\": 462, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hklokv7pr2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 917, \"height\": 503, \"label\": \"Table\"}]"
motivation: 离线RL数据来自多种专家，需要拼接最佳行为以提取高效策略。
method: 将离线RL视为最优传输问题，学习状态到最佳专家动作部分分布的映射。
result: 在D4RL连续控制基准上超越现有方法。
conclusion: 最优传输框架有效解决了离线RL中的行为拼接问题。
---

## Abstract
We propose a novel algorithm for offline reinforcement learning using optimal transport. Typically, in offline reinforcement learning, the data is provided by various experts and some of them can be sub-optimal. To extract an efficient policy, it is necessary to \emph{stitch} the best behaviors from the dataset. To address this problem, we rethink offline reinforcement learning as an optimal transportation problem. And based on this, we present an algorithm that aims to find a policy that maps states to a \emph{partial} distribution of the best expert actions for each given state. We evaluate the performance of our algorithm on continuous control problems from the D4RL suite and demonstrate improvements over existing methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
离线强化学习（Offline RL）面临的核心挑战是：训练数据通常由多个专家收集，其中包含次优甚至错误的轨迹。传统方法（如行为克隆）会不加区分地模仿整个数据集的行为，从而限制了策略提升。为此，论文提出**重新思考离线强化学习问题**，将其建模为一个**最优传输（Optimal Transport, OT）问题**，旨在从多专家数据中“拼接（stitch）”出最佳行为：即对于每个状态，从数据中选出最优动作，而非克隆整体分布。作者基于部分最优传输（Partial OT）理论，提出了**部分策略学习（Partial Policy Learning, PPL）** 算法，能够将状态映射到专家动作分布的**最优部分**，从而在避免分布偏移的同时实现策略改进。

## 2. 论文提出的方法论
### 核心思想
将离线RL视为一个**状态分布到动作分布的最优传输问题**，其中：
- **传输成本**：负Q函数（-Q(s,a)）
- **传输映射**：策略 π(s)
- **目标**：找到π，使得π将状态分布推送到专家动作分布β(·|s)中**成本最小**的部分，而非全部。

### 关键技术细节
- **部分最优传输的约束**：改用不等式约束 `π♯d(s) ≤ w·β(·|s)`，其中w≥1控制映射的目标分布质量比例。当w越大，允许忽略越多的次优动作。
- **最大化-极小化（Maximin）优化**：利用对偶形式和Rockafellar交换定理，将原问题转化为无约束的max-min问题：
  ```
  max_{f≥0} min_π  E_{s∼D, a∼π(s)}[ -Q(s,a) - f(s,a) ] + w·E_{(s,a)∼D}[f(s,a)]
  ```
  其中f(s,a)是一个非负的拉格朗日乘子函数，用于惩罚次优动作。
- **算法流程（Algorithm 1 Partial Policy Learning）**：
  1. 从离线数据集D采样一批样本。
  2. 更新Q函数（使用标准贝尔曼误差，或结合保守更新避免过估计）。
  3. 更新f：最大化 `-E[f(s,π(s))] + w·E[f(s,a)]`。
  4. 更新策略π：最小化 `E[-Q(s,π(s)) - f(s,π(s))]`。
  5. 重复步骤1-4。

**关键区别**：不同于以往将OT作为额外正则化项的方法（如W-BRAC），本文**整个策略优化过程就是OT求解**，且f不需要满足1-Lipschitz条件，仅需非负。

## 3. 实验设计
### 数据集与场景
使用 **D4RL** 基准套件，涵盖三类环境：
- **MuJoCo**（连续控制）：HalfCheetah、Hopper、Walker2D，每种包含Medium、Medium-Replay、Medium-Expert三种数据。
- **AntMaze**（稀疏奖励导航）：umaze、umaze-diverse、medium-play、medium-diverse、large-play、large-diverse。
- **Adroit**（灵巧操作）：Pen、Door、Hammer、Relocate，每种含Human、Cloned、Expert数据。

### Benchmark与对比方法
- **Baselines**：BC、One-Step RL、CQL、IQL、OTR+IQL、TD3+BC、ReBRAC。
- **PPL的三种变体**：
  - **PPL**（基于One-Step RL设置，预训练Qβ，然后优化π）。
  - **PPL CQL**（将PPL与CQL结合，使用CQL的Q函数）。
  - **PPL R**（与ReBRAC结合，使用TD3+BC目标作为成本函数）。

### 实验设置
- 每个实验使用**5个随机种子**，报告最终100次评估（AntMaze）或10次评估（MuJoCo/Adroit）的均值±标准差。
- 超参数：除w外，其余与对应backbone（CQL、ReBRAC）保持一致。
- PPL训练：One-Step设置中先预训练β 500k步、Qβ 2M步，再优化π 100k步；其余直接从头训练1M步。

## 4. 资源与算力
- **GPU**：Nvidia 1080（12GB）单卡。
- **训练时间**：每个任务收敛需2-3小时。
- **框架**：PyTorch和JAX。
- **文中未明确说明使用的GPU数量**，推测为单卡。

## 5. 实验数量与充分性
- **实验数量**：
  - MuJoCo：3个环境 × 3种数据 = 9个任务。
  - AntMaze：6个任务。
  - Adroit：4个环境 × 3种数据 = 12个任务（但部分数据结果未全报告，如OTR+IQL缺失几项）。
  - 消融实验：对参数w在AntMaze上测试了4个值（3,5,8,12）。
  - 总计约30+个任务比较，涵盖多数主流离线RL场景。
- **充分性与公平性**：
  - 采用与baseline相同的网络架构、优化器、训练步数（PPL R保持ReBRAC原超参数）。
  - 报告了多次重复的结果，附带标准差。
  - **不足之处**：部分baseline结果（如OTR+IQL）在Adroit上未完全报告（见表3中“-”）；PPL未与IQL直接结合，而是只与CQL和ReBRAC结合，可能缺失直接对标IQL+OTR的公平性。此外，w的选取未自适应，对每个任务手动选择最优值，可能引入额外优势。

## 6. 论文的主要结论与发现
- **PPL显著优于其基于的baseline**：在AntMaze上，PPL R总得分520，比原始ReBRAC（461.2）高约60分；在large-play/diverse任务上分别提升16.4和22.2分。
- **在MuJoCo上略有提升**：PPL R总分799.45，略高于ReBRAC的796.9；在Hopper、Walker等任务上进步较明显。
- **在Adroit上也有改善**：总分711.44，对比ReBRAC的703.2。
- **参数w的作用**：w控制选择最佳动作的激进程度，需要在不同任务上调参。在复杂任务（如large-play）中，较高的w（8-12）效果更好，表明需要更聚焦于最优动作。
- **理论保证**：证明了当w→∞时，PPL近似于选取支持集上的最优动作，且能保证策略改进（优于行为策略）。

## 7. 优点
1. **视角创新**：将离线RL整体视为OT问题，而非仅作为正则项，为利用OT理论解决RL问题提供了新范式。
2. **方法简洁有效**：PPL算法无需复杂约束（如1-Lipschitz），可直接与现有RL算法（CQL、ReBRAC）融合，提升效果。
3. **清晰的理论支撑**：给出了策略改进的证明（命题1），并利用部分OT理论解释了“拼接”行为的机理。
4. **实验覆盖全面**：在多个领域（连续控制、导航、灵巧操作）验证，结果具有说服力。
5. **消融研究细致**：对关键超参数w进行了系统分析，展示了其影响。

## 8. 不足与局限
1. **参数w任务依赖**：没有提出自适应选择w的方法，需要手动调参，可能限制实际部署的便利性。
2. **局限性未完全讨论**：文中承认w是任务相关的，但未探讨如何自动确定或鲁棒性。
3. **与最先进方法的全面对比不足**：仅与CQL、ReBRAC等结合，未与最新方法如IQL+OTR直接进行公平对比（因为PPL R与ReBRAC结合，而ReBRAC本身可能已比IQL+OTR强）。此外，缺失部分baseline在Adroit上的完整结果。
4. **理论仅近似成立**：策略改进的证明依赖于w→∞的极限假设，实际使用的有限w可能不严格保证单调提升。
5. **计算开销**：需要训练额外的f网络，且需交替优化三个网络（Q、f、π），虽运行时间尚可，但相比简单方法（如TD3+BC）复杂度略高。
6. **未考虑随机策略**：方法基于确定性策略，可能不适合需要随机探索的任务。

（完）
