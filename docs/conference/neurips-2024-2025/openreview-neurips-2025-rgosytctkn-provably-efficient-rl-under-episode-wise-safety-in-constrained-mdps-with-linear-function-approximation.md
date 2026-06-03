---
title: Provably Efficient RL under Episode-Wise Safety in Constrained MDPs with Linear Function Approximation
title_zh: 线性函数近似约束马尔可夫决策过程中回合安全的高效可证明强化学习
authors: "Toshinori Kitamura, Arnob Ghosh, Tadashi Kozuno, Wataru Kumagai, Kazumi Kasaura, Kenta Hoshino, Yohei Hosoe, Yutaka Matsuo"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rgoSyTCTkn"
tags: ["query:graph-part"]
score: 6.0
evidence: 在线性函数近似约束MDP中实现可证明高效且安全的强化学习
tldr: 在约束马尔可夫决策过程（CMDP）中，智能体需在每回合满足安全性约束。现有表格设定已很好理解，但函数近似设定理论结果稀缺。本文提出针对线性CMDP的强化学习算法，达到~O(√K)遗憾且每回合零违反，计算复杂度与状态空间规模无关，多项式依赖于问题参数。算法填补了线性函数近似下安全RL的理论空白。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rgosytctkn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1412, \"height\": 1356, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rgosytctkn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1421, \"height\": 277, \"label\": \"Table\"}]"
motivation: 安全关键场景要求RL在每回合满足约束，但函数近似设定下理论匮乏。
method: 设计线性CMDP算法，通过精巧的探索策略实现遗憾界与零违反保证。
result: 达到~O(√K)遗憾且每回合零违反，计算高效。
conclusion: 首次为线性函数近似下的回合安全RL提供了可证明高效算法。
---

## Abstract
We study the reinforcement learning (RL) problem in a constrained Markov decision process (CMDP), where an agent explores the environment to maximize the expected cumulative reward while satisfying a single constraint on the expected total utility value in every episode. While this problem is well understood in the tabular setting, theoretical results for function approximation remain scarce. This paper closes the gap by proposing an RL algorithm for linear CMDPs that achieves $\widetilde{\mathcal{O}}(\sqrt{K})$ regret with an episode-wise zero-violation guarantee. Furthermore, our method is computationally efficient, scaling polynomially with problem-dependent parameters while remaining independent of the state space size. Our results significantly improve upon recent linear CMDP algorithms, which either violate the constraint or incur exponential computational costs.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：在安全关键应用中，强化学习（RL）需满足每回合的约束（episode-wise safety）。约束马尔可夫决策过程（CMDP）是形式化安全决策的框架。表格型CMDP已有成熟的结果，但线性函数近似下的可证明高效算法仍缺失。
- **核心问题**：能否在线性函数近似CMDP中，设计一个计算高效、达到次线性后悔（$\widetilde{O}(\sqrt{K})$）且保证每回合零违反约束的RL算法？
- **意义**：本文首次在线性CMDP中同时实现上述三个目标，填补了理论空白，推动了安全RL向大规模、可扩展方向的发展。

### 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：结合乐观‑悲观探索框架与软策略（softmax policy），通过双参数调整实现乐观目标与悲观约束的权衡，并设计安全策略部署规则限制其使用次数。
- **关键技术细节**：
  - **安全策略部署规则**：仅在算法对安全策略 $\pi_{\text{sf}}$ 的置信度不足时（即 $\beta^{(k)}_{\pi_{\text{sf}}} > \xi/(2C_u)$）才部署 $\pi_{\text{sf}}$，利用椭圆势引理证明部署次数为对数级（Theorem 1）。
  - **复合软策略**：定义 $\pi^{(k),\lambda}_h(\cdot|s) = \text{SoftMax}\big(\frac{1}{\kappa}(Q^{(k),\dagger}_{\pi^{(k),\lambda},h} + Q^{(k),r}_{\pi^{(k),\lambda},h}[\kappa] + \lambda Q^{(k),u}_{\pi^{(k),\lambda},h})\big)$，通过调节 $\lambda$ 平衡乐观（小 $\lambda$ 促进探索）与悲观（大 $\lambda$ 保证安全）。
  - **二分搜索**：在每个回合，算法通过二分搜索寻找最小的 $\lambda$ 使得悲观约束 $V^{(k),u}_{\pi^{(k),\lambda},1}(s_1) \ge b$ 成立，若最大 $\lambda = C_\lambda$ 仍不满足则部署 $\pi_{\text{sf}}$。
  - **混合策略可行性**：通过构建安全策略与最优策略的凸组合，证明存在可行解并用于后悔分析（Lemma 7）。
- **算法流程（文字说明）**：每个回合 $k$，算法先检查 $\pi_{\text{sf}}$ 的置信度；若置信度低则直接使用 $\pi_{\text{sf}}$；否则利用当前估计的价值函数（包含乐观奖励与悲观约束）构造复合软策略，通过二分搜索寻找 $\lambda$ 并得到策略 $\pi^{(k),\lambda}$；部署该策略采集一条轨迹，更新正则化最小二乘估计和协方差矩阵。

### 3. 实验设计

- **数据集/场景**：
  - **合成表格环境**（$|S|=5$, $|A|=3$, $H=4$）：类似Dann等构造，转移概率随机，奖励/效用随机，约束阈值 $b=0.6\max_\pi V^{\pi,u}$。
  - **媒体流环境**（来自Bura等）：基站传输服务（快/慢），缓冲长度状态 $|S|=6$, $H=4$，目标满足缓冲需求同时限制快速服务使用。
  - **合成线性环境**（$S=100$, $A=3$, $d=5$, $H=4$）：随机生成特征和转移核，可计算最优策略。
- **基准（Benchmark）**：最优策略由线性规划计算，作为比较基础。
- **对比方法**：
  - **Ghosh et al. (2024)**：最近线性CMDP算法，提供 $\widetilde{O}(\sqrt{K})$ 后悔与违反后悔，但无回合安全保证。
  - **DOPE (Bura et al., 2022)**：表格型CMDP算法，零违反但需状态空间大小依赖的计算，无法扩展至线性环境。
  - **均匀策略**：作为下界参考。

### 4. 资源与算力

- 文中明确说明：“All experiments were conducted within 30 minutes using eight Intel Core i7 CPUs and 32 GiB of RAM.” 未提及GPU，所有实验在CPU上快速完成。

### 5. 实验数量与充分性

- **实验数量**：三个不同环境（表格、媒体流、线性），每个环境运行10个随机种子，绘制平均曲线（如Figure 1）。未进行消融实验（如对参数 $\kappa$, $C_\lambda$ 的敏感性分析）。
- **充分性与公平性**：
  - 对比了两种主要基线，覆盖了可扩展与零违反两种类型。
  - 各算法超参数经过启发式调整，均采用较小值以保证数值稳定性。
  - 线性环境下未运行DOPE因其指数计算成本（文中Remark 3说明），这属于合理排除。
  - 实验设计基本客观，但缺乏消融实验和对参数鲁棒性的分析，可视为少量不足。

### 6. 主要结论与发现

- 本文提出的OPSE-LCMDP算法在所有测试环境中均实现 **零约束违反** 且 **后悔随回合数呈次线性增长**（近似 $\widetilde{O}(\sqrt{K})$），验证了Theorem 4的理论保证。
- 对比方法Ghosh et al. (2024) 虽然后悔同样次线性，但违反后悔持续增加；DOPE在表格环境中也达零违反但无法扩展到大状态空间。
- 安全策略部署次数的对数增长（Figure 1右图）支持Theorem 3，说明算法早期使用 $\pi_{\text{sf}}$ 后迅速停止，不会影响长期效率。

### 7. 优点

- **理论创新**：首次在线性CMDP中同时实现 $\widetilde{O}(\sqrt{K})$ 后悔和每回合零违反，填补了理论空白。
- **计算高效**：算法计算复杂度关于状态空间大小独立，仅多项式依赖于维度 $d$、回合长度 $H$、动作数 $A$，优于先前指数成本方法（如Ghosh et al. 2024的 $K^H$ 成本）。
- **算法设计**：利用软策略的单调性（Lemma 6）和二分搜索，有效避免了复杂线性规划或拉格朗日方法的指数计算开销。
- **实验验证**：尽管理论性强，仍提供了多种环境的数值结果，覆盖表格、线性、实际场景，增强了可信度。

### 8. 不足与局限

- **多约束扩展性**：方法依赖单调性（Lemma 6），当有多个约束时 $\lambda$ 变为向量，单调性推广非平凡，论文明确指出此局限性（Section 4）。
- **初始状态假设**：核心技术（$\pi_{\text{sf}}$ 部署次数上界、混合策略可行性）均依赖于固定的初始状态 $s_1$，扩展到对抗性初始状态面临挑战。
- **实验覆盖**：未进行超参数敏感性分析、消融实验（如不同 $\kappa$ 值的影响），也未展示计算时间对比。线性环境的状态空间仅100，相对较简单。
- **偏差风险**：所有环境均为人工合成，可能无法完全代表真实动态系统的复杂性。媒体流环境虽有实用背景但仍为模拟。
- **应用限制**：假设已知奖励/效用函数且噪声为子高斯，实际系统中这些假设可能不成立。

（完）
