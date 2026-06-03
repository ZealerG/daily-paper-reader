---
title: Random Policy Evaluation Uncovers Policies of Generative Flow Networks
title_zh: 随机策略评估揭示生成流网络的策略
authors: "Haoran He, Emmanuel Bengio, Qingpeng Cai, Ling Pan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=pbkwh7QivE"
tags: ["query:graph-part"]
score: 7.0
evidence: 将GFlowNet与标准RL联系起来，通过随机策略评估揭示策略
tldr: 该论文研究了生成流网络（GFlowNet）与标准强化学习之间的关系，提出通过随机策略评估来揭示GFlowNet的潜在策略。实验表明，GFlowNet的目标函数与RL的最大熵目标存在等价性，为理解两种框架的融合提供了新视角。该工作有助于推动生成式与决策式方法的统一。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 748, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 879, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 469, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1407, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1245, \"height\": 336, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1289, \"height\": 654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1726, \"height\": 1018, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pbkwh7qive/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1595, \"height\": 812, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-pbkwh7qive/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 870, \"height\": 583, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pbkwh7qive/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 538, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pbkwh7qive/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1459, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pbkwh7qive/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1250, \"height\": 414, \"label\": \"Table\"}]"
motivation: GFlowNet与标准RL之间的关系尚不明确，尽管二者都涉及序列决策。
method: 采用随机策略评估方法，分析GFlowNet训练过程中学习到的策略，并与RL策略对比。
result: 发现GFlowNet的策略可以通过随机评估恢复，揭示了与标准RL的深层联系。
conclusion: 为GFlowNet和RL的融合提供了理论基础，有助于设计更通用的学习框架。
---

## Abstract
The Generative Flow Network (GFlowNet) is a probabilistic framework in which an agent learns a stochastic policy and flow functions to sample objects with probability proportional to an unnormalized reward function. GFlowNets share a strong connection with reinforcement learning (RL) that typically aims to maximize reward. A number of recent works explored connections between GFlowNets and maximum entropy (MaxEnt) RL, which incorporates entropy regularization into the standard RL objective. However, the relationship between GFlowNets and standard RL remains largely unexplored, despite the inherent similarities in their sequential decision-making nature.
While GFlowNets can discover diverse solutions through specialized flow-matching objectives, connecting them to standard RL can simplify their implementation through well-established RL principles and also improve RL's capabilities in diverse solution discovery (a critical requirement in many real-world applications), and bridging this gap can further unlock the potential of both fields. In this paper, we bridge this gap by revealing a fundamental connection between GFlowNets and one of the most basic components of RL -- policy evaluation. Surprisingly, we find that the value function obtained from evaluating a uniform policy is closely associated with the flow functions in GFlowNets. Building upon these insights, we introduce a rectified random policy evaluation (RPE) algorithm, which achieves the same reward-matching effect as GFlowNets based on simply evaluating a fixed random policy, offering a new perspective. 
Empirical results across extensive benchmarks demonstrate that RPE achieves competitive results compared to previous approaches, shedding light on the previously overlooked connection between (non-MaxEnt) RL and GFlowNets.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：生成流网络（GFlowNet）是一种基于概率框架的生成模型，通过学习随机策略和流函数，以与未归一化奖励函数成正比的概率采样对象。GFlowNet与强化学习（RL）具有天然的序列决策相似性，但以往工作主要将其与最大熵RL（MaxEnt RL）联系起来，而忽略了与标准（非MaxEnt）RL的关系。本文旨在填补这一空白，揭示GFlowNet与标准RL最基本组件——策略评估之间的内在联系。
- **整体含义**：通过建立GFlowNet的流函数与均匀随机策略的评估值函数之间的等价关系，作者提出了一种新的算法——校正随机策略评估（RPE），该算法仅通过评估固定的均匀策略即可实现与GFlowNet相同的奖励匹配能力，从而简化了GFlowNet的实现，并拓展了对两种框架统一理解的理论基础。

#### 2. 方法论：核心思想、关键技术细节
- **核心思想**：GFlowNet的流函数与均匀策略下的值函数在特定结构条件下存在等价关系。具体地，通过对原始终端奖励进行缩放（缩放因子为路径上的动作/分支数之比），并采用策略评估（Policy Evaluation）计算均匀策略的值函数，该值函数恰好等于GFlowNet中的状态流函数乘以缩放因子。
- **关键技术细节**：
  - **流迭代（Flow Iteration）**：作者首先定义了GFlowNet的动态规划视角——流迭代算法（Algorithm 2），通过状态流从子节点向父节点传播（使用向后策略 \(P_B\)）来迭代更新流函数。
  - **定理4.1（树结构DAG）**：在树结构中，每个状态只有唯一父节点。设 \(A(s)\) 为状态 \(s\) 的可用动作数，则均匀策略下，使用变换后奖励 \(R'(x) = R(x) \prod_{i=0}^{t-1} A(s_i)\) 进行评估，得到 \(V(s_t) = F(s_t) \prod_{i=0}^{t-1} A(s_i)\)。
  - **定理4.2（非树DAG）**：推广到一般非树DAG，引入分支比因子 \(g(\tau, s_t) = \prod_{i=0}^{t-1} \frac{|A(s_i)|}{|B(s_{i+1})|}\)，其中 \(B(s)\) 为进入状态 \(s\) 的入边数。在路径不变性条件（所有到达同一状态的轨迹具有相同 \(g\) 值）下，\(V(s_t) = F(s_t) g(\tau, s_t)\)。该条件在集合生成等任务中自然满足。
  - **RPE算法（Algorithm 3）**：
    1. 使用均匀策略 \(\pi\) 采样轨迹。
    2. 计算轨迹中各状态的分支比 \(g(s)\)。
    3. 对非终端状态，\(V(s) \leftarrow \sum_a \pi(a|s) F_\theta(s') g(s')\)；对终端状态，\(V(s) \leftarrow g(s) R(s)\)。
    4. 通过最小化均方误差 \(L_{\text{MSE}}(g(s)F_\theta(s), V(s))\) 更新参数 \(\theta\)。
    5. 学习完成后，前向策略 \(P_F(s'|s) = F_\theta(s') / F_\theta(s) \cdot P_B(s|s')\)（使用均匀 \(P_B\)）可用于采样。
- **与MaxEnt RL的区别**：RPE无需中间奖励修正或对数尺度操作，直接使用变换后的终端奖励和均匀策略评估，实现更简单。

#### 3. 实验设计：数据集/场景、基准、对比方法
- **场景与数据集**：
  - **TF Bind生成**：DNA序列生成任务，使序列与人类转录因子有高结合活性。分为树结构生成（左到右添加）和DAG结构生成（prepend-append MDP）。
  - **RNA序列生成**：生成14个核苷酸的RNA序列，使用ViennaRNA计算结合能量作为奖励，任务分为RNA1-4。
  - **分子生成（QM9）**：基于QM9数据集，利用预训练的MXMNet预测HOMO-LUMO能隙作为奖励，生成5个块组成的分子。
- **Benchmark**：标准GFlowNet评估指标：**准确率（Accuracy）**（衡量采样分布与目标奖励分布的匹配程度）和 **发现的模式数量（Number of Modes）**（衡量能否发现多模态高奖励区域）。
- **对比方法**：
  - GFlowNet变体：FM、DB、TB、SubTB（使用学习到的向后策略，部分实验也使用了均匀向后策略）。
  - MaxEnt RL：Soft DQN和Munchausen DQN（M-DQN）。

#### 4. 资源与算力
- 论文中明确说明：使用 **RTX 3090 GPU** 进行所有实验。
- **未提及**具体的GPU数量、训练总时长或总计算量。

#### 5. 实验数量与充分性
- **实验组数**：
  - TF Bind：在树和DAG两种结构下，各使用4个不同奖励函数（文中仅展示2个，其余见附录），共约8组对比曲线。
  - RNA：4个任务，包括准确率和模式数曲线及最终表格式结果（Tables C1, C2）。
  - QM9：1个任务（准确率和模式数曲线）。
  - 消融研究：在RNA任务中比较了GFlowNet使用均匀向后策略时的性能（附录C）。
- **充分性与公平性**：
  - 所有方法使用相同的网络架构（2层MLP 2048隐藏单元）、优化器（Adam）、学习率等超参数。
  - 报告3个随机种子的均值和标准差。
  - 实验覆盖了树结构、非树DAG结构以及不同复杂度的真实世界任务，具有较好的代表性。
  - 但缺少在超网格（HyperGrid）等违反路径不变性条件的任务上的实验（论文已指出该局限性）。

#### 6. 主要结论与发现
- **理论发现**：首次建立了GFlowNet的流函数与标准RL中均匀策略值函数之间的等价关系，并严格给出了适用条件（树结构无条件成立，非树DAG需路径不变性）。
- **算法贡献**：提出RPE，仅通过评估固定均匀策略即可实现GFlowNet的奖励匹配能力，无需训练过程中的策略迭代或熵正则化。
- **实验结论**：RPE在大多数任务上取得了与现有GFlowNet和MaxEnt RL方法相当或更优的性能，尤其是在RNA生成任务上准确性接近100%，且能发现更多模式。RPE收敛速度更快，训练更稳定（因评估的是固定策略，避免了非平稳性问题）。

#### 7. 优点
- **理论创新**：将GFlowNet与标准RL最基本的组件——策略评估联系起来，提供了全新的理论视角，不同于以往仅关注MaxEnt RL的工作。
- **方法简洁高效**：RPE只需要学习流函数 \(F_\theta\)，无需学习向后策略或依赖熵正则化，实现简单且训练稳定。
- **实验充分**：在多种结构（树、DAG）和多种真实世界任务上进行了系统性比较，结果可信度高。
- **公平性**：统一了网络架构、优化器等超参数，对比方法来自公开源代码。

#### 8. 不足与局限
- **适用条件限制**：非树DAG需要满足路径不变性条件（所有到达同一状态的轨迹具有相同的分支比），这在某些任务（如超网格）中不成立，限制了通用性。
- **计算效率**：当前RPE在推导前向策略时需对每个子状态进行独立前向传播，存在计算优化空间。
- **长轨迹问题**：论文未明确讨论长轨迹下的性能，但提及可借鉴现有信用分配方法改进。
- **实验覆盖**：缺少对违反路径不变性条件的任务（如超网格）的定量比较；也未在随机转移或连续动作空间中进行验证。
- **资源信息不完整**：未提及训练总时长、GPU数量等算力细节，不利于完全复现。

（完）
