---
title: "RICE: Breaking Through the Training Bottlenecks of Reinforcement Learning with Explanation"
title_zh: RICE：利用解释突破强化学习训练瓶颈
authors: "Zelei Cheng, Xian Wu, Jiahao Yu, Sabrina Yang, Gang Wang, Xinyu Xing"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=PKJqsZD5nQ"
tags: ["query:graph-part"]
score: 7.0
evidence: 基于解释的强化学习训练瓶颈突破
tldr: 本文针对深度强化学习中训练瓶颈问题，提出RICE方案，利用解释方法识别关键状态，并将其作为新的初始状态分布，鼓励智能体探索。该方法在稀疏奖励任务中有效突破训练瓶颈，提升最终性能。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1747, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1768, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 526, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1782, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1772, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1771, \"height\": 815, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1776, \"height\": 820, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1609, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1770, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1773, \"height\": 954, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1776, \"height\": 959, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1777, \"height\": 954, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1769, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pkjqszd5nq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1059, \"height\": 568, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 604, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 972, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1766, \"height\": 308, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 737, \"height\": 662, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1528, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1627, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1099, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1353, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pkjqszd5nq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1766, \"height\": 307, \"label\": \"Table\"}]"
motivation: DRL训练容易陷入瓶颈，尤其稀疏奖励场景。
method: 利用解释方法构建混合初始状态分布。
result: 有效突破训练瓶颈，性能提升。
conclusion: 为强化学习训练提供了基于解释的改进策略。
---

## Abstract
Deep reinforcement learning (DRL) is playing an increasingly important role in real-world applications. However, obtaining an optimally performing DRL agent for complex tasks, especially with sparse rewards, remains a significant challenge. The training of a DRL agent can be often trapped in a bottleneck without further progress. In this paper, we propose RICE, an innovative refining scheme for reinforcement learning that incorporates explanation methods to break through the training bottlenecks. The high-level idea of RICE is to construct a new initial state distribution that combines both the default initial states and critical states identified through explanation methods, thereby encouraging the agent to explore from the mixed initial states. Through careful design, we can theoretically guarantee that our refining scheme has a tighter sub-optimality bound. We evaluate RICE in various popular RL environments and real-world applications. The results demonstrate that RICE significantly outperforms existing refining schemes in enhancing agent performance.

---

## 论文详细总结（自动生成）

# RICE论文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：深度强化学习（DRL）在复杂任务中常陷入训练瓶颈，尤其是在稀疏奖励场景下，智能体难以进一步提升性能。
- **现有方案缺陷**：
  - StateMask-R（Cheng et al., 2023）仅从关键状态精调，导致初始分布多样性缺失，引发过拟合；单独精调难以跳出局部最优。
  - Jump-Start RL（JSRL）随机选择探索边界，无法保证正收益。
- **核心动机**：利用解释方法自动识别关键状态，构建新的初始分布，结合探索突破瓶颈，并给出理论保证。

## 2. 方法论
- **核心思想**：通过解释方法（改进的StateMask）识别轨迹中的关键状态，构建混合初始状态分布（默认初始状态 + 关键状态），并采用随机网络蒸馏（RND）鼓励探索，从而提升策略性能。
- **关键技术细节**：
  - **步骤级解释**：改进StateMask，用奖励奖励（α·a_m）替代原约束优化，简化训练；用PPO直接训练掩码网络，输出“盲化”概率，重要状态得分高。
  - **混合初始分布构建**：从预训练策略π采样轨迹，用掩码网络选出最重要的状态，构成分布d̂_π；最终初始分布μ = β·d̂_π + (1-β)·ρ（ρ为默认初始分布）。
  - **探索机制**：采用RND奖励（||f(s') - f̂(s')||²）加入PPO优化，鼓励访问新状态。
- **理论保证**：
  - 定理3.3：扰动策略η(π̄) ≤ η(π)，因此最大化η(π̄)可替代原目标。
  - 引理3.5：采样改写相当于从更优策略π̂中采样。
  - 定理3.6：精炼策略的次优界限与分布不匹配系数成比例，使用解释方法可收紧界限。

## 3. 实验设计
- **数据集/场景**：
  - **模拟游戏**：MuJoCo（Hopper, Walker2d, Reacher, HalfCheetah）及稀疏奖励变体（SparseHopper等）。
  - **真实应用**：自私挖矿、网络防御（CAGE Challenge 2）、自动驾驶（MetaDrive）、恶意软件变异（MalConv环境）。
- **基准方法**：
  - **精炼方法对比**：PPO微调、StateMask-R（仅从关键状态微调）、JSRL。
  - **解释方法对比**：Random、StateMask、自己的掩码网络。
  - **额外对比**：自模仿学习（SIL），以及与其他解释方法（AIRS、Integrated Gradients）的组合。
- **评估指标**：Fidelity score（保真度）、最终奖励（累计奖励或逃避概率）。
- **超参数分析**：混合概率p、探索权重λ、掩码奖励α的敏感性。

## 4. 资源与算力
- 论文明确提到：所有实验在一台配备**8块NVIDIA A100 GPU**的服务器上进行。
- 训练时长：未给出具体小时数，但对比了效率：自己的掩码网络训练时间比原StateMask平均减少**16.8%**（见表4：如Hopper从15393秒降至12426秒等）。
- 未报告总训练轮次/步数对应的总能耗。

## 5. 实验数量与充分性
- **实验数量**：覆盖8个环境（4个MuJoCo + 4个真实应用），以及3个稀疏MuJoCo；每个环境多次重复（3个随机种子），报告均值和标准差。
- **消融研究**：
  - 固定解释方法，变化精炼方法（表1、图2）。
  - 固定精炼方法，变化解释方法（Random vs StateMask vs Ours）。
  - 混合初始分布必要性（p=0 vs p=1 vs 混合），探索必要性（λ=0 vs >0）。
  - 不同预训练算法（SAC + 模仿学习→PPO精炼，图3）。
  - 其他解释方法对比（表6）。
  - 案例研究（恶意软件变异）逐项加入设计思想验证过拟合（表7）。
- **充分性评价**：实验设计全面，涵盖了核心贡献的各个方面，对比基线合理，超参数敏感性分析充分，并补充了失败案例分析（MountainCar）。实验公平且客观。

## 6. 主要结论与发现
- RICE在所有测试环境上均显著优于现有精炼方案（PPO微调、StateMask-R、JSRL），平均提升最大。
- 自己的解释方法在保真度上与StateMask相当，但训练效率更高（平均省时16.8%）。
- 混合初始分布（0<p<1）和探索（λ>0）均为性能提升的关键因素；纯关键状态精调易过拟合。
- 理论分析表明，基于解释的混合初始分布可收紧次优界限。
- 发现恶意软件变异环境中的奖励设计缺陷（非马尔可夫性、中间奖励稀疏），修正后逃避率从42.2%升至72.0%。

## 7. 优点
- **方法创新**：首次将解释方法与混合初始分布、RND探索结合，系统解决精炼瓶颈问题。
- **理论支撑**：给出了次优界限分析，证明解释引导的采样比随机采样更优。
- **实验广泛**：覆盖多种模拟和真实应用，并包含稀疏奖励、不同预训练算法等扩展场景。
- **效率提升**：简化原StateMask训练过程，降低计算开销。
- **实际价值**：能够帮助开发者发现应用中的设计缺陷（如恶意软件变异），具有调试辅助作用。

## 8. 不足与局限
- **冷启动限制**：假定预训练策略已覆盖最优策略状态分布（Assumption 3.2）；若策略太弱（如MountainCar），解释无意义，方法退化为纯RND。
- **环境要求**：需要可在模拟器中重置到特定状态，现实场景中难以操作（如机器人物理环境）；可通过目标条件策略缓解但未验证。
- **关键状态过滤不足**：未考虑状态上策略是否已收敛到最优；面对已最优的关键状态时，重置无益。
- **超参数敏感性**：虽然文中说明p和λ在一定范围内鲁棒，但不同任务最优值仍需手动调整（如p=0.25或0.5，λ=0.01普遍好）。
- **未探讨其他解释方法**：仅验证了自己改进的StateMask，虽与AIRS/IG简单对比，但进一步泛化性未深入。

（完）
