---
title: Bayesian Ego-graph Inference for Networked Multi-Agent Reinforcement Learning
title_zh: 基于贝叶斯自我图推理的网络化多智能体强化学习
authors: "Wei Duan, Jie Lu, Junyu Xuan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=3qeTs05bRL"
tags: ["query:graph-part"]
score: 8.0
evidence: 基于随机图策略的网络化多智能体强化学习贝叶斯框架
tldr: 现有网络化多智能体强化学习方法假设静态邻域，难以适应动态环境。本文提出随机图策略，每个智能体基于局部物理邻域采样子图进行决策。在此基础上设计贝叶斯图推断框架BayesG，以去中心化方式学习动态图结构。实验表明该方法在异构和动态网络环境中显著优于静态邻域方法，同时保持了通信效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1425, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 754, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1424, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1359, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1441, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1406, \"height\": 1662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1455, \"height\": 2043, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-3qets05brl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1044, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3qets05brl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 1095, \"label\": \"Table\"}]"
motivation: 网络化MARL中静态邻域假设限制了智能体对动态环境的适应能力。
method: 提出随机图策略和贝叶斯图推断框架，每个智能体去中心化地从局部邻域采样子图并基于此决策。
result: 在多个动态网络基准任务上，方法在性能和通信效率上优于现有静态邻域方法和集中式方法。
conclusion: 通过学习动态图结构，网络化MARL能更好地适应环境变化，是实际部署的关键进步。
---

## Abstract
In networked multi-agent reinforcement learning (Networked-MARL), decentralized agents must act autonomously under local observability and constrained communication over fixed physical graphs. Existing methods often assume static neighborhoods, limiting adaptability to dynamic or heterogeneous environments. While centralized frameworks can learn dynamic graphs, their reliance on global state access and centralized infrastructure is impractical in real-world decentralized systems. We propose a stochastic graph-based policy for Networked-MARL, where each agent conditions its decision on a sampled subgraph over its local physical neighborhood. Building on this formulation, we introduce \textbf{BayesG}, a decentralized actor–critic framework that learns sparse, context-aware interaction structures via Bayesian variational inference. Each agent operates over an ego-graph and samples a latent communication mask to guide message passing and policy computation. The variational distribution is trained end-to-end alongside the policy using an evidence lower bound (ELBO) objective, enabling agents to jointly learn both interaction topology and decision-making strategies.
BayesG outperforms strong MARL baselines on large-scale traffic control tasks with up to 167 agents, demonstrating superior scalability, efficiency, and performance.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：现有网络化多智能体强化学习（Networked-MARL）方法大多假设静态邻域结构，智能体只能与固定物理邻居通信，无法根据动态环境自适应调整交互关系。这限制了在交通信号控制等实际场景中的协调效率和性能。
- **核心问题**：如何让去中心化的智能体仅基于局部观测和任务反馈，动态地学习并适应交互结构，同时遵守物理拓扑约束。
- **整体含义**：提出一种去中心化的贝叶斯变分推理框架（BayesG），使每个智能体在学习决策策略的同时，推断出稀疏、上下文相关的通信子图，从而提升协调效率、可扩展性和可解释性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：
  - 引入**随机图策略**（stochastic graph-based policy）：每个智能体从学习的分布中采样一个子图（ego-graph），并基于该子图进行决策。
  - 将交互图学习视为**贝叶斯变分推断**问题：将边掩码（edge mask）视为隐变量，用变分分布近似后验，通过ELBO目标联合优化策略和通信结构。
- **关键技术细节**：
  - **图策略定义**：`π_i(ui, G_{V_i} | s_{V_i}) = ρ(G_{V_i} | s_{V_i}; φ_i) · π̃_i(ui | f̃_i(s_{V_i}, G_{V_i}); θ_i)`，其中 `ρ` 为子图采样分布，`G_{V_i} ⪯ G^{env}_{V_i}` 保证物理可行。
  - **贝叶斯图推断**：隐变量 `Z_i`（二进制掩码）的后验 `p(Z_i | G^{env}_{V_i}, D_i)` 用变分分布 `q(Z_i; φ_i) = ∏ Bern(z_ij; σ(φ_ij))` 近似，使用Gumbel-Softmax重参数化实现离散采样可微。
  - **ELBO目标**：`L_ELBO = E_q[ -L_{θ,φ} + 对数先验 - log q ]`，其中`L_{θ,φ}` 是图条件化的策略损失（包含优势估计和熵正则），`-log q` 相当于掩码熵正则，防止过早坍缩。
  - **训练流程**：每个agent采样掩码 → 构造有效子图 → GNN编码邻域信息 → 策略选择动作 → 执行并收集轨迹 → 更新actor、critic和变分参数。
- **算法流程**（文字说明）：
  - 初始化：策略参数θ_i，价值网络ω_i，变分参数φ_i。
  - 循环时间步：
    1. 每个agent从`q(Z_i; φ_i)`采样二进制掩码，得到有效邻接矩阵 `A_i^* = Z_i ⊙ G^{env}_{V_i}`。
    2. 用GCN对观测、策略指纹、轨迹特征进行掩码消息传递，产生编码 `s̃_i`。
    3. 更新LSTM隐藏状态，采样动作，计算价值。
    4. 执行动作，模拟环境获得下一状态和奖励。
    5. 积累批量数据，计算优势估计。
    6. 使用ELBO更新actor和变分参数，使用MSE更新critic。

## 3. 实验设计：使用了哪些数据集/场景，benchmark，对比了哪些方法
- **场景**：自适应交通信号控制（ATSC），基于SUMO仿真器。
  - 中等规模：`ATSC_Grid`（5×5合成网格），`Monaco`（28个路口真实布局）
  - 大规模：`NewYork33`（33个路口）、`NewYork51`（51个路口）、`NewYork167`（167个路口），均基于曼哈顿真实路网。
- **奖励**：负的排队车辆数（归一化）。
- **对比方法**（统一Actor-Critic骨干）：
  - 非通信类：IA2C、ConseNet（共识平均）、FPrint（策略指纹）、LToS（局部奖励分享）
  - 通信类：CommNet（平均消息）、NeurComm（编码拼接消息）、BayesG（本文）
- **实现细节**：所有方法共享类似的网络架构和超参数；控制间隔、训练步数等均统一设置。

## 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量或训练时长。仅提到实验在5个随机种子下运行，但未提供具体硬件配置。因此算力细节缺失，无法评估计算成本。

## 5. 实验数量与充分性
- **实验数量**：
  - **主实验**：5个场景×7种方法 = 35条学习曲线（每个曲线5 seeds平均）。
  - **定性可视化**：Grid环境下的交通拥堵对比图（多个时间点）。
  - **案例研究**：在Grid上展示了学习到的交互图与交通密度对应关系。
  - **消融实验**（2个场景）：
    - 图掩码策略：无掩码 vs 随机掩码 vs 学习掩码（BayesG）
    - 输入特征类型：状态 vs 轨迹 vs 策略 vs 组合
  - **训练损失分析**：在3个场景上绘制了各损失分量曲线。
- **充分性与公平性**：
  - 对比方法覆盖了主流网络化MARL基线，且实现一致（统一A2C骨干）。
  - 消融实验验证了关键组件的必要性。
  - 实验覆盖了从合成到真实路网、从小规模到大规模（167 agents）的场景，具有较好的代表性。
  - 不足之处：仅使用交通控制领域，未在其它类型网络化MARL任务（如机器人编队、电力网络）上验证；与Dec-POMDP类动态图方法（如CASEC）的对比被明确排除，可能遗漏部分潜在更强的基线。

## 6. 论文的主要结论与发现
- **性能领先**：BayesG在所有5个场景中均优于所有基线，特别是在大规模NewYork场景中收敛更快、最终回报更高。
- **自适应通信**：可视化显示BayesG能学习到与交通拥堵模式相关的动态交互图——当某区域拥堵时，上游交叉口会增大通信权重，主动调节信号以缓解拥堵。
- **稀疏性与效率**：随机图策略和贝叶斯推断使得每个agent仅需要与少量关键邻居通信，避免冗余消息，同时保持高性能。
- **消融结论**：学习掩码优于固定或随机掩码；使用多种特征（状态+轨迹+策略）组合比单一特征效果更好。

## 7. 优点
- **方法创新**：将贝叶斯变分推断引入网络化MARL的图结构学习，使得每个agent能基于局部信息自适应地选择邻居，兼顾物理约束和任务反馈。
- **去中心化**：完全去中心化训练与执行，无需全局信息或中心服务器，适用于真实分布式系统。
- **可解释性**：学习到的通信概率矩阵和网络图可被可视化，直观展示协调模式。
- **理论连接**：与最大熵强化学习（SAC）建立联系，双熵正则（动作熵+掩码熵）有助于鲁棒性和探索。
- **实验充分**：多尺度场景、多种基线、消融研究、定性分析等较全面地验证了方法有效性。

## 8. 不足与局限
- **固定物理拓扑**：假设环境图是静态预定义的，无法处理拓扑动态变化的场景（例如移动机器人）。
- **局部可观测限制**：每个agent仅基于ego-graph局部信息推断图，无法捕捉长程依赖或全局上下文。
- **超参数敏感**：Gumbel-Softmax温度、稀疏先验λ等需要适当调参，否则可能导致过度剪枝或欠剪枝。
- **计算开销**：相比非通信方法，增加了变分采样和GNN计算；训练时间随邻域规模增长，但文中未量化。
- **领域单一**：仅在交通信号控制上评测，在其它网络化MARL问题（如无人机编队、智能电网）上的泛化性未验证。
- **与CTDE方法对比不足**：虽说明了Dec-POMDP方法不适用，但未与可应用的去中心化动态图学习方法（如某些基于注意力的方法）直接对比。

（完）
