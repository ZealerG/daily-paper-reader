---
title: Logarithmic Regret for Online KL-Regularized Reinforcement Learning
title_zh: 在线KL正则化强化学习的对数遗憾界
authors: "Heyang Zhao, Chenlu Ye, Wei Xiong, Quanquan Gu, Tong Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=6QH9IB53uy"
tags: ["query:graph-part"]
score: 8.0
evidence: KL正则化在线强化学习的理论成果
tldr: 针对KL正则化强化学习在在线设置下的理论分析缺失问题，本文提出基于乐观主义的在线上下文赌博机算法，并给出了对数遗憾界。该结果揭示了KL正则化在在线决策中的优势，为RLHF等应用提供了理论支撑。
source: ICML-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-6qh9ib53uy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1721, \"height\": 477, \"label\": \"Table\"}]"
motivation: KL正则化RL的理论分析不足，缺乏在线设置下的遗憾界。
method: 提出乐观型KL正则化在线上下文赌博机算法并分析其遗憾。
result: 获得了对数遗憾界，证明KL正则化在在线场景有效。
conclusion: 为KL正则化在在线RL中的应用奠定了理论基础。
---

## Abstract
Recent advances in Reinforcement Learning from Human Feedback (RLHF) have shown that KL-regularization plays a pivotal role in improving the efficiency of RL fine-tuning for large language models (LLMs). Despite its empirical advantage, the theoretical difference between KL-regularized RL and standard RL remains largely under-explored. While there is a recent line of work on the theoretical analysis of KL-regularized objective in decision making (Xiong et al., 2024a; Xie et al., 2024; Zhao et al., 2024), these analyses either reduce to the traditional RL setting or rely on strong coverage assumptions. In this paper, we propose an optimism-based KL-regularized online contextual bandit algorithm, and provide a novel analysis of its regret. By carefully leveraging the benign optimization landscape induced by the KL-regularization and the optimistic reward estimation, our algorithm achieves an $\mathcal{O}\big(\eta\log (N_{\mathcal R} T)\cdot d_{\mathcal R}\big)$ logarithmic regret bound, where $\eta, N_{\mathcal R},T,d_{\mathcal R}$ denote the KL-regularization parameter, the cardinality of the reward function class, number of rounds, and the complexity of the reward function class. Furthermore, we extend our algorithm and analysis to reinforcement learning by developing a novel decomposition over transition steps and also obtain a similar logarithmic regret bound.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义

这篇论文的核心问题在于：**KL正则化在RLHF等实际场景中表现出显著的样本效率优势，但其理论基础尚未建立**。现有在线RL算法（如Xiong等2024a）只能得到 $\tilde{O}(\sqrt{T})$ 的遗憾界，或依赖强覆盖假设（Zhao等2024）。本文旨在回答：
> 在线设置下，KL正则化RL是否比标准RL更高效，且无需额外覆盖假设？

### 方法论

#### 核心思想
利用**乐观主义原则（Optimism in the Face of Uncertainty, OFU）** 结合KL正则化诱导的良性优化景观，对子优度进行精细分解，得到平方项，从而避免传统分析中直接求和bonus导致的 $\sqrt{T}$ 界。

#### 关键技术细节
1. **KL-UCB（上下文赌博机）**：
   - 每轮更新奖励估计 $\hat{R}_t$，构造信心集并加入探索奖金 $b_t(x,a) = \min\{1, \beta_T \cdot U_{R_t}(\lambda, x,a; D_{t-1})\}$。
   - 策略为 $\pi_t(\cdot|x) \propto \pi_{\mathrm{ref}}(\cdot|x) \exp(\eta(\hat{R}_t(x,\cdot) + b_t(x,\cdot)))$。
   - 通过**函数梯度分析**（Lemma 4.4）和**均值定理**将子优度转化为平方误差，再借助eluder dimension得到 $\mathcal{O}(\eta \log(N_R T) \cdot d_R)$ 的对数界。

2. **KL-LSVI-UCB（MDP）**：
   - 采用LSVI框架，从后向前构建乐观Q值 $Q_h^t = \hat{f}_h^t + b_h^t$，其中bonus基于信心集和eluder uncertainty。
   - 关键创新是**策略分解**：将子优度拆分为 $H$ 个步骤间的差值 $I_{h+1}$，每个差值可化为赌博机形式，再应用Bandit的分析得到平方项，最终得到 $\mathcal{O}(\eta H^2 d_F \log(N_{F\oplus B}T))$ 的对数界。

### 实验设计

本文为**纯理论研究**，未进行任何数值实验或数据集验证。论文中所有结果均为数学定理和证明，没有与传统方法进行实验对比。

### 资源与算力

文中未提及任何GPU型号、数量或训练时长等计算资源信息。

### 实验数量与充分性

无实验。因此无法评估实验的充分性或公平性。

### 主要结论与发现

- 针对KL正则化上下文赌博机，提出KL-UCB算法，首次在标准在线设置下实现**对数遗憾界** $\mathcal{O}(\eta \log(N_R T) \cdot d_R)$，显著优于之前 $\mathcal{O}(\sqrt{T})$ 的结果，且不需要覆盖假设。
- 针对KL正则化MDP，提出KL-LSVI-UCB算法，同样获得对数遗憾界 $\mathcal{O}(\eta H^2 d_F \log(N_{F\oplus B}T))$，为在线RLHF理论提供首个对数界保证。
- 揭示了KL正则化在在线决策中的统计优势，为RLHF等实际应用提供了理论支撑。

### 优点

- **理论创新强**：提出了新颖的梯度分析和策略分解技术，突破传统RL分析的瓶颈。
- **结果显著**：从 $\sqrt{T}$ 改进到 $\log T$，且不依赖覆盖假设，更贴近实际场景。
- **方法通用**：可扩展到偏好反馈等更一般的设置。

### 不足与局限

- **无实验验证**：纯理论分析，缺乏实际数据或仿真环境对结论的检验。
- **MDP遗憾界中的H因子**：$H^2$ 可能不是最优，未来可优化。
- **函数类假设**：假设有限函数类或覆盖数，实际中无限函数类需额外处理。
- **未考虑偏好反馈**：虽然理论上可扩展，但文中重点在绝对奖励，与部分RLHF场景（仅偏好）有差距。
- **bonus计算复杂度**：实际中eluder uncertainty的计算可能困难。

（完）
