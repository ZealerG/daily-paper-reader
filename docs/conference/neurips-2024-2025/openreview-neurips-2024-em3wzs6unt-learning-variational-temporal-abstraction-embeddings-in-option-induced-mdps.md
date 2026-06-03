---
title: Learning Variational Temporal Abstraction Embeddings in Option-Induced MDPs
title_zh: 选项诱导马尔可夫决策过程中学习变分时间抽象嵌入
authors: "Chang Li, Xiaodong He"
date: 2024-05-13
pdf: "https://openreview.net/pdf?id=eM3Wzs6Unt"
tags: ["query:graph-part"]
score: 6.0
evidence: 基于选项框架的层次强化学习，采用变分推断稳定更新
tldr: 层次强化学习中，选项发现面临探索不足和更新不稳定问题。本文提出变分马尔可夫选项评论家（VMOC），一种离线策略算法，通过变分推断稳定动作和选项策略的联合学习，并引入最大熵内在奖励促进探索。采用低维选项嵌入替代传统元组，提升可扩展性。理论证明收敛性，实验表明在长时任务上优于现有方法。
source: NeurIPS-2024-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-em3wzs6unt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-em3wzs6unt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 1074, \"label\": \"Figure\"}]"
motivation: 选项框架在层次RL中自动发现时间扩展动作，但存在探索和更新不稳定问题。
method: 使用变分推断稳定选项与动作策略学习，结合最大熵奖励和低维选项嵌入。
result: 理论证明收敛，实验在长时任务上取得更优性能。
conclusion: 变分推断可有效提升层次RL中选项学习的稳定性与效率。
---

## Abstract
The option framework in hierarchical reinforcement learning has notably advanced the automatic discovery of temporally-extended actions from long-horizon tasks. However, existing methods often struggle with ineffective exploration and unstable updates when learning action and option policies simultaneously. Addressing these challenges, we introduce the Variational Markovian Option Critic (VMOC), an off-policy algorithm with provable convergence that employs variational inference to stabilize updates. VMOC naturally integrates maximum entropy intrinsic rewards to promote the exploration of diverse and effective options. Furthermore, we adopt low-cost option embeddings instead of traditional, computationally expensive option tuples, enhancing scalability and expressiveness. Extensive experiments in challenging Mujoco environments validate VMOC’s superior performance over existing on-policy and off-policy methods, demonstrating its effectiveness in learning coherent and diverse option sets suitable for complex tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **研究背景**：层次强化学习（HRL）中的选项框架通过自动发现时间扩展动作（options）来分解长时任务，但在同时学习动作策略和选项策略时存在三个核心挑战：
  - **探索不足与退化**：传统最大似然方法导致策略快速收敛到局部最优，选项多样性低，出现单一选项主导或每步切换选项。
  - **样本效率低**：半马尔可夫决策过程（SMDP）的本质导致每次策略更新需收集长序列样本，且大多为on-policy算法，样本利用率低。
  - **计算开销大**：传统选项用三元组（起始集、内部策略、终止函数）表示，需用神经网络建模，训练复杂且昂贵。
- **整体目标**：提出一种离线策略（off-policy）变分推断算法，同时解决上述三个问题，实现稳定、高效、可扩展的选项学习。

## 2. 方法论
### 核心思想
- 将最优选项轨迹建模为概率图模型（PGM），引入最优性随机变量（\(E^A, E^O\)），将奖励和选项选择偏好转化为概率似然。
- 使用结构变分推断（structured variational inference），用HiT-MDP（隐时间马尔可夫决策过程）作为变分分布近似最优轨迹，避免风险偏好的乐观行为。
- 变分下界（ELBO）自然推导出最大熵目标：\( \mathcal{L} = \mathbb{E}_{q(\tau)}[r + f + H[\pi_A] + H[\pi_O]] \)，其中 \(H\) 为策略熵，作为内在奖励促进探索。
- 采用**选项嵌入**（低维稠密向量）替代传统选项三元组，通过可学习的嵌入矩阵 \(W \in \mathbb{R}^{K \times d}\) 表示选项，降低计算复杂度并提升表达力。

### 关键技术细节
- **软值函数定义**：
  - 选项软价值：\( Q^{\text{soft}}_O[s_t, o_t] = f(\cdot) + \mathbb{E}_{a_t \sim \pi_A}[Q^{\text{soft}}_A[s_t, o_t, a_t]] + H[\pi_A] \)
  - 动作软价值：\( Q^{\text{soft}}_A[s_t, o_t, a_t] = r(s,a) + \mathbb{E}_{s_{t+1}, o_{t+1}}[Q^{\text{soft}}_O[s_{t+1}, o_{t+1}]] + H[\pi_O] \)
- **定理保证**：在表格设置下，软选项策略迭代收敛到最优（定理2）；在函数近似下，ELBO优化保证收敛（定理3）。
- **算法流程**（VMOC）：
  - 使用双重Q网络（clipped double Q-learning）减少过估计。
  - 交替优化动作策略 \(\pi_A\) 和选项策略 \(\pi_O\) 的ELBO目标，并自动调节温度参数 \(\alpha_A, \alpha_O\)。
  - 从经验回放缓冲区采样，实现离线策略学习。

## 3. 实验设计
- **环境**：OpenAI Gym MuJoCo 中的10个连续控制任务（如Humanoid-v2、HumanoidStandup-v2、InvertedDoublePendulum等）。
- **基准**：与6种选项变体（MOPG, DAC+PPO, AHP+PPO, IOPG, PPOC, OC）及无层次结构的PPO进行比较。
- **超参数**：VMOC固定温度率0.05，添加探索噪声 \( \mathcal{N}(\mu=0,\sigma=0.2) \)；其他基线使用DAC开源代码的默认参数。
- **评估指标**：每个任务运行10个不同随机种子，曲线平滑后报告均值与标准差（1-sigma阴影区域）。

## 4. 资源与算力
- 文中明确说明：所有实验在 **Intel Core i9-9900X CPU @ 3.50GHz** 上以单线程、单进程运行，**未使用GPU**。
- 每个环境运行约1百万环境步数，但未报告总耗时。

## 5. 实验数量与充分性
- **实验组数**：10个Mujoco环境 × 10次独立运行 = 100次独立实验（每个环境一个学习曲线）。
- **消融实验**：**未进行**（文中承认“Due to limited computing resources, we did not conduct an ablation study”）。
- **公平性**：所有基线使用统一代码库（DAC）的公开超参数，VMOC的参数固定且未刻意调优，对比较公平。
- **充分性评价**：实验覆盖了不同难度（状态/动作维度各异）的任务，但缺少对选项数量、温度自动调节等关键因素的消融，也未与SAC等非选项离线算法直接比较，充分性有欠缺。

## 6. 主要结论与发现
- VMOC在几乎所有10个Mujoco环境上**显著优于**所有基线（包括同基于HiT-MDP的MOPG），尤其在状态/动作维度大的Humanoid任务上提升明显，归因于最大熵探索能力。
- 作为离线策略算法，VMOC相比on-policy的MOPG具备更好的样本效率和稳定性。
- 选项嵌入（而非三元组）有效降低了计算成本，且能学习到多样化、可重用的选项集。

## 7. 优点
- **理论贡献**：首次将结构变分推断严格应用于选项框架，证明了软选项策略迭代的收敛性（定理2、3），为算法提供稳定性保证。
- **方法论创新**：最大熵项自然源自ELBO，无需额外人工正则项；选项嵌入简化了表示，兼具可扩展性与表达力。
- **实验验证**：在10个连续控制任务上全面比较，结果具有统计显著性（10次重复），且代码开源。

## 8. 不足与局限
- **消融缺失**：未对选项数量、温度调节方式、嵌入维度等关键组件进行消融研究，无法明确各组件贡献。
- **参数固定**：温度参数固定为0.05，论文承认自动调节可能更优（如SAC），但未实现。
- **对比不充分**：未与SAC、TD3等主流非层次离线算法比较，也未与更近期的选项学习方法（如SOAC）对比。
- **计算资源限制**：仅使用CPU单线程训练，可能影响大规模环境下的收敛速度；未报告GPU实验。
- **单任务设置**：实验仅限单任务（非迁移学习场景），选项的泛化重用优势未充分体现。
- **收敛性证明局限**：定理3依赖于SGD和神经网络表达能力假设，实际收敛性可能受非凸优化影响。

（完）
