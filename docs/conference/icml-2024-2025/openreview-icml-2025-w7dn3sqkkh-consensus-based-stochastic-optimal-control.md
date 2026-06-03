---
title: Consensus Based Stochastic Optimal Control
title_zh: 基于共识的随机最优控制
authors: "Liyao Lyu, Jingrun Chen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=W7dN3SQKkH"
tags: ["query:graph-part"]
score: 6.0
evidence: 无梯度深度强化学习求解高维随机控制
tldr: 该论文针对策略梯度方法在求解高维随机控制问题时方差大的缺陷，提出基于共识的梯度-free深度强化学习算法，包括动量CBO和自适应动量CBO。这些方法使用值函数的蒙特卡洛估计而非梯度来优化策略，并通过可调高斯噪声实现高效探索，在复杂非凸环境下收敛到最优策略。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 传统策略梯度方法在高维随机控制问题中方差高、效率低。
method: 引入基于共识的优化框架，利用值函数的蒙特卡洛估计替代梯度更新。
result: 数值实验表明方法在多个高维控制问题上优于现有梯度方法。
conclusion: 提供了无梯度的深度强化学习替代方案，适用于复杂控制场景。
---

## Abstract
We propose a *gradient-free* deep reinforcement learning algorithm to solve *high-dimensional*, finite-horizon stochastic control problems. 
Although the recently developed deep reinforcement learning framework has achieved great success in solving these problems, direct estimation of policy gradients from Monte Carlo sampling often suffers from high variance.  To address this, we introduce the Momentum Consensus-Based Optimization (M-CBO) and Adaptive Momentum Consensus-Based Optimization (Adam-CBO) frameworks. These methods optimize policies using Monte Carlo estimates of the value function, rather than its gradients. Adjustable Gaussian noise supports efficient exploration, helping the algorithm converge to optimal policies in complex, nonconvex environments. Numerical results confirm the accuracy and scalability of our approach across various problem dimensions and show the potential for extension to mean-field control problems. Theoretically, we prove that M-CBO can converge to the optimal policy under some assumptions.

---

## 论文详细总结（自动生成）

# 基于共识的随机最优控制——论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：高维有限时间随机最优控制（SOC）问题在金融、经济、化学、生物等领域广泛存在。传统数值方法（如有限体积法、Galerkin方法、单调逼近法）求解对应的Hamilton-Jacobi-Bellman（HJB）方程时，面临“维度灾难”——计算复杂度随状态和动作空间维度指数增长。
- **现有深度强化学习方法的问题**：基于值函数的方法（如深度BSDE方法）需要显式建模转移核，属于模型依赖方法，实际中难以获得精确模型；而基于策略梯度的方法（如PPO、SAC等）虽为模型无关，但蒙特卡洛估计策略梯度存在高方差问题，且大多局限于无限时间 horizon 问题。有限时间 horizon 下模型无关且梯度-free 的方法非常缺乏。
- **论文目标**：提出一种**无梯度、无模型、无网格**的深度强化学习算法，能够高效求解高维、有限时间、非凸的随机最优控制问题。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程
- **核心思想**：将**基于共识的优化（CBO）**框架引入随机最优控制，使用值函数的蒙特卡洛估计（而非梯度）来更新策略参数。通过引入动量项和自适应动量估计，增强探索能力并加速收敛。
- **关键技术细节**：
  - **M-CBO（动量共识优化）**：
    - 初始化一群策略参数（粒子）Θᵢ 和动量 Ωᵢ。
    - 计算共识策略：\( M_\beta(\Theta) = \frac{\sum_i \Theta_i w_\beta(\Theta_i)}{\sum_j w_\beta(\Theta_j)} \)，其中 \( w_\beta(\Theta)=\exp(-\beta J(\Theta)) \)，β 为逆温度参数。
    - 使用随机微分方程（SDE）更新每个粒子的策略和动量：
      \[
      d\Theta_t^i = \Omega_t^i dt - \gamma_1(\Theta_t^i - M_\beta(\Theta)) dt + \sigma(t) dW_{\theta,t}^i,
      \]
      \[
      d\Omega_t^i = -m (\Theta_t^i - M_\beta(\Theta)) dt - \gamma_2 \Omega_t^i dt + \sqrt{m}\sigma(t) dW_{\omega,t}^i.
      \]
    - 实际使用 Euler-Maruyama 离散化实现（算法1）。
  - **Adam-CBO（自适应动量共识优化）**：
    - 将 M-CBO 中的常数动量项 m 替换为基于二阶矩的自适应项：\( (V_\beta[\Theta] + \epsilon I)^{-1} \)，其中 \( V_\beta[\Theta] \) 是加权的二阶矩。
    - 引入类似 Adam 优化器的动量和二阶矩滑动平均（β₁, β₂），实现自适应步长（算法2）。
  - **梯度-free 特性**：更新中不需要计算 J(Θ) 的梯度，仅需值函数的估计值。
  - **探索机制**：通过可调的高斯噪声 σ(t) 控制探索强度，避免陷入局部最优。
- **理论证明**：在满足一定正则性假设（局部 Lipschitz、有界性等）下，证明了 M-CBO 方法的 Fokker-Planck 方程解的存在唯一性、平均场极限，以及能量函数 \( E[\rho_t] = \frac{1}{2}\int (\|\theta - \tilde{\theta}\|^2 + m^{-1}\|\omega\|^2) d\rho \) 的指数衰减收敛到最优策略。

## 3. 实验设计：数据集/场景、基准、对比方法
- **场景与问题**：
  1. **线性二次高斯（LQG）控制问题**：维度 1,2,4,8,16，终端成本分为凸（\( g(x)=\ln\frac{1+\|x\|^2}{2} \)）和非凸（双势阱 \( g(x)=\ln\frac{1+(\|x\|^2-1)^2}{2} \)）。
  2. **Ginzburg-Landau 模型**：控制超导体在外电磁场下的行为，维度 2,4,8,16,32。
  3. **系统性风险均值场控制**：模拟银行间借贷网络，测试不同初始分布（单高斯、两高斯混合、三高斯混合）和不同 agent 数量（50,100,200,400,800）。
  4. **多智能体机器人系统**：2、4、50 个 agent 的避障导航任务。
  5. **标准强化学习环境**：Pendulum-v1 和 CartPole-v1。
- **基准方法**：
  - BSDE 方法（深度 BSDE，Han et al., 2018）——用于 LQG 和 Ginzburg-Landau。
  - DDPG, PPO, SAC, TD3, TQC, CrossQ ——用于 Pendulum-v1；PPO, DQN ——用于 CartPole-v1。
- **评价指标**：值函数 u(t,x) 或策略与理论最优控制的误差（对于 LQG 有精确蒙特卡洛估计作为参考）；对于均值场问题，比较不同 agent 数下的值函数；对于机器人任务，展示轨迹可视化；对于 RL 任务，比较值函数收敛曲线和计算时间。

## 4. 资源与算力
- **论文未明确说明具体的 GPU 型号、数量或训练时长**，仅提供了计算时间比较表（表4）：在 Pendulum-v1 和 CartPole-v1 上运行 100,000 步，Adam-CBO 的 wall-time 分别为 1124.88 秒和 3444 秒，远高于其他方法（如 PPO 约 145-150 秒）。但论文指出这是因为 Adam-CBO 是单策略优化，而基准方法同时优化多个组件，且 Adam-CBO 在有限时间 horizon 的设置下需要更多采样步骤来评估成本函数。对于高维 LQG 和 Ginzburg-Landau 实验，仅提到 batch size、agent 数等，未报告训练时长。

## 5. 实验数量与充分性
- **实验组数**：相当充分。
  - LQG：5 种维度 × 2 种成本 = 10 组，对比 BSDE 和两种 CBO 方法。
  - Ginzburg-Landau：5 种维度，对比理论最优策略。
  - 均值场控制：3 种初始分布 × 4 种 agent 数 = 12 组，报告了不同时间的值函数。
  - 机器人系统：3 种 agent 数，可视化轨迹。
  - RL 任务：2 个环境，对比 6-7 种基线方法。
- **充分性评价**：实验覆盖了从简单到高维、从凸到非凸、从单体到多智能体/均值场的多种场景，且展示了收敛曲线和定量误差。但消融实验较少（仅对 batch size 做了变化，见图4）。未进行 M-CBO 与 Adam-CBO 的详细消融对比（例如动量项、自适应 m 的影响）。
- **客观性**：使用稳定基线库（stable-baselines3）的实现，比较时标注了基准方法的训练步骤和计算时间，并指出与直接比较存在不公平（基准优化多个组件，而 Adam-CBO 仅优化策略），但强调其优势在于梯度不可用时的通用性。这些说明较为客观。

## 6. 论文的主要结论与发现
- **主要结论**：提出的 Adam-CBO 方法能够**无梯度、无模型、无网格**地求解高维有限时间随机最优控制问题，在非凸成本下显著优于基于梯度的 BSDE 方法；在 RL 标准环境中，收敛速度更快（更少的迭代次数），虽然单步计算成本更高。
- **关键发现**：
  - CBO 框架结合动量有助于避免局部最优。
  - 自适应动量（类似 Adam）能进一步加速收敛。
  - 训练对 batch size 敏感，但总体鲁棒。
  - 在均值场控制中，训练好的策略可以推广到不同数量的智能体。
  - 理论上证明了 M-CBO 在假设下指数收敛到最优策略。

## 7. 优点
- **创新性**：首次将基于共识的优化（CBO）引入随机最优控制，提出梯度-free 的模型无关算法，填补了有限时间 horizon 下高维 SOC 方法的空白。
- **理论贡献**：提供了 M-CBO 的收敛性分析（Fokker-Planck 方程、平均场极限、能量指数衰减），这在强化学习中较为罕见。
- **方法优势**：
  - 无梯度：避免高方差问题。
  - 无模型：不依赖转移核知识。
  - 可扩展：在高维（16维以上）和非凸问题上表现优于深度 BSDE。
  - 可推广：均值场场景下训练策略可泛化至不同 agent 数。
  - 并行友好：粒子群可并行更新。
- **实验全面性**：覆盖 LQG（凸/非凸）、Ginzburg-Landau、均值场、多智能体导航、标准 RL benchmark，验证了广泛适用性。

## 8. 不足与局限
- **计算成本高**：Adam-CBO 的 wall-time 显著长于 PPO/SAC 等方法（表4），主要是由于需要为每个粒子评估值函数（需运行控制轨迹），采样开销大。论文未讨论如何通过并行化或减少采样来缓解。
- **缺乏消融研究**：未系统地分析 β、γ₁、γ₂、m、σ(t) 衰减率等超参数对性能的影响，仅对 batch size 做了简单测试。
- **理论假设较强**：收敛性证明中假设成本函数满足 Lipschitz、二次增长、局部反函数等条件，这些在真实复杂问题中可能不成立。且仅分析了 M-CBO，未分析 Adam-CBO 的收敛性。
- **实验局限性**：
  - 在 Ginzburg-Landau 问题中，将训练策略与有限差分计算的“理论最优”比较，作者自己承认这并非真正的误差度量，而是验证一致性。
  - RL 基准比较中，论文承认直接对比不公平（基准优化多个网络），但未进行公平化处理（如用 CBO 替换 PPO 的优化器）。
  - 未在更复杂的连续控制任务（如 MuJoCo）上测试。
- **可复现性**：提供了代码链接，但未详细说明随机种子、硬件配置、超参数选择细节，可能导致复现困难。
- **batch size 敏感性**：图4显示训练精度对 batch size 敏感，论文未提出自适应采样等有效缓解策略。

（完）
