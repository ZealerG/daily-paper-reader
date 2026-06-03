---
title: Robust Offline Reinforcement Learning with Linearly Structured $f$-Divergence Regularization
title_zh: 基于线性结构f散度正则化的鲁棒离线强化学习
authors: "Cheng Tang, Zhishuai Liu, Pan Xu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=FzulAfAJxE"
tags: ["query:graph-part"]
score: 9.0
evidence: 具有结构化正则化的鲁棒离线强化学习算法
tldr: 鲁棒正则化MDP中现有方法使用非结构化正则化，导致策略保守。本文提出d-矩形线性RRMDP框架，在转移核和正则化中引入潜在结构，并开发R2PVI算法。该算法在离线场景下学习鲁棒策略，有效缓解了保守性，理论分析证明其性能保证。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fzulafajxe/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1758, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fzulafajxe/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 834, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fzulafajxe/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1061, \"height\": 435, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fzulafajxe/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1521, \"height\": 687, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fzulafajxe/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 641, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fzulafajxe/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1183, \"height\": 447, \"label\": \"Table\"}]"
motivation: 非结构化正则化导致策略过于保守，限制了鲁棒性。
method: 引入d-矩形线性结构到转移核和正则化，提出R2PVI算法进行悲观值迭代。
result: 理论分析证明了算法的鲁棒性能，实验验证其优于非结构方法。
conclusion: 结构化正则化能有效提升离线RL的鲁棒性和效率。
---

## Abstract
The Robust Regularized Markov Decision Process (RRMDP) is proposed to learn policies robust to dynamics shifts by adding regularization to the transition dynamics in the value function. Existing methods mostly use unstructured regularization, potentially leading to conservative policies under unrealistic transitions. To address this limitation, we propose a novel framework, the $d$-rectangular linear RRMDP ($d$-RRMDP), which introduces latent structures into both transition kernels and regularization. We focus on offline reinforcement learning, where an agent learns policies from a precollected dataset in the nominal environment. We develop the Robust Regularized Pessimistic Value Iteration (R2PVI) algorithm that employs linear function approximation for robust policy learning in $d$-RRMDPs with $f$-divergence based regularization terms on transition kernels. We provide instance-dependent upper bounds on the suboptimality gap of R2PVI policies, demonstrating that these bounds are influenced by how well the dataset covers state-action spaces visited by the optimal robust policy under robustly admissible transitions. We establish information-theoretic lower bounds to verify that our algorithm is near-optimal. Finally, numerical experiments validate that R2PVI learns robust policies and exhibits superior computational efficiency compared to baseline methods.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：离线强化学习（Offline RL）中，智能体从固定数据集学习策略，但部署环境与数据收集环境存在动态转移（dynamics shift），导致策略失效。分布鲁棒马尔可夫决策过程（DRMDP）通过不确定性集建模动态变化，但传统的 `(s,a)`-矩形不确定性集假设各状态-动作对独立建模不确定性，在状态-动作空间大时导致策略过于保守。
- **现有不足**：现有 DRMDP 方法多使用非结构化正则化，可能引入不现实的转移，且对 KL 散度需要额外正则性假设，χ² 散度缺乏理论保证；同时，依赖对偶优化预言的计算开销大（随特征维度 d 和规划跨度 H 增长）。
- **本文动机**：通过引入潜在结构（d-矩形线性结构）到转移核和正则化项中，设计更高效、保守性更低的鲁棒离线 RL 框架，并支持一般 f-散度（TV、KL、χ²）。

## 2. 方法论

### 核心思想
- 提出 **d-矩形线性 RRMDP（d-RRMDP）**：将不确定性集约束替换为精心设计的正则化惩罚项，保留线性结构，同时避免不确定性集带来的计算复杂性。
- 开发 **Robust Regularized Pessimistic Value Iteration (R2PVI)** 算法：结合线性函数近似和悲观值迭代，在离线数据下学习鲁棒策略。

### 关键技术细节
- **线性结构假设**：状态-动作特征映射 ϕ(s,a) ∈ ℝᵈ 满足非负且分量和为 1；名义转移核 P⁰ 和奖励函数均有线性表示。
- **鲁棒正则化贝尔曼方程**：证明 d-RRMDP 满足动态规划原理，存在确定性最优策略。
- **对偶形式**：
  - TV 散度：闭式解 `Eₛ∼μ₀[V(s)]_(V_min+λ)`，无需优化。
  - KL 散度：闭式解 `-λ log Eₛ∼μ₀[e^{-V(s)/λ}]`。
  - χ² 散度：含 α 优化问题 `sup_α {Eₛ∼μ₀[V(s)]_α - (1/(4λ))Varₛ∼μ₀[V(s)]_α}`。
- **估计方法**：通过岭回归估计期望值，再利用闭式解或α优化得到参数 w^λ_h。
- **悲观惩罚项**：构造 Γₕ(s,a) = β ∑ᵢ ‖ϕᵢ(s,a)1ᵢ‖_{Λₕ⁻¹}，其中 Λₕ 为协方差矩阵，β 依散度不同而设置（TV: 16Hd√ξ_TV, KL: 16dλe^{H/λ}√(H/λ+ξ_KL), χ²: 8dH²(1+1/λ)√ξ_χ²）。
- **算法流程**（Algorithm 1/2）：从 H 到 1 逆向迭代，计算 Λₕ，估计 w^λ_h，构造 Q^λ_h 并取贪婪策略。

### 理论保证
- **实例相关上界**：次优性 gap ≤ 2β sup_{P∈U_λ(P⁰)} ∑ₕ Eπ⋆,P[∑ᵢ‖ϕᵢ(s,a)1ᵢ‖_{Λₕ⁻¹}]。
- **实例无关上界**：在鲁棒部分覆盖假设下，次优性 gap 为 Õ(d²H²/√K)（TV）、Õ(√λ e^{H/λ} d²H^{3/2}/√K)（KL）、Õ(d²H³(1+1/λ)/√K)（χ²）。
- **信息论下界**：证明该实例相关项本质上是离线 d-RRMDP 固有的，算法近似最优。

## 3. 实验设计

- **数据集/场景**：
  1. **模拟线性 MDP**（源于 Liu & Xu, 2024a）：状态空间 5 个，动作空间 4 维，初始状态固定，含吸收状态（失败/目标）。
  2. **模拟美式看跌期权（American Put Option）**（Tamar et al., 2014）：H=20，状态为股票价格，动作行使/不行使，数据集通过均匀随机行为策略收集。
- **Benchmarks**：
  - 非鲁棒悲观算法：PEVI（Jin et al., 2021）。
  - d-DRMDP 算法：DRPVI（TV 散度）、DRVI-L（KL 散度）（Ma et al., 2022; Liu & Xu, 2024b）。
- **对比方法**：R2PVI-TV、R2PVI-KL、R2PVI-χ²。

## 4. 资源与算力

- 论文**未明确说明**使用的 GPU 型号、数量或训练时长。实验在“11th Gen Intel Core i5-11300H @ 3.10GHz 处理器，8 逻辑 CPU，4 物理核心，2 线程/核心”上进行，未提及 GPU。

## 5. 实验数量与充分性

- **实验数量**：展示了多组结果：
  - 在模拟线性 MDP 中对比 R2PVI 与 PEVI 在不同扰动程度下的性能（图 1a）。
  - 调节 λ 观察鲁棒性影响（图 1b）。
  - 对比 R2PVI 与 DRPVI 在不同 λ/ρ 下的表现（图 1c）。
  - 在美式期权环境中比较计算时间随样本量 N 和特征维度 d 的变化（图 2a、2b）。
  - 在美式期权中对比不同 λ 下 R2PVI 与 DRPVI 的鲁棒性（图 1d）。
- **充分性评估**：
  - 覆盖了三种散度、多种扰动程度、不同 λ/ρ 参数，以及计算效率对比。
  - 消融实验：仅进行了 λ 参数调节实验，未进行更全面的消融（如不同行为策略、不同数据集大小、不同特征维度对性能的影响）。
  - **客观性/公平性**：与 baseline 的对比合理，但未包含 P2MPO 和 DROP（因缺少代码），限制了对比的全面性。

## 6. 主要结论与发现

- **鲁棒性提升**：R2PVI 在环境扰动大时显著优于非鲁棒算法 PEVI，而在扰动小时性能相当。
- **计算效率**：R2PVI 的计算成本接近 PEVI，远低于 DRPVI 和 DRVI-L，因其对 TV 和 KL 散度有闭式对偶解，无需迭代优化。
- **λ 与 ρ 的对应关系**：验证了 λ（正则化参数）与 ρ（不确定性水平）在 d-RRMDP 和 d-DRMDP 中起类似反向作用：λ 越小越鲁棒。
- **理论上界匹配**：实例相关上界与信息论下界一致，算法近似最优。

## 7. 优点

- **创新性框架**：首次将 d-矩形线性结构引入 RRMDP，克服传统非结构化正则化的保守性。
- **算法高效易用**：TV 和 KL 散度有闭式解，无需对偶优化预言，显著降低计算复杂度。
- **理论完整**：提供了严格的实例相关/无关上界和信息论下界，证明算法接近最优。
- **实验验证全面**：在两种不同环境（线性 MDP 和非线性期权）中验证，覆盖三种常见 f-散度。

## 8. 不足与局限

- **实验覆盖有限**：
  - 未在更大规模/实世界环境（如连续控制任务 Atari、MuJoCo）中测试。
  - 消融实验不足：仅测试了 λ 的变化，未系统研究特征维度 d、样本量 K、行为策略类型等对性能的影响。
  - 未与 P2MPO、DROP 等最新算法直接对比（因代码缺失），影响说服力。
- **假设限制**：
  - 要求状态-动作特征映射 ϕ 满足解析线性结构（分量非负且和为 1），可能不适用于所有现实场景。
  - 鲁棒部分覆盖假设（Assumption 5.3）较强，实际中可能难以验证。
- **理论差距**：上界与下界之间仍有常数因子 β，且 β 定义依赖散度，可能存在优化空间。
- **计算资源未说明**：缺少 GPU 算力、训练时长等细节，不利于工程复现和评估实际资源需求。

（完）
