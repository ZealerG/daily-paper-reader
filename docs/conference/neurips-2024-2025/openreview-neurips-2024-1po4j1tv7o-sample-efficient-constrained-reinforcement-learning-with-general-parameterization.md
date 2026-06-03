---
title: Sample-Efficient Constrained Reinforcement Learning with General Parameterization
title_zh: 基于通用参数化的样本高效约束强化学习
authors: "Washim Uddin Mondal, Vaneet Aggarwal"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=1po4j1Tv7O"
tags: ["query:graph-part"]
score: 7.0
evidence: 样本高效的约束强化学习算法，基于原对偶加速自然策略梯度
tldr: "约束强化学习中，智能体需最大化奖励同时满足成本约束。本文提出基于动量加速的原对偶自然策略梯度算法，在通用参数化策略下实现了最优的样本复杂度~O((1-gamma)^{-7} epsilon^{-2})，相比现有方法改进了一个因子。理论分析显示了算法的高效性。"
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-1po4j1tv7o/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1040, \"height\": 512, \"label\": \"Table\"}]"
motivation: 约束强化学习在通用参数化策略下的样本复杂度最优性尚未解决。
method: 提出原对偶加速自然策略梯度算法，结合动量加速技术迭代更新策略和拉格朗日乘子。
result: 理论证明了全局最优性差距和约束违反的epsilon-次优性，样本复杂度优于现有方法。
conclusion: 该算法为约束RL提供了第一个在通用参数化策略下的样本复杂度保证。
---

## Abstract
We consider a constrained Markov Decision Problem (CMDP) where the goal of an agent is to maximize the expected discounted sum of rewards over an infinite horizon while ensuring that the expected discounted sum of costs exceeds a certain threshold. Building on the idea of momentum-based acceleration, we develop the Primal-Dual Accelerated Natural Policy Gradient (PD-ANPG) algorithm that ensures an $\epsilon$ global optimality gap and $\epsilon$ constraint violation with $\tilde{\mathcal{O}}((1-\gamma)^{-7}\epsilon^{-2})$ sample complexity for general parameterized policies where $\gamma$ denotes the discount factor. This improves the state-of-the-art sample complexity in general parameterized CMDPs by a factor of $\mathcal{O}((1-\gamma)^{-1}\epsilon^{-2})$ and achieves the theoretical lower bound in $\epsilon^{-1}$.

---

## 论文详细总结（自动生成）

### 论文总结：Sample-Efficient Constrained Reinforcement Learning with General Parameterization

#### 1. 核心问题与整体含义（研究动机和背景）
- 研究问题：在通用参数化策略下，解决约束马尔可夫决策过程（CMDP），即最大化无限时域期望折扣奖励，同时确保期望折扣成本不低于给定阈值。
- 背景：CMDP 在机器人、通信网络、交通等领域有广泛应用；现有方法在通用参数化策略下的样本复杂度为 \(\tilde{\mathcal{O}}(\epsilon^{-4})\)，远低于理论下界 \(\Omega(\epsilon^{-2})\)。软最大参数化需要 \(O(SA)\) 参数，而通用参数化只需 \(d \ll SA\) 参数，更适合大规模或连续状态空间。
- 动机：能否在通用参数化 CMDP 上实现样本复杂度接近理论下界？本文给出肯定答案，提出 PD-ANPG 算法，将样本复杂度提升至 \(\tilde{\mathcal{O}}((1-\gamma)^{-7}\epsilon^{-2})\)，在 \(\epsilon^{-1}\) 因子上达到下界。

#### 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：基于原对偶框架，利用动量加速（Accelerated Stochastic Gradient Descent, ASGD）在自然策略梯度（NPG）的内循环中估计梯度，从而降低样本复杂度。
- **关键技术细节**：
  - 采用原对偶更新：对外循环中的策略参数 \(\theta\) 和拉格朗日乘子 \(\lambda\) 交替更新。
  - 策略更新使用自然策略梯度：\(\theta_{k+1} = \theta_k + \eta \omega_k\)，其中 \(\omega_k\) 是 NPG 的近似估计，通过最小化相容函数近似误差得到。
  - 内循环中，使用 ASGD（动量梯度下降）迭代求解 \(\omega_k\)，并采用尾部平均（tail-averaging）提高估计精度。
  - 拉格朗日乘子更新：\(\lambda_{k+1} = \mathcal{P}_\Lambda[\lambda_k - \zeta \hat{J}_{c,\rho}(\theta_k)]\)，其中 \(\hat{J}_{c,\rho}\) 通过无偏采样算法（Algorithm 1）获得。
  - 核心分析：建立全局到局部收敛引理（Lemma 3），将全局最优性差距分解为 NPG 估计的偏差项和高阶项；偏差项可解释为 ASGD 在确定性梯度下的收敛误差，进而利用 ASGD 收敛结果（Jain et al. 2018）得到拉格朗日函数的收敛率。
  - 最后通过优化超参数（\(\eta, \zeta, H, K\)）平衡目标收敛和约束违反，得到 \(\tilde{\mathcal{O}}(\epsilon^{-2})\) 样本复杂度。
- **算法流程（文字说明）**：
  - 外循环 \(k = 0,...,K-1\)：
    - 初始化内循环变量 \(x_0, v_0 = 0\)。
    - 内循环 \(h = 0,...,H-1\)：执行 ASGD 更新（公式 15-18），使用 Algorithm 1 的无偏梯度估计。
    - 尾部平均得到 \(\omega_k\)（公式 19）。
    - 通过 Algorithm 1 估计 \(\hat{J}_{c,\rho}(\theta_k)\)。
    - 更新 \(\theta_{k+1} = \theta_k + \eta \omega_k\)。
    - 更新 \(\lambda_{k+1} = \mathcal{P}_\Lambda[\lambda_k - \zeta \hat{J}_{c,\rho}(\theta_k)]\)。
  - 输出策略参数序列。

#### 3. 实验设计
- **该论文为纯理论分析，未进行任何实验或数值仿真**。因此无数据集、benchmark 或对比方法（仅在引言中与现有理论结果进行复杂度比较，如表1所示）。

#### 4. 资源与算力
- 论文未提及任何计算资源或算力需求。由于无实验，不涉及 GPU 型号、数量、训练时长等信息。

#### 5. 实验数量与充分性
- 论文未进行实验，因此不涉及实验数量或充分性评估。所有贡献均为理论证明，并通过严格数学推导保证结果正确性。

#### 6. 主要结论与发现
- 提出 PD-ANPG 算法，在通用参数化策略下实现 \(\epsilon\) 最优性差距和 \(\epsilon\) 约束违反，样本复杂度为 \(\tilde{\mathcal{O}}((1-\gamma)^{-7}\epsilon^{-2})\)。
- 相比现有最优方法（C-NPG-PDA，\(\tilde{\mathcal{O}}((1-\gamma)^{-8}\epsilon^{-4})\)），改进了一个 \(\mathcal{O}((1-\gamma)^{-1}\epsilon^{-2})\) 因子，并在 \(\epsilon^{-1}\) 维度上达到理论下界。
- 证明了拉格朗日函数收敛误差可分解为 ASGD 偏差，从而通过动量加速降低样本复杂度。
- 提出如何选择超参数（\(\eta, \zeta, H, K\)）以权衡目标收敛和约束违反，得到最终复杂度。

#### 7. 优点
- **理论创新**：首次在通用参数化 CMDP 上实现 \(\tilde{\mathcal{O}}(\epsilon^{-2})\) 样本复杂度，解决了长期存在的开放问题。
- **技巧巧妙**：将 NPG 估计的偏差与 ASGD 确定性收敛联系起来，实现更紧的误差控制。
- **分析深入**：建立了全局到局部收敛引理，明确区分了偏差项和方差项，为后续加速方法提供了分析框架。
- **通用性**：适用于任意满足 Fisher 非退化、Lipschitz 和光滑假设的策略参数化，包括神经网络。
- **与现有工作对比清晰**：论文表1系统总结了各种参数化下的样本复杂度，凸显本文改进。

#### 8. 不足与局限
- **缺乏实验验证**：纯理论论文，未提供数值仿真或实际场景验证，算法的实际有效性有待实证检验。
- **假设较强**：需要 Slater 条件、Fisher 非退化、函数近似误差有界等假设，可能在某些实际环境中不成立或难以验证。
- **依赖参数选择**：理论最优参数（如内循环步数 \(H\)）依赖未知常数（如 \(\mu_F, G\)），实际中需调参或自适应。
- **未考虑探索**：算法基于生成模型（generative model）假设，可无偏采样；无探索机制，不适用于在线交互场景。
- **未讨论计算复杂度**：虽然样本复杂度提升，但每步内循环 ASGD 需要多次梯度计算（\(H\) 次），总计算负载可能较高。
- **应用限制**：假设动作空间有限，状态空间可数（尽管可推广到紧集），但未处理连续动作空间。

（完）
