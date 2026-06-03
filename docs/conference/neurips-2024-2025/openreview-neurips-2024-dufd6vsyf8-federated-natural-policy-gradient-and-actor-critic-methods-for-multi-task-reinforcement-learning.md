---
title: Federated Natural Policy Gradient and Actor Critic Methods for Multi-task Reinforcement Learning
title_zh: 面向多任务强化学习的联邦自然策略梯度与演员-评论家方法
authors: "Tong Yang, Shicong Cen, Yuting Wei, Yuxin Chen, Yuejie Chi"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=DUFD6vsyF8"
tags: ["query:graph-part"]
score: 8.0
evidence: 基于图拓扑的联邦自然策略梯度与演员-评论家方法用于多任务强化学习
tldr: 分布式强化学习中多个智能体协作决策但需保护数据隐私。本文研究多任务设置，每个智能体有私有奖励函数但共享环境转移内核。提出联邦自然策略梯度和演员-评论家方法，智能体仅与图中的邻居通信，通过熵正则化实现全局最优策略。理论分析了算法的收敛性，并在实验中验证了效果。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-dufd6vsyf8/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1033, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dufd6vsyf8/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1119, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dufd6vsyf8/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1360, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dufd6vsyf8/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1106, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-dufd6vsyf8/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 755, \"height\": 580, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-dufd6vsyf8/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1159, \"height\": 397, \"label\": \"Table\"}]"
motivation: 分布式多智能体强化学习中，隐私保护和数据共享之间的矛盾亟待解决。
method: 提出联邦NPG和actor-critic算法，智能体通过图拓扑与邻居通信，协调学习全局最优策略。
result: 理论证明算法收敛到全局最优，实验在多任务环境中优于独立学习和集中式方法。
conclusion: 联邦学习框架能有效解决多任务RL中的隐私与协作问题，图通信结构是高效协调的关键。
---

## Abstract
Federated reinforcement learning (RL) enables collaborative decision making of multiple distributed agents without sharing local data trajectories. In this work, we consider a multi-task setting, in which each agent has its own private reward function corresponding to different tasks, while sharing the same transition kernel of the environment. Focusing on infinite-horizon Markov decision processes, the goal is to learn a globally optimal policy that maximizes the sum of the discounted total rewards of all the agents in a decentralized manner, where each agent only communicates with its neighbors over some prescribed graph topology.

We develop federated vanilla and entropy-regularized natural policy gradient (NPG) methods in the tabular setting under softmax parameterization, where gradient tracking is applied to estimate the global Q-function to mitigate the impact of imperfect information sharing. We establish non-asymptotic global convergence guarantees under exact policy evaluation, where the rates are nearly independent of the size of the state-action space and illuminate the impacts of network size and connectivity. To the best of our knowledge, this is the first time that global convergence is established for federated multi-task RL using policy optimization. We further go beyond the tabular setting by proposing a federated natural actor critic (NAC) method for multi-task RL with function approximation, and establish its finite-time sample complexity taking the errors of function approximation into account.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：在联邦强化学习（Federated RL）中，多个分布式智能体协作学习一个全局最优策略，同时保护各智能体的本地数据隐私。本文聚焦于多任务设定（multi-task RL），即每个智能体拥有私有的奖励函数（对应不同任务），但共享相同的环境转移核。其目标是，在完全去中心化的通信拓扑下（智能体仅与图中邻居通信），学习一个全局策略，最大化所有智能体折扣总奖励之和。

- **研究动机**：现有联邦RL研究多假设同质任务，而多任务场景下奖励异质性导致全局价值函数与本地价值函数存在差异，缺乏全局信息共享使得策略更新需要权衡邻域信息（促进共识）与本地数据（促进学习）。目前即使对于表格型无限时域MDP，也鲜有带非渐近收敛保证的算法。

- **整体含义**：本文首次为联邦多任务RL提供了基于策略优化的、几乎与状态-动作空间大小无关的全局收敛保证，填补了该领域的理论空白，且方法能扩展到函数逼近和随机策略评估。

## 2. 方法论

### 2.1 核心思想

- 采用软最大化参数化（softmax parameterization），将策略对数形式用于去中心化更新。
- 利用**动态平均共识**（dynamic average consensus）和**梯度追踪**（gradient tracking）技术，使每个智能体能够估计全局Q函数，克服信息共享不完美的影响。
- 提出了两种主要算法：
  - **FedNPG**：联邦自然策略梯度方法，包含普通版本和熵正则化版本。
  - **FedNAC**：联邦自然演员-评论家方法，结合函数逼近和随机策略评估。

### 2.2 关键技术细节

- **图拓扑与混合矩阵**：通信网络为无向加权图，混合矩阵 \(W\) 对称且双随机，谱半径 \(\sigma\) 衡量信息传播速度。
- **FedNPG更新规则**（算法1）：  
  每个迭代中，智能体更新策略对数形式：  
  \[
  \log \pi_n^{(t+1)}(a|s) = \sum_{j} W_{nj} \left( \log \pi_j^{(t)}(a|s) + \frac{\eta}{1-\gamma} T_j^{(t)}(s,a) \right) - \text{归一化项}
  \]  
  其中 \(T_n^{(t)}\) 为全局Q函数估计，通过追踪Q函数变化更新：  
  \[
  T_n^{(t+1)} = \sum_j W_{nj} \left( T_j^{(t)} + Q_j^{(t+1)} - Q_j^{(t)} \right)
  \]  
  （梯度追踪思想）

- **熵正则化FedNPG**（算法2）：在更新中引入正则化参数 \(\tau\)，鼓励探索，更新形式变为：
  \[
  \log \pi^{(t+1)} = W\left( (1-\frac{\eta\tau}{1-\gamma})\log \pi^{(t)} + \frac{\eta}{1-\gamma} T^{(t)} \right) - \text{归一化}
  \]

- **FedNAC**（算法3）：使用线性函数逼近，每个智能体本地运行评论家（Critic）通过随机梯度下降最小化Q函数逼近误差，并通过混合矩阵追踪全局Q函数；演员（Actor）更新类似FedNPG但使用线性特征。

### 2.3 理论保证

- **精确策略评估下**：  
  - 普通FedNPG：平均迭代收敛速率为 \(O(1/T^{2/3})\)，迭代复杂度几乎与状态-动作空间大小无关，依赖网络规模 \(N\)、谱半径 \(\sigma\) 和折扣因子 \(\gamma\)。  
  - 熵正则化FedNPG：全局线性收敛，速率 \(\rho(\eta) = \max\{1-\tau\eta/2, (3+\sigma)/4\} < 1\)。  
  - 相比于集中式NPG（\(\sigma=0\)），去中心化导致收敛变慢但依然保持近维度无关性。

- **不精确策略评估下**：证明了只要Q函数估计误差足够小（\(\ell_\infty\) 界），收敛速率保持不变，并给出样本复杂度 \(O(1/\varepsilon^{3.5})\)。

- **FedNAC**：在函数逼近和随机评估下，样本复杂度为 \(O(1/\varepsilon^{7/2})\)，与FedNPG在生成模型下的复杂度匹配。

## 3. 实验设计

- **环境**：使用 \(K \times K\) 网格世界（GridWorld）多任务场景。
- **任务目标**：多个智能体（\(N\)）学习一个全局最优策略，以跟随一条预定的从左上方到右下方的路径。每个智能体只拥有路径的部分信息（仅在其地图的阴影位置获得奖励1，其他位置0）。
- **动作空间**：仅允许向右或向下移动。
- **参数设置**：折扣因子 \(\gamma = 0.99\)；正则化系数 \(\tau\) 取 0, 0.005, 0.05；学习率 \(\eta = 0.1\)；智能体数量 \(N\) 变化；通信图使用标准环形图（每节点两个邻居，权重0.5）。也测试了不同邻居数和不同权重分配。
- **对比方法**：没有直接对比现有方法（因为是首个该类工作），但对比了无Q-tracking的朴素基线。
- **实验组数**：
  - 改变地图大小 \(K\)（5,10,20,30,50,70）测试收敛速度（图2）。
  - 改变智能体数量 \(N\)（10,20,30,40,50）测试影响（图3）。
  - 改变通信拓扑（邻居数从2.5到20，权重随机或等权）测试影响（图4）。
  - 对比有无Q-tracking（图5）。

## 4. 资源与算力

- **未明确说明**：论文仅提到实验在标准CPU上运行，没有给出GPU型号、数量或训练时长等具体算力信息。

## 5. 实验数量与充分性

- **实验数量**：共进行了约5组不同维度的实验（K变化、N变化、拓扑变化、正则化对比、Q-tracking消融），每组包含多个参数设置。
- **充分性与公平性**：
  - 实验覆盖了关键超参数（K, N, τ, 邻居数, 权重方式），验证了理论中关于网络规模、连通性和正则化的影响。
  - 消融实验（有无Q-tracking）验证了梯度追踪的必要性。
  - 由于缺乏现有多任务去中心化联邦RL基线，无法与同类方法直接对比，但通过参数扫描和趋势分析证明算法有效性。
  - 未提供统计误差棒，且结果在单次运行下展示，可能存在随机性影响。
  - 总体而言，实验设计较为全面，足以支撑主要结论，但缺乏与最先进方法的定量比较。

## 6. 主要结论与发现

1. **提出的FedNPG和熵正则化FedNPG在表格型设定下具有全局收敛保证**，收敛速率几乎独立于状态-动作空间大小，且依赖网络谱半径σ和智能体数量N。
2. **FedNPG对不精确策略评估具有鲁棒性**：只要Q函数估计误差足够小，收敛速率不变。
3. **熵正则化加速收敛**：获得线性收敛速率，鼓励探索。
4. **FedNAC扩展到函数逼近**，在去中心化多任务RL中首次给出了有限时间样本复杂度。
5. **实验验证**：
   - 收敛速度对地图大小K不敏感，符合理论。
   - 智能体数量N增加会减慢收敛（因网络共识更困难）。
   - 增加邻居数量（提高网络连通性）加速收敛；等权权重优于随机权重。
   - Q-tracking对收敛至关重要，无追踪时算法发散。

## 7. 优点

- **理论深度**：首次为联邦多任务RL提供几乎维度无关的全局收敛保证，推导细致，包含精确和不精确评估情形。
- **方法创新**：将梯度追踪思想与自然策略梯度结合，解决了去中心化场景下全局Q函数估计难题。
- **算法完备性**：从表格型到函数逼近，从精确评估到随机评估，覆盖全面。
- **实验设计**：通过网格世界多任务场景，直观验证理论预测的参数影响（K, N, σ等）。
- **对抗噪声**：证明了算法对Q函数估计误差的鲁棒性，实际应用价值高。

## 8. 不足与局限

- **假设较强**：
  - 需要转移核共享、混合矩阵双随机且对称、策略评估误差足够小（ℓ∞）。
  - 函数逼近假设特征有界且协方差矩阵正定，线性近似误差有界。
  - 实际中满足这些假设可能需要仔细设计。
- **实验局限**：
  - 仅在模拟网格世界上验证，未扩展到更复杂环境（如Atari、机器人控制）。
  - 缺乏与现有去中心化联邦RL方法的定量对比（虽然现有方法不完全对齐）。
  - 未报告统计误差棒，结果可靠性缺少统计支撑。
  - 未公开代码和详细复现步骤，可复现性受限。
- **通信与计算成本**：理论复杂度中包含了网络谱半径相关项，实际中（σ接近1）可能收敛很慢，未讨论通信轮数与样本量的权衡。
- **隐私假设**：虽然不共享奖励函数，但仍需共享策略参数和Q函数估计，可能存在信息泄露风险。

（完）
