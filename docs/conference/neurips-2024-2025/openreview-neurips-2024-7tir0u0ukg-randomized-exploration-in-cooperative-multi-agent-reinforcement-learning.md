---
title: Randomized Exploration in Cooperative Multi-Agent Reinforcement Learning
title_zh: 合作多智能体强化学习中的随机化探索
authors: "Hao-Lun Hsu, Weixin Wang, Miroslav Pajic, Pan Xu"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=7Tir0u0ukg"
tags: ["query:graph-part"]
score: 9.0
evidence: 合作多智能体强化学习中的并行MDP随机化探索
tldr: 多智能体强化学习中的探索效率缺乏理论保证。本文首次针对合作式多智能体RL提出可证明高效的随机化探索方法，在并行MDP框架下设计了基于汤普森采样的CoopTS-PHE和CoopTS-LMC算法。理论证明在线性近似条件下实现了亚线性遗憾界，同时保持较低的通信复杂度。实验验证了算法在并行环境中的高效性。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1394, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 597, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1162, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1351, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1354, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1390, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1390, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 890, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1352, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1349, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1351, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 881, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1407, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7tir0u0ukg/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1353, \"height\": 911, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-7tir0u0ukg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 446, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7tir0u0ukg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1291, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7tir0u0ukg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1297, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7tir0u0ukg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1435, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7tir0u0ukg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7tir0u0ukg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1495, \"height\": 460, \"label\": \"Table\"}]"
motivation: 现有MARL探索方法缺乏理论保证，尤其在并行决策场景下探索效率低下。
method: 提出统一随机化探索框架，基于并行MDP设计两种汤普森采样类型算法，分别采用扰动历史探索和朗之万蒙特卡洛探索策略。
result: "在线性MDP假设下，算法实现了~O(d^{3/2}H^2 sqrt(MK))的遗憾界，且通信复杂度低。"
conclusion: 随机化探索能在并行多智能体环境中实现理论最优的探索效率，是实际部署的有效工具。
---

## Abstract
We present the first study on provably efficient randomized exploration in cooperative multi-agent reinforcement learning (MARL). We propose a unified algorithm framework for randomized exploration in parallel Markov Decision Processes (MDPs), and two Thompson Sampling (TS)-type algorithms, CoopTS-PHE and CoopTS-LMC, incorporating the perturbed-history exploration (PHE) strategy and the Langevin Monte Carlo exploration (LMC) strategy respectively, which are flexible in design and easy to implement in practice. For a special class of parallel MDPs where the transition is (approximately) linear, we theoretically prove that both CoopTS-PHE and CoopTS-LMC achieve a $\widetilde{\mathcal{O}}(d^{3/2}H^2\sqrt{MK})$ regret bound with communication complexity $\widetilde{\mathcal{O}}(dHM^2)$, where $d$ is the feature dimension, $H$ is the horizon length, $M$ is the number of agents, and $K$ is the number of episodes. This is the first theoretical result for randomized exploration in cooperative MARL. We evaluate our proposed method on multiple parallel RL environments, including a deep exploration problem (i.e., $N$-chain), a video game, and a real-world problem in energy systems. Our experimental results support that our framework can achieve better performance, even under conditions of misspecified transition models. Additionally, we establish a connection between our unified framework and the practical application of federated learning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：合作多智能体强化学习（MARL）中探索与利用的平衡至关重要，但现有方法大多基于乐观上置信界（UCB），理论强大却实践效果差、计算昂贵。随机化探索（如Thompson Sampling）在单智能体设定中已显示优越性，但在合作MARL中缺乏可证明高效的理论工作。
- **动机**：填补合作MARL中随机化探索的理论空白，提出既具有理论保证又易于实践的统一算法框架。
- **整体含义**：首次为合作并行MDP中的随机化探索提供遗憾界分析与通信复杂度保证，并验证其在真实场景中的有效性。

## 2. 方法论
### 核心思想
基于并行MDP建立统一算法框架，各智能体独立执行Least-Square Value Iteration（LSVI），通过与服务器通信共享全局数据，采用两种随机化探索策略近似Thompson Sampling。

### 关键技术细节
- **算法框架**（Algorithm 1）：每个episode各智能体并行执行策略收集数据，定期按同步条件（如行列式条件）与服务器交换数据，服务器聚合全局数据集后下发。
- **CoopTS-PHE**（Algorithm 2）：通过向奖励和正则化项添加独立高斯噪声来扰动历史，求解带噪声的最小二乘问题得到参数估计，然后取多个样本的最大值作为Q函数估计。
- **CoopTS-LMC**（Algorithm 3）：利用Langevin Monte Carlo更新参数，在梯度下降中加入高斯噪声，迭代多步后得到后验近似样本，同样多采样取最大值。
- **线性MDP假设**：当转移和奖励可线性表示时，Q函数为线性形式，损失函数取平方损失。
- **同步条件**：基于行列式比值条件
  \[
  \log \frac{\det(\Lambda_{\text{ser}} + \Lambda_{\text{loc}} + \lambda I)}{\det(\Lambda_{\text{ser}} + \lambda I)} \ge \frac{\gamma}{k - k_s}
  \]
  控制通信频率。

### 公式与理论结果
- 遗憾界：$\widetilde{\mathcal{O}}(d^{3/2}H^2\sqrt{MK})$，与最优UCB方法匹配。
- 通信复杂度：$\widetilde{\mathcal{O}}(dHM^2)$，与异步算法持平。
- 在misspecified setting下也给出了相应边界，指出PHE对模型误设定容忍度略高于LMC。

## 3. 实验设计
- **环境/场景**：
  1. **N-chain**：深度探索问题，链长N=25（主实验）和N=10（消融）。
  2. **Super Mario Bros**：视频游戏，4个不同关卡（异构环境）。
  3. **BuildingEnv**：建筑能源系统热控制，多城市不同气候类型。
- **Baseline方法**：vanilla DQN, Double DQN, Bootstrapped DQN, NoisyNet DQN。部分设置还对比了NeuralTS, NeuralUCB, LinTS, LinUCB。
- **评价指标**：训练过程中每episode的平均回报（带标准差），部分实验用violin plot展示最终性能分布。

## 4. 资源与算力
- **明确信息**：文中说明“All experiments are run on Nvidia RTX A5000 with 24GB RAM”。
- **未明确信息**：未提供GPU数量、具体训练时长/批次时间、超参数搜索总计算量等。各实验种子数为10 runs。

## 5. 实验数量与充分性
- **实验数量**：
  - N-chain：多组agent数（m=2,3,4），N=25主实验+ N=10消融（不同同步策略、缓冲区大小、采样机制、超参数调优等）。
  - Super Mario Bros：平行学习（图1c）和联邦学习（图1d）场景，同步策略为行列式条件。
  - BuildingEnv：4个城市，violin plot展示10 runs分布。
- **充分性与公平性**：
  - 每个结果均为10次随机种子平均，带标准差，统计性较好。
  - 与5种以上常见baseline对比，且涵盖多种随机化方法（Bootstrapped, NoisyNet）。
  - 对超参数（学习率、逆温度、噪声规模等）进行了扫描，并列出最终使用的参数。
  - 不同同步条件（常数、指数、线性行列式）均有对比。
- **评价**：实验设计较充分，覆盖简单迷宫、复杂视频游戏、真实工程问题，验证了算法在多种异质性设置下的优势。

## 6. 主要结论与发现
- 随机化探索（PHE和LMC）在合作并行MDP中可达到与最优UCB方法相同的理论遗憾界，但实现更简单、实际性能更好。
- 在N-chain中，PHE与LMC均优于所有baseline，且随着agent数量增加优势更明显。
- 在Super Mario Bros中，LMC在平行设置下表现出显著优势，PHE在联邦学习中也能有效协作。
- 在建筑能源系统中，PHE和LMC平均回报最高，且方差较小。
- 理论分析支持算法对模型误设定具有一定鲁棒性，PHE容忍度略高于LMC。

## 7. 优点
- **理论贡献**：首次为合作MARL中随机化探索提供可证明的遗憾界，填补空白。
- **算法实用性**：无需像UCB那样计算置信区间，仅需添加高斯噪声或进行Langevin更新，易于集成到深度RL。
- **通信高效**：同步条件设计合理，通信复杂度与最优异步算法匹配。
- **实验全面**：涵盖不同规模、不同异质性的环境，并包含联邦学习扩展。
- **代码开源**：提供完整实现，便于复现。

## 8. 不足与局限
- **理论假设较强**：主要结果依赖于线性MDP假设，对深度非线性函数类未给出理论保证。
- **实验覆盖**：虽然环境多样，但均为离散动作空间（通过DQN），未在连续控制任务或更复杂的多智能体交互（如麻将、星际争霸）上验证。
- **资源细节缺失**：未报告训练时间、GPU数量、单次实验耗时等，不利于量化可复现性。
- **联邦学习探索有限**：仅有一个Super Mario Bros的场景，且同步方式为常数间隔，未深入分析通信效率。
- **与最先进算法比较**：未对比PPO、QMIX等当代MARL主流算法，限制了对标范围。
- **应用限制**：建筑能源系统使用离散动作映射，可能引入额外偏差；实际部署时还需考虑安全约束等。

（完）
