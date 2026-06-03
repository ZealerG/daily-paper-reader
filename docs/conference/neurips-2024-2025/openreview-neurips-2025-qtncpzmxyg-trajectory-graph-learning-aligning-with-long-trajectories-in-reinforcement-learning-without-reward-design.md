---
title: "Trajectory Graph Learning: Aligning with Long Trajectories in Reinforcement Learning Without Reward Design"
title_zh: 轨迹图学习：无需奖励设计的强化学习长轨迹对齐
authors: "Yunfan Li, Eric Liu, Lin Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QtnCPZMxYg"
tags: ["query:graph-part"]
score: 7.0
evidence: 利用轨迹图进行无奖励设计的RL对齐
tldr: 本文针对强化学习依赖人工奖励函数的问题，提出轨迹图学习方法，通过构建专家轨迹的图结构来直接对齐策略，避免了手动设计奖励的困难。该方法在多个长视界任务上优于逆RL和偏好RL方法，有效保持了轨迹的长期连贯性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qtncpzmxyg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1454, \"height\": 926, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qtncpzmxyg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1133, \"height\": 599, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qtncpzmxyg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 806, \"height\": 953, \"label\": \"Table\"}]"
motivation: RL依赖人工奖励函数，现有替代方法无法捕捉长视界轨迹的连贯性。
method: 构建专家轨迹的图结构，用图匹配损失对齐策略与轨迹序列。
result: 在长视界任务中取得更优的对齐效果，且无需奖励建模。
conclusion: 轨迹图学习是一种有效的无奖励策略对齐方法。
---

## Abstract
Reinforcement learning (RL) often relies on manually designed reward functions, which are difficult to specify and can lead to issues such as reward hacking and suboptimal behavior. Alternatives like inverse RL and preference-based RL attempt to infer surrogate rewards from demonstrations or preferences but suffer from ambiguity and distribution mismatch. A more direct approach, inspired by imitation learning, avoids reward modeling by leveraging expert demonstrations. However, most existing methods align actions only at individual states, failing to capture the coherence of long-horizon trajectories.

In this work, we study the problem of directly aligning policies with expert-labeled trajectories to preserve long-horizon behavior without relying on reward signals. Specifically, we aim to learn a policy that maximizes the probability of generating the expert trajectories. Nevertheless, we prove that, in its general form, this trajectory alignment problem is NP-complete. 
To address this, we propose Trajectory Graph Learning (TGL), a framework that leverages structural assumptions commonly satisfied in practice—such as bounded realizability of expert trajectories or a tree-structured MDP. These enable a graph-based policy planning algorithm that computes optimal policies in polynomial time under known dynamics. For settings with unknown dynamics, we develop a sample-efficient algorithm based on UCB-style exploration and establish sub-linear regret. Experiments on grid-world tasks demonstrate that TGL substantially outperforms standard imitation learning methods for long-trajectory planning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：强化学习（RL）在实际应用中严重依赖手动设计的奖励函数，但奖励设计往往需要大量先验知识，容易导致奖励黑客（reward hacking）和奖励塑造（reward shaping）等次优行为。现有替代方法如逆强化学习（IRL）和基于偏好的强化学习（PbRL）试图从演示或偏好中推断替代奖励，但存在歧义性、过拟合和分布偏移等问题，无法保证与专家意图的对齐。
- **研究动机**：模仿学习虽然避免了奖励建模，但经典的行为克隆（BC）仅对齐单步状态-动作对，忽略了长视界轨迹的连贯性，导致误差累积。因此，本文研究直接对齐专家标注的完整轨迹的方法，旨在最大化生成专家轨迹的概率，尤其适用于大语言模型响应生成和自动驾驶等对整体质量与安全至关重要的应用。
- **核心挑战**：作者证明，在一般形式下，直接轨迹对齐问题（求解最优确定性策略）是NP完全的（通过归约到最大权独立集问题）。因此需要借助实际中常满足的结构性假设来获得可计算性。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出轨迹图学习（TGL）框架，将直接轨迹对齐问题转化为轨迹诱导图上的最大权独立集（MWIS）问题，并利用结构性假设（如专家轨迹的有界可实现性或树状MDP）实现多项式时间求解。在未知动力学环境下，结合UCB探索策略设计具有次线性遗憾的在线学习算法。

- **关键技术细节**：
  - **冲突定义**：两个轨迹若在同一时间步处于相同状态但采取不同动作，则称为冲突。冲突轨迹不能由同一个确定性策略同时实现。
  - **冲突图构建**：以每个专家轨迹为节点，冲突轨迹之间连边，赋予每个轨迹权重为其在环境中的可实现概率乘积。
  - **已知动力学下的算法**：
    - **TGL-CP（算法1）**：构建冲突图后，调用MWIS oracle（如枚举算法，利用ε-可实现假设限制独立集大小≤⌊1/ε₀⌋）选择最大权独立集，再根据所选轨迹制定策略。时间复杂度 O(M²H + M^{1/ε₀})。
    - **TGL-PrunedTree（算法4）**：针对树状MDP（定义5，无后续状态交叉、无合并、无重访），从叶子到根进行反向的权重聚合和动作剪枝，每步保留总权重最大的动作，最终得到最优策略。时间复杂度 O(H·M·|A|)。
  - **未知动力学下的在线学习（TGL-UCB，算法2）**：初始化阶段为每个轨迹执行一次对应的策略；之后每轮计算每个轨迹的乐观上置信界（UCB），调用MWIS oracle选择总UCB最大的独立集并执行对应策略，随后更新估计。遗憾上界为 O(M³ log K·Δ_max / Δ²_min)。

## 3. 实验设计

- **场景与环境**：采用4×4 Frozen Lake环境，但修改为洞不终止且给-1奖励，目标格给+1并结束，水平线H=10。动作以0.1概率被随机有效动作替换。观测为一维one-hot状态向量，动作为四个基本方向。
- **专家轨迹集**：由确定性专家（经PPO训练）和随机变体生成不同组合的轨迹集，数量从1到20，包含不同确定性/随机性比例。
- **对比方法**：
  - TGL-UCB（本文方法，使用MWIS精确求解）
  - 行为克隆（BC，使用开源库imitation，batch size=8，训练20轮）
  - PPO Expert（参考专家策略，作为上界基准）
- **评估指标**：轨迹匹配概率 P_match(π) = Pr[rollout ∈ D]，即生成轨迹完全匹配演示集中某一条的概率。在10,000个回合中统计，并报告95%置信区间。

## 4. 资源与算力

文中在附录 A.8 中明确说明：
- 使用单个 Google Colab 实例，配备 NVIDIA T4（16 GB GPU RAM）内核。
- PPO expert 训练 50,000 步约需 1 分 20 秒；一次 TGL-UCB 运行（50 次迭代，20 个节点）约需 45 秒；三种方法评估约需 1 分 30 秒。
- 大部分代码未使用 GPU 加速，因此 CPU 内核也可运行。

## 5. 实验数量与充分性

- **实验数量**：表1展示了13种不同的专家轨迹集配置（不同数量的确定性与随机性轨迹组合），每种配置下比较了三种方法，并报告了95%置信区间。此外，还对不同轨迹集大小（从1到20）进行了测试。
- **充分性与公平性**：
  - 覆盖了多种演示组合，包括纯确定性、纯随机性、混合比例等，验证了不同条件下的表现。
  - 误差线使用 Wald 区间从10,000次试验中计算，具有统计意义。
  - 对比方法BC和PPO expert的设置均给出了具体超参数，确保了可重复性。
  - 但局限在于仅在一个离散网格世界（4×4 Frozen Lake）上评估，未扩展到连续或更高维环境；也未与历史条件BC或循环模型对比。

## 6. 主要结论与发现

- 在所有演示组合下，TGL-UCB 始终达到或超过 BC 基线，且经常超过 PPO expert，尽管从未观察过奖励。
- 当演示稀少或混合度高时，TGL的增益最为显著，体现了直接轨迹对齐的优势。
- 理论结果证实了在一般MDP下直接轨迹对齐的NP难度，但借助有界可实现性或树状结构可以在多项式时间内求解。
- 在线学习算法实现了次线性遗憾，支持未知动力学下的高效学习。

## 7. 优点

- **理论贡献**：首次系统研究直接轨迹对齐问题，给出了NP完备性证明，并提出了在合理假设下可高效求解的框架。
- **方法创新**：将轨迹对齐转化为图上的MWIS问题，巧妙利用冲突结构；对树状MDP设计线性时间动态规划算法；在线版本结合UCB探索与MWIS oracle。
- **实验设计**：采用轨迹匹配概率作为直接度量，而非替代奖励，更贴合优化目标；误差线报告规范，结果稳健。
- **可复现性**：超参数、环境设置、计算资源均详细公开（附录A.7, A.8）。

## 8. 不足与局限

- **实验覆盖**：仅在一个离散网格世界（4×4 Frozen Lake）上验证，未涉及连续状态/动作空间或更复杂的环境（如机器人、自动驾驶、自然语言生成）。
- **计算效率**：TGL-UCB 需要每次调用MWIS oracle，在节点数多时成为瓶颈，文中限制了迭代次数为50次。未来需借助近似求解器或可扩展图方法。
- **对比方法**：未与历史条件BC或循环序列模型（如RNN）比较，也未考虑部分可观测设置。
- **应用局限性**：当前理论和算法针对有限MDP和有限专家集，无法直接扩展到连续MDP或无限专家集。
- **社区贡献**：未提供现成代码或基准数据集，可复现性依赖手动描述。

（完）
