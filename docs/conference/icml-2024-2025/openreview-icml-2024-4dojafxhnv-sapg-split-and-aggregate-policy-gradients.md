---
title: "SAPG: Split and Aggregate Policy Gradients"
title_zh: SAPG：拆分与聚合策略梯度
authors: "Jayesh Singla, Ananye Agarwal, Deepak Pathak"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=4dOJAfXhNV"
tags: ["query:graph-part"]
score: 9.0
evidence: 通过拆分聚合策略梯度实现RL并行决策
tldr: 当前的on-policy RL方法在利用大规模并行环境时性能饱和。该论文提出SAPG算法，将并行环境拆分为多个块，并通过重要性采样融合梯度，显著提升了在多种挑战性环境中的性能，有效解决了并行化带来的收益递减问题。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-4dojafxhnv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 865, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-4dojafxhnv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 841, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-4dojafxhnv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1778, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-4dojafxhnv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-4dojafxhnv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1770, \"height\": 841, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-4dojafxhnv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1769, \"height\": 843, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-4dojafxhnv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1769, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-4dojafxhnv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1772, \"height\": 436, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-4dojafxhnv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1777, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-4dojafxhnv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 710, \"height\": 637, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-4dojafxhnv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 703, \"height\": 587, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-4dojafxhnv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 706, \"height\": 592, \"label\": \"Table\"}]"
motivation: 现有RL方法如PPO在大规模并行环境中性能饱和，无法充分利用并行化优势。
method: 提出SAPG算法，将并行环境拆分为块，通过重要性采样聚合梯度进行训练。
result: 在多个挑战性环境中，SAPG显著优于PPO等基线方法。
conclusion: SAPG是一种能有效利用大规模并行环境的on-policy RL算法。
---

## Abstract
Despite extreme sample inefficiency, on-policy reinforcement learning, aka policy gradients, has become a fundamental tool in decision-making problems. With the recent advances in GPU-driven simulation, the ability to collect large amounts of data for RL training has scaled exponentially. However, we show that current RL methods, e.g. PPO, fail to ingest the benefit of parallelized environments beyond a certain point and their performance saturates. To address this, we propose a new on-policy RL algorithm that can effectively leverage large-scale environments by splitting them into chunks and fusing them back together via importance sampling. Our algorithm, termed SAPG, shows significantly higher performance across a variety of challenging environments where vanilla PPO and other strong baselines fail to achieve high performance. Webpage at https://sapg-rl.github.io/.

---

## 论文详细总结（自动生成）

# SAPG: Split and Aggregate Policy Gradients 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：On-policy 强化学习方法（如 PPO）在大规模并行环境（>10k 并行环境）下，随着批大小增加，性能会出现饱和。根本原因在于从同一高斯策略进行独立同分布采样，导致大量环境执行相似动作，数据多样性不足，浪费了并行计算能力。
- **背景**：现代 GPU 物理引擎（如 IsaacGym）可同时模拟数万环境，但现有 on-policy 算法无法有效利用这种大规模数据生成能力。需要一种新方法，在保持 on-policy 稳定性的同时，充分挖掘大规模并行带来的多样性收益。
- **整体含义**：作者提出了一种“拆分-聚合”策略梯度框架（SAPG），通过将环境分组并训练多个差异化策略，再借助重要性采样将异构数据聚合到单一领导者策略上，从而在更大数据规模下实现更高渐进性能。

## 2. 方法论

### 核心思想
- **拆分**：将 $N$ 个并行环境划分为 $M$ 个块（chunk），每个块训练一个不同的策略 $\pi_1,\ldots,\pi_M$。策略共享骨干网络参数 $B_\theta$，但拥有各自独立的条件参数 $\phi_i$ 以促进差异化。
- **聚合**：指定一个“领导者”策略（通常为 $\pi_1$）同时使用自己的 on-policy 数据和来自其他所有策略（跟随者）的 off-policy 数据，通过重要性采样进行更新。跟随者只使用各自的 on-policy 数据进行标准 PPO 更新。
- **促进多样性**：
  - **潜在条件编码**：共享骨干网络 + 每个策略独有的可学习参数 $\phi_i$（$R^{16}$ 或 $R^{32}$）。
  - **熵正则化**：对跟随者策略施加不同系数的熵损失 $\sigma \cdot H(\pi(a|s))$，调节探索-利用权衡。领导者无熵损失。

### 关键技术细节
- **Off-policy 更新公式**（基于 Meng et al., 2023）：
  $$L_{off}(\pi_i; X) = \frac{1}{|X|}\sum_{j\in X} \mathbb{E}_{(s,a)\sim\pi_j} [\min(r_{\pi_i}(s,a),\ \text{clip}(r_{\pi_i}(s,a), \mu(1-\epsilon), \mu(1+\epsilon))) A^{\pi_{i,old}}(s,a)]$$
  其中 $r_{\pi_i}=\frac{\pi_i}{\pi_j}$，$\mu=\frac{\pi_{i,old}}{\pi_j}$。
- **总损失**：$L(\pi_i) = L_{on}(\pi_i) + \lambda \cdot L_{off}(\pi_i; X)$，默认 $\lambda=1$，并通过子采样使 off-policy 数据量与 on-policy 数据量匹配。
- **Critic 更新**：on-policy 使用 n-step return（n=3），off-policy 使用 1-step return。
- **算法流程**（Algorithm 1）：
  1. 初始化共享参数 $\theta,\psi$ 及各策略条件参数 $\phi_i$。
  2. 每个迭代中，每个策略在其分配的环境块中收集数据。
  3. 领导者从所有跟随者数据中抽取子集，与自身 on-policy 数据合并，计算联合损失。
  4. 所有跟随者只使用自身数据计算 on-policy 损失。
  5. 更新共享参数 $\theta,\psi$ 及各 $\phi_i$。

## 3. 实验设计

### 使用场景/任务
- **平台**：GPU 加速模拟器 IsaacGym，并行 24576 个环境（默认）。
- **任务类型**：5 个操作任务，分为硬难度和易难度。
  - **硬任务（AllegroKuka）**：Allegro 手（16 DoF）+ Kuka 臂（7 DoF），共 23 自由度。包括：
    - **Regrasping**：将物体抓起到目标位置并保持。
    - **Throw**：将物体扔入桶中。
    - **Reorientation**：拿起物体并重新定向到目标位姿。
  - **易任务**：
    - **Shadow Hand**：24-DoF Shadow Hand 的 in-hand 重定向。
    - **Allegro Hand**：16-DoF Allegro Hand 的 in-hand 重定向。
- **性能指标**：硬任务使用“episode successes”（每次成功数），易任务使用 episode rewards。

### Benchmark 对比方法
- **PPO**（Schulman et al., 2017）：标准 on-policy，直接扩大批大小。
- **PQL**（Parallel Q-Learning, Li et al., 2023）：并行化 off-policy DDPG。
- **DexPBT**（Petrenko et al., 2023）：基于 PPO 的群体训练，引入超参数突变和策略替换。

### 参数设置
- SAPG 使用 $M=6$ 个策略（1 领导者 + 5 跟随者），总环境数 $N=24576$。
- 熵正则化系数 $\sigma$ 从 $\{0, 0.003, 0.005\}$ 中选择。
- 每个实验运行 5 个随机种子，报告均值与标准误。

## 4. 资源与算力

- **文中明确说明**：由于任务复杂，每轮实验约需 **48–60 小时**（在单 GPU 上），收集约 $2\times 10^{10}$ 个时间步的转换数据。
- **未明确说明**：GPU 型号（未指定是 A100、V100 还是其他），是否使用多 GPU 并行训练（从“single GPU”描述推测为单卡）。
- 作者指出由于在不同机器上运行，无法直接比较 wall-clock 时间，故以样本数量作为横轴。

## 5. 实验数量与充分性

### 实验组数
- **主要对比**：5 个任务 × 4 种方法（PPO、PBT、PQL、SAPG） × 5 种子 = 100 运行曲线。
- **消融实验**：
  - 不同熵系数（0, 0.003, 0.005）
  - 高 off-policy 比率（不去子采样）
  - 对称聚合（所有策略相互使用 off-policy 数据）
  - 无 off-policy 组合（仅用 on-policy）
- **多样性分析**：额外进行了 PCA 重建误差和 MLP 重建误差的对比实验（图 7、8）。

### 充分性与公平性
- **充分**：覆盖了多种任务难度，对比了 SOTA 基线，进行了关键设计选择消融。
- **公平**：所有方法使用相同环境数（24576）和类似策略容量；PBT 参数突变机制在超参数上具有额外自由度，但 SAPG 仍更优。
- **潜在偏差**：仅聚焦于操作任务，未在导航、运动控制等领域验证；熵正则化系数需针对环境手动调整。

## 6. 主要结论与发现

- PPO 和 PQL 在硬任务（AllegroKuka）上几乎无法学习有用行为（successes 接近 0）。
- SAPG 在所有任务上优于或持平所有基线：
  - **硬任务**：SAPG 比 DexPBT 高 12–66%（Regrasping 35.7 vs 31.9；Throw 23.7 vs 19.2；Reorientation 38.6 vs 23.2）。
  - **易任务**：SAPG 在 Allegro Hand 上比 PQL 高 21%（12300 vs 10100），在 Shadow Hand 上性能相当（12800 vs 12800），但渐进性能更高。
- **消融结论**：
  - 对称聚合导致所有策略行为趋同，性能大幅下降。
  - 高 off-policy 比率在简单环境中带来噪声，反而降低性能；在复杂环境中初期有益但后期应子采样。
  - 熵正则化在 Reorientation 任务（最复杂）中提升 16.5%，在其他任务中无显著收益。
- **多样性分析**：SAPG 遍历的状态空间比 PPO 更丰富（PCA 重建误差下降更慢，MLP 重建误差更高）。

## 7. 优点

- **方法创新性**：提出“拆分-聚合”范式，将大规模并行环境的优势从“量”转化为“质”，通过多策略差异化采样和 off-policy 重要性采样融合，解决了经典 on-policy 方法的数据冗余问题。
- **工程实用性**：基于 PPO 实现，保持其稳定性（clip、trust region），易于集成现有代码库；在 IsaacGym 上可直接部署。
- **实验完备性**：包含多任务、多基线、消融、多样性量化分析，结论可靠。
- **性能显著**：在多个挑战性任务上大幅超越 SOTA (DexPBT) 和 off-policy 方法 (PQL)，展示了大规模并行环境下 on-policy 算法的新潜力。

## 8. 不足与局限

- **实验覆盖范围有限**：仅涉及操作任务（AllegroKuka、Shadow Hand、Allegro Hand），未在运动控制（如四足/双足行走）、导航、游戏等场景测试。泛化能力未验证。
- **超参数敏感性**：熵正则化系数 $\sigma$ 需针对不同环境手动选择（文中只从有限集合搜索），缺乏自适应机制。
- **计算开销**：需要维护 $M$ 个策略（本文 M=6），虽共享骨干但参数和梯度计算量增加；训练时间达 48-60 小时，实际应用中对算力需求仍较高。
- **对称聚合失败**：实验中对称方案导致策略趋同，说明如何避免策略收敛仍是一个开放问题。
- **理论基础**：重要性采样在长序列 off-policy 更新中的偏差-方差分析较弱，仅采用 n-step 和 1-step return 的简化组合，缺乏严格收敛保证。
- **潜在偏差风险**：领导者-跟随者结构可能使领导者过度依赖跟随者选出的轨迹，若跟随者探索不足，领导者可能被困于局部最优。

（完）
