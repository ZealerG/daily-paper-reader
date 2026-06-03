---
title: "Outcome-Based Online Reinforcement Learning: Algorithms and Fundamental Limits"
title_zh: 基于结果的在线强化学习：算法与基本极限
authors: "Fan Chen, Zeyu Jia, Alexander Rakhlin, Tengyang Xie"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=sYfIpZzojf"
tags: ["query:graph-part"]
score: 7.0
evidence: 基于结果的在线强化学习与通用函数逼近
tldr: 在线强化学习中，奖励仅在轨迹终点观测时存在信用分配难题。本文首次对基于结果反馈的在线RL进行系统分析，提出一种样本高效算法，使用通用函数逼近在大状态空间中工作。理论证明了~O(C_cov H^3/epsilon^2)的样本复杂度，为结果反馈RL提供了理论基础和实用算法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-syfipzzojf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 516, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-syfipzzojf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 737, \"height\": 234, \"label\": \"Table\"}]"
motivation: 奖励仅在轨迹终点观测时，如何给正确动作分配信用是关键难题。
method: 提出使用通用函数逼近的样本高效算法，通过覆盖性系数分析复杂度，仅需值函数和奖励函数属于适当函数类。
result: 理论证明了样本复杂度上界，并在数值实验中验证了算法在大状态空间中的有效性。
conclusion: 该方法为结果反馈RL提供了理论保证和实用算法，拓展了RL在延迟奖励场景的应用。
---

## Abstract
Reinforcement learning with outcome-based feedback faces a fundamental challenge: when rewards are only observed at trajectory endpoints, how do we assign credit to the right actions? This paper provides the first comprehensive analysis of this problem in online RL with general function approximation. We develop a provably sample-efficient algorithm achieving $\widetilde{O}({C_{\rm cov} H^3}/{\varepsilon^2})$ sample complexity, where $C_{\rm cov}$ is the coverability coefficient of the underlying MDP. By leveraging general function approximation, our approach works effectively in large or infinite state spaces where tabular methods fail, requiring only that value functions and reward functions can be represented by appropriate function classes. Our results also characterize when outcome-based feedback is statistically separated from per-step rewards, revealing an unavoidable exponential separation for certain MDPs. For deterministic MDPs, we show how to eliminate the completeness assumption, dramatically simplifying the algorithm. We further extend our approach to preference-based feedback settings, proving that equivalent statistical efficiency can be achieved even under more limited information. Together, these results constitute a theoretical foundation for understanding the statistical properties of outcome-based reinforcement learning.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：在强化学习中，当奖励仅在完整轨迹结束时才被观测（即结果反馈，outcome-based feedback），而无法在每个时间步获得每步奖励（过程反馈）时，如何给正确的动作分配信用（信用分配问题）？在线探索在此设置下是否统计可行？
- **研究背景**：结果反馈在现实场景中广泛存在，例如大语言模型的训练（仅对整个输出提供人类偏好）、临床试验（仅在整个疗程后观察患者结局）。传统RL依赖每步奖励信号，结果反馈使得学习更加困难。此前工作主要假设线性奖励或低 eluder 维度，但本文首次使用通用函数逼近（general function approximation）系统分析该问题。
- **整体含义**：本文揭示了结果反馈在何种条件下在线学习是统计可行的，并刻画了其与每步反馈之间的基本分离（指数级困难差距），为基于轨迹奖励的RL提供了理论基础。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：采用乐观原则（optimism），联合优化值函数和奖励模型来解决信用分配。主要算法为 Algorithm 1（基于结果奖励的乐观探索），另为确定性MDP提供简化版本 Algorithm 2，并扩展至偏好反馈的 Algorithm 3。
- **关键技术细节**：
  - **函数逼近**：假设存在值函数类 $\mathcal{F}$、奖励函数类 $\mathcal{R}$ 和比较函数类 $\mathcal{G}$，满足可实现性（realizability）和贝尔曼完备性（Bellman completeness）。
  - **损失函数设计**：使用贝尔曼损失 $\mathcal{L}_{\rm BE}$ 和奖励模型损失 $\mathcal{L}_{\rm RM}$，通过减去 $\inf_{g \in \mathcal{G}}$ 克服双采样问题。
  - **联合优化**：在每轮 $t$ 中，求解优化问题 $(f^{(t)}, R^{(t)}) = \max_{f \in \mathcal{F}, R \in \mathcal{R}} [\lambda f_1(s_1) - \mathcal{L}_{\rm BE}(f;R) - \mathcal{L}_{\rm RM}(R)]$ 得到乐观估计，然后执行贪心策略 $\pi_{f^{(t)}}$ 并用 $\pi_{\rm ref}$ 进行分层探索（layer-wise exploration）收集数据。
  - **确定性MDP简化**：利用贝尔曼残差损失 $\mathcal{L}_{\rm BR}(f) = \sum_{(\tau,r) \in D} (\sum_h [f_h(s_h,a_h) - f_{h+1}(s_{h+1})] - r)^2$，无需奖励函数类 $\mathcal{R}$ 和比较函数类 $\mathcal{G}$。
  - **偏好反馈扩展**：采用逻辑损失 $\mathcal{L}_{\rm PbRM}$ 代替平方损失，利用 BTL 模型。
- **理论保证**：在覆盖性系数 $C_{\rm cov}$ 下，样本复杂度为 $\widetilde{O}(C_{\rm cov} H^3 / \varepsilon^2)$（Algorithm 1），确定性 MDP 下为 $\widetilde{O}(C'_{\rm cov} H^4 \log T / \varepsilon^2)$（Algorithm 2），偏好反馈下类似（Theorem 3）。证明依赖于集中不等式、Freedman 不等式、覆盖数论证以及覆盖性比例引理。

## 3. 实验设计
- **本文为纯理论论文，未进行任何实验或数值模拟。**
- 没有使用数据集、benchmark 或对比方法。所有贡献均以定理与证明形式呈现。

## 4. 资源与算力
- 文中未提及任何计算资源（GPU型号、数量、训练时长等）。作为理论论文，不涉及实验，因此无算力需求说明。

## 5. 实验数量与充分性
- 不适用。本文无实验。理论结果通过严谨的数学证明（含附录）支持，覆盖了多种设置（一般MDP、确定性MDP、偏好反馈）及下界，逻辑链条完整，充分性通过证明保证。

## 6. 主要结论与发现
- **上界结果**：在合理假设（可实现性、贝尔曼完备性、有界覆盖性）下，基于结果反馈的在线RL可实现 $\widetilde{O}(C_{\rm cov} H^3/\varepsilon^2)$ 样本复杂度，与过程反馈仅差 $\widetilde{O}(H)$ 因子，表明在覆盖性条件下两者几乎统计等价。
- **简化算法**：确定性MDP下可消除完备性假设，采用更简单的贝尔曼残差最小化（Algorithm 2），样本复杂度类似。
- **偏好反馈扩展**：偏好反馈（BTL模型）下可达到相同统计效率（Theorem 3）。
- **下界（指数级分离）**：存在 horizon $H=2$、转移已知、奖励为 $d$ 维广义线性函数的MDP类，使用过程反馈只需 $\widetilde{O}(d^2/\varepsilon^2)$ 轮，但使用结果反馈则需 $\Omega(e^{c d})$ 轮。这展示了基于贝尔曼误差/eluder维度的分析在结果反馈下会失效，证明了两者之间存在不可避免的指数级差距。
- **联合优化必要性**：分离式学习（先拟合奖励再优化值函数）可能导致失败，因奖励模型不匹配会使算法陷入信息不足区域（Appendix F.1）。

## 7. 优点
- **首次系统性分析**：第一个在通用函数逼近下全面研究结果反馈在线RL的工作，并给出了与覆盖性相关的紧致上界。
- **理论深度与完整性**：同时包含上界、下界以及偏好反馈扩展，提供了完整的统计复杂度刻画，并揭示了过程反馈与结果反馈的本质区别。
- **方法简洁且具扩展性**：联合优化思想自然统一了奖励与值函数学习；确定性MDP下的简化算法（Algorithm 2）计算更高效；偏好反馈扩展贴近实际 RLHF 场景。
- **证明技术新颖**：利用覆盖性比例引理并结合奖励误差的分解（Proposition 15），将轨迹级别的误差转化为逐步骤的期望误差，再用于椭圆势论证。

## 8. 不足与局限
- **未提供实验验证**：作为纯理论论文，缺乏在标准RL基准上的数值实验或模拟，无法验证算法的实际效率或超参数敏感性。
- **假设较强**：需要可实现性、贝尔曼完备性以及覆盖性有界；实际中这些条件可能难以满足或验证。例如完备性要求 $\mathcal{G}$ 类足够大。
- **计算复杂性**：Algorithm 1 需要求解复杂的 max-min 优化问题（涉及 $\inf_{g\in\mathcal{G}}$），实际中难以高效实现。虽然确定性MDP简化问题，但一般情况仍面临计算挑战。
- **覆盖性可能指数级大**：$C_{\rm cov}$ 在某些MDP中可能非常大，导致样本复杂度上界失去实际意义。
- **仅考虑总奖励形式**：结果奖励是各步奖励之和，未泛化到更一般的轨迹级奖励函数。
- **偏好反馈假设BTL模型**：若真实偏好模型偏离BTL假设，算法性能可能下降。

（完）
