---
title: "DISCOVER: Automated Curricula for Sparse-Reward Reinforcement Learning"
title_zh: DISCOVER：面向稀疏奖励强化学习的自动课程
authors: "Leander Diaz-Bone, Marco Bagatella, Jonas Hübotter, Andreas Krause"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=guZBnsKPsw"
tags: ["query:graph-part"]
score: 4.0
evidence: 稀疏奖励强化学习的自动课程生成
tldr: 该论文提出自动课程学习方法DISCOVER，通过从已有任务中提取方向感来引导探索，专门针对稀疏奖励强化学习中的高效探索难题，解决了当前方法在复杂高维任务中的可扩展性问题。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1306, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 884, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1429, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 600, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 602, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 664, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1259, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 673, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1460, \"height\": 996, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1462, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 568, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1433, \"height\": 1196, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1432, \"height\": 690, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guzbnskpsw/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1466, \"height\": 516, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-guzbnskpsw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-guzbnskpsw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 597, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-guzbnskpsw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1192, \"height\": 619, \"label\": \"Table\"}]"
motivation: 稀疏奖励强化学习在解决复杂任务时面临探索效率低下的问题，现有工作缺乏针对目标相关任务的引导机制。
method: 提出自动课程生成框架，从现有强化学习经验中提取方向信号，为智能体构建逐步递增的关联任务序列。
result: 在多个稀疏奖励基准任务上取得了更高效的探索和更好的最终性能。
conclusion: 该工作为稀疏奖励RL提供了一种有效的自动课程机制，有望加速智能体的自主能力提升。
---

## Abstract
Sparse-reward reinforcement learning (RL) can model a wide range of highly complex tasks.
Solving sparse-reward tasks is RL's core premise — requiring efficient exploration coupled with long-horizon credit assignment — and overcoming these challenges is key for building self-improving agents with superhuman ability.
We argue that solving complex and high-dimensional tasks requires solving simpler tasks that are *relevant* to the target task.
In contrast, most prior work designs strategies for selecting exploratory tasks with the objective of solving *any* task, making exploration of challenging high-dimensional, long-horizon tasks intractable.
We find that the sense of direction, necessary for effective exploration, can be extracted from existing reinforcement learning algorithms, without needing any prior information.
Based on this finding, we propose a method for _**di**rected **s**parse-reward goal-**co**nditioned **ve**ry long-horizon **R**L_ (DISCOVER), which selects exploratory goals in the direction of the target task.
We connect DISCOVER to principled exploration in bandits, formally bounding the time until the target task becomes achievable in terms of the agent's initial distance to the target, but independent of the volume of the space of all tasks.
Empirically, we perform a thorough evaluation in high-dimensional simulated environments. We find that the directed goal selection of DISCOVER solves exploration problems that are beyond the reach of prior state-of-the-art exploration methods in RL.

---

## 论文详细总结（自动生成）

好的，以下是基于您提供的论文PDF文本，生成的结构化、深入且客观的中文总结。

### 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：稀疏奖励强化学习（Sparse-Reward RL）在面对复杂、高维、长时域任务时，面临巨大的探索挑战。任务只有在被完成时才给出非零奖励，这使得智能体几乎无法通过随机探索获得任何有效信号，从而导致学习过程极其缓慢甚至失败。
- **研究动机**：现有的大量工作在探索策略上旨在“解决所有可能的子任务”，这在高维空间中是低效且不切实际的，因为任务空间会随维度指数级爆炸。论文的核心论点在于，解决复杂任务的关键在于解决一系列*与目标任务相关*的简单子任务，这种“方向感”或“任务相关性”是高效探索的关键。
- **整体含义**：论文旨在提出一种自动课程学习方法，通过从智能体自身的经验中提取“方向感”，引导其优先探索那些能够为最终目标任务提供技能积累的中间子任务，从而系统性地且高效地攻克稀疏奖励强化学习的难题。

### 2. 方法论：DISCOVER

- **核心思想**：提出DISCOVER方法，一种用于解决硬任务的自动课程学习策略。其核心是通过一个巧妙的、完全从数据中习得的“方向感”来设计和选择中间探索目标。该方法遵循三个基本原则：
    - **可达性**：选择的目标是目前智能体“踮脚能够到”的，保证探索能产出有效经验。
    - **新颖性**：选择的目标是智能体尚不确定、价值函数估计方差较大的区域，以获取最大化信息增益的经验。
    - **相关性**：选择的目标是与最终目标任务“关系更近”的，确保所学的技能能直接沿用到目标上。
- **关键技术细节**：
    - **DISCOVER目标函数**：每个探索回合，从已实现的目标集合中，根据一个优化目标选取下一个目标：
      `gt = arg max_g [ α_t * (V(s0, g) + β_t * σ(s0, g)) + (1-α_t) * (V(g, g*) + β_t * σ(g, g*)) ]`
        - `V(s0, g)`: 从初始状态 `s0` 到目标 `g` 的价值函数估计（> <font color="gray">衡量**可达性**</font>）。
        - `σ(s0, g)`: 该估计的不确定性（方差）（> <font color="gray">衡量**新颖性**</font>）。
        - `V(g, g*)`: 从目标 `g` 到最终目标 `g*` 的价值函数估计（> <font color="gray">衡量**相关性**</font>）。
        - `σ(g, g*)`: 该估计的不确定性。
        - `α_t`, `β_t`: 可调超参数（> <font color="gray">通过在线自适应决定权重</font>）。
    - **自动在线参数自适应**：通过动态调整 `α_t` 来维持一个固定的目标达成率 `p*`（论文设为50%）。如果达成率太低（任务太难），增加 `α_t` 以提高选择更简单目标的可能性；反之亦然。这避免了手动调参，并自动平衡探索和利用。
    - **不确定性估计**：通过训练一个价值函数集成（Ensemble of Critics），将集成的均值作为 `V`，方差作为 `σ²`，来获取模型的不确定性。
    - **与探索-利用的关联**：方法本质上是将经典的Upper Confidence Bound (UCB) 探索策略应用到了目标选择这一更高层面的决策上。利用部分由相关性和可达性项驱动，探索部分由不确定性项驱动。

### 3. 实验设计

- **场景和环境**：
    - **点迷宫 (Point Maze)**：从2维到6维的、带有随机生成路径的迷宫，用于验证方法在高维搜索空间中的可扩展性。
    - **蚂蚁迷宫 (Ant Maze)**：高维（27维状态、8维动作）的四足机器人导航任务，包含有/无墙壁遮挡的简单和困难模式。
    - **机械臂 (Arm)**：高维（23维状态、5维动作）的机器人操作任务，需将方块移动到指定位置，包含有/无障碍物的简单和困难模式。
- **基准方法 (Benchmark)**：
    - **HER (Hindsight Experience Replay)**：始终选择最终目标作为探索目标，是经典但简单的基线。
    - **DISCERN (Uniform)**：从已实现的目标状态中均匀采样。
    - **MEGA (Maximum Entropy Gain Achievement)**：强调**可达性+新颖性**，选择当前模型最不确定的目标。
    - **Achievability + Novelty**：论文消融实验中去除“相关性”项的变体。
    - **标准RL算法**：如TD3、SAC、RND（随机网络蒸馏）、MaxInfoRL等，以证明稀疏奖励场景下，专门的课程和子目标选择策略的必要性。
- **对比分析方式**：全面对比在不同环境的简单/困难变体下的成功率曲线（Sample Efficiency）。此外，还对目标选择策略的行为（如选择位置的可视化）进行了定性分析。

### 4. 资源与算力

- 实验在单块 NVIDIA GeForce RTX 2080 Ti GPU 上运行。
- 最长单个实验约耗时 **50 小时**。
- 要复现所有实验（约800次运行），总计估算耗时约 **8000 个GPU小时**。
- 论文开源了代码，并提供了详细的计算资源信息，确保了可复现性。

### 5. 实验数量与充分性

- **实验数量**：非常充分。报告了10个不同随机种子的平均值和标准误差，覆盖了3个主要场景变体的全面对比。
- **充分性**：实验设计非常全面和公平。
    - **多维度对比**：对比了基于目标选择的课程方法（HER、DISCERN、MEGA）和标准RL方法。
    - **消融实验**：仔细对方法的每个核心组件（可达性、新颖性、相关性）进行了消融分析（如“Achievability + Novelty”对比完整版本）。
    - **高维泛化性**：在点迷宫中从2维到6维的系统性实验，有力证明了DISCOVER相比基线在维度上的显著韧性（基线在高维完全失败）。
    - **鲁棒性分析**：在方向估计中加入噪声，测试了方向感即使在有偏差的情况下也足够有用。
    - **超参数分析**：分析了集合大小对性能的影响，以及参数自适应策略的 `p*` 选择。
    - **可视化分析**：直观展示了不同策略在蚂蚁迷宫中的探索行为，以解释性能提升的原因。
- **结论**：实验设置非常严谨、全面，结果令人信服。

### 6. 主要结论与发现

1.  **显著超越SOTA**：DISCOVER在全部三个环境及其难点配置中，均显著且一致地优于所有基线方法，尤其是在高维和复杂障碍物场景中。
2.  **方向感是关键**：实验明确表明，结合“相关性”的引导是提升性能的核心。缺少相关性（即“Achievability + Novelty”策略）的变体在复杂任务中性能骤降。
3.  **有效应对维度灾难**：在点迷宫任务中，当维度增加到3以上时，所有无方向或无课程引导的基线方法均无法成功，而DISCOVER成功扩展到了6维。其关键优势在于，搜索空间被限制在目标附近的一维“管状”区域，而非指数增长的全空间。
4.  **自举式学习**：DISCOVER展示了“自举”（Bootstrapping）的能力。早期探索的价值函数虽不完美，但可以提供有意义的关于“方向”的弱信号，引导后续探索不断改进方向估计，形成正向循环。
5.  **子目标选择 > 单纯奖赏塑造**：标准RL探索方法（如RND）通过在每一步奖励中添加“好奇心”来引导探索，但仍需要随机探索找到奖励。DISCOVER通过构建和选择具体的子目标，实现了在线搜索之外的“深度探索”，比这些方法更有效。

### 7. 优点（方法或实验设计）

- **理论严谨性**：将方法连接到线性臂的UCB理论，并给出了一个关于目标可达时间的界。这个界**独立于整个任务空间体积**，只取决于从初始点到目标点的初始距离，这对于高维问题是一个重要的突破性理论贡献。它解释了为什么方法能克服维度灾难。
- **“相关性”概念的提出与实现精美**：简单地将“相关性”定义为从子目标到最终目标的价值函数V(g,g*)，并通过价值函数集成网络实现，非常灵巧。它完全从数据中自主学习“方向感”，无需任何外部知识或预定义度量。
- **在线自适应机制**：通过动态调整参数来稳定维持50%的目标成功率，使得方法在不同难度的场景下都能保持稳定的性能，避免了复杂的手动调参。
- **全面的实验验证与消融**：系统性地对比了多种基线，还对方法的每个核心组成部分（可达性、新颖性、相关性）、超参数、集合大小等进行了消融，清晰地展示了每个元素的具体贡献，实验设计非常硬核。
- **实验的开放性与可复现性**：提供了开源代码，并详细说明了计算资源与超参数，增强了研究的公信力。

### 8. 不足与局限

- **对价值函数泛化的依赖**：该方法假设价值函数既能衡量“可达性”，也能一定程度上泛化到未访问过的状态来评估“相关性”和“新颖性”。如果神经网络的泛化能力太差，或者训练过程中价值估计波动太大（特别是早期），方法可能失效。
- **计算开销**：训练一个价值函数集成（论文中大小为6）增加了计算资源的开销。这在大规模模型（如基于大语言模型的应用）中可能成为瓶颈。
- **理论假设简化**：文中的理论分析基于“价值函数为线性”等强假设。虽然在实践中有效，但这与实际应用中大规模神经网络的非线性、非平稳训练过程仍有差距，理论结果的直接适用性有限（论文自身也承认了这一点）。
- **目标选择方式的局限**：目前的目标选择是从**已实现目标集**中**选择**，而非**生成**。这意味着方法的探索上限受限于能否首次随机构建出某个关键状态的路径（尽管方法会通过“新颖性”鼓励探索新区域，然后将其纳入选择池）。对于环境状态空间特别巨大且高度离散的情况，可能会遇到瓶颈。
- **实验环境覆盖范围**：尽管实验做得很好，但主要集中在仿真导航和操作任务。未来可考虑将其推广到更复杂、更具组合性的任务（如数学推理或LLM编程），以检验其在统一目标上的潜力。
- **缺乏对元学习/跨任务迁移的讨论**：论文中的每个目标任务是独立的。虽然可将方向作为先验信息注入，但并未探讨如何将学会探索目标任务的技能或价值函数重用到全新的目标任务上。

（完）
