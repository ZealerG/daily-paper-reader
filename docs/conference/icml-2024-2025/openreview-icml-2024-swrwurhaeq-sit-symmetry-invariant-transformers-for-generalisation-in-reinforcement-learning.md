---
title: "SiT: Symmetry-invariant Transformers for Generalisation in Reinforcement Learning"
title_zh: SiT：用于强化学习泛化的对称不变Transformer
authors: "Matthias Weissenbacher, Rishabh Agarwal, Yoshinobu Kawahara"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=SWrwurHAeq"
tags: ["query:graph-part"]
score: 6.0
evidence: 用于强化学习泛化的对称不变Transformer
tldr: 本文针对强化学习泛化挑战，提出对称不变Transformer（SiT），利用图对称注意力机制保留图对称性，得到不变性和等变性表示。在MiniGrid和Procgen等RL基准上超越传统ViT，展示了更好的泛化能力和样本效率。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1702, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1709, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1522, \"height\": 932, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 878, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1778, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 941, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 632, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 780, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 786, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1777, \"height\": 1264, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1410, \"height\": 1417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 773, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 775, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 777, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 894, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 880, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-swrwurhaeq/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 874, \"height\": 466, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-swrwurhaeq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1705, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-swrwurhaeq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1720, \"height\": 697, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-swrwurhaeq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 517, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-swrwurhaeq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1715, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-swrwurhaeq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1721, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-swrwurhaeq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1703, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-swrwurhaeq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1701, \"height\": 244, \"label\": \"Table\"}]"
motivation: 强化学习策略在环境变化时泛化能力差。
method: 图对称注意力机制实现对称不变表示。
result: 在多个RL基准上表现更优。
conclusion: 提供了利用图对称性提升RL泛化的新方法。
---

## Abstract
An open challenge in reinforcement learning (RL) is the effective deployment of a trained policy to new or slightly different situations as well as semantically-similar environments. We introduce **S**ymmetry-**I**nvariant **T**ransformer (**SiT**), a scalable vision transformer (ViT) that leverages both local and global data patterns in a self-supervised manner to improve generalisation. Central to our approach is Graph Symmetric Attention, which refines the traditional self-attention mechanism to preserve graph symmetries, resulting in invariant and equivariant latent representations. We showcase SiT's superior generalization over ViTs on MiniGrid and Procgen RL benchmarks, and its sample efficiency on Atari 100k and CIFAR10.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义
- **研究动机**：强化学习（RL）中训练好的策略在新环境或语义相似但略有不同的情形下泛化能力差，是当前开放挑战。现有的数据增强方法虽然常用，但可能导致过正则化且不高效；同时，环境中的对称性（局部与全局）未被充分利用。
- **核心问题**：如何设计一种能够自适应学习局部和全局对称性、同时保持动作方向语义的神经网络架构，以提升RL的泛化性能和样本效率。
- **整体含义**：本文提出对称不变Transformer（SiT），通过新型图对称注意力（GSA）机制在自注意力中融入图对称性，实现不变性与等变性表示，从而在多个RL基准上显著改进泛化。

## 2. 论文提出的方法论
- **核心思想**：在视觉Transformer（ViT）基础上，将自注意力机制改造为图对称注意力（GSA），使之能保留输入图像的二维网格对称性（平移、旋转、翻转）。通过局部和全局GSA模块的结合，兼顾局部邻域与全局图像结构，并利用token嵌入实现不变性、利用patch表示实现等变性。
- **关键技术细节**：
  - **GSA层**：定义图拓扑矩阵 \(G \in \mathbb{R}^{P \times P}\)，其共享权重根据对称性（水平翻转、垂直翻转、旋转）设计（如图2所示）。注意力计算为 \(\text{softmax}(\frac{1}{\sqrt{d_f}}\Gamma(Q,K)) G_v V\)，其中 \(\Gamma\) 包含对称化操作和哈达玛积。
  - **局部与全局GSA**：局部GSA在像素级小窗口内应用，全局GSA在图像块（patch）级应用。SiT通过串联局部和全局Transformer块，使最终表示既保留局部对称性又保留全局对称性。
  - **翻转对称破缺层**：为保留动作方向语义，引入基于有向三角形子图的旋转对称性保持但翻转对称破缺机制（公式4），使注意力矩阵在翻转下改变方向，在旋转下不变。
  - **不变性与等变性**：通过token嵌入（第P+1个patch）实现模型输出的不变性；通过patch维度的表示传递实现等变性。
  - **图对称Dropout**：通过将共享权重置零保持对称性。

## 3. 实验设计
- **数据集与场景**：
  - **MiniGrid（LavaCrossing）**：用于测试组合泛化和分布外泛化，包含不同难度级别和目标位置变化。
  - **Procgen（CaveFlyer、StarPilot、Fruitbot、Chaser等16个游戏）**：标准分布外泛化基准，训练固定200个关卡，测试全部关卡分布。
  - **Atari 100k（SpaceInvaders、Pong、Breakout、KungFuMaster、MsPacman）**：样本效率基准。
  - **DM-control（Walker-walk）**：连续控制任务。
  - **CIFAR-10**：用于监督学习的消融实验。
- **基准方法**：对比CNN（ResNet、数据高效CNN）、ViT（标准Transformer）、E2CNN（等变CNN）、UCB-DrAC（带数据增强的CNN）。
- **对比方式**：在相同RL算法（IMPALA、PPO+DrAC、Rainbow、SAC）下，控制模型参数量相近或进行公平比较。

## 4. 资源与算力
- 文中未明确说明使用的GPU型号、数量及训练时长等具体算力信息。仅提及SiT实现比ViT慢2-5倍，以及通过改进（如建立图矩阵与深度可分离卷积的等价性）缓解计算和内存问题。

## 5. 实验数量与充分性
- **实验数量**：
  - MiniGrid：训练+测试多种任务（难度1-3、旋转、目标位置变化），多个种子。
  - Procgen：报告4个游戏（表1）和一个全16游戏平均结果（图8），每个运行4个种子。
  - Atari 100k：5个游戏，每个3个种子（表3及图12-13）。
  - DM-control：1个任务（Walker-walk）。
  - CIFAR-10：不同patch-size和训练轮次消融（表6-7）。
- **充分性判断**：实验覆盖了离散和连续控制、分布内及分布外泛化、样本效率等多个维度，且进行了消融（局部/全局层数、对称破缺、图矩阵选择等）。但部分实验（如全Procgen套件）仅使用小模型（41k权重），且未在所有任务上与超大规模基线全面比较。总体上实验设计较充分，但规模中等。

## 6. 论文的主要结论与发现
- SiT在MiniGrid上显著优于CNN和ViT（图4），尤其在旋转和位置变化任务上。
- 在Procgen上，SiT（约70k权重）比ViT（216k）提升7-9倍性能，与9倍参数量ResNet（620k）相当或更优（表1）。
- SiT在Atari 100k上具有与CNN相当的样本效率（表3），在DM-control上无需调参即可与1M权重ViT基线可比。
- CIFAR-10上，SiT在更少训练轮次下达到ViT相同准确率（图7b），证明样本效率优势。
- 局部GSA对性能提升至关重要（图15、表5）。

## 7. 优点
- **方法创新**：首次在ViT中引入可学习的图对称注意力，同时实现局部与全局对称性处理，且对称性可通过训练自适应调整（如恢复置换不变性）。
- **泛化能力**：在无需数据增强或仅需少量增强的情况下，显著提升分布外泛化。
- **样本效率**：在多个基准上以较少参数和训练步数达到或超越强基线。
- **理论保障**：对GSA层的对称性保证给出形式化命题（Proposition 3.1）。
- **开源**：提供GitHub代码。

## 8. 不足与局限
- **计算开销**：当前实现中SiT比ViT慢2-5倍，局部GSA带来额外内存和计算负担，限制了大规模应用（如高分辨率图像、大批次）。
- **对称性假设**：在对称性弱或不存在对称性的环境中，SiT的优势可能不显著（如作者承认Procgen中一些游戏并非旋转对称）。
- **实验覆盖有限**：Atari 100k仅测试5个游戏，DM-control仅1个任务；全Procgen套件结果使用较小模型（41k），部分任务（如BossFight）学习不佳。
- **超参数敏感性**：虽然声称SiT对超参数不敏感，但局部窗口大小、图矩阵维度等仍可能影响性能，文中未深入分析。
- **缺乏消融**：未单独评估翻转对称破缺层和三角形子图在不同环境下的必要性。
- **可扩展性**：提及未来可通过定制CUDA优化计算，但当前未实现。

（完）
