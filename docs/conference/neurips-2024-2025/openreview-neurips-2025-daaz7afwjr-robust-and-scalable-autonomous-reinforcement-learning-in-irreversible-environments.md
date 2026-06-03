---
title: Robust and Scalable Autonomous Reinforcement Learning in Irreversible Environments
title_zh: 不可逆环境中鲁棒且可扩展的自主强化学习
authors: Sang-Hyun Lee
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dAAz7afWJR"
tags: ["query:graph-part"]
score: 9.0
evidence: 无需任务特定知识、鲁棒不可逆状态的自主强化学习算法
tldr: 该文针对自主强化学习中需要人工重置和任务特定知识的问题，提出鲁棒可扩展的自主RL算法RSA。RSA通过联合训练前向策略和重置策略，并利用分布鲁棒方法处理多样初始和目标状态，同时自动避免不可逆状态。在多个基准任务上，RSA大幅减少人工干预并提高了训练效率。该工作推动了强化学习向真实自主环境的应用。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-daaz7afwjr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1369, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-daaz7afwjr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1361, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-daaz7afwjr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-daaz7afwjr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1435, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-daaz7afwjr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1450, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-daaz7afwjr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1451, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-daaz7afwjr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 787, \"height\": 347, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-daaz7afwjr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 288, \"label\": \"Table\"}]"
motivation: 自主强化学习需要大量人工重置且依赖任务特定知识。
method: 提出RSA算法，联合训练前向和重置策略，并用分布鲁棒方法处理多样性。
result: 在多种任务中显著降低人工干预并提升训练效率。
conclusion: 实现了无需任务知识的鲁棒自主强化学习框架。
---

## Abstract
Reinforcement learning (RL) typically assumes repetitive resets to provide an agent with diverse and unbiased experiences. These resets require significant human intervention and result in poor training efficiency in real-world settings. Autonomous RL (ARL) addresses this challenge by jointly training forward and reset policies. While recent ARL algorithms have shown promise in reducing human intervention, they assume narrow support over the distributions of initial or goal states and rely on task-specific knowledge to identify irreversible states. In this paper, we propose a robust and scalable ARL algorithm, called RSA, that enables an agent to handle diverse initial and goal states and to avoid irreversible states without task-specific knowledge. RSA generates a curriculum by identifying informative states based on the learning progress of an agent. We hypothesize that informative states are neither overly difficult nor trivially easy for the agent being trained. To detect and avoid irreversible states without task-specific knowledge, RSA encodes the behaviors exhibited in those states rather than the states themselves. Experimental results demonstrate that RSA outperforms existing ARL algorithms with fewer manual resets in both reversible and irreversible environments.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：传统强化学习（RL）依赖每轮 episode 结束后的人工重置来提供多样化经验，这在实际机器人任务中导致高昂的人力成本与低下的训练效率。自主强化学习（ARL）通过同时训练前向策略和重置策略来减少人工干预，但现有 ARL 方法存在两个关键缺陷：
  - 假设初始状态或目标状态分布狭窄，无法应对真实场景中的多样状态。
  - 依赖任务特定知识（如重置奖励函数或可逆性标签）才能识别不可逆状态（如机器人损坏、物体掉落等），而这些知识在实践中往往不可获取。
- **动机**：设计一种鲁棒且可扩展的 ARL 算法，使其能在无需任务特定知识的情况下，自动适应多样的初始和目标状态，并自主检测和避免不可逆状态，从而显著降低人工干预，提升在真实环境中的实用性。

#### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：
  - **基于学习进度的课程生成**：识别“有信息量”的初始和目标状态——这些状态对当前智能体既不过于困难也不过于简单，从而引导智能体循序渐近地探索。
  - **基于行为编码的不可逆状态检测**：利用后继特征（Successor Features, SFs）编码重置策略下的行为模式，而不是直接建模状态本身。因为不可逆状态的任务特定特征各异，但行为模式具有共性：智能体在此类状态下失去对目标相关特征的控制。
- **关键技术细节**：
  - **状态信息估计器** \(I(s,g)\)：估计从状态 \(s\) 出发，在当前前向策略下能够到达目标 \(g\) 的概率。通过自监督方式从前向 rollouts 中提取标签：成功 rollouts 为正例，失败为负例，损失函数为二分类交叉熵。
  - **目标状态选择**：在第 \(k\) 次迭代，从之前遇到的且满足 \(\lambda_1 \leq \mathbb{E}_{s \sim B_r}[I(s, g)] \leq \lambda_2\) 的目标集合中均匀采样一个目标状态。
  - **初始状态发现**：激活重置策略，直到当前状态满足 \(\lambda_1 \leq I(s, g_k) \leq \lambda_2\)，此时将该状态设为初始状态，切换至前向策略。
  - **失败处理**：若前向 episode 未能达到目标，则将最终状态设为下一次迭代的目标（类似 HER，但跨迭代复用）。
  - **不可逆状态检测**：训练重置策略的 SFs \(\psi^{\pi_r}(s,a)\)，特征定义为相邻时刻目标相关特征的差分的范数。若 \(\psi^{\pi_r}(s,a) \leq \lambda_3\)，则判定为不可逆状态。采用保守策略：提前终止前向 episode 并给予惩罚。
- **算法流程**（Algorithm 1）：
  1. 初始化前向和重置策略、两个 replay buffer、状态信息估计器 \(I\) 和 SFs \(\psi^{\pi_r}\)。
  2. 每次迭代：通过 \(I\) 获取信息量高的目标状态 → 执行重置策略直到进入信息量高的初始状态 → 执行前向策略，同时用 SFs 监测不可逆状态，若触发则提前终止 → 更新策略和估计器。

#### 3. 实验设计：数据集/场景、benchmark、对比方法
- **环境**：Gymnasium-Robotics 提供的 6 个任务：
  - 可逆环境：PointIMaze, AntOpen, HandReach
  - 不可逆环境：PointIMaze-Trap, AntOpen-Trap, HandManipulate（含陷阱或物体掉落等不可逆事件）
- **对比方法**：
  - **LNT**（Eysenbach et al., 2018）：使用重置奖励函数检测不可逆状态，假设狭窄初始状态分布。
  - **R3L**（Zhu et al., 2020）：生成多样化初始状态，但不能处理不可逆状态。
  - **LNT-MG** 和 **R3L-MG**：分别为 LNT 和 R3L 的变体，通过随机采样目标使其适应多目标场景。
- **评价指标**：成功率（success rate）和手动重置次数（number of manual resets）。
- **公平性**：所有方法使用相同 episode 集合，初始和目标状态多样。

#### 4. 资源与算力
- 论文在附录 C 中提供了计算资源信息：实验使用单台机器，配备 Intel Core i9-10900K CPU 和 **NVIDIA RTX 3090 GPU**（24 GB 显存）。未明确说明每次训练的具体时长，但代码已在补充材料中开源，可复现。

#### 5. 实验数量与充分性
- **实验数量**：
  - 每个任务在 5 个随机种子下运行，报告均值和标准差。
  - 消融实验：在 HandReach 上对比 RSA 与 **RSA w/o SIE**（无状态信息估计器）；在 HandManipulate 上对比 RSA 与 **RSA w/o SFs**（无后继特征检测不可逆状态）。
  - 可视化分析：展示了信息量初始状态和目标状态集合随训练进度的变化。
- **充分性评价**：实验覆盖了可逆和不可逆环境、不同难度（导航与操作）、多种基线。消融实验验证了关键组件的作用。可视化直观展示了课程生成过程。总体设计较为充分、客观、公平。

#### 6. 论文的主要结论与发现
- RSA 能基于智能体的学习进度自动生成课程，自适应地调整初始和目标状态的难度，从而以更少的手动重置实现更好的性能。
- 利用后继特征编码行为模式，RSA 可在无需任务特定知识（如重置奖励或可逆性标签）的情况下准确检测并避免不可逆状态。
- 在可逆和不可逆的导航、操作任务中，RSA 的成功率均高于 LNT、R3L 及其多目标变体，且手动重置次数显著减少（在可逆环境中甚至无需手动重置）。
- 消融实验表明：状态信息估计器（SIE）和后继特征（SFs）对性能提升均有关键贡献，缺失任何一方都会导致性能下降或手动重置增加。

#### 7. 优点
- **无需任务特定知识**：检测不可逆状态时不需要重置奖励函数或可逆性标签，仅依靠行为编码，增强了实用性和通用性。
- **处理多样状态分布**：通过基于学习进度的课程，使智能体能够自适应地探索越来越难的初始和目标状态，避免了因分布狭窄导致的次优性能。
- **算法可扩展**：与任何探索算法兼容（实验中采用 RND），且后继特征的构建可结合更先进的表示学习。
- **方法新颖**：首次将后继特征用于识别不可逆状态的行为模式，利用了跨任务共有的行为丧失控制特征。

#### 8. 不足与局限
- **随机重置行为效率低**：使用随机策略发现信息量初始状态，在复杂环境中可能不够高效，未来可尝试结构化探索。
- **预定义特征依赖**：后继特征依赖于手工定义的目标相关特征，学习了更优的表示可能进一步提升性能。
- **滞后检测**：无法在进入不可逆状态之前预防（SFs 需要训练后才能捕捉行为模式），这在前训练初期存在风险。
- **自监督标签的准确性**：状态信息估计器完全依赖前向 rollouts 的成功/失败标签，在探索初期、智能体能力不足时可能产生不准确的可达概率估计。
- **实验环境有限**：仅评估了仿真环境中的导航和操作任务，未涉及真实机器人或更复杂场景；且不可逆状态的种类较少（陷阱、掉落），通用性有待进一步验证。

（完）
