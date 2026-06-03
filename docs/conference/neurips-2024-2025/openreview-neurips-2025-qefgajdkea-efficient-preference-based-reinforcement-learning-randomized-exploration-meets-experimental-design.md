---
title: "Efficient Preference-Based Reinforcement Learning: Randomized Exploration meets Experimental Design"
title_zh: 高效基于偏好的强化学习：随机探索与实验设计
authors: "Andreas Schlaginhaufen, Reda Ouhamma, Maryam Kamgarpour"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=qEfgajdKea"
tags: ["query:graph-part"]
score: 4.0
evidence: 基于偏好反馈和随机探索的强化学习算法
tldr: 研究基于轨迹偏好比较的强化学习，提出随机探索元算法，避免乐观方法计算难题，在保证遗憾界的同时降低查询复杂度。适用于通用RL算法研究，但与图划分无直接关联。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qefgajdkea/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qefgajdkea/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 689, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qefgajdkea/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 567, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qefgajdkea/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1419, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qefgajdkea/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 673, \"height\": 397, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qefgajdkea/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1473, \"height\": 824, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qefgajdkea/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1268, \"height\": 323, \"label\": \"Table\"}]"
motivation: 偏好强化学习中，如何选择信息性查询来识别潜在奖励并保证理论保证是核心挑战。
method: 提出基于随机探索的元算法，结合批次轨迹对收集与实验设计。
result: 建立了遗憾和最后迭代收敛保证，并改进了查询复杂度。
conclusion: 该算法为偏好强化学习提供了高效可扩展方案。
---

## Abstract
We study reinforcement learning from human feedback in general Markov decision processes, where agents learn from trajectory-level preference comparisons. A central challenge in this setting is to design algorithms that select informative preference queries to identify the underlying reward while ensuring theoretical guarantees. We propose a meta-algorithm based on randomized exploration, which avoids the computational challenges associated with optimistic approaches and remains tractable. We establish both regret and last-iterate guarantees under mild reinforcement learning oracle assumptions. To improve query complexity, we introduce and analyze an improved algorithm that collects batches of trajectory pairs and applies optimal experimental design to select informative comparison queries. The batch structure also enables parallelization of preference queries, which is relevant in practical deployment as feedback can be gathered concurrently. Empirical evaluation confirms that the proposed method is competitive with reward-based reinforcement learning while requiring a small number of preference queries.

---

## 论文详细总结（自动生成）

# 高效基于偏好的强化学习：随机探索与实验设计

## 1. 论文的核心问题与整体含义（研究动机和背景）

在强化学习（RL）中，设计符合人类目标的奖励函数往往非常困难，错误的奖励函数会导致次优或危险的行为。基于人类反馈的强化学习（RLHF）通过偏好比较（preference feedback）来指导学习，避免了手动设计奖励的难题。然而，RLHF面临两个关键挑战：**计算复杂性**——传统乐观方法（optimistic approaches）需要最大化一个涉及状态分布范数的探索奖励，该问题即使在表格设定下也难以求解；**查询效率**——人类反馈昂贵，需要主动选择信息量大的偏好查询来降低反馈次数。本文针对一般马尔可夫决策过程（MDP），研究如何设计**可计算且查询高效**的RLHF算法，同时提供严格的遗憾界（regret）和最后迭代收敛（last-iterate）保证。

## 2. 论文提出的方法论

### 2.1 核心思想
- **随机探索**：采用线性汤普森采样（linear Thompson sampling）风格的随机化，替代计算困难的乐观原则。每次从当前置信椭球中采样一个奖励参数，然后通过RL oracle求解该参数下的近似最优策略。
- **最大似然估计（MLE）**：使用逻辑回归损失（Bradley-Terry模型）估计真实奖励参数，并构造基于设计矩阵的置信椭球。
- **批量查询与最优实验设计**：通过懒惰更新（lazy updates）收集成批轨迹对，再使用D-最优设计（D-optimal design）从批中选择最具信息量的轨迹对进行偏好查询，从而减少查询次数并支持并行化。

### 2.2 关键技术细节
- **奖励模型**：线性奖励模型 \( r_{\theta^*}(s,a)=\langle\theta^*,\phi(s,a)\rangle \)，偏好概率符合Bradley-Terry模型：\( P(\tau\succ\tau')=\sigma(\langle\theta^*,\phi(\tau)-\phi(\tau')\rangle) \)。
- **置信椭球**：基于设计矩阵 \( V_t = \lambda I + \sum_k x_k x_k^\top \) 构建，其中 \( x_k = \phi(\tau_k)-\phi(\tau'_k) \)。MLE估计 \( \hat{\theta}_t \) 满足 \( \|\theta^*-\hat{\theta}_t\|_{V_t} \leq O(\sqrt{\kappa(d\log(t)+\log(1/\delta))}) \)。
- **随机采样**：从 \( \mathcal{N}(\hat{\theta}_t,\beta_t^2 V_t^{-1}) \) 中采样 \( \tilde{\theta}_t \)，用于驱动探索。
- **RL Oracle**：假设存在一个 \( (\varepsilon,\delta) \)-PAC RL算法（如PPO），可在给定奖励参数下输出近似最优策略。
- **三种算法变体**：
  - **RPO-Regret**（Algorithm 1）：逐轮采样参数、执行策略、收集偏好反馈，并更新MLE；适用于遗憾最小化。
  - **RPO-Explore**（Algorithm 2）：使用零均值采样进行偏好无关探索，所有偏好反馈留到最后一批处理，输出最终策略；适用于PAC保证（最后迭代子优度界）。
  - **LRPO-OD-Regret**（Algorithm 3）：引入懒惰更新（仅当信息增益超过常数倍时才触发更新）和贪婪D-最优设计（Algorithm 4），选择信息量最大的轨迹对进行查询；理论遗憾界仅增加常数因子，批大小平均为 \( \tilde{O}(T/(d\log T)) \)。

### 2.3 算法流程（文字说明）
1. **初始化**：设置超参数、空数据集、初始设计矩阵 \( V_1=\lambda I \)。
2. **循环（每个RLHF轮次 \( t=1,\dots,T \)）**：
   - 根据当前MLE估计 \( \hat{\theta}_{t_{\text{stop}}} \) 和设计矩阵 \( V_{t_{\text{stop}}} \) 采样 \( \tilde{\theta}_t \)。
   - 调用RL Oracle得到 \( \pi_t = \text{PAC-RL}(\tilde{\theta}_t,\varepsilon,\delta'/T) \)。
   - 采样两个轨迹 \( \tau_t\sim P_{\pi_t},\tau'_t\sim P_{\pi'_{t}} \)（\( \pi'_t \) 为比较策略，如前一策略或当前MLE最优策略）。
   - 计算 \( x_t = \phi(\tau_t)-\phi(\tau'_t) \)，更新 \( V_{t+1}/W_{t+1} \)。
   - **RPO-Regret**：立即收集偏好反馈 \( y_t \)，更新MLE。
   - **LRPO-OD-Regret**：判断是否触发更新（\( \det(W_t) > (1+C)\det(V_{t_{\text{stop}}}) \)），若是则对缓冲池 \( D \) 运行最优设计选择子集 \( D_{\text{opt}} \)，仅对该子集查询偏好反馈，并更新MLE和比较策略。
3. **输出**：对RPO-Explore，最终用所有反馈数据计算MLE并输出策略；对RPO-Regret和LRPO-OD-Regret，输出遗憾曲线。

## 3. 实验设计

### 3.1 实验场景与数据集
- **网格世界（Gridworld）**：\( 6\times 6 \) 表格环境，确定性转移，4个动作，6个边界状态特征（one-hot），两个目标状态给予奖励0.5。折扣因子 \( \gamma=0.9 \)。
- **Isaac-Cartpole-v0**：来自Nvidia Isaac Lab的连续控制任务，目标为平衡倒立摆。奖励为5个线性特征（存活、终止、目标跟踪、小车速度、关节速度）的组合。

### 3.2 Benchmark与对比方法
- **Gridworld**：对比 RPO-Regret 与基于熵探索的RLHF基线（entropy-based exploration）。
- **Cartpole**：对比三种算法：RPO-Regret、LRPO-Regret（Algorithm 3不带最优设计）、LRPO-OD-Regret（Algorithm 3带最优设计）。所有方法使用PPO作为RL Oracle，每轮采样100条轨迹。
- **额外实验（Appendix F）**：包括RPO-Explore及其懒惰/最优设计变体，比较最后迭代奖励和查询数量。

### 3.3 实验设置
- 每轮RLHF使用30步PPO训练。
- 总共30个RLHF迭代，重复20个独立种子（seed）。
- 合成偏好：利用真实奖励参数生成偏好标签。
- 评估指标：累积遗憾（cumulative regret）、查询数量、最终策略的奖励值。

## 4. 资源与算力

论文在Appendix F中明确说明：实验运行在一台配备 **Intel i9-14900KS CPU 和 NVIDIA RTX 4090 GPU** 的单机上。完成30轮RLHF迭代约需 **2分50秒**。未提及多GPU或大规模分布式训练。文中也指出Gridworld实验无需GPU，Cartpole实验使用单GPU。

## 5. 实验数量与充分性

- **实验数量**：每个对比实验均进行了 **20次独立运行**，并报告中位数和0.2/0.8分位数（误差带）。
- **覆盖场景**：一个表格环境（验证理论）和一个连续控制环境（验证实际可行性）。未涉及更复杂的任务（如Atari、LLM微调）或真实人类反馈。
- **消融研究**：Cartpole实验中比较了带/不带懒惰更新、带/不带最优设计三种变体，显示了查询数量的显著减少。
- **充分性评价**：实验设计基本合理，误差带提供了统计可靠性。但环境种类偏少，且仅使用合成偏好，缺乏真实人类标注或LLM生成的反馈，限制了结论的泛化性。此外，未与最新的RLHF基线（如基于乐观的算法，尽管明言其不可计算）进行性能对比（可能因为那些方法在此环境下不可行）。总体而言，实验充分验证了所提算法的有效性，但不足以证明其在更复杂场景下的优势。

## 6. 论文的主要结论与发现

- **理论贡献**：
  - RPO-Regret 实现 \( O(\sqrt{\kappa d^3 T \log^3(dT/\delta)}) \) 的遗憾界，与现有随机探索RLHF方法相当或更优，且无需线性MDP假设。
  - RPO-Explore 输出策略的次优性为 \( \tilde{O}(\sqrt{\kappa d^3/T}) \) ，是首个基于随机探索的偏好无关探索算法。
  - LRPO-OD-Regret 在仅增加常数因子的前提下，将查询次数降低至平均 \( \tilde{O}(T/(d\log T)) \)，同时保持相同遗憾阶。
- **实验发现**：
  - RPO-Regret 显著优于基于熵探索的基线，验证了随机探索的有效性。
  - LRPO-OD-Regret 在Cartpole上达到与RPO-Regret相当的性能，但使用了**显著更少的偏好查询**（数量级减少），说明最优设计在实际中能高效选取信息性轨迹。
  - 三种算法均能达到与基于真实奖励的PPO相近的性能，表明仅需少量偏好查询即可学习有效策略。

## 7. 优点

- **计算高效**：摒弃了不可计算的乐观方法，采用随机探索，使得算法可扩展到一般MDP（只需调用PAC-RL Oracle）。
- **理论保证完整**：同时提供了遗憾和PAC式保证，且依赖假设合理（RL Oracle在线性MDP、表格MDP中已有实现）。
- **查询效率改进**：通过批量收集和最优实验设计，大幅减少人类反馈需求，并支持并行化，更贴近实际部署。
- **算法设计新颖**：将实验设计工具（D-optimal design）引入RLHF的在线主动查询选择，并证明有理论保证。
- **实验复现性好**：代码开源，提供详细超参数和实验环境描述。

## 8. 不足与局限

- **偏好模型假设**：假设Bradley-Terry模型（线性奖励加sigmoid偏好概率），可能无法完全反映真实人类偏好的复杂性（如非传递性、异质性）。作者承认这一局限。
- **对RL Oracle的依赖**：算法每步都需要调用PAC-RL Oracle，实践中PPO等并非真正的PAC Oracle，且多次调用可能导致高样本复杂度。理论上虽可用reward-free Oracle，但实际实现复杂。
- **实验覆盖面窄**：仅测试了简单的表格环境和单一连续控制任务（Cartpole），未在更复杂任务（如Atari、机器人操作、LLM对齐）上验证，也未使用真实人类/LLM反馈。
- **缺少与最新方法的直接对比**：虽然论文论证了乐观方法不可计算，但未能提供一个“弱但可计算”的基线（如基于奖励拟合的RLHF基线）的对比，可能削弱实证说服力。
- **理论因子潜在改进**：随机探索引入了额外的 \( \sqrt{d} \) 因子，能否消除尚待研究。懒惰更新和最优设计的最坏情况理论保证虽与原始算法一致，但实际查询减少程度依赖于具体实例，论文未提供下界分析。

（完）
