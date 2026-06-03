---
title: "RVI-SAC: Average Reward Off-Policy Deep Reinforcement Learning"
title_zh: RVI-SAC：基于平均奖励的离策略深度强化学习方法
authors: "Yukinari Hisaki, Isao Ono"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=xB6YJZOKyT"
tags: ["query:graph-part"]
score: 7.0
evidence: 使用平均奖励标准的新型离策略深度强化学习方法
tldr: 该论文针对折现奖励准则在持续任务中训练目标与性能指标不一致的问题，提出了基于平均奖励的离策略深度强化学习方法RVI-SAC。它通过相对值迭代Q学习更新Critic，结合平均奖励软策略改进定理更新Actor，并自动调整重置成本，使得方法更适用于持续学习环境。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-xb6yjzokyt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1606, \"height\": 975, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xb6yjzokyt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1648, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xb6yjzokyt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1551, \"height\": 989, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xb6yjzokyt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1565, \"height\": 994, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-xb6yjzokyt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1106, \"height\": 671, \"label\": \"Table\"}]"
motivation: 折现奖励准则在持续任务中可能导致训练目标与实际性能不符。
method: 采用相对值迭代Q学习和平均奖励策略改进，扩展SAC至平均奖励设置。
result: 在多个持续控制任务上优于折现奖励基线和平均奖励基线。
conclusion: RVI-SAC为持续任务中的深度强化学习提供了更一致的优化目标。
---

## Abstract
In this paper, we propose an off-policy deep reinforcement learning (DRL) method utilizing the average reward criterion. While most existing DRL methods employ the discounted reward criterion, this can potentially lead to a discrepancy between the training objective and performance metrics in continuing tasks, making the average reward criterion a recommended alternative. We introduce RVI-SAC, an extension of the state-of-the-art off-policy DRL method, Soft Actor-Critic (SAC), to the average reward criterion. Our proposal consists of (1) Critic updates based on RVI Q-learning, (2) Actor updates introduced by the average reward soft policy improvement theorem, and (3) automatic adjustment of Reset Cost enabling the average reward reinforcement learning to be applied to tasks with termination. We apply our method to the Gymnasium's Mujoco tasks, a subset of locomotion tasks, and demonstrate that RVI-SAC shows competitive performance compared to existing methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **折现奖励准则的局限性**：现有的深度强化学习（DRL）方法大多采用折现奖励准则，该准则在持续任务中可能导致训练目标（折现累积回报）与实际性能指标（长期平均奖励）不一致。即使将折扣因子设为接近 1 也无法从根本上解决，反而会带来收敛不稳定、速度慢的问题。
- **平均奖励准则的优势**：在持续任务（如机器人运动）中，平均奖励准则以无限时域上的时间平均回报为目标，更符合任务本质，但此前在该准则下的离策略DRL方法（特别是结合最大熵思想的）几乎空白。
- **论文目标**：将最先进的离策略最大熵方法 Soft Actor-Critic (SAC) 扩展到平均奖励准则，提出 RVI-SAC，以解决折现准则带来的偏差，并保持样本效率。

## 2. 方法论：核心思想、关键技术细节
### 2.1 整体框架
RVI-SAC 在 Actor-Critic 架构下，将折扣奖励下的 SAC 改造成平均奖励版本，包含三个关键组件：

### 2.2 Critic 更新：基于 RVI Q-learning + Delayed f(Q) Update
- **RVI Q-learning**：采用相对值迭代（Relative Value Iteration）形式的 Bellman 方程，其目标为：
  - \( Y(r,s') = r - f(Q) + \max_{a'} Q(s',a') \)
  - 其中 \( f(Q) \) 是用于估计平均奖励的参考函数（如 \(\mathbb{E}_s[\max_a Q(s,a)]\)）。
- **Delayed f(Q) Update**：为避免直接使用 mini-batch 估计 \( f(Q) \) 引入的高方差，引入平滑参数 \(\xi_t\)：
  - \(\xi_{t+1} = \xi_t + \beta_t (f(Q; B) - \xi_t)\)
  - 用 \(\xi_t\) 替代原目标中的 \( f(Q) \)，稳定学习。论文给出了表格设定下的渐近收敛证明。
- **Q 网络更新**：最小化 MSE 损失：
  - \( \frac{1}{|B|} \sum (r - \xi + \min_j Q_{\phi'_j}(s',a') - \alpha \log \pi(a'|s') - Q_{\phi_i}(s,a))^2 \)

### 2.3 Actor 更新：平均奖励软策略改进定理
- **定义**：平均奖励下的软 Q 函数和软平均奖励 \( \rho^\pi_{\text{soft}} \)。
- **定理证明**：若新策略 \( \pi_{\text{new}} \) 通过最小化 KL 散度（同 SAC 形式）得到，则其软平均奖励不低于旧策略，即 \( \rho^{\pi_{\text{new}}}_{\text{soft}} \ge \rho^{\pi_{\text{old}}}_{\text{soft}} \)。
- **实际更新**：沿用 SAC 的策略损失形式：
  - \( J(\theta) = \frac{1}{|B|} \sum \left( \alpha \log \pi_\theta(a'|s) - \min_j Q_{\phi_j}(s,a') \right) \)

### 2.4 自动重置成本调整（Automatic Reset Cost Adjustment）
- **问题**：运动任务中因摔倒导致 episode 终止，违反平均奖励的无限时域假设。需要引入重置成本（Reset Cost）并将终止视为继续。
- **方法**：构建约束优化问题：max \(\rho^\pi\)  s.t. \(\rho^\pi_{\text{reset}} \le \epsilon_{\text{reset}}\)，其中 \(\rho^\pi_{\text{reset}}\) 是到达终止状态的频率。
- **求解**：利用对偶变量 \(\lambda\)（即重置成本），通过交替更新：内层固定 \(\lambda\) 优化策略（等价于带固定重置成本的平均奖励 RL），外层调整 \(\lambda\) 以约束终止频率。用另一个 Q 网络估计 \(\rho^\pi_{\text{reset}}\)。

## 3. 实验设计
### 3.1 数据集 / 场景
- **环境**：Gymnasium 的 Mujoco 任务，包括 Ant、HalfCheetah、Hopper、Walker2d、Humanoid、Swimmer。其中 Swimmer 和 HalfCheetah 无终止，其余有终止。
- **评价指标**：总回报（1,000 步累积奖励）及平均奖励（总回报 / 生存步数）。

### 3.2 Benchmark 与对比方法
- **对比方法**：
  - SAC 在三个折扣率（0.97、0.99、0.999）下的表现。
  - 现有平均奖励离策略方法 ARO-DDPG（基于 DDPG）。
  - 消融实验中的变体（固定重置成本的 RVI-SAC、无延迟更新的版本、使用参考状态的版本）。

### 3.3 实验设置
- **随机种子**：每个算法 10 个不同随机种子。
- **评估频率**：每 5,000 步采样一次评估分数。

## 4. 资源与算力
论文中**未明确说明**所使用的 GPU 型号、数量以及训练时长。仅提供了超参数表（如学习率 3e-4、batch size 256、replay buffer 大小 1e6 等），但未涉及硬件配置。

## 5. 实验数量与充分性
- **主实验**：在 6 个 Mujoco 任务上与 SAC（三个折扣率）和 ARO-DDPG 对比，每个种子运行完整训练，曲线平滑，比较充分。
- **消融实验**：
  1. **自动重置成本 vs 固定重置成本**：在 Ant 上比较了 rcost=0,10,100,250,500。
  2. **延迟更新 vs 无延迟 vs 参考状态**：对比 RVI-SAC、无延迟版本、三种不同参考状态的变体。
  3. **与带重置成本的 SAC 和 ARO-DDPG 对比**：在四个含终止的环境上验证平均奖励准则本身的效果。
- **充分性与客观性**：实验设计较为全面，覆盖了主要对比对象和关键组件验证，种子数适中，结果呈现均值和标准差，客观性较好。但缺少与平均奖励在线策略方法（如 APO、ATRPO）的对比。

## 6. 主要结论与发现
1. **性能优势**：RVI-SAC 在除 HalfCheetah 外的任务上表现持平或超越 SAC 在最优折扣率下的性能；在所有任务上显著优于 ARO-DDPG。
2. **折扣率选择的解放**：RVI-SAC 无需手动调优折扣率，避免了 SAC 因折扣率不当导致的性能波动（如 Swimmer 需极高折扣率，而高折扣率在其他任务上不稳定）。
3. **自动重置成本有效**：自动调整几乎达到最优固定重置成本的效果，而错误的手动设置会严重损害性能。
4. **延迟更新稳定学习**：相比直接使用 mini-batch 估计 f(Q)，延迟更新显著提升了学习稳定性和最终性能。
5. **理论支撑**：证明了平均奖励软策略改进定理，并给出了延迟更新的渐近收敛分析。

## 7. 优点
- **创新性**：首次将最大熵离策略方法（SAC）成功扩展到平均奖励准则，填补了该方向空白。
- **实用性**：自动重置成本调整使方法能直接应用于有终止的实际任务，减少了调参负担。
- **理论贡献**：提供平均奖励软策略改进定理和延迟更新的收敛性证明，增强了方法的可信度。
- **实验质量**：在多种 Mujoco 任务上进行了系统性对比和消融，结果清晰展示了各组件的必要性。

## 8. 不足与局限
- **对比缺失**：未与平均奖励在线策略方法（如 APO、ATRPO）对比，无法全面评估离策略 vs 在线策略在平均奖励下的优劣。
- **理论局限**：收敛证明仅在表格设定下完成，未扩展到函数逼近（神经网络）场景；实际应用中仍需依赖经验技巧。
- **实验覆盖**：仅在 Gymnasium Mujoco 任务上测试，缺乏更多类型的持续任务（如复杂机器人控制、真实世界物理系统）。
- **资源信息缺失**：未报告计算资源消耗，不利于复现和资源需求评估。
- **超参数敏感性**：虽然减少了折扣率调优，但引入了新的超参数（如 \(\epsilon_{\text{reset}}\)、延迟更新学习率 \(\kappa\)），其影响未深入分析。
- **未解决负值平均奖励下的收敛问题**：对于平均奖励可能为负的任务，文中未讨论是否影响算法稳定性。

（完）
