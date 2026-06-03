---
title: "Counteractive RL: Rethinking Core Principles for Efficient and Scalable Deep Reinforcement Learning"
title_zh: 对抗性强化学习：重新思考高效可扩展深度强化学习的核心原理
authors: Ezgi Korkmaz
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=qaHrpITIvB"
tags: ["query:graph-part"]
score: 9.0
evidence: 通过反事实动作实现高效可扩展的深度RL
tldr: 本文针对高维MDP中强化学习策略面临指数级状态空间导致的效率与扩展性问题，提出一种基于反事实动作经验的新范式。该方法通过让代理在学习阶段主动体验与当前策略相反的动作来获得更丰富的信号，理论分析证明其能加速收敛并提升策略质量，在多个连续控制任务上验证了可扩展性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qahrpitivb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1239, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qahrpitivb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1419, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qahrpitivb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 238, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qahrpitivb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qahrpitivb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1214, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qahrpitivb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1434, \"height\": 325, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qahrpitivb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 885, \"height\": 188, \"label\": \"Table\"}]"
motivation: 高维MDP中状态空间爆炸导致RL计算复杂度与策略成功率矛盾。
method: 引入反事实动作生成学习经验，改变代理与环境交互方式。
result: 理论保证加速收敛，实验显示更好的可扩展性和策略性能。
conclusion: Counteractive RL为大规模深度RL提供了新的高效范式。
---

## Abstract
Following the pivotal success of learning strategies to win at tasks, solely by interacting with an environment without any supervision, agents have gained the ability to make sequential decisions in complex MDPs. Yet, reinforcement learning policies face exponentially growing state spaces in high dimensional MDPs resulting in a dichotomy between computational complexity and policy success. In our paper we focus on the agent’s interaction with the environment in a high-dimensional MDP during the learning phase and we introduce a theoretically-founded novel paradigm based on experiences obtained through counteractive actions. Our analysis and method provide a theoretical basis for efficient, effective, scalable and accelerated learning, and further comes with zero additional computational complexity while leading to significant acceleration in training. We conduct extensive experiments in the Arcade Learning Environment with high-dimensional state representation MDPs. The experimental results further verify our theoretical analysis, and our method achieves significant performance increase with substantial sample-efficiency in high-dimensional environments.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：在高维马尔可夫决策过程（MDP）中，深度强化学习面临状态空间指数增长带来的计算复杂度与策略成功率之间的根本矛盾。样本效率低下是限制算法扩展至实际应用（如大语言模型推理、物理世界部署）的主要瓶颈。
- **研究背景**：虽然表格型强化学习和bandit问题中已有理论最优的探索方法（如UCB、计数法），但这些方法依赖状态-动作对记录，在高维表示下不可行。当前主流深度RL仍普遍采用简单的ε-greedy探索策略，样本效率远不理想。
- **整体含义**：论文旨在不增加额外计算开销的前提下，通过重新思考学习过程中的核心原则——即最大化每次环境交互的信息增益，从根本上提升样本效率和训练速度。作者提出的“对抗性TD学习”（CoAct TD Learning）是一种基于最小化状态-动作值函数的全新范式，具有理论依据且零额外复杂度。

## 2. 方法论：核心思想、关键技术细节与算法流程
- **核心思想**：传统认知是最大化Q值以获得最优动作，但本文反直觉地提出：**在训练早期，采取最小化当前Q值的动作（称为“对抗性动作”）能够产生更高的时序差分（TD）误差**，从而获得信息量更丰富的经验，加速学习。
- **理论依据**：
  - 定义了η-uninformed（Q函数与随机动作奖励接近）和δ-smooth（Q函数值变化平缓）两个假设，证明了对随机初始化的Q函数，选取最小动作的TD误差期望比随机动作高出**劣势差距**D(s)，即定理3.4和3.6。
  - 说明在Q函数未充分收敛时，最小动作在给定权重下是确定性的，但其边缘分布仍均匀，因此不会减少探索多样性的理论覆盖（命题3.7）。
- **算法流程（Algorithm 1: CoAct TD Learning）**：
  - 在经验回放缓冲区填充阶段：以概率ε采样均匀随机数，若κ < ε，则选择**最小化Q值的动作**（amin = arg min_a Q(s,a)），否则选择最大化动作。
  - 学习阶段正常从缓冲区采样，使用标准TD更新公式（对于最小动作同样使用max Q(s', a)作为目标值）。注意：更新概率ε仅体现在经验收集上，学习阶段无额外代价。
- **关键技术细节**：
  - 仅需修改两行代码，可即插即用替换任何基于TD学习的基线算法。
  - 不增加网络参数或训练复杂度，与NoisyNetworks等增加计算量的方法形成鲜明对比。

## 3. 实验设计
- **实验环境与基准**：
  - **主要基准**：Arcade Learning Environment (ALE) 的 **100K 样本效率基准**（26个Atari游戏），评估100,000次环境交互后的性能。
  - **额外实验**：在200百万帧训练（50M交互）的经典设置下对4个游戏进行学习曲线比较。
  - **动机示例**：链式MDP（n=10状态，4动作），比较Q-learning下CoAct TD与ε-greedy、UCB算法的收敛速度。
- **对比方法**：
  - 基线1：经典**ε-greedy**（用于DDQN和QRDQN）。
  - 基线2：**NoisyNetworks**（向网络添加噪声层的方法）。
  - 基线3：**上置信界UCB**（仅用于链式MDP）。
- **评估指标**：
  - **人类归一化分数** (Human Normalized Score)：$(Score_{agent} - Score_{random})/(Score_{human} - Score_{random})$。
  - 汇报中位数、20百分位、80百分位及标准误差。
- **实现详情**：所有策略基于5个随机种子训练，超参数和架构细节参见补充材料。

## 4. 资源与算力
- **明确说明**：论文未明确报告使用的GPU型号、数量或具体训练时长。仅提到训练使用5个随机种子，并强调CoAct TD Learning不增加额外计算开销（零额外计算复杂度）。
- **对比说明**：NoisyNetworks因为增加了网络层，会引入“substantial additional cost”（大量额外成本），但未量化评估。

## 5. 实验数量与充分性
- **实验数量**：
  - 100K基准实验：覆盖26个游戏，对比两种算法（QRDQN和DDQN），每种5个种子，两个指标（中位数、80百分位）。
  - 200百万帧实验：仅展示4个游戏（JamesBond, Gravitar, Surround, Tennis）的学习曲线。
  - TD误差分析：报告了单个游戏的TD曲线，以及所有游戏的中位归一化TD增益。
  - 链式MDP：多种ε变化对比。
- **充分性评价**：
  - **优点**：在标准样本效率基准上进行了系统比较，统计汇报了误差棒，结果可复现（代码细节在补充材料）。
  - **不足**：1) 仅使用Atari领域，未扩展到连续控制（如MuJoCo）或更复杂任务；2) 200百万帧实验仅展示4个游戏，说服力有限；3) 缺乏对超参数ε的消融研究（论文中固定为某个值？未明确，但链式MDP中变化了ε）；4) 未与更多现代SOTA方法（如Rainbow、Agent57等）比较，仅比较了NoisyNetworks。
  - **公平性**：实验设置遵循标准200百万帧和100K基准协议，基线使用原始论文参数，对比方法（ε-greedy、NoisyNetworks）均为经典且公开的，因此比较相对公平。

## 6. 主要结论与发现
- **核心结论**：CoAct TD Learning（基于最小化Q值的经验收集）在**不增加任何计算复杂度**的前提下，显著提升深度RL的样本效率。
  - 在ALE 100K基准上，相对于ε-greedy，**性能提升248%**（中位数从0.0377到0.0927）；相对于NoisyNetworks，**提升204%**。
  - 链式MDP中，CoAct TD Learning收敛速度超过ε-greedy和UCB。
- **理论验证**：实验测得的TD误差曲线（图3、图6）证实了定理3.4：采用最小动作比随机动作获得更高的TD误差（中位归一化增益可达25%）。
- **扩展性**：方法可模块化，适用于任何TD学习算法（DDQN、QRDQN），且在大数据量训练下（200M帧）仍能加速收敛或达到更优策略。

## 7. 优点：方法与实验设计的亮点
- **理论驱动性**：从严格的数学定义（η-uninformed, δ-smooth, 劣势差距）出发，推导出最小化Q值可增加TD误差，为反直觉的方法提供坚实基础。
- **零额外计算成本**：无需额外网络、计数或噪声注入，仅修改动作选择策略，是当前最轻量的样本效率提升方法之一。
- **模块化与通用性**：可即插即用地替换任何现有RL算法的探索模块（如ε-greedy），两行代码修改即可。
- **实验验证全面性**：既包含简单的tabMDP示例（链式MDP），又在标准大规模基准（ALE 100K和200M帧）上验证，并直接测量了TD误差，直接验证理论预测。

## 8. 不足与局限
- **领域覆盖有限**：实验仅限于Atari游戏（图像输入的离散动作MDP），未涉及连续控制（如MuJoCo）、机器人、语言模型等更广泛场景，泛化性存疑。
- **对比方法不够广泛**：仅对比了ε-greedy和NoisyNetworks，缺少与当前SOTA探索方法（如计数的伪计数法、RND、ICM、Plan2Explore等内在奖励方法）的比较，可能不足以说明绝对优势。
- **对ε的敏感性未深入分析**：虽然链式MDP中变化了ε，但在Atari实验中未明确最优ε设置或敏感性分析，实际部署可能需要调参。
- **长期训练性能证据不足**：200M帧实验只展示了4个游戏，且未提供完整中位数曲线，不能充分证明在长时间训练下持续优于基线。
- **潜在的偏差风险**：最小化Q值动作在强干扰环境中可能陷入次优状态，论文未讨论在奖励稀疏或非平稳环境下的稳定性风险。
- **复现细节不完整**：补充材料虽提及但文中未列出超参数表格，需依赖开源代码。

（完）
