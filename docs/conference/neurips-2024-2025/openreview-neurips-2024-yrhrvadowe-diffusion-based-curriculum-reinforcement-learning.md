---
title: Diffusion-based Curriculum Reinforcement Learning
title_zh: 基于扩散的课程强化学习
authors: "Erdi Sayar, Giovanni Iacca, Ozgur S. Oguz, Alois Knoll"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=yRhrVaDOWE"
tags: ["query:graph-part"]
score: 7.0
evidence: 基于扩散模型的课程强化学习，融合Q函数和对抗内部动机
tldr: 现有课程强化学习方法在无领域知识时难以高效引导智能体。本文提出DiCuRL，利用条件扩散模型生成课程目标，并创新地融合Q函数和基于对抗内部动机的可训练奖励函数来评估目标接近度。扩散模型的去噪机制天然促进了探索。实验表明该方法在稀疏奖励环境中显著提升了学习效率和最终性能。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1406, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1429, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1324, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1407, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1406, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1176, \"height\": 992, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1173, \"height\": 1249, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1173, \"height\": 1166, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1427, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1240, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1428, \"height\": 654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1239, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1426, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1235, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1408, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yrhrvadowe/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1338, \"height\": 321, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-yrhrvadowe/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yrhrvadowe/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1374, \"height\": 607, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yrhrvadowe/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1233, \"height\": 494, \"label\": \"Table\"}]"
motivation: 课程强化学习在缺乏领域知识时难以有效生成递进任务序列指导智能体学习。
method: 利用条件扩散模型生成课程目标，结合Q函数和对抗内部动机设计的可训练奖励函数，并利用扩散过程促进探索。
result: 在多个稀疏奖励任务上，DiCuRL相比现有CRL方法实现了更快的收敛和更高的累积奖励。
conclusion: 扩散模型能有效生成结构化的课程目标，结合内在奖励机制能显著提升RL在困难任务中的学习效果。
---

## Abstract
Curriculum Reinforcement Learning (CRL) is an approach to facilitate the learning process of agents by structuring tasks in a sequence of increasing complexity. Despite its potential, many existing CRL methods struggle to efficiently guide agents toward desired outcomes, particularly in the absence of domain knowledge. This paper introduces DiCuRL (Diffusion Curriculum Reinforcement Learning), a novel method that leverages conditional diffusion models to generate curriculum goals. To estimate how close an agent is to achieving its goal, our method uniquely incorporates a $Q$-function and a trainable reward function based on Adversarial Intrinsic Motivation within the diffusion model. Furthermore, it promotes exploration through the inherent noising and denoising mechanism present in the diffusion models and is environment-agnostic. This combination allows for the generation of challenging yet achievable goals, enabling agents to learn effectively without relying on domain knowledge. We demonstrate the effectiveness of DiCuRL in three different maze environments and two robotic manipulation tasks simulated in MuJoCo, where it outperforms or matches nine state-of-the-art CRL algorithms from the literature.

---

## 论文详细总结（自动生成）

# 基于扩散的课程强化学习（DiCuRL）论文总结

## 1. 核心问题与整体含义（研究动机和背景）

课程强化学习（CRL）通过将任务按难度递增排列来辅助智能体学习，但现有方法在缺乏领域知识时难以高效生成合适的中间目标。许多方法依赖特定的分布假设、欧氏距离或几何信息，导致在复杂稀疏奖励环境中探索困难、样本效率低。本文旨在提出一种**环境无关**、无需领域知识的课程目标生成方法，利用扩散模型的生成能力和内在噪声机制来促进探索，并结合价值函数与内在奖励来确保目标的挑战性与可行性。

## 2. 方法论

### 核心思想
- 使用**条件扩散模型**，以当前状态为条件，从高斯噪声反向扩散生成课程目标。
- 训练损失由三部分组成：
  - 扩散损失（L_d）：最小化预测噪声误差，使模型捕捉已访问状态分布。
  - Q函数（最大化）：预测当前策略下从状态和目标出发的累积回报，确保目标可行。
  - 对抗内在动机（AIM）奖励函数（最大化）：估计智能体接近期望目标的程度，驱动课程逐渐向期望目标偏移。
- 扩散模型的加噪‑去噪过程天然引入探索性，生成的目标分布覆盖广泛区域。

### 关键技术细节
- 扩散模型基于DDPM框架，以状态s为条件，采样N=10个反向扩散步。
- 总损失函数：L = ξ_d·L_d - ξ_q·Q(s, g0, π) - ξ_r·r_φ(g0, g_d)，其中ξ_d=1, ξ_q=10, ξ_r=1。
- 反向扩散使用均值公式：μ_θ(g_k, s, k) = (1/√α_k)[g_k - (β_k/√(1-ᾱ_k)) ε_θ(g_k, s, k)]。
- 从重放缓冲区采样minibatch输入扩散模型，生成候选课程目标集G_c，再通过**最小费用最大流**二分图匹配选出最优目标gc。
- 基础RL算法使用**Soft Actor-Critic (SAC)**（迷宫任务）或**DDPG**（机器人任务），均为离线策略算法。

## 3. 实验设计

### 环境与场景
- **三个点迷宫**（PointUMaze、PointNMaze、PointSpiralMaze），在MuJoCo中模拟，目标为(x,y)位置，稀疏奖励。
- **两个机器人操作任务**（FetchPush、FetchPickAndPlace），在MuJoCo中模拟，扩大目标区域以增加难度，使用二元稀疏奖励。

### Benchmark与对比方法
- 对比9种SOTA CRL方法：**ACL、GoalGAN、HGG、ALP-GMM、VDS、PLR、CURROT、GRADIENT、OUTPACE**。
- 迷宫任务中统一使用SAC作为基础算法，机器人任务中使用DDPG，保证公平。

### 实验设置
- 每个方法在每种环境下使用**5个不同随机种子**，报告均值和标准差。
- 最大训练步数：迷宫任务1e6步，机器人任务20000步。
- 成功阈值：与期望目标距离小于0.5。

## 4. 资源与算力

- 硬件：**NVIDIA RTX A5000 GPU、64GB RAM、4核CPU**。
- 训练时长（主方法）：
  - PointSpiralMaze：约23小时。
  - PointUMaze/PointNMaze：约11.5小时。
  - sT策略（仅使用最后状态）在上述环境下分别约5小时和2.5小时。

## 5. 实验数量与充分性

- **三大类实验**：迷宫导航（3个难度）、机器人操作（2个任务）、消融研究。
- **消融分析**：分别移除AIM奖励或Q函数，验证两者必要性；同时对比sT策略（仅用最后状态）和固定/随机初始状态。
- **统计充分性**：每个实验5个随机种子，报告均值±标准差，曲线附可信区间。
- **客观性**：所有基线代码采用原始实现或官方修改版本，超参数从原论文或公共仓库获取；机器人任务中与HGG和HER公平对比。
- 实验覆盖了从简单到复杂、从连续控制到稀疏奖励的多种场景，结论具有良好泛化性。

## 6. 主要结论与发现

- DiCuRL在**所有迷宫任务上优于或持平**9种基线方法，在复杂迷宫（PointSpiralMaze）中收敛速度显著更快（约30万步达到1.0成功率，而OUTPACE需约40万步，其他基线无法达到）。
- 在机器人操作任务中，DiCuRL也**超越HGG和HER**，样本效率更高。
- **AIM奖励和Q函数是生成合适课程目标的关键**：去除任意一个都导致成功率显著下降。
- 扩散模型的反向去噪过程能有效探索环境，生成覆盖从起点到目标的课程序列。
- 环境无关性：无需领域知识，无需几何或障碍物信息。

## 7. 优点

- **环境无关**：不依赖领域知识、几何结构或预定义分布，适用于多种连续控制任务。
- **天然促进探索**：扩散过程的噪声机制使课程目标覆盖未访问区域，缓解稀疏奖励探索困难。
- **目标难度自适应**：通过最大化Q和AIM奖励，生成“有挑战性但可实现”的目标，避免过于简单或不可达。
- **在线学习**：与离线扩散策略不同，DiCuRL与智能体交互同步更新模型，无需预收集演示数据。
- **模块化设计**：可结合任意离线策略算法（如SAC、DDPG），易于扩展。

## 8. 不足与局限

- **高维输入的局限性**：扩散模型擅长处理图像等高维数据，但AIM奖励函数在高维下可能效果不佳，阻碍课程目标生成。
- **课程选择策略**：当前使用最小费用最大流二分图匹配来选择最佳课程目标，该策略可能并非最优；替代选择方法（如仅用最后状态）反而导致性能下降（附录B）。
- **计算开销**：扩散模型训练需要额外的梯度传播和多次反向去噪步，比简单插值方法更重。
- **实验覆盖**：虽然展示了机器人操作任务，但未测试更复杂的多步奖励或视觉输入环境（如图像观测），限制了泛化性验证。

（完）
