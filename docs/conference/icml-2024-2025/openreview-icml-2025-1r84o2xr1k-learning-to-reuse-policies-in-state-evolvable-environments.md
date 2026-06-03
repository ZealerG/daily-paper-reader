---
title: Learning to Reuse Policies in State Evolvable Environments
title_zh: 在状态可演化环境中学习重用策略
authors: "Ziqian Zhang, Bohan Yang, Lihe Li, Yuqi Bian, Ruiqi Xue, Feng Chen, Yi-Chen Li, Lei Yuan, Yang Yu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=1R84O2Xr1k"
tags: ["query:graph-part"]
score: 7.0
evidence: 强化学习中状态演化下的策略重用
tldr: 该论文将状态特征演化问题形式化为状态可演化强化学习（SERL），提出一种策略重用方法以应对传感器变化导致的状态空间改变。所提方法能够在状态特征部分更新时，通过巧妙的迁移学习机制保持策略性能，避免从头训练。实验证明该方法在多种演化场景下优于现有基线。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1550, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1736, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 821, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 809, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 835, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1023, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1027, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1721, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 868, \"height\": 269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1752, \"height\": 845, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1267, \"height\": 1316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1761, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1388, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1711, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1768, \"height\": 1110, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1754, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1r84o2xr1k/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 868, \"height\": 591, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-1r84o2xr1k/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1752, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1r84o2xr1k/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1744, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1r84o2xr1k/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 732, \"height\": 1340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1r84o2xr1k/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 914, \"height\": 832, \"label\": \"Table\"}]"
motivation: 部署的RL策略在状态特征发生变化（如传感器更换）时会失效，现有方法无法保证性能。
method: 形式化SERL问题，并设计一种策略重用机制，利用源策略的知识适应新状态空间。
result: 在多种演化场景下显著缓解了策略性能下降，优于现有基线方法。
conclusion: 为解决实际部署中状态变化导致的策略失效问题提供了有效方案。
---

## Abstract
The policy trained via reinforcement learning (RL) makes decisions based on sensor-derived state features. It is common for state features to evolve for reasons such as periodic sensor maintenance or the addition of new sensors for performance improvement. The deployed policy fails in new state space when state features are unseen during training. Previous work tackles this challenge by training a sensor-invariant policy or generating multiple policies and selecting the appropriate one with limited samples. However, both directions struggle to guarantee the performance when faced with unpredictable evolutions. In this paper, we formalize this problem as state evolvable reinforcement learning (SERL), where the agent is required to mitigate policy degradation after state evolutions without costly exploration. We propose **Lapse** by reusing policies learned from the old state space in two distinct aspects. On one hand, Lapse directly reuses the *robust* old policy by composing it with a learned state reconstruction model to handle vanishing sensors. On the other hand, the behavioral experience from the old policy is reused by Lapse to train a newly adaptive policy through offline learning, better utilizing new sensors. To leverage advantages of both policies in different scenarios, we further propose *automatic ensemble weight adjustment* to effectively aggregate them. Theoretically, we justify that robust policy reuse helps mitigate uncertainty and error from both evolution and reconstruction. Empirically, Lapse achieves a significant performance improvement, outperforming the strongest baseline by about $2\times$ in benchmark environments.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：强化学习（RL）策略依赖于传感器-derived 的状态特征进行决策。实际部署中，状态特征可能因周期性传感器维护、新传感器性能提升等原因发生演化（evolve），导致已训练的策略在新状态空间中失效（因为训练时未见过的特征）。
- **现有方法局限**：①训练传感器不变策略（sensor-invariant policy）需要已知哪些特征是任务相关的，且假设先验知识；②生成多个源策略并在部署时选择合适的一个（通过高层策略或价值函数），但需要穷举所有可能的演化，不现实。两者都无法保证在不可预测的演化下的性能。
- **核心问题**：在无昂贵探索的条件下，如何使策略适应状态演化？论文将该问题形式化为**状态可演化强化学习（SERL）**，提出一种策略重用方法，在状态变化后缓解策略退化。

## 2. 方法论

### 核心思想
- 从两个方向重用旧策略的知识：①直接重用：通过**状态重建模型**将新状态映射回旧状态，组合旧鲁棒策略；②间接重用：通过**离线RL**从旧策略的行为经验中训练新自适应策略，并利用新传感器信息。
- 最后通过**自动集成权重调整**聚合两个策略的优势。

### 关键技术细节

1. **鲁棒策略重用（Robust Policy Reuse with State Reconstruction）**
   - 假设在短暂过渡期内可以同时观测到新旧状态特征，收集配对数据 $(s_n, s_{n+1})$。
   - 使用条件生成对抗网络（Conditional GAN）学习状态重建模型 $g_n: \mathcal{S}_{n+1} \to \Delta(\mathcal{S}_n)$，目标函数：
     $$L_{n+1}^{\text{recon}} = L_{n+1}^{\text{GAN}} + \lambda L_{n+1}^{L_p}$$
   - 组合得到策略 $\pi_{n+1}^{\text{recon}} = \pi_n \circ g_n$。
   - 为缓解重建误差导致的行为变化，对初始策略 $\pi_0$ 进行**鲁棒正则化**（通过Wocar-PPO或RADIAL-DQN），最小化扰动下的动作分布差异：
     $$L_n^{\text{robust}} = \mathbb{E}\left[ \max_{\hat{s}_n \in T_{\epsilon_n}(s_n)} D_{\text{TV}}(\pi_n(\cdot|s_n), \pi_n(\cdot|\hat{s}_n)) \right]$$

2. **行为知识重用（Offline Policy Learning with Knowledge Reuse）**
   - 使用离线RL从数据集 $\mathcal{D}_n$ 中学习新策略 $\pi_{n+1}^{\text{off}}$。
   - 连续动作空间（MuJoCo）：采用TD3+BC，损失为：
     $$\hat{L}_{n+1}^{\text{off}} = -\mathbb{E}_{(s_{n+1},a)\sim\mathcal{D}_n}\left[ -(\pi_{n+1}^{\text{off}}(s_{n+1})-a)^2 + \beta_{n+1} Q_{n+1}(s_{n+1}, \pi_{n+1}^{\text{off}}(s_{n+1})) \right]$$
   - 离散动作空间（Atari）：采用CQL。
   - 同时加入鲁棒正则化项 $L_{n+1}^{\text{robust}}$（基于函数平滑）。

3. **自动集成权重调整（Automatic Ensemble Weight Adjustment）**
   - 最终策略为线性集成：$\pi_{n+1} = \kappa_{n+1} \pi_{n+1}^{\text{recon}} + (1-\kappa_{n+1}) \pi_{n+1}^{\text{off}}$。
   - 权重 $\kappa_{n+1}$ 根据旧策略性能衰退和两个子策略与旧策略的相似度自动计算：
     $$\kappa_{n+1} = \frac{J_n(\pi_n)}{J_0(\pi_0)} \cdot \frac{D(\pi_n, \pi_{n+1}^{\text{off}})}{D(\pi_n, \pi_{n+1}^{\text{recon}}) + D(\pi_n, \pi_{n+1}^{\text{off}})}$$

4. **理论分析**
   - 定义了 $\epsilon_R-\epsilon_P$ 一致性来刻画演化不确定性。
   - 命题3.2表明，若使用理想的逆映射 $f_n^{-1}$，性能差距仅由演化不确定性决定。
   - 命题3.3证明，若旧策略鲁棒，结合近似重建模型 $g_n$ 的性能差距有界，从而验证鲁棒正则化的必要性。

## 3. 实验设计

- **环境与任务**：
  - **MuJoCo**（向量状态、连续动作）：Ant, HalfCheetah, Hopper, Walker
  - **Atari**（像素图像、离散动作）：BankHeist, Freeway, Pong, RoadRunner
- **演化设定**：每个任务经历5个演化阶段，演化包括传感器去除、添加、旋转、线性映射（带噪声）等。每次演化前收集少量过渡数据（MuJoCo 10条轨迹，Atari 15条）。
- **对比方法**：RL-GAN, LUSR, PAD, Offline（直接离线RL）, FPT（Few-shot Policy Transfer）, CUP（Critic-guided policy reuse）。所有方法在同样设置下评估。
- **评估指标**：归一化回报（相对初始阶段），5个阶段平均值。每个结果基于5个随机种子和标准差。

## 4. 资源与算力

- 论文**未明确说明**所用的GPU型号、数量或训练时长。仅提及代码已开源，但未提供算力细节。因此无法评估其计算开销。

## 5. 实验数量与充分性

- **实验数量**：
  - 8个任务上对比6个基线，报告5阶段平均性能（Table 1）。
  - 连续适应能力曲线（Figure 2，8个任务全部展示）。
  - 单阶段理论验证（Figure 3）：鲁棒和 vanilla 策略重建对比。
  - 学习过程分析（Figure 4）：HalfCheetah中重建策略、离线策略、集成权重动态。
  - 消融研究（Figure 5a, 12）：去除各组件（W/o recon, W/o offline, W/o robust, W/o kappa）在Pong等任务上。
  - 参数敏感性（Figure 5b, 15）：λ, β_max, α_robust等。
  - 数据集大小敏感性（Figure 16）：6~18条轨迹。
  - 更多演化阶段（15 stage，Figure 17）。
  - 剪枝策略效果（Table 4）。
- **充分性与公平性**：
  - 实验覆盖向量和像素两种输入，动作连续和离散，演化类型多样。
  - 基线方法包括域适应、多策略重用、离线RL等，比较全面。
  - 多次随机种子，标准差已报告。消融实验充分验证各组件贡献。
  - 但**缺乏大规模真实机器人实验**，仅在模拟器中验证。

## 6. 主要结论与发现

- Lapse在全部8个任务上平均保留**91.09%**的初始性能，最强基线（Offline）为45.51%，提升约2倍。
- 鲁棒策略重用能有效缓解重建误差导致的性能下降，离线自适应策略能利用新传感器信息，自动集成权重策略能自适应调整两个策略的依赖。
- 理论分析表明鲁棒性可限制性能差距，实验验证了行动差异与重建误差的关系。
- 在15个演化阶段中，Lapse在三个任务上仍保持良好性能，但在Walker上后期下降（可能与TD3+BC内置局限性有关）。

## 7. 优点

1. **问题新颖性与完整性**：首次形式化SERL问题，并提出完整的策略重用框架。
2. **方法创新**：双重重用（直接通过重建+间接通过离线学习）与自动集成权重设计巧妙，无需额外探索。
3. **理论支撑**：给出性能差距上界，证明鲁棒正则化的必要性。
4. **实验全面**：覆盖多种环境、多种演化类型、多组消融和敏感性分析，结果具说服力。
5. **可扩展性**：提出剪枝策略降低存储和推理开销，适用于多阶段演化。

## 8. 不足与局限

1. **依赖过渡期数据**：需要短暂时间同时观测新旧特征，某些无法暂停的场景可能不适用。
2. **极端演化情况下性能下降**：如在Walker任务15阶段后，因离线RL算法（TD3+BC）效率不足，性能退化。
3. **缺少真实世界验证**：仅在模拟器上实验，未在真实机器人或传感器平台上测试。
4. **未报告计算资源**：无法评估方法的训练成本，限制了可复现性评估。
5. **假设先验知道哪些传感器变化**：虽然合理，但在某些完全不可预测的演化中可能不成立。

（完）
