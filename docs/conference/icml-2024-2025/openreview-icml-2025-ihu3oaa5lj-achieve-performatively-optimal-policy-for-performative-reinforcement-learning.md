---
title: Achieve Performatively Optimal Policy for Performative Reinforcement Learning
title_zh: 实现执行式强化学习的执行最优策略
authors: "Ziyi Chen, Heng Huang"
date: 2025-01-23
pdf: "https://openreview.net/pdf?id=iHu3oAA5lJ"
tags: ["query:graph-part"]
score: 9.0
evidence: 执行式强化学习中的策略梯度算法
tldr: 执行式强化学习中，现有方法只能达到次优的稳定策略。本文提出0-PPG算法，首次在温和条件下以多项式复杂度收敛到真正的最优策略。该算法无需对价值函数求导，适用于策略影响环境动力学的场景，为动态决策提供了新工具。
source: ICML-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 现有执行式RL方法只能逼近稳定策略，与真正最优策略存在常数差距。
method: 提出零阶执行策略梯度算法，无需精确梯度信息即可收敛到最优策略。
result: 理论证明0-PPG算法多项式收敛到执行最优策略，实验验证其有效性。
conclusion: 0-PPG为执行式RL提供了首个最优策略保证。
---

## Abstract
Performative reinforcement learning is an emerging dynamical decision making framework, which extends reinforcement learning to the common applications where the agent's policy can change the environmental dynamics. Existing works on performative reinforcement learning only aim at a performatively stable (PS) policy that maximizes an approximate value function. However, there can be a positive constant gap between the PS policy and the desired performatively optimal (PO) policy that maximizes the original value function. In contrast, this work proposes a zeroth-order performative policy gradient (0-PPG) algorithm that **for the first time converges to the desired PO policy with polynomial computation complexity under mild conditions**. For the convergence analysis, we prove two important properties of the nonconvex value function. First, when the policy regularizer dominates the environmental shift, the value function satisfies a certain gradient dominance property, so that any stationary point of the value function is a desired PO. Second, though the value function has unbounded gradient, we prove that all the sufficiently stationary points lie in a convex and compact policy subspace $\Pi_{\Delta}$, where the policy value has a constant lower bound $\Delta>0$ and thus the gradient becomes bounded and Lipschitz continuous.

---

## 论文详细总结（自动生成）

好的，根据您提供的论文内容，以下是按照要求生成的中文总结。

# 论文总结：实现执行式强化学习的执行最优策略

## 1. 论文的核心问题与整体含义（研究动机和背景）

-   **核心问题**：在“执行式强化学习”（Performative Reinforcement Learning）框架中，智能体的策略（policy）会改变其所处的环境动态（包括转移概率和奖励函数）。现有研究（如 Mandal et al., 2023）只能找到“执行稳定”（Performatively Stable, PS）策略——即在当前策略固定环境下的最优策略。然而，PS 策略与真正期望的“执行最优”（Performatively Optimal, PO）策略之间存在一个恒定的正差距。
-   **研究动机**：回答一个根本性的问题：“能否设计一种算法，使其收敛到期望的 PO 策略？” 本文致力于解决这一挑战，首次证明在温和条件下可以实现对 PO 策略的多项式时间收敛。
-   **整体含义**：该工作将执行式强化学习从寻找次优稳定策略推进到寻找真正最优策略，为动态决策框架提供了更坚实的基础，尤其适用于策略显著影响环境的实际应用（如推荐系统、自动驾驶）。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
-   利用**熵正则化** (entropy regularization) 的强化学习目标函数，证明其满足**梯度主导性** (gradient dominance) 条件，使得任意一个驻点（stationary point）在正则化强度足够大时即为 PO 策略。
-   发现目标函数梯度在某些区域（*π*(*a*|*s*) → 0）是无界的，因此证明了一个**策略下界**，将所有足够优的驻点限制在一个凸紧致子空间 Π<sub>Δ</sub> 内，在该子空间中梯度有界且 Lipschitz 连续。
-   由于执行式 RL 中策略梯度没有解析形式且只能采样，采用**零阶 (zeroth-order) 梯度估计** 来近似梯度，并结合**Frank-Wolfe 算法**进行优化。

### 关键技术细节与公式
1.  **熵正则化价值函数**：
    \( V_{\lambda}^{\pi, \pi'} = \mathbb{E}_{\pi, p^{\pi'}, \rho} \left[ \sum_{t=0}^{\infty} \gamma^t [r^{\pi'}(s_t, a_t) - \lambda \log \pi(a_t|s_t)] \right] \)
    文中采用了负熵正则器 \( H_{\pi'}(\pi) = \mathbb{E}_{\pi, p^{\pi'}, \rho} \left[ \sum_{t=0}^{\infty} \gamma^t \log \pi(a_t|s_t) \right] \)。

2.  **梯度主导性** (Theorem 1, Corollary 1)：
    -   在温和条件下（Assumptions 1-3 和正则化强度 λ 足够大以主导环境变化），价值函数满足梯度主导性，即任意 *ϵ* 驻点都是 *ϵ*-PO 策略。这从理论上保障了寻找驻点即是寻找最优解。

3.  **策略下界** (Theorem 2)：
    -   证明了对于任意策略 *π*，其最小动作概率 *π*[*a*<sub>min</sub>(*s*)|*s*] 有一个严格正的下界 π<sub>min</sub>，该下界是策略梯度内积的函数。这揭示了当某个动作概率趋于 0 时，梯度会趋向无穷大，从而无法直接优化。

4.  **Lipschitz 性质** (Theorem 3)：
    -   在具有正下界 Δ 的策略子空间 Π<sub>Δ</sub> 内，价值函数是 Lipschitz 连续且 Lipschitz 光滑的（即梯度 Lipschitz 连续）。这为使用一阶优化方法（如 Frank-Wolfe）提供了理论基础。

5.  **零阶策略梯度估计 (0-PPG)** (Proposition 1, Algorithm 1)：
    -   利用两点差分法在策略空间 Π 上估计梯度。由于策略空间是线性子空间 L<sub>0</sub> 的仿射子集，论文通过正交变换将估计问题映射到标准欧几里得空间进行分析。
    -   估计公式：
        \[
        \hat{g}_{\lambda, \delta}(\pi) = \frac{|S|(|A|-1)}{2N\delta} \sum_{i=1}^{N} (\hat{V}_{\lambda}^{\pi+\delta u_i, \pi+\delta u_i} - \hat{V}_{\lambda}^{\pi-\delta u_i, \pi-\delta u_i}) u_i
        \]
        其中 *u*<sub>*i*</sub> 是 L<sub>0</sub> 单位球面上的均匀采样方向。

6.  **算法流程 (Algorithm 1)**：
    -   **输入**：迭代次数 *T*，采样数 *N*，子空间下界 Δ，扰动大小 δ，策略评估误差 ϵ<sub>V</sub>，步长 β。
    -   **循环** *t* = 0 到 *T*-1：
        1.  采样 *N* 个随机方向 *u*<sub>*i*</sub>。
        2.  基于当前策略 *π*<sub>*t*</sub> 评估扰动策略 *π*<sub>*t*</sub> ± *δu*<sub>*i*</sub> 的价值。
        3.  计算零阶梯度估计 \(\hat{g}_{\lambda, \delta}(\pi_t)\)。
        4.  **Frank-Wolfe 步骤**：找到使 \(\langle \pi, \hat{g}_{\lambda, \delta}(\pi_t) \rangle\) 最大化的 \(\tilde{\pi}_t \in \Pi_{\Delta}\)，其解析解为单点分布（将概率集中在梯度最大的动作上）。
        5.  更新策略：\( \pi_{t+1} = \pi_t + \beta(\tilde{\pi}_t - \pi_t) \)。
    -   **输出**：使梯度估计内积最小的策略 \(\pi_{\tilde{T}}\)。

## 3. 实验设计

-   论文**没有进行任何数值实验或仿真**。全文完全聚焦于理论分析、算法设计和收敛性证明。因此，没有涉及数据集、benchmark 或对比方法。

## 4. 资源与算力

-   由于论文未包含实验，**没有提及任何计算资源、GPU 型号、数量或训练时长**。

## 5. 实验数量与充分性

-   不适用。论文属于纯理论研究，其“实验”相当于严格的数学定理证明和推导。其充分性体现在：
    -   理论推导完整，所有假设和结论均有严密证明。
    -   定理的适用条件（如正则化强度）明确给出。
    -   与现有工作进行了理论层面的对比（如说明现有算法只能收敛到 PS 而非 PO，而本文算法可以收敛到 PO）。

## 6. 论文的主要结论与发现

-   **理论突破**：首次提出并证明了在熵正则化执行式 RL 中，通过 0-PPG 算法可以在多项式计算复杂度 \(O(\epsilon^{-4} \log(\eta^{-1}\epsilon^{-1}))\) 内收敛到一个 **ϵ-PO 策略**（执行最优策略）。而现有工作最多只能收敛到次优的 PS 策略。
-   **关键性质揭示**：证明了在正则化强度主导环境变化时，非凸的价值函数具有梯度主导性，从而将优化目标从全局最优简化为寻找驻点。
-   **解决了梯度无界问题**：利用策略下界定理，将优化空间限制在一个紧凸子空间，在该子空间内梯度有界且光滑，使得零阶优化可行。
-   **方法可迁移性**：指出所有结果（包括梯度主导性、Lipschitz 性质、有限时间收敛性）也可以调整至现有工作中使用的二次正则化器。

## 7. 优点：方法或实验设计上的亮点

-   **目标明确，理论深刻**：清晰地指出了现有工作的不足（PS 与 PO 的差距），并针对性地提出了完全不同的算法目标（收敛到 PO）。
-   **算法设计巧妙**：零阶梯度估计 + Frank-Wolfe 算法的组合非常契合执行式 RL 的特性（无法获得梯度解析形式、策略空间为概率单形），解决了梯度无界的关键难题。
-   **理论分析严密**：提供了从梯度主导性、策略下界到 Lipschitz 性质、梯度估计误差分析再到算法收敛性的完整理论链条。
-   **多项式复杂度保证**：在理论上证明了算法能以多项式级计算量收敛到任意精度的最优策略，这是该领域的首个此类保证。

## 8. 不足与局限

-   **缺乏实验验证**：作为一篇机器学习论文，完全没有实验来支撑理论结论。虽然理论本身很强大，但缺少对算法在具体问题（如小型推荐系统、简单导航任务）上的有效性和实际性能的评估。论文本身有一个潜在的隐含假设——“理论结果足以证明算法的价值”，但这在 ML 领域通常是不够的。
-   **应用限制**：算法的多项式复杂度虽然从理论上很好，但具体系数（如涉及 |*S*|、|*A*|、状态空间大小等）可能较大，对于大规模问题可能仍然昂贵。
-   **对参数敏感性**：算法需要选择多个超参数（Δ、δ、β、*T*、*N*、ϵ<sub>V</sub>），文中仅给出了理论上的选择示例，实际应用中如何有效调参仍是一个挑战。
-   **正则化强度的要求**：梯度主导性条件要求正则化强度 λ 足够大以“主导”环境变化。如果环境变化非常剧烈而λ不可任意大，则该方法可能退化为寻找次优解或无法保证收敛。
-   **假设的严格性**：论文依赖于一些较强的假设，如状态-动作空间有限、状态被充分访问（Assumption 3）、环境的敏感性和光滑性（Assumptions 1-2）。这些假设在复杂现实系统中可能不完全成立。

（完）
