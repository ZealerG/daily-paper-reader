---
title: In-Context Fully Decentralized Cooperative Multi-Agent Reinforcement Learning
title_zh: 上下文中的完全去中心化合作多智能体强化学习
authors: "Chao Li, Bingkun BAO, Yang Gao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=5J4IpiMKkq"
tags: ["query:graph-part"]
score: 9.0
evidence: 去中心化多智能体强化学习
tldr: 本文针对完全去中心化多智能体强化学习中的非平稳性和相对过泛化问题，提出返回感知上下文（RAC）方法，让每个智能体利用局部回报信息建模联合策略，解决了现有方法无法同时处理这两个问题的局限。实验表明RAC在多个合作任务上显著优于基线。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-5j4ipimkkq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1315, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5j4ipimkkq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 977, \"height\": 807, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5j4ipimkkq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1389, \"height\": 1016, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5j4ipimkkq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1392, \"height\": 651, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5j4ipimkkq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1389, \"height\": 1019, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-5j4ipimkkq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 367, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5j4ipimkkq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 501, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5j4ipimkkq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 502, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5j4ipimkkq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1089, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5j4ipimkkq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 937, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5j4ipimkkq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1433, \"height\": 397, \"label\": \"Table\"}]"
motivation: 去中心化多智能体RL中，缺乏他人动作信息导致非平稳性和过泛化问题。
method: 提出Return-Aware Context，通过局部回报动态建模任务变化。
result: 在多个合作环境下优于现有方法，同时解决了两个关键问题。
conclusion: RAC有效实现了去中心化环境下的联合策略建模。
---

## Abstract
In this paper, we consider fully decentralized cooperative multi-agent reinforcement learning, where each agent has access only to the states, its local actions, and the shared rewards. The absence of information about other agents' actions typically leads to the non-stationarity problem during per-agent value function updates, and the relative overgeneralization issue during value function estimation. However, existing works fail to address both issues simultaneously, as they lack the capability to model the agents' joint policy in a fully decentralized setting. To overcome this limitation, we propose a simple yet effective method named Return-Aware Context (RAC). RAC formalizes the dynamically changing task, as locally perceived by each agent, as a contextual Markov Decision Process (MDP), and addresses both non-stationarity and relative overgeneralization through return-aware context modeling. Specifically, the contextual MDP attributes the non-stationary local dynamics of each agent to switches between contexts, each corresponding to a distinct joint policy. Then, based on the assumption that the joint policy changes only between episodes, RAC distinguishes different joint policies by the training episodic return and constructs contexts using discretized episodic return values. Accordingly, RAC learns a context-based value function for each agent to address the non-stationarity issue during value function updates. For value function estimation, an individual optimistic marginal value is constructed to encourage the selection of optimal joint actions, thereby mitigating the relative overgeneralization problem. Experimentally, we evaluate RAC on various cooperative tasks (including matrix game, predator and prey, and SMAC), and its significant performance validates its effectiveness.

---

## 论文详细总结（自动生成）

## 论文详细总结

### 1. 核心问题与整体含义（研究动机和背景）
- **研究问题**：在完全去中心化的合作多智能体强化学习（MARL）中，每个智能体只能访问状态、自身局部动作和共享奖励，无法获取其他智能体的动作信息。这导致两个关键问题：
  - **非平稳性（non-stationarity）**：由于其他智能体的策略不断演化，每个智能体感知到的局部任务动态（状态转移和奖励）随之变化，破坏了值函数更新的收敛性。
  - **相对过泛化（relative overgeneralization）**：在估计局部动作值时，其他智能体的探索性或次优动作会干扰估计，使得智能体倾向于选择次优的联合动作，而非最优联合动作。
- **现有方法局限**：现有完全去中心化方法通常只针对其中一个问题（非平稳性或相对过泛化），无法同时解决两者，因为它们缺乏在完全去中心化设置下建模智能体联合策略的能力。
- **本文目标**：提出一种统一框架，同时缓解非平稳性和相对过泛化问题，提升完全去中心化合作策略的学习效率与最终性能。

---

### 2. 方法论：核心思想、技术细节与算法流程
#### 核心思想
- **返回感知上下文（Return-Aware Context，RAC）**：将每个智能体局部感知的动态任务形式化为**上下文马尔可夫决策过程（Contextual MDP）**，其中上下文对应其他智能体的联合策略。利用**训练回合回报（episodic return）** 作为上下文的表示，区分不同的联合策略。
- 通过学习**基于上下文的值函数**解决非平稳性，通过构造**个体乐观边际值（individual optimistic marginal value）** 缓解相对过泛化。

#### 关键技术细节
1. **任务形式化**：
   - 每个智能体 i 的局部任务建模为 Contextual MDP：⟨C, S, Aᵢ, M(c)⟩，其中上下文 c ∈ C 对应其他智能体的一种联合策略 π_⁻ⁱ。
   - 非平稳性归因于上下文在时间上的切换。

2. **上下文建模**：
   - 假设联合策略仅在回合间更新（回合内固定），这是多数 MARL 方法的常用设定。
   - 每个智能体根据自身局部轨迹的**回合回报 R(τⁱ)** 来估计当前联合策略。将连续回报离散化为 m 个区间，每个区间索引 κ 作为上下文 c_κ 的 one-hot 编码。
   - 计算方式：κ = ⌊ (R(τⁱ) - R_min) / ((R_max - R_min)/m) ⌋。

3. **基于上下文的值函数学习**：
   - 学习 Qᵢ(s_t, c_κ, aᵢ_t) ，并使用 TD 损失更新（公式7）：
     - L_C(θᵢ) = E[(r_t + γ max_{a^{i}_{t+1}} Qᵢ(s_{t+1}, c_κ, a^{i}_{t+1}) - Qᵢ(s_t, c_κ, a^{i}_t))²]

4. **个体乐观边际值**：
   - 定义 ϕᵢ(s_t, aᵢ_t) = max_{c_κ ∈ C} Qᵢ(s_t, c_κ, aᵢ_t) （公式8），取所有上下文下 Q 值的最大值，体现“其他智能体总能采取合作动作”的乐观假设，从而消除次优动作的影响。

5. **辅助学习与动作选择**：
   - 由于早期训练时回报空间覆盖不全，直接使用 ϕᵢ 选择动作效果不佳。故额外学习一个独立的值函数 Qᵢ_S(s_t, aᵢ_t)，其损失包括标准 TD 损失和一个**监督损失**（KL 散度），使 πᵢ_S 模仿由 ϕᵢ 导出的策略 πᵢ（公式9-11）。
   - 智能体在训练早期根据 Qᵢ_S 选择动作，以保证探索效率；后期逐渐引导 Qᵢ_S 模仿 ϕᵢ 的策略，实现最优动作选择。

6. **整体算法流程（Algorithm 1）**：
   - 初始化每个智能体的 Qᵢ 和 Qᵢ_S。
   - 每个回合内，智能体基于 Qᵢ_S（或 ε-贪婪）选择动作，存储轨迹到回放缓冲区。
   - 训练时，采样回合轨迹，计算回合回报并离散化得到上下文 c_κ，分别更新 Qᵢ 和 Qᵢ_S。

---

### 3. 实验设计
#### 使用场景/数据集
- **Matrix Game**：双智能体合作矩阵博弈（2×3 动作），存在相对过泛化的陷阱。
- **Predator and Prey**：8 个捕食者 vs 8 个猎物，部分可观测，需要合作捕获（两两同时捕获获+10，单独捕获罚-2）。
- **StarCraft Multi-Agent Challenge (SMAC)**：7 张经典地图（2s3z, 3s5z, 3s_vs_4z, 3s_vs_5z, 5m_vs_6m, 10m_vs_11m, 2s_vs_1sc），涵盖对称/非对称、同质/异质单元。

#### 对比方法
- **完全去中心化基线**：IQL (Independent Q-learning)、Hysteretic Q-learning、I2Q。
- **补充对比（附录C.4）**：集中训练-分散执行的代表方法 QMIX 和 VDN。

#### 评估指标
- Matrix Game：测试回报（Test Return）。
- Predator and Prey：测试回报。
- SMAC：测试胜率（Test Win Rates）。

---

### 4. 资源与算力
- 原文在附录 C.5 中指出：所有实验在配备 **AMD EPYC 7542 32-Core CPU、504GB RAM、8× NVIDIA GeForce RTX 4090 D GPU** 的服务器上运行。但未明确给出每个实验的具体 GPU 使用数、训练时长等详细算力统计。

---

### 5. 实验数量与充分性
#### 实验数量
- 主对比实验：共 3 个场景（Matrix Game + Predator & Prey + 7个 SMAC 地图），每个场景对比 3-4 种完全去中心化方法（加上 QMIX/VDN 为 5-6 种）。
- 消融实验（Ablation Study）：针对**离散区间数 m**（5, 10, 15）和**监督损失权重 β**（0.01, 0.1, 1.0, 10.0）在 Predator & Prey 和 5m_vs_6m 上分别进行。
- 附加变体实验：比较 RAC 与 RAC_w_ϕi（不使用 Qᵢ_S）。
- 均使用 5 个随机种子，报告中位数和标准误差。

#### 充分性与公平性
- 对比方法均来自公开代码库或官方实现，超参数按照推荐设置或调优（如 Hysteretic Q 对 β 进行了多值扫描）。
- 实验覆盖了简单博弈、部分可观测协作任务、复杂多智能体对抗任务，验证了方法的可扩展性。
- 消融实验分析了关键超参数的影响，并解释了为什么需要额外学习 Qᵢ_S。
- 在附录中还与 CTDE 方法进行了补充对比，说明 RAC 在简单任务上甚至优于 QMIX/VDN，但在复杂 SMAC 地图上略逊，体现了公平的讨论。
- 结论客观，既展示了优势（如 5m_vs_6m、10m_vs_11m），也指出了不足（如 2s3z、3s_vs_5z 上优势不明显，I2Q 在部分地图上更强）。

---

### 6. 主要结论与发现
- RAC 在完全去中心化设置下，通过**回报感知上下文建模**，同时缓解了非平稳性和相对过泛化问题，在多个合作任务上显著优于 IQL、Hysteretic Q-learning 和 I2Q。
- 在 Matrix Game 中，RAC 正确选择了最优联合动作（a1,a1）获得 8 奖励，而 IQL 陷入次优。
- 在 Predator & Prey 中，RAC 实现了高效的协作捕获（+40 回报），Hysteretic Q 因过度乐观和过估计表现差，I2Q 因部分可观测下 QSS 估计不准而失败。
- 在 SMAC 的 7 张地图中，RAC 在 5m_vs_6m、10m_vs_11m、3s5z、3s_vs_4z 上大幅领先 IQL；在部分地图上（如 2s3z）与 IQL 相当或略逊于 I2Q，表明其优势依赖于任务特性。
- 消融实验表明：合理的 m 和 β 对性能至关重要；单独使用 ϕᵢ（RAC_w_ϕi）在复杂任务中因回报空间覆盖不足而失败，需要 Qᵢ_S 辅助。

---

### 7. 优点
- **理论框架清晰**：将非平稳性归因于上下文切换，统一了两种问题的解决方案。
- **简单有效**：仅需利用已有的训练回合回报，无需访问其他智能体动作或额外通信，完全去中心化。
- **泛化性**：可扩展到部分可观测设置（Dec-POMDP），在实验中验证了有效性。
- **实验设计全面**：从简单博弈到复杂多智能体对抗，对比多种基线，并进行了充分的消融分析和超参数敏感性研究。
- **可重复性**：提供了源代码和详细超参数（附录C.3），且遵循 PyMARL 框架。

---

### 8. 不足与局限
- **回报空间覆盖不全**：在复杂任务早期，低回报区域占主导，导致 ϕᵢ 无法正确估计最优动作。虽引入 Qᵢ_S 缓解，但在 SMAC 部分地图上仍不如 CTDE 方法（QMIX/VDN），也说明当前方法可能无法充分利用回报空间。
- **手动离散化回报区间**：依赖事先设定的最大最小回报边界和区间数量 m，适应性和鲁棒性有限。
- **仅支持回合间上下文切换**：假设策略仅在回合间更新（Case 2），对于回合内策略频繁切换的场景（Case 1）未涉及，作者在讨论中承认这是未来工作。
- **计算复杂度**：当 m 很大时，计算 max_{c_κ} 需枚举所有上下文，可能导致复杂度增加（作者提出可用交叉熵方法近似，但未实验验证）。
- **部分地图上优势不明显**：在 2s3z、3s_vs_5z、2s_vs_1sc 上与 IQL 相近，说明这些任务中非平稳性和相对过泛化较轻，RAC 的额外建模收益有限。
- **未与最新去中心化方法（如 MA2QL）对比**：文中仅在相关工作中提及 MA2QL，但未在实验部分比较，可能遗漏近期强有力的基线。

（完）
