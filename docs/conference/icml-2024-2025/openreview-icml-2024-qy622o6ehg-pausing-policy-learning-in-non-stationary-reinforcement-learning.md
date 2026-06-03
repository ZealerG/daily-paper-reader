---
title: Pausing Policy Learning in Non-stationary Reinforcement Learning
title_zh: 非平稳强化学习中的策略学习暂停
authors: "Hyunin Lee, Ming Jin, Javad Lavaei, Somayeh Sojoudi"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=qY622O6Ehg"
tags: ["query:graph-part"]
score: 9.0
evidence: 通过暂停策略更新应对非平稳性的强化学习框架
tldr: 在非平稳强化学习中，持续更新策略并非最优。本文提出一个在线学习框架，通过策略性地暂停决策更新来管理偶然不确定性，并理论计算了最优的更新与暂停时长比。实验证明暂停操作能提供更紧的动态遗憾上界，在多个任务上提升了整体性能。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 808, \"height\": 228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 821, \"height\": 167, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 832, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 828, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 829, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 850, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 816, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 816, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1532, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1531, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1714, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1714, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1715, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-qy622o6ehg/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1711, \"height\": 659, \"label\": \"Figure\"}]"
motivation: 持续更新策略在时变环境中可能不是最优，需要管理偶然不确定性。
method: 提出在线强化学习框架，通过预测环境和暂停策略更新来平衡探索与利用。
result: 导出了最优策略更新与暂停时长比，并在实验中验证了性能提升。
conclusion: 策略性地暂停更新能改善非平稳RL的动态遗憾和整体表现。
---

## Abstract
Real-time inference is a challenge of real-world reinforcement learning due to temporal differences in time-varying environments: the system collects data from the past, updates the decision model in the present, and deploys it in the future. We tackle a common belief that continually updating the decision is optimal to minimize the temporal gap. We propose forecasting an online reinforcement learning framework and show that strategically pausing decision updates yields better overall performance by effectively managing aleatoric uncertainty. Theoretically, we compute an optimal ratio between policy update and hold duration, and show that a non-zero policy hold duration provides a sharper upper bound on the dynamic regret. Our experimental evaluations on three different environments also reveal that a non-zero policy hold duration yields higher rewards compared to continuous decision updates.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：在非平稳强化学习（Non-stationary RL）中，环境随时间变化，智能体基于过去数据更新策略并部署到未来。常见假设是“持续更新策略可以最小化时间差距”，但本文挑战这一假设，指出持续更新并非最优，反而可能因过度反应而增加动态遗憾。
- **整体含义**：本文提出一种“预测加策略性暂停”的在线RL框架，通过管理**偶然不确定性（aleatoric uncertainty）**（即环境内在不确定性）来提升整体性能。理论证明暂停策略更新能获得更紧的动态遗憾上界，实验验证在多个非平稳任务中非零暂停时长可带来更高奖励。

## 2. 方法论
- **核心思想**：将学习过程分为**策略更新阶段**和**策略暂停阶段**，通过计算最优的更新时长与暂停时长之比，平衡策略优化误差与环境变化带来的非平稳性误差。
- **关键技术细节**：
  - **预测未来Q值**：在每次策略更新时刻 \(t_m\)，利用过去 \(l_p\) 步的Q值估计，通过线性预测（最小二乘）得到未来Q值 \(\tilde{Q}_{t_{m+1}|t_m}\)，并保证预测误差被界。
  - **策略更新**：基于预测的未来Q值，使用**自然策略梯度（Natural Policy Gradient）** 结合熵正则化，更新 \(G_m\) 次。
  - **策略暂停**：在 \(N_m\) 时长内保持最新策略不变，暂停优化。
  - **算法流程**：Algorithm 1（Forecasting Online RL）描述了整体流程，其中 `ForQ` 函数实现未来Q值预测，`Update` 函数执行策略更新，并在暂停阶段固定策略。
  - **理论结果**：
    - 将动态遗憾分解为策略优化遗憾 \(R^\pi_m\)、Q值预测遗憾 \(R^f_m\) 和非平稳性遗憾 \(R^\text{env}_m\)（Theorem 5.3）。
    - 在非平稳环境下，存在非零最优暂停时长 \(N^*_m\)（Proposition 5.6）。
    - 通过求解凸优化问题得到最优更新/暂停时长关系（Theorem 5.8），并给出数值示例（Figures 4,5）展示如何随环境不确定性参数变化。

## 3. 实验设计
- **数据集/场景**：
  - **Switching Goal Cliffworld**：低维表格MDP（12×3），奖励目标在训练中途切换一次。
  - **MuJoCo 环境**：高维连续控制，包括 **Swimmer-v2** 和 **HalfCheetah-v2**。通过修改奖励函数（前进速度随正弦变化）引入非平稳性。
- **Benchmark 和对比方法**：
  - Cliffworld：对比 **Q-learning**（反应式方法） vs  **Future Q（FQ）**（使用预测的未来Q值）。
  - MuJoCo：对比 **SAC（Soft Actor-Critic）**（基线） vs  **FSAC（Forecasting SAC）**（本文提出的预测+暂停版本）。FSAC的超参数包括预测长度 \(l_f\) 和更新频率 \(\gamma_f\)（决定暂停比例）。
- **评估指标**：平均奖励/步（对应动态遗憾）。

## 4. 资源与算力
- 文中在附录 F.1 中明确说明：所有实验基于 **12 个 Intel Xeon CPU E5-2690 v4** 和 **2 块 Tesla V100 GPU**。
- 未提及具体训练时长或分布式配置，但符合标准学术实验规模。

## 5. 实验数量与充分性
- **Cliffworld**：在 6 组不同的步长 \(\alpha\) 和 \(\epsilon\) 超参数组合下运行，结果展示了平均奖励曲线（Figure 6）。
- **MuJoCo**：对每个环境，使用 36 种不同超参数组合（学习率 4×、软更新参数 3×、熵正则参数 3×），分别测试了 \(l_f=5,20\)（HalfCheetah）和 \(l_f=5,15\)（Swimmer），共 36×2 = 72 组实验。每个实验绘制了 FSAC 和 SAC 的奖励曲线（Figures 7-8 及附录详细图），误差棒为 0.5 标准差。
- **充分性与公平性**：实验覆盖了多个超参数空间，并统计了平均表现，对比了同一超参数下 FSAC 与 SAC。但缺少对暂停时长最优性的直接验证（如消融不同 \(\gamma_f\) 的统计检验），也未与其他非平稳RL方法（如 Restart Q-learning）对比。整体实验设计较为充分，但仍有拓展空间。

## 6. 论文的主要结论与发现
1. **暂停策略更新可提升性能**：在三个非平稳环境中，非零暂停时长（\(\gamma_f < 1\)）的 FSAC 平均奖励普遍高于持续更新（\(\gamma_f = 1.0\)）的 SAC。
2. **预测优于反应**：Cliffworld 中，使用未来Q值预测的 FQ 在目标切换后更快收敛到最优策略，而反应式 Q-learning 失败。
3. **理论支持**：非零策略暂停时长能提供更紧的动态遗憾上界，最优更新/暂停比取决于环境非平稳性（如变化速率、幅度）。
4. **学习率影响**：高学习率下策略优化更快收敛，因此最优暂停时长更长（Figure 5b）。

## 7. 优点
- **理论深度**：给出了完整的动态遗憾上界分解，并推导了最优更新/暂停时长的解析表达式（尽管是隐式方程），揭示了暂停机制在非平稳环境中的关键作用。
- **方法新颖**：将预测未来Q值与暂停策略更新结合，区别于传统的持续学习或重启策略，对实时推断问题有实际意义。
- **实验验证**：在低维和高维环境中均进行了验证，且考虑了多种超参数变体，结果稳健。
- **清晰的可视化**：通过数值模拟展示了最优暂停时长如何随环境不确定性参数（\(\alpha, B^{\max}\)）变化，增强理论直观性。

## 8. 不足与局限
- **假设较强**：理论部分依赖指数阶变化预算假设（Assumption 3.1）和精确Q值估计（Corollary 4.3），现实中可能不成立。
- **预测误差影响未深入分析**：虽然给出了预测误差的界，但未研究如何自适应地选择预测长度 \(l_f\) 或更新频率 \(\gamma_f\)；实验中的 \(l_f\) 和 \(\gamma_f\) 为人工设定。
- **对比方法有限**：仅与标准 SAC 和 Q-learning 对比，未与其他非平稳RL方法（如 restart-based、meta-learning）比较。
- **可扩展性不足**：实验仅在 2 GPU 上运行，未测试更大规模或真实物理系统；高维环境仅用 MuJoCo 两个任务。
- **缺乏统计显著性检验**：实验结果以平均和标准差展示，但未进行 t 检验等显著性分析，部分差异可能由随机波动引起。
- **应用限制**：暂停策略适用于具有明确“计划-部署”周期的系统（如推荐、控制），不适用于需要实时响应的连续交互任务。

（完）
