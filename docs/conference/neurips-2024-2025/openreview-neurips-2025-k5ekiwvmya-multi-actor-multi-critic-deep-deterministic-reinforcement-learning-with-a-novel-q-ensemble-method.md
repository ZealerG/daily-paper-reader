---
title: Multi-Actor Multi-Critic Deep Deterministic Reinforcement Learning with a Novel Q-Ensemble Method
title_zh: 多智能体多评论家深度确定性强化学习与新型Q集成方法
authors: "Andy Wu, Chun-Cheng Lin, Rung-Tzuo Liaw, Yuehua Huang, Chihjung Kuo, Chia-Tong Weng"
date: 2025-05-10
pdf: "https://openreview.net/pdf?id=k5ekIwvmYA"
tags: ["query:graph-part"]
score: 8.0
evidence: 多智能体多评论家深度确定性强化学习与Q集成方法
tldr: 现有深度确定性强化学习存在值函数高估或低估问题。本文提出多智能体多评论家架构，通过Q集成方法提高策略评估准确性。实验表明该方法在连续控制任务上提升了样本效率和最终性能，为解决复杂RL问题提供了新思路。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-k5ekiwvmya/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1396, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k5ekiwvmya/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1422, \"height\": 211, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k5ekiwvmya/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1418, \"height\": 408, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-k5ekiwvmya/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1379, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k5ekiwvmya/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1215, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k5ekiwvmya/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1208, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k5ekiwvmya/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k5ekiwvmya/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1386, \"height\": 177, \"label\": \"Table\"}]"
motivation: 现有深度强化学习在连续动作空间中存在值函数估计偏差，影响策略学习效果。
method: 提出多智能体多评论家架构，集成多个Q函数来减少估计偏差，采用确定性策略梯度进行优化。
result: 在多个连续控制基准任务上，该方法优于现有单评论家和集成方法，提升了样本效率和最终回报。
conclusion: 多智能体多评论家架构结合Q集成能有效缓解值函数偏差，是深度RL性能提升的有效手段。
---

## Abstract
Abstract Reinforcement learning has gathered much attention in recent years due to its rapid development and rich applications, especially on control systems and robotics. When tackling real-world applications with reinforcement learning method, the corresponded Markov decision process may have huge discrete or even continuous state/action space. Deep reinforcement learning has been studied for handling these issues through deep learning for years, and one promising branch is the actor-critic architecture. Many past studies leveraged multiple critics to enhance the accuracy of evaluation of a policy for addressing the overestimation and underestimation issues. However, few studies have considered the architecture with multiple actors together with multiple critics. This study proposes a novel multi-actor multi-critic (MAMC) deep deterministic reinforcement learning method. The proposed method has three main features, including selection of actors based on non-dominated sorting for exploration with respect to skill and creativity factors, evaluation for actors and critics using a quantile-based ensemble strategy, and exploiting actors with best skill factor. Theoretical analysis proves the learning stability and bounded estimation bias for the MAMC. The present study examines the performance on a well-known reinforcement learning benchmark MuJoCo. Experimental results show that the proposed framework outperforms state-of-the-art deep deterministic based reinforcement learning methods. Experimental analysis also indicates the proposed components are effective. Empirical analysis further investigates the validity of the proposed method, and shows its benefit on complicated problems.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在深度强化学习中，基于 Actor-Critic 架构的方法在处理连续动作空间时，常面临值函数估计偏差（过高估计或过低估计）以及学习不稳定的问题。现有研究主要通过引入多个评论家（Critics）来提高估计精度，但很少探索同时使用多个行动者（Actors）和多个评论家的架构。
- **研究动机**：多行动者可以带来更好的探索多样性和策略多样性，而多评论家可以降低估计偏差和方差。将两者结合有望同时改善探索效率和学习稳定性。
- **整体含义**：本文提出一种新颖的多行动者多评论家（MAMC）深度确定性强化学习方法，通过非支配排序选择行动者、分位数集成评估以及技能因子等机制，在理论上保证学习稳定性和有界估计偏差，并在 MuJoCo 基准上验证了有效性。

## 2. 论文提出的方法论

### 核心思想
- **多行动者多评论家架构**：同时维护 $N_A$ 个行动者网络和 $N_C$ 个评论家网络，无预定配对关系，通过分位数集成估计目标值。
- **行动者选择与探索**：基于“技能因子”（Skill factor）和“创造力因子”（Creativity factor）两个目标，采用非支配排序（类似 NSGA-II 的拥挤比较算子）选择前 $\sqrt{N_A}$ 个行动者作为候选，然后随机选择一个与环境交互。
- **评论家学习**：每个评论家在自己的 mini-batch 上，以分位数集成的目标值进行 M 次更新（样本多次复用），并使用软更新目标网络。

### 关键技术细节
1. **分位数集成目标值**：
   - 对每个行动者 $\pi_{\phi_i}$，它在下一个状态 $s'$ 的估计值定义为：所有评论家网络输出的 $Q$ 值的 $q$ 分位数。
   - 然后取所有行动者估计值的中位数作为最终目标值 $y = r + \gamma \hat{V}_A(s')$。
   - 每个评论家通过最小化与这个目标值的均方误差来更新。
2. **行动者更新**：每个行动者轮流由每个评论家指导，使用标准确定性策略梯度损失。
3. **行动者评估因子**：
   - 技能因子：$J_s(\phi_i; C) = \frac{1}{N_B} \sum_{k} \hat{V}_{\phi_i}(s(k))$，衡量行动者的平均性能。
   - 创造力因子：$J_c(\phi_i; C) = \frac{1}{N_B N_C} \sum_k \sum_j |Q_{\theta_j}(s(k), \pi_{\phi_i}(s(k))) - \hat{V}_{\phi_i}(s(k))|$，衡量行动者对评论家的分歧程度（多样性）。
4. **算法流程**：初始化后，循环执行评论家学习、行动者学习、探索三个阶段，每轮用非支配排序选出候选行动者，并记录具有最高技能因子的最优策略用于最终部署。

### 公式说明（文字）
- 评论家损失：$J_Q(\theta_j) = \mathbb{E}[(Q_{\theta_j}(s,a) - (r + \gamma \hat{V}_A(s')))^2]$
- 行动者损失：$J_\pi(\phi_i) = \mathbb{E}[-Q_{\theta_j}(s, \pi_{\phi_i}(s))]$

## 3. 实验设计

- **数据集/场景**：使用 MuJoCo 基准中的5个连续控制环境：Hopper-v5, HalfCheetah-v5, Walker2d-v5, Ant-v5, Humanoid-v5。这些环境具有不同维度和难度。
- **基准方法**：
  - 确定性策略方法：TD3（双评论家）、DARC（双行动者双评论家）
  - 随机策略方法：SAC（双评论家）、REDQ（单行动者+10评论家）
- **对比方式**：所有基线方法都采用样本多次复用（SMR）版本以公平比较。实验进行了10次试验，每次试验平均20个种子。使用 Wilcoxon 秩和检验进行显著性分析（显著性水平0.05）。

## 4. 资源与算力

- 文中在附录中说明了计算资源：一台服务器，配备 Intel Xeon W7-2475X CPU（2.6 GHz，20核40线程），两块 NVIDIA RTX 4090 GPU（每块24GB显存），128GB 主内存。实验总步数为300k步，但未具体给出每实验的运行时长或总GPU时长。

## 5. 实验数量与充分性

- **实验组数**：
  - 主对比实验：5个环境 × 4个基线方法 = 20组对比，每个方法10次试验（每个试验20种子），计算平均回报和标准差。
  - 消融实验：MAMC vs MAMC-SO（单目标行动者选择）在Ant-v5上8次试验。
  - 成分分析：展示了最佳/最差/被选行动者的回报曲线。
  - 灵敏度分析：对分位数参数 q 在 {0.1, 0.2, 0.3, 0.4, 0.5} 上测试了 HalfCheetah 和 Walker2d。
- **充分性**：实验覆盖了多个难度的环境，进行了统计检验，消融和灵敏度分析较为充分。但环境数量仅为5个，且均为MuJoCo连续控制任务，可能缺乏对离散动作空间或更复杂场景的验证。对比方法均为SMR版本，但未与原始版本对比，可能存在差异。整体实验设计较为客观公平。

## 6. 论文的主要结论与发现

- MAMC 在早期和中期阶段（100k、200k步）显著优于 TD3-SMR 和 DARC-SMR，在后期（300k步）优势缩小但仍较优。
- 与 SAC-SMR 相比，MAMC 在前中期较好，后期略优；与 REDQ-SMR 相比，MAMC 在大部分环境上略逊一筹，尤其在 Humanoid 上被反超。
- 多目标行动者选择（技能+创造力）优于单目标平均方式，验证了其有效性。
- 分位数参数 q 的选择受环境偏好影响（乐观/悲观），推荐范围在 0.2~0.4 之间。
- 理论证明 MAMC 的方差低于单行动者和单评论家方法，估计误差介于最小和最大之间，具有有界性。

## 7. 优点

- **创新性**：首次系统性地提出多行动者多评论家架构，并设计了基于非支配排序的行动者选择机制，同时考虑性能（技能）和多样性（创造力）。
- **理论贡献**：给出了方差降低和估计误差有界的理论证明，为稳定性提供了保证。
- **工程技巧**：采用分位数集成、样本多次复用、软更新等，增强了学习鲁棒性。
- **实验验证**：在多个连续控制任务上进行了充分对比，并做了消融和灵敏度分析。

## 8. 不足与局限

- **环境覆盖不足**：只测试了5个 MuJoCo 环境，且均为连续动作空间，未涉及离散动作空间或更复杂的现实场景。
- **计算开销**：使用10个行动者和10个评论家，计算资源需求较大，未讨论可扩展性。
- **后期性能**：在与 REDQ（随机策略）的对比中后期被超越，表明确定性策略可能在探索更后期存在劣势，论文承认这一点。
- **超参数敏感**：分位数 q 的设置需要根据环境调整，缺乏自适应机制。
- **开放性代码**：虽然提供了匿名 GitHub 链接，但论文中未明确代码是否经过完整测试或公开许可。
- **未讨论社会影响**：论文指出是基础研究，未涉及潜在负面社会影响。

（完）
